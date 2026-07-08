## TestScript Name
VTS_dsDisplay_L1_test

## TestScript ID
VTS_Test_17

## Table of Contents

1. [Objective](#objective)
2. [Pre-conditions](#pre-conditions)
3. [Test Cases](#test-cases)
   - [dsDisplayInit_pos](#dsdisplayinit_pos)
   - [dsDisplayInit_neg](#dsdisplayinit_neg)
   - [dsDisplayTerm_pos](#dsdisplayterm_pos)
   - [dsDisplayTerm_neg](#dsdisplayterm_neg)
   - [dsGetDisplay_pos](#dsgetdisplay_pos)
   - [dsGetDisplay_neg](#dsgetdisplay_neg)
   - [dsGetEDID_pos](#dsgetedid_pos)
   - [dsGetEDID_neg](#dsgetedid_neg)
   - [dsGetEDIDBytes_pos](#dsgetedidbytes_pos)
   - [dsGetEDIDBytes_neg](#dsgetedidbytes_neg)
   - [dsGetDisplayAspectRatio_pos](#dsgetdisplayaspectratio_pos)
   - [dsGetDisplayAspectRatio_neg](#dsgetdisplayaspectratio_neg)
   - [dsRegisterDisplayEventCB_pos](#dsregisterdisplayeventcb_pos)
   - [dsRegisterDisplayEventCB_neg](#dsregisterdisplayeventcb_neg)
   - [dsGetAVIContentType_pos](#dsgetavicontenttype_pos)
   - [dsGetAVIContentType_neg](#dsgetavicontenttype_neg)
   - [dsSetAVIContentType_pos](#dssetavicontenttype_pos)
   - [dsSetAVIContentType_neg](#dssetavicontenttype_neg)
   - [dsGetAVIScanInfo_pos](#dsgetaviscaninfo_pos)
   - [dsGetAVIScanInfo_neg](#dsgetaviscaninfo_neg)
   - [dsSetAVIScanInfo_pos](#dssetaviscaninfo_pos)
   - [dsSetAVIScanInfo_neg](#dssetaviscaninfo_neg)
   - [dsGetAllmEnabled_pos](#dsgetallenabled_pos)
   - [dsGetAllmEnabled_neg](#dsgetallenabled_neg)
   - [dsSetAllmEnabled_pos](#dssetallenabled_pos)
   - [dsSetAllmEnabled_neg](#dssetallenabled_neg)
4. [Post-conditions](#post-conditions)
5. [Test Attributes](#test-attributes)

---

## Objective

This script executes VTS L1 (Level 1) test cases for the Device Settings Display HAL module (`dsDisplay`). L1 tests validate individual HAL APIs in isolation — each test case calls a single API with valid or invalid parameters and verifies the correct return code is produced. No external stimulus (connected displays, EDID signals, etc.) is required; the tests rely solely on the HAL implementation and the profile configuration. The binary used is `hal_test_dshal`, invoked with the profile `Source_4K_Display.yaml`.

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

<a id="dsdisplayinit_pos"></a>
### TestCase Name
dsDisplayInit_pos

### TestCase ID
dsDisplay L1-1

### TestCase Objective
Validate that `dsDisplayInit()` successfully initializes the DS Display sub-system and can be re-initialized after termination.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |
| Re-initialize the DS Display sub-system | Invoke `dsDisplayInit()` again | `dsDisplayInit()` must return `dsERR_NONE` |
| Re-terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |

---

<a id="dsdisplayinit_neg"></a>
### TestCase Name
dsDisplayInit_neg

### TestCase ID
dsDisplay L1-2

### TestCase Objective
Validate that `dsDisplayInit()` returns the correct error code when called while the module is already initialized.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Initialize again while already initialized | Invoke `dsDisplayInit()` again without calling `dsDisplayTerm()` | `dsDisplayInit()` must return `dsERR_ALREADY_INITIALIZED` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |

---

<a id="dsdisplayterm_pos"></a>
### TestCase Name
dsDisplayTerm_pos

### TestCase ID
dsDisplay L1-3

### TestCase Objective
Validate that `dsDisplayTerm()` successfully terminates the DS Display sub-system and the system can be re-initialized after termination.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |
| Re-initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Re-terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |

---

<a id="dsdisplayterm_neg"></a>
### TestCase Name
dsDisplayTerm_neg

### TestCase ID
dsDisplay L1-4

### TestCase Objective
Validate that `dsDisplayTerm()` returns the correct error code when called without prior initialization or after already being terminated.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Terminate the module without prior initialization | Invoke `dsDisplayTerm()` before calling `dsDisplayInit()` | `dsDisplayTerm()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |
| Terminate again while module is already terminated | Invoke `dsDisplayTerm()` again | `dsDisplayTerm()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetdisplay_pos"></a>
### TestCase Name
dsGetDisplay_pos

### TestCase ID
dsDisplay L1-5

### TestCase Objective
Validate that `dsGetDisplay()` retrieves a valid display device handle for all supported video ports.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handle for each valid port | Invoke `dsGetDisplay(vType, portIndex, &displayHandle1)` for all ports in the profile | `dsGetDisplay()` must return `dsERR_NONE` and a valid non-null handle |
| Retrieve display handle again for comparison | Invoke `dsGetDisplay(vType, portIndex, &displayHandle2)` with the same port parameters | `dsGetDisplay()` must return `dsERR_NONE` and handles from both calls must be equal |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |

---

<a id="dsgetdisplay_neg"></a>
### TestCase Name
dsGetDisplay_neg

### TestCase ID
dsDisplay L1-6

### TestCase Objective
Validate that `dsGetDisplay()` returns correct error codes for invalid parameters and when called without initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get display handle without prior initialization | Invoke `dsGetDisplay(vType, 0, &displayHandle)` before `dsDisplayInit()` | `dsGetDisplay()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Get display handle with invalid video type | Invoke `dsGetDisplay(dsVIDEOPORT_TYPE_MAX, index, &displayHandle)` | `dsGetDisplay()` must return `dsERR_INVALID_PARAM` |
| Get display handle with invalid index | Invoke `dsGetDisplay(vType, -1, &displayHandle)` | `dsGetDisplay()` must return `dsERR_INVALID_PARAM` |
| Get display handle with NULL output pointer | Invoke `dsGetDisplay(vType, 0, NULL)` | `dsGetDisplay()` must return `dsERR_INVALID_PARAM` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |
| Get display handle after termination | Invoke `dsGetDisplay(vType, 0, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetedid_pos"></a>
### TestCase Name
dsGetEDID_pos

### TestCase ID
dsDisplay L1-7

### TestCase Objective
Validate that `dsGetEDID()` successfully retrieves EDID information for each connected display.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handle for each valid port | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` and a valid handle |
| Retrieve EDID information (first call) | Invoke `dsGetEDID(displayHandle, &edid1)` | `dsGetEDID()` must return `dsERR_NONE` |
| Retrieve EDID information (second call) | Invoke `dsGetEDID(displayHandle, &edid2)` | `dsGetEDID()` must return `dsERR_NONE` and results must match the first call |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |

---

<a id="dsgetedid_neg"></a>
### TestCase Name
dsGetEDID_neg

### TestCase ID
dsDisplay L1-8

### TestCase Objective
Validate that `dsGetEDID()` returns correct error codes for invalid parameters and when called without initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get EDID without prior initialization | Invoke `dsGetEDID(handle, edid)` before `dsDisplayInit()` | `dsGetEDID()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handles for all valid ports | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` |
| Get EDID with invalid handle | Invoke `dsGetEDID(NULL, edid)` | `dsGetEDID()` must return `dsERR_INVALID_PARAM` |
| Get EDID with NULL EDID pointer | Invoke `dsGetEDID(displayHandle, NULL)` | `dsGetEDID()` must return `dsERR_INVALID_PARAM` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |
| Get EDID after termination | Invoke `dsGetEDID(displayHandle, edid)` | `dsGetEDID()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetedidbytes_pos"></a>
### TestCase Name
dsGetEDIDBytes_pos

### TestCase ID
dsDisplay L1-9

### TestCase Objective
Validate that `dsGetEDIDBytes()` successfully retrieves the raw EDID buffer and its length.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handle for each valid port | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` and a valid handle |
| Retrieve raw EDID bytes | Invoke `dsGetEDIDBytes(displayHandle, edid, &length)` | `dsGetEDIDBytes()` must return `dsERR_NONE` and a valid EDID buffer with non-zero length |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |

---

<a id="dsgetedidbytes_neg"></a>
### TestCase Name
dsGetEDIDBytes_neg

### TestCase ID
dsDisplay L1-10

### TestCase Objective
Validate that `dsGetEDIDBytes()` returns correct error codes for invalid parameters and when called without initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get EDID bytes without prior initialization | Invoke `dsGetEDIDBytes(handle, edid, &length)` before `dsDisplayInit()` | `dsGetEDIDBytes()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handles for all valid ports | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` |
| Get EDID bytes with invalid handle | Invoke `dsGetEDIDBytes(NULL, edid, &length)` | `dsGetEDIDBytes()` must return `dsERR_INVALID_PARAM` |
| Get EDID bytes with NULL EDID buffer | Invoke `dsGetEDIDBytes(displayHandle, NULL, &length)` | `dsGetEDIDBytes()` must return `dsERR_INVALID_PARAM` |
| Get EDID bytes with NULL length pointer | Invoke `dsGetEDIDBytes(displayHandle, edid, NULL)` | `dsGetEDIDBytes()` must return `dsERR_INVALID_PARAM` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |
| Get EDID bytes after termination | Invoke `dsGetEDIDBytes(displayHandle, edid, &length)` | `dsGetEDIDBytes()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetdisplayaspectratio_pos"></a>
### TestCase Name
dsGetDisplayAspectRatio_pos

### TestCase ID
dsDisplay L1-11

### TestCase Objective
Validate that `dsGetDisplayAspectRatio()` retrieves the display aspect ratio for source platforms.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handle for each valid port | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` and a valid handle |
| Get display aspect ratio | Invoke `dsGetDisplayAspectRatio(displayHandle, &aspectRatio)` | `dsGetDisplayAspectRatio()` must return `dsERR_NONE` and aspect ratio must equal `dsVIDEO_ASPECT_RATIO_16x9` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |

---

<a id="dsgetdisplayaspectratio_neg"></a>
### TestCase Name
dsGetDisplayAspectRatio_neg

### TestCase ID
dsDisplay L1-12

### TestCase Objective
Validate that `dsGetDisplayAspectRatio()` returns correct error codes for invalid parameters and when called without initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get aspect ratio without prior initialization | Invoke `dsGetDisplayAspectRatio(handle, &aspectRatio)` before `dsDisplayInit()` | `dsGetDisplayAspectRatio()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handles for all valid ports | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` |
| Get aspect ratio with invalid handle (source only) | Invoke `dsGetDisplayAspectRatio(NULL, &aspectRatio)` | `dsGetDisplayAspectRatio()` must return `dsERR_INVALID_PARAM` |
| Get aspect ratio with NULL aspect ratio pointer (source only) | Invoke `dsGetDisplayAspectRatio(displayHandle, NULL)` | `dsGetDisplayAspectRatio()` must return `dsERR_INVALID_PARAM` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |
| Get aspect ratio after termination | Invoke `dsGetDisplayAspectRatio(displayHandle, &aspectRatio)` | `dsGetDisplayAspectRatio()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsregisterdisplayeventcb_pos"></a>
### TestCase Name
dsRegisterDisplayEventCB_pos

### TestCase ID
dsDisplay L1-13

### TestCase Objective
Validate that `dsRegisterDisplayEventCallback()` successfully registers a display event callback.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handle for each valid port | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` and a valid handle |
| Register display event callback | Invoke `dsRegisterDisplayEventCallback(displayHandle, testDisplayCallback)` | `dsRegisterDisplayEventCallback()` must return `dsERR_NONE` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |

---

<a id="dsregisterdisplayeventcb_neg"></a>
### TestCase Name
dsRegisterDisplayEventCB_neg

### TestCase ID
dsDisplay L1-14

### TestCase Objective
Validate that `dsRegisterDisplayEventCallback()` returns correct error codes for invalid parameters and when called without initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Register callback without prior initialization | Invoke `dsRegisterDisplayEventCallback(handle, callback)` before `dsDisplayInit()` | `dsRegisterDisplayEventCallback()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handles for all valid ports | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` |
| Register callback with NULL handle | Invoke `dsRegisterDisplayEventCallback(NULL, testDisplayCallback)` | `dsRegisterDisplayEventCallback()` must return `dsERR_INVALID_PARAM` |
| Register callback with NULL callback function | Invoke `dsRegisterDisplayEventCallback(displayHandle, NULL)` | `dsRegisterDisplayEventCallback()` must return `dsERR_INVALID_PARAM` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |
| Register callback after termination | Invoke `dsRegisterDisplayEventCallback(displayHandle, callback)` | `dsRegisterDisplayEventCallback()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetavicontenttype_pos"></a>
### TestCase Name
dsGetAVIContentType_pos

### TestCase ID
dsDisplay L1-15

### TestCase Objective
Validate that `dsGetAVIContentType()` retrieves the AVI content type signalling information for source platforms.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handle for each valid port | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` and a valid handle |
| Get AVI content type | Invoke `dsGetAVIContentType(displayHandle, &contentType)` | `dsGetAVIContentType()` must return `dsERR_NONE` and content type must equal `dsAVICONTENT_TYPE_NOT_SIGNALLED` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |

---

<a id="dsgetavicontenttype_neg"></a>
### TestCase Name
dsGetAVIContentType_neg

### TestCase ID
dsDisplay L1-16

### TestCase Objective
Validate that `dsGetAVIContentType()` returns correct error codes for invalid parameters and when called without initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get AVI content type without prior initialization | Invoke `dsGetAVIContentType(handle, &contentType)` before `dsDisplayInit()` | `dsGetAVIContentType()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handles for all valid ports | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` |
| Get AVI content type with invalid handle (source only) | Invoke `dsGetAVIContentType(NULL, &contentType)` | `dsGetAVIContentType()` must return `dsERR_INVALID_PARAM` |
| Get AVI content type with NULL output pointer (source only) | Invoke `dsGetAVIContentType(displayHandle, NULL)` | `dsGetAVIContentType()` must return `dsERR_INVALID_PARAM` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |
| Get AVI content type after termination | Invoke `dsGetAVIContentType(displayHandle, &contentType)` | `dsGetAVIContentType()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dssetavicontenttype_pos"></a>
### TestCase Name
dsSetAVIContentType_pos

### TestCase ID
dsDisplay L1-17

### TestCase Objective
Validate that `dsSetAVIContentType()` successfully configures the AVI content type for all valid content type values.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handle for each valid port | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` and a valid handle |
| Set AVI content type for each valid value | Invoke `dsSetAVIContentType(displayHandle, contentType)` for each value from `dsAVICONTENT_TYPE_GRAPHICS` to `dsAVICONTENT_TYPE_MAX-1` | `dsSetAVIContentType()` must return `dsERR_NONE` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |

---

<a id="dssetavicontenttype_neg"></a>
### TestCase Name
dsSetAVIContentType_neg

### TestCase ID
dsDisplay L1-18

### TestCase Objective
Validate that `dsSetAVIContentType()` returns correct error codes for invalid parameters and when called without initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set AVI content type without prior initialization | Invoke `dsSetAVIContentType(handle, contentType)` before `dsDisplayInit()` | `dsSetAVIContentType()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handles for all valid ports | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` |
| Set AVI content type with invalid handle (source only) | Invoke `dsSetAVIContentType(NULL, contentType)` | `dsSetAVIContentType()` must return `dsERR_INVALID_PARAM` |
| Set AVI content type with invalid content type value (source only) | Invoke `dsSetAVIContentType(displayHandle, dsAVICONTENT_TYPE_MAX)` | `dsSetAVIContentType()` must return `dsERR_INVALID_PARAM` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |
| Set AVI content type after termination | Invoke `dsSetAVIContentType(displayHandle, contentType)` | `dsSetAVIContentType()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetaviscaninfo_pos"></a>
### TestCase Name
dsGetAVIScanInfo_pos

### TestCase ID
dsDisplay L1-19

### TestCase Objective
Validate that `dsGetAVIScanInformation()` retrieves the AVI scan information for source platforms.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handle for each valid port | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` and a valid handle |
| Get AVI scan information | Invoke `dsGetAVIScanInformation(displayHandle, &scanInfo)` | `dsGetAVIScanInformation()` must return `dsERR_NONE` and scan info must equal `dsAVI_SCAN_TYPE_NO_DATA` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |

---

<a id="dsgetaviscaninfo_neg"></a>
### TestCase Name
dsGetAVIScanInfo_neg

### TestCase ID
dsDisplay L1-20

### TestCase Objective
Validate that `dsGetAVIScanInformation()` returns correct error codes for invalid parameters and when called without initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get AVI scan info without prior initialization | Invoke `dsGetAVIScanInformation(handle, &scanInfo)` before `dsDisplayInit()` | `dsGetAVIScanInformation()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handles for all valid ports | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` |
| Get AVI scan info with invalid handle (source only) | Invoke `dsGetAVIScanInformation(NULL, &scanInfo)` | `dsGetAVIScanInformation()` must return `dsERR_INVALID_PARAM` |
| Get AVI scan info with NULL output pointer (source only) | Invoke `dsGetAVIScanInformation(displayHandle, NULL)` | `dsGetAVIScanInformation()` must return `dsERR_INVALID_PARAM` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |
| Get AVI scan info after termination | Invoke `dsGetAVIScanInformation(displayHandle, &scanInfo)` | `dsGetAVIScanInformation()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dssetaviscaninfo_pos"></a>
### TestCase Name
dsSetAVIScanInfo_pos

### TestCase ID
dsDisplay L1-21

### TestCase Objective
Validate that `dsSetAVIScanInformation()` can be called on all valid scan type values; returns success or `dsERR_OPERATION_NOT_SUPPORTED` when HDMI is disconnected.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handle for each valid port | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` and a valid handle |
| Set AVI scan info for each valid value | Invoke `dsSetAVIScanInformation(displayHandle, scanInfo)` for each value from `dsAVI_SCAN_TYPE_NO_DATA` to `dsAVI_SCAN_TYPE_MAX-1` | `dsSetAVIScanInformation()` must return `dsERR_NONE` or `dsERR_OPERATION_NOT_SUPPORTED` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |

---

<a id="dssetaviscaninfo_neg"></a>
### TestCase Name
dsSetAVIScanInfo_neg

### TestCase ID
dsDisplay L1-22

### TestCase Objective
Validate that `dsSetAVIScanInformation()` returns correct error codes for invalid parameters and when called without initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set AVI scan info without prior initialization | Invoke `dsSetAVIScanInformation(handle, scanInfo)` before `dsDisplayInit()` | `dsSetAVIScanInformation()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handles for all valid ports | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` |
| Set AVI scan info with invalid handle (source only) | Invoke `dsSetAVIScanInformation(NULL, scanInfo)` | `dsSetAVIScanInformation()` must return `dsERR_INVALID_PARAM` |
| Set AVI scan info with invalid scan info value (source only) | Invoke `dsSetAVIScanInformation(displayHandle, dsAVI_SCAN_TYPE_MAX)` | `dsSetAVIScanInformation()` must return `dsERR_INVALID_PARAM` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |
| Set AVI scan info after termination | Invoke `dsSetAVIScanInformation(displayHandle, scanInfo)` | `dsSetAVIScanInformation()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetallenabled_pos"></a>
### TestCase Name
dsGetAllmEnabled_pos

### TestCase ID
dsDisplay L1-23

### TestCase Objective
Validate that `dsGetAllmEnabled()` retrieves the HDMI ALLM enabled status for source platforms.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handle for each valid port | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` and a valid handle |
| Get ALLM enabled status | Invoke `dsGetAllmEnabled(displayHandle, &enabled)` | `dsGetAllmEnabled()` must return `dsERR_NONE` and `enabled` must equal `false` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |

---

<a id="dsgetallenabled_neg"></a>
### TestCase Name
dsGetAllmEnabled_neg

### TestCase ID
dsDisplay L1-24

### TestCase Objective
Validate that `dsGetAllmEnabled()` returns correct error codes for invalid parameters and when called without initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get ALLM status without prior initialization | Invoke `dsGetAllmEnabled(handle, &enabled)` before `dsDisplayInit()` | `dsGetAllmEnabled()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handles for all valid ports | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` |
| Get ALLM status with invalid handle (source only) | Invoke `dsGetAllmEnabled(NULL, &enabled)` | `dsGetAllmEnabled()` must return `dsERR_INVALID_PARAM` |
| Get ALLM status with NULL output pointer (source only) | Invoke `dsGetAllmEnabled(displayHandle, NULL)` | `dsGetAllmEnabled()` must return `dsERR_INVALID_PARAM` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |
| Get ALLM status after termination | Invoke `dsGetAllmEnabled(displayHandle, &enabled)` | `dsGetAllmEnabled()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dssetallenabled_pos"></a>
### TestCase Name
dsSetAllmEnabled_pos

### TestCase ID
dsDisplay L1-25

### TestCase Objective
Validate that `dsSetAllmEnabled()` can enable and disable HDMI ALLM; returns success or `dsERR_OPERATION_NOT_SUPPORTED` when HDMI is disconnected.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handle for each valid port | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` and a valid handle |
| Enable ALLM | Invoke `dsSetAllmEnabled(displayHandle, true)` | `dsSetAllmEnabled()` must return `dsERR_NONE` or `dsERR_OPERATION_NOT_SUPPORTED` |
| Disable ALLM | Invoke `dsSetAllmEnabled(displayHandle, false)` | `dsSetAllmEnabled()` must return `dsERR_NONE` or `dsERR_OPERATION_NOT_SUPPORTED` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |

---

<a id="dssetallenabled_neg"></a>
### TestCase Name
dsSetAllmEnabled_neg

### TestCase ID
dsDisplay L1-26

### TestCase Objective
Validate that `dsSetAllmEnabled()` returns correct error codes for invalid parameters and when called without initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set ALLM without prior initialization | Invoke `dsSetAllmEnabled(handle, enabled)` before `dsDisplayInit()` | `dsSetAllmEnabled()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the DS Display sub-system | Invoke `dsDisplayInit()` | `dsDisplayInit()` must return `dsERR_NONE` |
| Retrieve display handles for all valid ports | Invoke `dsGetDisplay(vType, portIndex, &displayHandle)` | `dsGetDisplay()` must return `dsERR_NONE` |
| Set ALLM with invalid handle (source only) | Invoke `dsSetAllmEnabled(NULL, enabled)` | `dsSetAllmEnabled()` must return `dsERR_INVALID_PARAM` |
| Terminate the DS Display sub-system | Invoke `dsDisplayTerm()` | `dsDisplayTerm()` must return `dsERR_NONE` |
| Set ALLM after termination | Invoke `dsSetAllmEnabled(displayHandle, enabled)` | `dsSetAllmEnabled()` must return `dsERR_NOT_INITIALIZED` |

---

## Post-conditions

1. The `hal_test_dshal` binary exits cleanly after completing all test cases in the `[L1 dsDisplay]` suite.
2. The DS Display HAL module is terminated (via `dsDisplayTerm()`) at the end of each test case, restoring the uninitialized default state.

---

## Test Attributes

| Attribute | Value |
| --- | --- |
| Supported Models | Video_Accelerator, RPI-Client |
| Estimated Duration | 20 minutes |
| Priority | High |
| TDK Release Version | M134 |
