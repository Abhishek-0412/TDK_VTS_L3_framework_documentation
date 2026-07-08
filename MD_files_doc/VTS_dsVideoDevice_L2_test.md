## TestScript Name
VTS_dsVideoDevice_L2_test

## TestScript ID
VTS_Test_05

## Table of Contents

1. [Objective](#objective)
2. [Pre-conditions](#pre-conditions)
3. [Test Cases](#test-cases)
   - [GetHDRCapabilities](#gethdrcapabilities)
   - [GetSupportedVideoCodingFormats](#getsupportedvideocodingformats)
   - [SetAndGetDFC](#setandgetdfc)
   - [GetVideoCodecInfo](#getvideocodecinfo)
4. [Post-conditions](#post-conditions)
5. [Test Attributes](#test-attributes)

---

## Objective

This script executes VTS L2 (Level 2) test cases for the Device Settings Video Device HAL module (`dsVideoDevice`). L2 tests validate end-to-end workflows that exercise sequences of HAL APIs and compare results against the device profile configuration to verify functional correctness on source platforms. No external stimulus is required; the tests rely on the HAL implementation and the profile configuration. The binary used is `hal_test_dshal`, invoked with the profile `Source_VideoDevice.yaml`.

---

## Pre-conditions

### Pre-condition 1: VTS Package Installed

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Read VTS Base Path | Check the device config file for `VTS_BASE_PATH`. If set (e.g., `VTS_BASE_PATH = /opt/VTS_Package/`), that path is used as the base; otherwise the default `/VTS_Package/` is used | Base path is determined |
| Verify Binary and Config | Confirm the module sub-directory `device_settings/` exists under the base path and contains the required files | `<VTS_BASE_PATH>/device_settings/` exists and contains the `hal_test_dshal` binary and `Source_VideoDevice.yaml` config file |

### Pre-condition 2: SSH Connectivity

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Read SSH Configuration | Read SSH connection parameters from the device config file: `SSH_PORT` (default: `22`), `SSH_METHOD` (e.g., `directSSH`), `SSH_USERNAME` (e.g., `root`), `SSH_PASSWORD` (`None` if no password required) | SSH parameters are available |
| Verify SSH Access | Establish an SSH session to the DUT using the configured parameters | SSH session is established successfully |

---

## Test Cases

<a id="gethdrcapabilities"></a>
### TestCase Name
GetHDRCapabilities

### TestCase ID
dsVideoDevice L2-1

### TestCase Objective
Validate that `dsGetHDRCapabilities()` returns HDR capabilities matching the expected values from the device profile configuration.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle for each index | Invoke `dsGetVideoDevice(i, &handle)` for each valid index | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid non-null handle |
| Get HDR capabilities | Invoke `dsGetHDRCapabilities(handle, &capabilities)` | `dsGetHDRCapabilities()` must return `dsERR_NONE` and `capabilities` must equal `HDRCapabilities` from the profile |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="getsupportedvideocodingformats"></a>
### TestCase Name
GetSupportedVideoCodingFormats

### TestCase ID
dsVideoDevice L2-2

### TestCase Objective
Validate that `dsGetSupportedVideoCodingFormats()` returns supported video coding formats matching the expected values from the device profile configuration.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI (REFPLTV-2536).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle for each index | Invoke `dsGetVideoDevice(i, &handle)` for each valid index | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Get supported video coding formats | Invoke `dsGetSupportedVideoCodingFormats(handle, &supportedFormats)` | `dsGetSupportedVideoCodingFormats()` must return `dsERR_NONE` and `supportedFormats` must equal `SupportedVideoCodingFormats` from the profile |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="setandgetdfc"></a>
### TestCase Name
SetAndGetDFC

### TestCase ID
dsVideoDevice L2-3

### TestCase Objective
Validate that `dsSetDFC()` and `dsGetDFC()` work correctly together — that each DFC value written can be read back with the same value on source platforms.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI (REFPLTV-2577).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle for each index | Invoke `dsGetVideoDevice(i, &handle)` for each valid index | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Set DFC for each supported zoom mode | Invoke `dsSetDFC(handle, supportedDFCs[j])` for each supported DFC value from the profile | `dsSetDFC()` must return `dsERR_NONE` |
| Verify DFC was set | Invoke `dsGetDFC(handle, &dfcGet)` after each set call | `dsGetDFC()` must return `dsERR_NONE` and `dfcGet` must equal the DFC value passed to `dsSetDFC()` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="getvideocodecinfo"></a>
### TestCase Name
GetVideoCodecInfo

### TestCase ID
dsVideoDevice L2-4

### TestCase Objective
Validate that `dsGetVideoCodecInfo()` retrieves video codec information matching the expected values from the device profile configuration for each supported codec on source platforms.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI (REFPLTV-2536).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle for each index | Invoke `dsGetVideoDevice(i, &handle)` for each valid index | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Get video codec info for each supported codec | Invoke `dsGetVideoCodecInfo(handle, codec, &info)` for each supported codec in the profile | `dsGetVideoCodecInfo()` must return `dsERR_NONE` |
| Verify codec info | Compare `info.num_entries` and `info.entries->profile` against profile values | Retrieved codec information must match `num_codec_entries` and `profile` from the profile configuration |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

## Post-conditions

1. The `hal_test_dshal` binary exits cleanly after completing all test cases in the `[L2 dsVideoDevice - Source]` suite.
2. The DS Video Device HAL module is terminated (via `dsVideoDeviceTerm()`) at the end of each test case, restoring the uninitialized default state.

---

## Test Attributes

| Attribute | Value |
| --- | --- |
| Supported Models | Video_Accelerator, RPI-Client |
| Estimated Duration | 5 minutes |
| Priority | High |
| TDK Release Version | M134 |
