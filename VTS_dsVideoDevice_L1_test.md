## TestScript Name
VTS_dsVideoDevice_L1_test

## TestScript ID
VTS_Test_02

## Table of Contents

1. [Objective](#objective)
2. [Pre-conditions](#pre-conditions)
3. [Test Cases](#test-cases)
   - [dsVideoDeviceInit_positive](#dsvideoddeviceinit_positive)
   - [dsVideoDeviceTerm_positive](#dsvideodeviceterm_positive)
   - [dsGetVideoDevice_positive](#dsgetvideodevice_positive)
   - [dsSetDFC_positive](#dssetdfc_positive)
   - [dsGetHDRCaps_positive](#dsgethdrcaps_positive)
   - [dsGetSupportVidFormats_positive](#dsgetsupportvidformats_positive)
   - [dsGetVideoCodecInfo_positive](#dsgetvideocodecinfo_positive)
   - [dsSetFRFMode_positive](#dssetfrfmode_positive)
   - [dsGetFRFMode_positive](#dsgetfrfmode_positive)
   - [dsGetCurrDispFramerate_positive](#dsgetcurrdispframerate_positive)
   - [dsSetDisplayframerate_positive](#dssetdisplayframerate_positive)
   - [dsRegFrameratePreCB_positive](#dsregframerateprecb_positive)
   - [dsRegFrameratePostCB_positive](#dsregframeratepostcb_positive)
   - [dsVideoDeviceInit_negative](#dsvideodeviceinit_negative)
   - [dsVideoDeviceTerm_negative](#dsvideodeviceterm_negative)
   - [dsGetVideoDevice_negative](#dsgetvideodevice_negative)
   - [dsSetDFC_negative](#dssetdfc_negative)
   - [dsGetHDRCaps_negative](#dsgethdrcaps_negative)
   - [dsGetSupportVidFormats_negative](#dsgetsupportvidformats_negative)
   - [dsGetVideoCodecInfo_negative](#dsgetvideocodecinfo_negative)
   - [dsSetFRFMode_negative](#dssetfrfmode_negative)
   - [dsGetFRFMode_negative](#dsgetfrfmode_negative)
   - [dsGetCurrDispFramerate_negative](#dsgetcurrdispframerate_negative)
   - [dsSetDisplayframerate_negative](#dssetdisplayframerate_negative)
   - [dsRegFrameratePreCB_negative](#dsregframerateprecb_negative)
   - [dsRegFrameratePostCB_negative](#dsregframeratepostcb_negative)
   - [dsGetDFC_positive](#dsgetdfc_positive)
   - [dsForceDisableHDR_positive](#dsforceDisableHDR_positive)
   - [dsGetDFC_negative](#dsgetdfc_negative)
   - [dsForceDisableHDR_negative](#dsforceDisableHDR_negative)
4. [Post-conditions](#post-conditions)
5. [Test Attributes](#test-attributes)

---

## Objective

This script executes VTS L1 (Level 1) test cases for the Device Settings Video Device HAL module (`dsVideoDevice`). L1 tests validate individual HAL APIs in isolation — each test case calls a single API with valid or invalid parameters and verifies the correct return code is produced. No external stimulus is required; the tests rely solely on the HAL implementation and the profile configuration. The binary used is `hal_test_dshal`, invoked with the profile `Source_VideoDevice.yaml`.

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

<a id="dsvideoddeviceinit_positive"></a>
### TestCase Name
dsVideoDeviceInit_positive

### TestCase ID
dsVideoDevice L1-1

### TestCase Objective
Validate that `dsVideoDeviceInit()` successfully initializes all video devices and can be re-initialized after termination.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |
| Re-initialize all video devices | Invoke `dsVideoDeviceInit()` again | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Re-terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="dsvideodeviceterm_positive"></a>
### TestCase Name
dsVideoDeviceTerm_positive

### TestCase ID
dsVideoDevice L1-2

### TestCase Objective
Validate that `dsVideoDeviceTerm()` successfully de-initializes all video devices.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |
| Re-initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Re-terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="dsgetvideodevice_positive"></a>
### TestCase Name
dsGetVideoDevice_positive

### TestCase ID
dsVideoDevice L1-3

### TestCase Objective
Validate that `dsGetVideoDevice()` retrieves a valid handle for each video device index.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle for each index | Invoke `dsGetVideoDevice(i, &handle)` for all valid indices from the profile | `dsGetVideoDevice()` must return `dsERR_NONE` and `handle` must be a valid non-null value |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="dssetdfc_positive"></a>
### TestCase Name
dsSetDFC_positive

### TestCase ID
dsVideoDevice L1-4

### TestCase Objective
Validate that `dsSetDFC()` successfully sets the screen zoom (DFC) mode for all supported DFC values on source platforms.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI (REFPLTV-2577).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Set DFC mode for each supported zoom mode (source) | Invoke `dsSetDFC(handle, supportedDFC[j])` for each supported DFC value from the profile | `dsSetDFC()` must return `dsERR_NONE` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="dsgethdrcaps_positive"></a>
### TestCase Name
dsGetHDRCaps_positive

### TestCase ID
dsVideoDevice L1-5

### TestCase Objective
Validate that `dsGetHDRCapabilities()` retrieves HDR capabilities and they match the profile value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Get HDR capabilities | Invoke `dsGetHDRCapabilities(handle, &hdrCapabilities)` | `dsGetHDRCapabilities()` must return `dsERR_NONE` and `hdrCapabilities` must match the profile value |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="dsgetsupportvidformats_positive"></a>
### TestCase Name
dsGetSupportVidFormats_positive

### TestCase ID
dsVideoDevice L1-6

### TestCase Objective
Validate that `dsGetSupportedVideoCodingFormats()` retrieves supported video formats and they match the profile value.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI (REFPLTV-2536).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Get supported video coding formats | Invoke `dsGetSupportedVideoCodingFormats(handle, &supportedFormats)` | `dsGetSupportedVideoCodingFormats()` must return `dsERR_NONE` and `supportedFormats` must match the profile value |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="dsgetvideocodecinfo_positive"></a>
### TestCase Name
dsGetVideoCodecInfo_positive

### TestCase ID
dsVideoDevice L1-7

### TestCase Objective
Validate that `dsGetVideoCodecInfo()` retrieves codec information matching the profile for each supported codec on source platforms.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI (REFPLTV-2536).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Get video codec info for each supported codec (source) | Invoke `dsGetVideoCodecInfo(handle, codec, &codecInfo)` for each supported codec | `dsGetVideoCodecInfo()` must return `dsERR_NONE` and codec info must match the profile |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="dssetfrfmode_positive"></a>
### TestCase Name
dsSetFRFMode_positive

### TestCase ID
dsVideoDevice L1-8

### TestCase Objective
Validate that `dsSetFRFMode()` returns `dsERR_OPERATION_NOT_SUPPORTED` on source platforms (API is sink-only).

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI (REFPLTV-2562).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Set FRF mode (source — not supported) | Invoke `dsSetFRFMode(handle, 0)` and `dsSetFRFMode(handle, 1)` | `dsSetFRFMode()` must return `dsERR_OPERATION_NOT_SUPPORTED` for source devices |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="dsgetfrfmode_positive"></a>
### TestCase Name
dsGetFRFMode_positive

### TestCase ID
dsVideoDevice L1-9

### TestCase Objective
Validate that `dsGetFRFMode()` returns `dsERR_OPERATION_NOT_SUPPORTED` on source platforms (API is sink-only).

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI (REFPLTV-2562).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Get FRF mode (source — not supported) | Invoke `dsGetFRFMode(handle, &fetchedFRFMode)` | `dsGetFRFMode()` must return `dsERR_OPERATION_NOT_SUPPORTED` for source devices |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="dsgetcurrdispframerate_positive"></a>
### TestCase Name
dsGetCurrDispFramerate_positive

### TestCase ID
dsVideoDevice L1-10

### TestCase Objective
Validate that `dsGetCurrentDisplayframerate()` returns `dsERR_OPERATION_NOT_SUPPORTED` on source platforms (API is sink-only).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Get current display framerate (source — not supported) | Invoke `dsGetCurrentDisplayframerate(handle, fetchedFramerate)` | `dsGetCurrentDisplayframerate()` must return `dsERR_OPERATION_NOT_SUPPORTED` for source devices |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="dssetdisplayframerate_positive"></a>
### TestCase Name
dsSetDisplayframerate_positive

### TestCase ID
dsVideoDevice L1-11

### TestCase Objective
Validate that `dsSetDisplayframerate()` returns `dsERR_OPERATION_NOT_SUPPORTED` on source platforms (API is sink-only).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Set display framerate for each supported rate (source — not supported) | Invoke `dsSetDisplayframerate(handle, supportedFramerate[j])` | `dsSetDisplayframerate()` must return `dsERR_OPERATION_NOT_SUPPORTED` for source devices |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="dsregframerateprecb_positive"></a>
### TestCase Name
dsRegFrameratePreCB_positive

### TestCase ID
dsVideoDevice L1-12

### TestCase Objective
Validate that `dsRegisterFrameratePreChangeCB()` returns `dsERR_OPERATION_NOT_SUPPORTED` on source platforms (API is sink-only).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Register framerate pre-change callback (source — not supported) | Invoke `dsRegisterFrameratePreChangeCB(mockFrameRatePreChangeCallback)` | `dsRegisterFrameratePreChangeCB()` must return `dsERR_OPERATION_NOT_SUPPORTED` for source devices |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="dsregframeratepostcb_positive"></a>
### TestCase Name
dsRegFrameratePostCB_positive

### TestCase ID
dsVideoDevice L1-13

### TestCase Objective
Validate that `dsRegisterFrameratePostChangeCB()` returns `dsERR_OPERATION_NOT_SUPPORTED` on source platforms (API is sink-only).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Register framerate post-change callback (source — not supported) | Invoke `dsRegisterFrameratePostChangeCB(mockFrameRatePostChangeCallback)` | `dsRegisterFrameratePostChangeCB()` must return `dsERR_OPERATION_NOT_SUPPORTED` for source devices |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="dsvideodeviceinit_negative"></a>
### TestCase Name
dsVideoDeviceInit_negative

### TestCase ID
dsVideoDevice L1-14

### TestCase Objective
Validate that `dsVideoDeviceInit()` returns the correct error code when called while the module is already initialized.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Initialize again while already initialized | Invoke `dsVideoDeviceInit()` again without calling `dsVideoDeviceTerm()` | `dsVideoDeviceInit()` must return `dsERR_ALREADY_INITIALIZED` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="dsvideodeviceterm_negative"></a>
### TestCase Name
dsVideoDeviceTerm_negative

### TestCase ID
dsVideoDevice L1-15

### TestCase Objective
Validate that `dsVideoDeviceTerm()` returns the correct error code when called without prior initialization or after already being terminated.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Terminate without prior initialization | Invoke `dsVideoDeviceTerm()` before `dsVideoDeviceInit()` | `dsVideoDeviceTerm()` must return `dsERR_NOT_INITIALIZED` |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |
| Terminate again while already terminated | Invoke `dsVideoDeviceTerm()` again | `dsVideoDeviceTerm()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetvideodevice_negative"></a>
### TestCase Name
dsGetVideoDevice_negative

### TestCase ID
dsVideoDevice L1-16

### TestCase Objective
Validate that `dsGetVideoDevice()` returns correct error codes for invalid parameters and when called without initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get video device without prior initialization | Invoke `dsGetVideoDevice(0, &handle)` before `dsVideoDeviceInit()` | `dsGetVideoDevice()` must return `dsERR_NOT_INITIALIZED` |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device with invalid index | Invoke `dsGetVideoDevice(-1, &handle)` | `dsGetVideoDevice()` must return `dsERR_INVALID_PARAM` |
| Get video device with NULL handle pointer | Invoke `dsGetVideoDevice(i, NULL)` for each valid index | `dsGetVideoDevice()` must return `dsERR_INVALID_PARAM` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |
| Get video device after termination | Invoke `dsGetVideoDevice(0, &handle)` | `dsGetVideoDevice()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dssetdfc_negative"></a>
### TestCase Name
dsSetDFC_negative

### TestCase ID
dsVideoDevice L1-17

### TestCase Objective
Validate that `dsSetDFC()` returns correct error codes for invalid parameters and when called without initialization on source platforms.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI (REFPLTV-2577).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set DFC without prior initialization (source) | Invoke `dsSetDFC(-1, dsVIDEO_ZOOM_NONE)` before `dsVideoDeviceInit()` | `dsSetDFC()` must return `dsERR_NOT_INITIALIZED` |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Set DFC with invalid handle (source) | Invoke `dsSetDFC(-1, defaultDFC)` | `dsSetDFC()` must return `dsERR_INVALID_PARAM` |
| Set DFC with invalid zoom mode (source) | Invoke `dsSetDFC(handle, SupportedDFCs[numDFCs-1]+1)` | `dsSetDFC()` must return `dsERR_INVALID_PARAM` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |
| Set DFC after termination (source) | Invoke `dsSetDFC(handle, defaultDFC)` | `dsSetDFC()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgethdrcaps_negative"></a>
### TestCase Name
dsGetHDRCaps_negative

### TestCase ID
dsVideoDevice L1-18

### TestCase Objective
Validate that `dsGetHDRCapabilities()` returns correct error codes for invalid parameters and when called without initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get HDR capabilities without prior initialization | Invoke `dsGetHDRCapabilities(handle, &hdrCapabilities)` before `dsVideoDeviceInit()` | `dsGetHDRCapabilities()` must return `dsERR_NOT_INITIALIZED` |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Get HDR capabilities with invalid handle | Invoke `dsGetHDRCapabilities(-1, &hdrCapabilities)` | `dsGetHDRCapabilities()` must return `dsERR_INVALID_PARAM` |
| Get HDR capabilities with NULL output pointer | Invoke `dsGetHDRCapabilities(handle, NULL)` | `dsGetHDRCapabilities()` must return `dsERR_INVALID_PARAM` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |
| Get HDR capabilities after termination | Invoke `dsGetHDRCapabilities(handle, &hdrCapabilities)` | `dsGetHDRCapabilities()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetsupportvidformats_negative"></a>
### TestCase Name
dsGetSupportVidFormats_negative

### TestCase ID
dsVideoDevice L1-19

### TestCase Objective
Validate that `dsGetSupportedVideoCodingFormats()` returns correct error codes for invalid parameters and when called without initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get supported video formats without prior initialization | Invoke `dsGetSupportedVideoCodingFormats(handle, &supportedFormats)` before `dsVideoDeviceInit()` | `dsGetSupportedVideoCodingFormats()` must return `dsERR_NOT_INITIALIZED` |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Get supported video formats with invalid handle | Invoke `dsGetSupportedVideoCodingFormats(-1, &supportedFormats)` | `dsGetSupportedVideoCodingFormats()` must return `dsERR_INVALID_PARAM` |
| Get supported video formats with NULL output pointer | Invoke `dsGetSupportedVideoCodingFormats(handle, NULL)` | `dsGetSupportedVideoCodingFormats()` must return `dsERR_INVALID_PARAM` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |
| Get supported video formats after termination | Invoke `dsGetSupportedVideoCodingFormats(handle, &supportedFormats)` | `dsGetSupportedVideoCodingFormats()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetvideocodecinfo_negative"></a>
### TestCase Name
dsGetVideoCodecInfo_negative

### TestCase ID
dsVideoDevice L1-20

### TestCase Objective
Validate that `dsGetVideoCodecInfo()` returns correct error codes for invalid parameters and when called without initialization on source platforms.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get video codec info without prior initialization (source) | Invoke `dsGetVideoCodecInfo(handle, dsVIDEO_CODEC_MPEGHPART2, &codecInfo)` before `dsVideoDeviceInit()` | `dsGetVideoCodecInfo()` must return `dsERR_NOT_INITIALIZED` |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Get video codec info with invalid handle (source) | Invoke `dsGetVideoCodecInfo(-1, dsVIDEO_CODEC_MPEGHPART2, &codecInfo)` | `dsGetVideoCodecInfo()` must return `dsERR_INVALID_PARAM` |
| Get video codec info with invalid codec format (source) | Invoke `dsGetVideoCodecInfo(handle, dsVIDEO_CODEC_MAX, &codecInfo)` | `dsGetVideoCodecInfo()` must return `dsERR_INVALID_PARAM` |
| Get video codec info with NULL output pointer (source) | Invoke `dsGetVideoCodecInfo(handle, dsVIDEO_CODEC_MPEGHPART2, NULL)` | `dsGetVideoCodecInfo()` must return `dsERR_INVALID_PARAM` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |
| Get video codec info after termination (source) | Invoke `dsGetVideoCodecInfo(handle, dsVIDEO_CODEC_MPEGHPART2, &codecInfo)` | `dsGetVideoCodecInfo()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dssetfrfmode_negative"></a>
### TestCase Name
dsSetFRFMode_negative

### TestCase ID
dsVideoDevice L1-21

### TestCase Objective
Validate that `dsSetFRFMode()` returns `dsERR_OPERATION_NOT_SUPPORTED` for all scenarios on source platforms (API is sink-only).

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI (REFPLTV-2562).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set FRF mode without prior initialization (source) | Invoke `dsSetFRFMode(handle, 1)` before `dsVideoDeviceInit()` | `dsSetFRFMode()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Set FRF mode with invalid handle (source) | Invoke `dsSetFRFMode(-1, 1)` | `dsSetFRFMode()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Set FRF mode with invalid framerate (source) | Invoke `dsSetFRFMode(handle, -1)` | `dsSetFRFMode()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |
| Set FRF mode after termination (source) | Invoke `dsSetFRFMode(handle, 1)` | `dsSetFRFMode()` must return `dsERR_OPERATION_NOT_SUPPORTED` |

---

<a id="dsgetfrfmode_negative"></a>
### TestCase Name
dsGetFRFMode_negative

### TestCase ID
dsVideoDevice L1-22

### TestCase Objective
Validate that `dsGetFRFMode()` returns `dsERR_OPERATION_NOT_SUPPORTED` for all scenarios on source platforms (API is sink-only).

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI (REFPLTV-2562).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get FRF mode without prior initialization (source) | Invoke `dsGetFRFMode(handle, &fetchedFRFMode)` before `dsVideoDeviceInit()` | `dsGetFRFMode()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Get FRF mode with invalid handle (source) | Invoke `dsGetFRFMode(-1, &fetchedFRFMode)` | `dsGetFRFMode()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Get FRF mode with NULL output pointer (source) | Invoke `dsGetFRFMode(handle, NULL)` | `dsGetFRFMode()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |
| Get FRF mode after termination (source) | Invoke `dsGetFRFMode(handle, &fetchedFRFMode)` | `dsGetFRFMode()` must return `dsERR_OPERATION_NOT_SUPPORTED` |

---

<a id="dsgetcurrdispframerate_negative"></a>
### TestCase Name
dsGetCurrDispFramerate_negative

### TestCase ID
dsVideoDevice L1-23

### TestCase Objective
Validate that `dsGetCurrentDisplayframerate()` returns `dsERR_OPERATION_NOT_SUPPORTED` for all scenarios on source platforms (API is sink-only).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get current display framerate without prior initialization (source) | Invoke `dsGetCurrentDisplayframerate(handle, fetchedFramerate)` before `dsVideoDeviceInit()` | `dsGetCurrentDisplayframerate()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Get current display framerate with invalid handle (source) | Invoke `dsGetCurrentDisplayframerate(-1, fetchedFramerate)` | `dsGetCurrentDisplayframerate()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Get current display framerate with NULL output buffer (source) | Invoke `dsGetCurrentDisplayframerate(handle, NULL)` | `dsGetCurrentDisplayframerate()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |
| Get current display framerate after termination (source) | Invoke `dsGetCurrentDisplayframerate(handle, fetchedFramerate)` | `dsGetCurrentDisplayframerate()` must return `dsERR_OPERATION_NOT_SUPPORTED` |

---

<a id="dssetdisplayframerate_negative"></a>
### TestCase Name
dsSetDisplayframerate_negative

### TestCase ID
dsVideoDevice L1-24

### TestCase Objective
Validate that `dsSetDisplayframerate()` returns `dsERR_OPERATION_NOT_SUPPORTED` for all scenarios on source platforms (API is sink-only).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set display framerate without prior initialization (source) | Invoke `dsSetDisplayframerate(handle, "30fps")` before `dsVideoDeviceInit()` | `dsSetDisplayframerate()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Set display framerate with invalid handle (source) | Invoke `dsSetDisplayframerate(-1, "30fps")` | `dsSetDisplayframerate()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Set display framerate with NULL string (source) | Invoke `dsSetDisplayframerate(handle, NULL)` | `dsSetDisplayframerate()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Set display framerate with invalid string (source) | Invoke `dsSetDisplayframerate(handle, "junk")` | `dsSetDisplayframerate()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |
| Set display framerate after termination (source) | Invoke `dsSetDisplayframerate(handle, "30fps")` | `dsSetDisplayframerate()` must return `dsERR_OPERATION_NOT_SUPPORTED` |

---

<a id="dsregframerateprecb_negative"></a>
### TestCase Name
dsRegFrameratePreCB_negative

### TestCase ID
dsVideoDevice L1-25

### TestCase Objective
Validate that `dsRegisterFrameratePreChangeCB()` returns `dsERR_OPERATION_NOT_SUPPORTED` for all scenarios on source platforms (API is sink-only).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Register framerate pre-change callback without prior initialization (source) | Invoke `dsRegisterFrameratePreChangeCB(mockCallback)` before `dsVideoDeviceInit()` | `dsRegisterFrameratePreChangeCB()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Register with NULL callback (source) | Invoke `dsRegisterFrameratePreChangeCB(NULL)` | `dsRegisterFrameratePreChangeCB()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |
| Register framerate pre-change callback after termination (source) | Invoke `dsRegisterFrameratePreChangeCB(mockCallback)` | `dsRegisterFrameratePreChangeCB()` must return `dsERR_OPERATION_NOT_SUPPORTED` |

---

<a id="dsregframeratepostcb_negative"></a>
### TestCase Name
dsRegFrameratePostCB_negative

### TestCase ID
dsVideoDevice L1-26

### TestCase Objective
Validate that `dsRegisterFrameratePostChangeCB()` returns `dsERR_OPERATION_NOT_SUPPORTED` for all scenarios on source platforms (API is sink-only).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Register framerate post-change callback without prior initialization (source) | Invoke `dsRegisterFrameratePostChangeCB(mockCallback)` before `dsVideoDeviceInit()` | `dsRegisterFrameratePostChangeCB()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Register with NULL callback (source) | Invoke `dsRegisterFrameratePostChangeCB(NULL)` | `dsRegisterFrameratePostChangeCB()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |
| Register framerate post-change callback after termination (source) | Invoke `dsRegisterFrameratePostChangeCB(mockCallback)` | `dsRegisterFrameratePostChangeCB()` must return `dsERR_OPERATION_NOT_SUPPORTED` |

---

<a id="dsgetdfc_positive"></a>
### TestCase Name
dsGetDFC_positive

### TestCase ID
dsVideoDevice L1-27

### TestCase Objective
Validate that `dsGetDFC()` retrieves the current DFC (zoom) mode on source platforms and the returned mode is one of the supported modes.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI (REFPLTV-2577).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Get DFC mode (source) | Invoke `dsGetDFC(handle, &dfcMode)` | `dsGetDFC()` must return `dsERR_NONE` and `dfcMode` must be one of the supported DFC values from the profile |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="dsforceDisableHDR_positive"></a>
### TestCase Name
dsForceDisableHDR_positive

### TestCase ID
dsVideoDevice L1-28

### TestCase Objective
Validate that `dsForceDisableHDRSupport()` returns `dsERR_OPERATION_NOT_SUPPORTED` for both enable and disable values (API is not supported for source or sink).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Force disable HDR support (set true) | Invoke `dsForceDisableHDRSupport(handle, true)` | `dsForceDisableHDRSupport()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Force disable HDR support (set false) | Invoke `dsForceDisableHDRSupport(handle, false)` | `dsForceDisableHDRSupport()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |

---

<a id="dsgetdfc_negative"></a>
### TestCase Name
dsGetDFC_negative

### TestCase ID
dsVideoDevice L1-29

### TestCase Objective
Validate that `dsGetDFC()` returns correct error codes for invalid parameters and when called without initialization on source platforms.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get DFC without prior initialization (source) | Invoke `dsGetDFC(handle, &dfcMode)` before `dsVideoDeviceInit()` | `dsGetDFC()` must return `dsERR_NOT_INITIALIZED` |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Get DFC with invalid handle (source) | Invoke `dsGetDFC(-1, &dfcMode)` | `dsGetDFC()` must return `dsERR_INVALID_PARAM` |
| Get DFC with NULL output pointer (source) | Invoke `dsGetDFC(handle, NULL)` | `dsGetDFC()` must return `dsERR_INVALID_PARAM` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |
| Get DFC after termination (source) | Invoke `dsGetDFC(handle, &dfcMode)` | `dsGetDFC()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsforceDisableHDR_negative"></a>
### TestCase Name
dsForceDisableHDR_negative

### TestCase ID
dsVideoDevice L1-30

### TestCase Objective
Validate that `dsForceDisableHDRSupport()` returns `dsERR_OPERATION_NOT_SUPPORTED` for all scenarios including invalid parameters (API is not supported).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Force disable HDR without prior initialization | Invoke `dsForceDisableHDRSupport(handle, true)` before `dsVideoDeviceInit()` | `dsForceDisableHDRSupport()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Initialize all video devices | Invoke `dsVideoDeviceInit()` | `dsVideoDeviceInit()` must return `dsERR_NONE` |
| Get video device handle | Invoke `dsGetVideoDevice(i, &handle)` | `dsGetVideoDevice()` must return `dsERR_NONE` and a valid handle |
| Force disable HDR with invalid handle | Invoke `dsForceDisableHDRSupport(-1, true)` | `dsForceDisableHDRSupport()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Terminate all video devices | Invoke `dsVideoDeviceTerm()` | `dsVideoDeviceTerm()` must return `dsERR_NONE` |
| Force disable HDR after termination | Invoke `dsForceDisableHDRSupport(handle, true)` | `dsForceDisableHDRSupport()` must return `dsERR_OPERATION_NOT_SUPPORTED` |

---

## Post-conditions

1. The `hal_test_dshal` binary exits cleanly after completing all test cases in the `[L1 dsVideoDevice]` suite.
2. The DS Video Device HAL module is terminated (via `dsVideoDeviceTerm()`) at the end of each test case, restoring the uninitialized default state.

---

## Test Attributes

| Attribute | Value |
| --- | --- |
| Supported Models | Video_Accelerator, RPI-Client |
| Estimated Duration | 45 minutes |
| Priority | High |
| TDK Release Version | M134 |
