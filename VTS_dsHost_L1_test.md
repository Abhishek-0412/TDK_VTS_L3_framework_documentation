## TestScript Name
VTS_dsHost_L1_test

## TestScript ID
VTS_Test_03

## Table of Contents

1. [Objective](#objective)
2. [Pre-conditions](#pre-conditions)
3. [Test Cases](#test-cases)
   - [dsHostInit_L1_positive](#dshostinit_l1_positive)
   - [dsHostInit_L1_negative](#dshostinit_l1_negative)
   - [dsHostTerm_L1_positive](#dshostterm_l1_positive)
   - [dsHostTerm_L1_negative](#dshostterm_l1_negative)
   - [dsGetCPUTemperature_L1_positive](#dsgetcputemperature_l1_positive)
   - [dsGetSocIDFromSDK_L1_positive](#dsgetsocedfromsdk_l1_positive)
   - [dsGetSocIDFromSDK_L1_negative](#dsgetsocedfromsdk_l1_negative)
   - [dsGetCPUTemperature_L1_negative](#dsgetcputemperature_l1_negative)
   - [dsGetHostEDID_L1_positive](#dsgethostdid_l1_positive)
   - [dsGetHostEDID_L1_negative](#dsgethostdid_l1_negative)
4. [Post-conditions](#post-conditions)
5. [Test Attributes](#test-attributes)

---

## Objective

This script executes VTS L1 (Level 1) test cases for the Device Settings Host HAL module (`dsHost`). L1 tests validate individual HAL APIs in isolation — each test case calls a single API with valid or invalid parameters and verifies the correct return code is produced. No external stimulus is required; the tests rely solely on the HAL implementation and the profile configuration. The binary used is `hal_test_dshal`, invoked with the profile `Source_HostSettings.yaml`.

---

## Pre-conditions

### Pre-condition 1: VTS Package Installed

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Read VTS Base Path | Check the device config file for `VTS_BASE_PATH`. If set (e.g., `VTS_BASE_PATH = /opt/VTS_Package/`), that path is used as the base; otherwise the default `/VTS_Package/` is used | Base path is determined |
| Verify Binary and Config | Confirm the module sub-directory `device_settings/` exists under the base path and contains the required files | `<VTS_BASE_PATH>/device_settings/` exists and contains the `hal_test_dshal` binary and `Source_HostSettings.yaml` config file |

### Pre-condition 2: SSH Connectivity

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Read SSH Configuration | Read SSH connection parameters from the device config file: `SSH_PORT` (default: `22`), `SSH_METHOD` (e.g., `directSSH`), `SSH_USERNAME` (e.g., `root`), `SSH_PASSWORD` (`None` if no password required) | SSH parameters are available |
| Verify SSH Access | Establish an SSH session to the DUT using the configured parameters | SSH session is established successfully |

---

## Test Cases

<a id="dshostinit_l1_positive"></a>
### TestCase Name
dsHostInit_L1_positive

### TestCase ID
dsHost L1-1

### TestCase Objective
Validate that `dsHostInit()` successfully initializes the DS Host HAL module and that the module can be re-initialized after termination.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Host HAL module | Invoke `dsHostInit()` | `dsHostInit()` must return `dsERR_NONE` |
| Terminate the DS Host HAL module | Invoke `dsHostTerm()` | `dsHostTerm()` must return `dsERR_NONE` |
| Re-initialize the DS Host HAL module | Invoke `dsHostInit()` again | `dsHostInit()` must return `dsERR_NONE` |
| Re-terminate the DS Host HAL module | Invoke `dsHostTerm()` | `dsHostTerm()` must return `dsERR_NONE` |

---

<a id="dshostinit_l1_negative"></a>
### TestCase Name
dsHostInit_L1_negative

### TestCase ID
dsHost L1-2

### TestCase Objective
Validate that `dsHostInit()` returns the correct error code when called while the module is already initialized.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Host HAL module | Invoke `dsHostInit()` | `dsHostInit()` must return `dsERR_NONE` |
| Initialize again while already initialized | Invoke `dsHostInit()` again without calling `dsHostTerm()` | `dsHostInit()` must return `dsERR_ALREADY_INITIALIZED` |
| Terminate the DS Host HAL module | Invoke `dsHostTerm()` | `dsHostTerm()` must return `dsERR_NONE` |

---

<a id="dshostterm_l1_positive"></a>
### TestCase Name
dsHostTerm_L1_positive

### TestCase ID
dsHost L1-3

### TestCase Objective
Validate that `dsHostTerm()` successfully terminates the DS Host HAL module and the module can be re-initialized after termination.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Host HAL module | Invoke `dsHostInit()` | `dsHostInit()` must return `dsERR_NONE` |
| Terminate the DS Host HAL module | Invoke `dsHostTerm()` | `dsHostTerm()` must return `dsERR_NONE` |
| Re-initialize the DS Host HAL module | Invoke `dsHostInit()` | `dsHostInit()` must return `dsERR_NONE` |
| Re-terminate the DS Host HAL module | Invoke `dsHostTerm()` | `dsHostTerm()` must return `dsERR_NONE` |

---

<a id="dshostterm_l1_negative"></a>
### TestCase Name
dsHostTerm_L1_negative

### TestCase ID
dsHost L1-4

### TestCase Objective
Validate that `dsHostTerm()` returns the correct error code when called without prior initialization or after already being terminated.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Terminate the module without prior initialization | Invoke `dsHostTerm()` before calling `dsHostInit()` | `dsHostTerm()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the DS Host HAL module | Invoke `dsHostInit()` | `dsHostInit()` must return `dsERR_NONE` |
| Terminate the DS Host HAL module | Invoke `dsHostTerm()` | `dsHostTerm()` must return `dsERR_NONE` |
| Terminate again while module is already terminated | Invoke `dsHostTerm()` again | `dsHostTerm()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetcputemperature_l1_positive"></a>
### TestCase Name
dsGetCPUTemperature_L1_positive

### TestCase ID
dsHost L1-5

### TestCase Objective
Validate that `dsGetCPUTemperature()` successfully retrieves the current CPU temperature within a valid range.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Host HAL module | Invoke `dsHostInit()` | `dsHostInit()` must return `dsERR_NONE` |
| Get CPU temperature (first call) | Invoke `dsGetCPUTemperature(&cpuTemperature1)` | `dsGetCPUTemperature()` must return `dsERR_NONE` and `cpuTemperature1` must be a valid float value |
| Get CPU temperature (second call) | Invoke `dsGetCPUTemperature(&cpuTemperature2)` | `dsGetCPUTemperature()` must return `dsERR_NONE` and `cpuTemperature2` must be a valid float value |
| Terminate the DS Host HAL module | Invoke `dsHostTerm()` | `dsHostTerm()` must return `dsERR_NONE` |

---

<a id="dsgetsocedfromsdk_l1_positive"></a>
### TestCase Name
dsGetSocIDFromSDK_L1_positive

### TestCase ID
dsHost L1-6

### TestCase Objective
Validate that `dsGetSocIDFromSDK()` successfully retrieves the SoC ID from the SDK.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Host HAL module | Invoke `dsHostInit()` | `dsHostInit()` must return `dsERR_NONE` |
| Get SoC ID from SDK (first call) | Invoke `dsGetSocIDFromSDK(socID1)` | `dsGetSocIDFromSDK()` must return `dsERR_NONE` and `socID1` must be a non-empty string |
| Get SoC ID from SDK (second call) | Invoke `dsGetSocIDFromSDK(socID2)` | `dsGetSocIDFromSDK()` must return `dsERR_NONE` and `socID2` must match `socID1` |
| Terminate the DS Host HAL module | Invoke `dsHostTerm()` | `dsHostTerm()` must return `dsERR_NONE` |

---

<a id="dsgetsocedfromsdk_l1_negative"></a>
### TestCase Name
dsGetSocIDFromSDK_L1_negative

### TestCase ID
dsHost L1-7

### TestCase Objective
Validate that `dsGetSocIDFromSDK()` returns the correct error codes for invalid parameters and when called without initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get SoC ID without prior initialization | Invoke `dsGetSocIDFromSDK(socID)` before `dsHostInit()` | `dsGetSocIDFromSDK()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the DS Host HAL module | Invoke `dsHostInit()` | `dsHostInit()` must return `dsERR_NONE` |
| Get SoC ID with NULL output buffer | Invoke `dsGetSocIDFromSDK(NULL)` | `dsGetSocIDFromSDK()` must return `dsERR_INVALID_PARAM` |
| Terminate the DS Host HAL module | Invoke `dsHostTerm()` | `dsHostTerm()` must return `dsERR_NONE` |
| Get SoC ID after termination | Invoke `dsGetSocIDFromSDK(socID)` | `dsGetSocIDFromSDK()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetcputemperature_l1_negative"></a>
### TestCase Name
dsGetCPUTemperature_L1_negative

### TestCase ID
dsHost L1-8

### TestCase Objective
Validate that `dsGetCPUTemperature()` returns the correct error codes for invalid parameters and when called without initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get CPU temperature without prior initialization | Invoke `dsGetCPUTemperature(&temperature)` before `dsHostInit()` | `dsGetCPUTemperature()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the DS Host HAL module | Invoke `dsHostInit()` | `dsHostInit()` must return `dsERR_NONE` |
| Get CPU temperature with NULL output pointer | Invoke `dsGetCPUTemperature(NULL)` | `dsGetCPUTemperature()` must return `dsERR_INVALID_PARAM` |
| Terminate the DS Host HAL module | Invoke `dsHostTerm()` | `dsHostTerm()` must return `dsERR_NONE` |
| Get CPU temperature after termination | Invoke `dsGetCPUTemperature(&temperature)` | `dsGetCPUTemperature()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgethostdid_l1_positive"></a>
### TestCase Name
dsGetHostEDID_L1_positive

### TestCase ID
dsHost L1-9

### TestCase Objective
Validate that `dsGetHostEDID()` successfully retrieves the host EDID buffer and its length.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI (REFPLTV-2571).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Host HAL module | Invoke `dsHostInit()` | `dsHostInit()` must return `dsERR_NONE` |
| Get host EDID (first call) | Invoke `dsGetHostEDID(edid1, &length1)` | `dsGetHostEDID()` must return `dsERR_NONE` and return a non-null EDID buffer with a non-zero length |
| Get host EDID (second call) | Invoke `dsGetHostEDID(edid2, &length2)` | `dsGetHostEDID()` must return `dsERR_NONE` and results must match the first call |
| Terminate the DS Host HAL module | Invoke `dsHostTerm()` | `dsHostTerm()` must return `dsERR_NONE` |

---

<a id="dsgethostdid_l1_negative"></a>
### TestCase Name
dsGetHostEDID_L1_negative

### TestCase ID
dsHost L1-10

### TestCase Objective
Validate that `dsGetHostEDID()` returns the correct error codes for invalid parameters and when called without initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get host EDID without prior initialization | Invoke `dsGetHostEDID(edid, &length)` before `dsHostInit()` | `dsGetHostEDID()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the DS Host HAL module | Invoke `dsHostInit()` | `dsHostInit()` must return `dsERR_NONE` |
| Get host EDID with NULL EDID buffer | Invoke `dsGetHostEDID(NULL, &length)` | `dsGetHostEDID()` must return `dsERR_INVALID_PARAM` |
| Get host EDID with NULL length pointer | Invoke `dsGetHostEDID(edid, NULL)` | `dsGetHostEDID()` must return `dsERR_INVALID_PARAM` |
| Terminate the DS Host HAL module | Invoke `dsHostTerm()` | `dsHostTerm()` must return `dsERR_NONE` |
| Get host EDID after termination | Invoke `dsGetHostEDID(edid, &length)` | `dsGetHostEDID()` must return `dsERR_NOT_INITIALIZED` |

---

## Post-conditions

1. The `hal_test_dshal` binary exits cleanly after completing all test cases in the `[L1 dsHost]` suite.
2. The DS Host HAL module is terminated (via `dsHostTerm()`) at the end of each test case, restoring the uninitialized default state.

---

## Test Attributes

| Attribute | Value |
| --- | --- |
| Supported Models | Video_Accelerator, RPI-Client |
| Estimated Duration | 5 minutes |
| Priority | High |
| TDK Release Version | M134 |
