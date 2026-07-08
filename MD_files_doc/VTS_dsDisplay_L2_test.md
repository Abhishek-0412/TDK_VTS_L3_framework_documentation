## TestScript Name
VTS_dsDisplay_L2_test

## TestScript ID
VTS_Test_18

## Table of Contents

1. [Objective](#objective)
2. [Pre-conditions](#pre-conditions)
3. [Test Cases](#test-cases)
   - [TestDefaultAspectRatio_src](#testdefaultaspectratio_src)
   - [SetAndGetAVIContentType_src](#setandgetavicontenttype_src)
4. [Post-conditions](#post-conditions)
5. [Test Attributes](#test-attributes)

---

## Objective

This script executes VTS L2 (Level 2) test cases for the Device Settings Display HAL module (`dsDisplay`). L2 tests validate end-to-end workflows that exercise sequences of HAL APIs to verify combined functional behaviour on source platforms. No external stimulus is required; the tests rely on the HAL implementation and the profile configuration. The binary used is `hal_test_dshal`, invoked with the profile `Source_4K_Display.yaml`.

---

## Pre-conditions

### Pre-condition 1: VTS Package Installed

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Read VTS Base Path | Check the device config file for `VTS_BASE_PATH`. If set (e.g., `VTS_BASE_PATH = /opt/VTS_Package/`), that path is used as the base; otherwise the default `/VTS_Package/` is used | Base path is determined |
| Verify Binary and Config | Confirm the module sub-directory `device_settings/` exists under the base path and contains the required files | `<VTS_BASE_PATH>/device_settings/` exists and contains the `hal_test_dshal` binary and `Source_4K_Display.yaml` config file |

### Pre-condition 2: SSH Connectivity

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Read SSH Configuration | Read SSH connection parameters from the device config file: `SSH_PORT` (default: `22`), `SSH_METHOD` (e.g., `directSSH`), `SSH_USERNAME` (e.g., `root`), `SSH_PASSWORD` (`None` if no password required) | SSH parameters are available |
| Verify SSH Access | Establish an SSH session to the DUT using the configured parameters | SSH session is established successfully |

---

## Test Cases

<a id="testdefaultaspectratio_src"></a>
### TestCase Name
TestDefaultAspectRatio_src

### TestCase ID
dsDisplay L2-1

### TestCase Objective
Validate that the default display aspect ratio reported by the HAL is `dsVIDEO_ASPECT_RATIO_16x9` on source platforms.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handle for each valid port | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` for each port in the profile | `dsGetDisplay()` must return `dsERR_NONE` and a valid non-null handle |
| Get display aspect ratio | Invoke `dsGetDisplayAspectRatio(displayHandle, &aspectRatio)` | `dsGetDisplayAspectRatio()` must return `dsERR_NONE` and `aspectRatio` must equal `dsVIDEO_ASPECT_RATIO_16x9` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |

---

<a id="setandgetavicontenttype_src"></a>
### TestCase Name
SetAndGetAVIContentType_src

### TestCase ID
dsDisplay L2-2

### TestCase Objective
Validate that `dsSetAVIContentType()` and `dsGetAVIContentType()` work correctly in combination — that a value written can be read back with the same value on source platforms.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handle for each valid port | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` for each port in the profile | `dsGetDisplay()` must return `dsERR_NONE` and a valid handle |
| Get initial AVI content type | Invoke `dsGetAVIContentType(displayHandle, &initialContentType)` | `dsGetAVIContentType()` must return `dsERR_NONE` and `initialContentType` must equal `dsAVICONTENT_TYPE_NOT_SIGNALLED` |
| Set AVI content type to each valid value | Invoke `dsSetAVIContentType(displayHandle, contentType)` for each value from `dsAVICONTENT_TYPE_GRAPHICS` to `dsAVICONTENT_TYPE_MAX-1` | `dsSetAVIContentType()` must return `dsERR_NONE` |
| Verify AVI content type was set | Invoke `dsGetAVIContentType(displayHandle, &retrievedContentType)` after each set call | `dsGetAVIContentType()` must return `dsERR_NONE` and `retrievedContentType` must equal the value passed to `dsSetAVIContentType()` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |

---

## Post-conditions

1. The `hal_test_dshal` binary exits cleanly after completing all test cases in the `[L2 dsDisplay Source ]` suite.
2. The DS Display HAL module is terminated (via `dsDisplayTerm()`) at the end of each test case, restoring the uninitialized default state.

---

## Test Attributes

| Attribute | Value |
| --- | --- |
| Supported Models | Video_Accelerator, RPI-Client |
| Estimated Duration | 30 minutes |
| Priority | High |
| TDK Release Version | M134 |
