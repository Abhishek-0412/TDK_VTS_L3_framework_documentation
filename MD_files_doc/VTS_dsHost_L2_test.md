## TestScript Name
VTS_dsHost_L2_test

## TestScript ID
VTS_Test_07

## Table of Contents

1. [Objective](#objective)
2. [Pre-conditions](#pre-conditions)
3. [Test Cases](#test-cases)
   - [L2_GetCPUTemperature](#l2_getcputemperature)
   - [L2_GetAndVerifySocID](#l2_getandverifysocid)
4. [Post-conditions](#post-conditions)
5. [Test Attributes](#test-attributes)

---

## Objective

This script executes VTS L2 (Level 2) test cases for the Device Settings Host HAL module (`dsHost`). L2 tests validate end-to-end workflows that exercise sequences of HAL APIs and compare results against the device profile configuration to verify functional correctness on source platforms. No external stimulus is required; the tests rely on the HAL implementation and the profile configuration. The binary used is `hal_test_dshal`, invoked with the profile `Source_HostSettings.yaml`.

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

<a id="l2_getcputemperature"></a>
### TestCase Name
L2_GetCPUTemperature

### TestCase ID
dsHost L2-1

### TestCase Objective
Validate that `dsGetCPUTemperature()` returns a valid CPU temperature within the range specified in the device profile configuration.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Host HAL module | Invoke `dsHostInit()` | `dsHostInit()` must return `dsERR_NONE` |
| Get CPU temperature | Invoke `dsGetCPUTemperature(&cpuTemperature)` | `dsGetCPUTemperature()` must return `dsERR_NONE` and `cpuTemperature` must be within the range defined by `dsHost.cpuTemperature.0` (min) and `dsHost.cpuTemperature.1` (max) in the profile |
| Terminate the DS Host HAL module | Invoke `dsHostTerm()` | `dsHostTerm()` must return `dsERR_NONE` |

---

<a id="l2_getandverifysocid"></a>
### TestCase Name
L2_GetAndVerifySocID

### TestCase ID
dsHost L2-2

### TestCase Objective
Validate that `dsGetSocIDFromSDK()` returns the SoC ID string that matches the expected value defined in the device profile configuration.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Host HAL module | Invoke `dsHostInit()` | `dsHostInit()` must return `dsERR_NONE` |
| Get SoC ID from SDK | Invoke `dsGetSocIDFromSDK(socID)` | `dsGetSocIDFromSDK()` must return `dsERR_NONE` and `socID` must be a non-empty string |
| Verify SoC ID against profile | Compare `socID` with the value from `dsHost.socID` in the profile using string search | The retrieved `socID` must contain the expected profile SoC ID value |
| Terminate the DS Host HAL module | Invoke `dsHostTerm()` | `dsHostTerm()` must return `dsERR_NONE` |

---

## Post-conditions

1. The `hal_test_dshal` binary exits cleanly after completing all test cases in the `[L2 dsHost - Source]` suite.
2. The DS Host HAL module is terminated (via `dsHostTerm()`) at the end of each test case, restoring the uninitialized default state.

---

## Test Attributes

| Attribute | Value |
| --- | --- |
| Supported Models | Video_Accelerator, RPI-Client |
| Estimated Duration | 5 minutes |
| Priority | High |
| TDK Release Version | M134 |
