## TestScript Name
VTS_dsVideoPort_L1_test

## TestScript ID
VTS_Test_02

## Table of Contents

1. [Objective](#objective)
2. [Pre-conditions](#pre-conditions)
3. [Test Cases](#test-cases)
   - [dsVideoPortInit_pos](#dsvideoportinit_pos)
   - [dsVideoPortInit_neg](#dsvideoportinit_neg)
   - [dsVideoPortTerm_pos](#dsvideoportterm_pos)
   - [dsVideoPortTerm_neg](#dsvideoportterm_neg)
   - [dsGetVideoPort_pos](#dsgetvideoport_pos)
   - [dsGetVideoPort_neg](#dsgetvideoport_neg)
   - [dsIsVideoPortEnabled_pos](#dsisvideoportenabled_pos)
   - [dsIsVideoPortEnabled_neg](#dsisvideoportenabled_neg)
   - [dsIsDisplayConnected_pos](#dsisdisplayconnected_pos)
   - [dsIsDisplayConnected_neg](#dsisdisplayconnected_neg)
   - [dsIsDisplaySurround_pos](#dsisdisplaysurround_pos)
   - [dsIsDisplaySurround_neg](#dsisdisplaysurround_neg)
   - [dsGetSurroundMode_pos](#dsgetsurroundmode_pos)
   - [dsGetSurroundMode_neg](#dsgetsurroundmode_neg)
   - [VideoFormatUpdateRegCB_pos](#videoformatupdateregcb_pos)
   - [VideoFormatUpdateRegCB_neg](#videoformatupdateregcb_neg)
   - [dsIsVideoPortActive_pos](#dsisvideoportactive_pos)
   - [dsIsVideoPortActive_neg](#dsisvideoportactive_neg)
   - [dsEnableHDCP_pos](#dsenablehdcp_pos)
   - [dsEnableHDCP_neg](#dsenablehdcp_neg)
   - [dsIsHDCPEnabled_pos](#dsishdcpenabled_pos)
   - [dsIsHDCPEnabled_neg](#dsishdcpenabled_neg)
   - [dsEnableVideoPort_pos](#dsenablevideoport_pos)
   - [dsEnableVideoPort_neg](#dsenablevideoport_neg)
   - [dsSetResolution_pos](#dssetresolution_pos)
   - [dsSetResolution_neg](#dssetresolution_neg)
   - [dsGetResolution_pos](#dsgetresolution_pos)
   - [dsGetResolution_neg](#dsgetresolution_neg)
   - [dsRegisterHdcpStatusCB_pos](#dsregisterhdcpstatuscb_pos)
   - [dsRegisterHdcpStatusCB_neg](#dsregisterhdcpstatuscb_neg)
   - [dsGetHDCPStatus_pos](#dsgethdcpstatus_pos)
   - [dsGetHDCPStatus_neg](#dsgethdcpstatus_neg)
   - [dsGetHDCPProtocol_pos](#dsgethdcpprotocol_pos)
   - [dsGetHDCPProtocol_neg](#dsgethdcpprotocol_neg)
   - [GetHDCPReceiverProtocol_pos](#gethdcpreceiverprotocol_pos)
   - [GetHDCPReceiverProtocol_neg](#gethdcpreceiverprotocol_neg)
   - [GetHDCPCurrentProtocol_pos](#gethdcpcurrentprotocol_pos)
   - [GetHDCPCurrentProtocol_neg](#gethdcpcurrentprotocol_neg)
   - [dsGetTVHDRCapabilities_pos](#dsgettvhdrcapabilities_pos)
   - [dsGetTVHDRCapabilities_neg](#dsgettvhdrcapabilities_neg)
   - [dsSupportedTvResolutions_pos](#dssupportedtvresolutions_pos)
   - [dsSupportedTvResolutions_neg](#dssupportedtvresolutions_neg)
   - [SetForceDisable4KSupport_pos](#setforcedisable4ksupport_pos)
   - [SetForceDisable4KSupport_neg](#setforcedisable4ksupport_neg)
   - [GetForceDisable4KSupport_pos](#getforcedisable4ksupport_pos)
   - [GetForceDisable4KSupport_neg](#getforcedisable4ksupport_neg)
   - [dsGetVideoEOTF_pos](#dsgetvideoeotf_pos)
   - [dsGetVideoEOTF_neg](#dsgetvideoeotf_neg)
   - [dsGetMatrixCoefficients_pos](#dsgetmatrixcoefficients_pos)
   - [dsGetMatrixCoefficients_neg](#dsgetmatrixcoefficients_neg)
   - [dsGetColorDepth_pos](#dsgetcolordepth_pos)
   - [dsGetColorDepth_neg](#dsgetcolordepth_neg)
   - [dsGetColorSpace_pos](#dsgetcolorspace_pos)
   - [dsGetColorSpace_neg](#dsgetcolorspace_neg)
   - [dsGetQuantizationRange_pos](#dsgetquantizationrange_pos)
   - [dsGetQuantizationRange_neg](#dsgetquantizationrange_neg)
   - [dsGetCurrentOutputSettings_pos](#dsgetcurrentoutputsettings_pos)
   - [dsGetCurrentOutputSettings_neg](#dsgetcurrentoutputsettings_neg)
   - [dsIsOutputHDR_pos](#dsisoutputhdr_pos)
   - [dsIsOutputHDR_neg](#dsisoutputhdr_neg)
   - [dsResetOutputToSDR_pos](#dsresetoutputtosdr_pos)
   - [dsResetOutputToSDR_neg](#dsresetoutputtosdr_neg)
   - [dsSetHdmiPreference_pos](#dssethdmipreference_pos)
   - [dsSetHdmiPreference_neg](#dssethdmipreference_neg)
   - [dsGetHdmiPreference_pos](#dsgethdmipreference_pos)
   - [dsGetHdmiPreference_neg](#dsgethdmipreference_neg)
   - [dsGetIgnoreEDIDStatus_pos](#dsgetignoreedidstatus_pos)
   - [dsGetIgnoreEDIDStatus_neg](#dsgetignoreedidstatus_neg)
   - [dsSetBackgroundColor_pos](#dssetbackgroundcolor_pos)
   - [dsSetBackgroundColor_neg](#dssetbackgroundcolor_neg)
   - [dsSetForceHDRMode_pos](#dssetforcehdrmode_pos)
   - [dsSetForceHDRMode_neg](#dssetforcehdrmode_neg)
   - [dsColorDepthCapb_pos](#dscolordepthcapb_pos)
   - [dsColorDepthCapb_neg](#dscolordepthcapb_neg)
   - [dsGetPreferredColorDepth_pos](#dsgetpreferredcolordepth_pos)
   - [dsGetPreferredColorDepth_neg](#dsgetpreferredcolordepth_neg)
   - [dsSetPreferredColorDepth_pos](#dssetpreferredcolordepth_pos)
   - [dsSetPreferredColorDepth_neg](#dssetpreferredcolordepth_neg)
4. [Post-conditions](#post-conditions)
5. [Test Attributes](#test-attributes)

---

## Objective

This script executes VTS L1 (Level 1) test cases for the Device Settings Video Port HAL module (`dsVideoPort`). L1 tests validate individual HAL APIs in isolation — each test case calls a single API with valid or invalid parameters and verifies the correct return code is produced. No external stimulus (physical display connections, HDCP handshake, etc.) is required; the tests rely solely on the HAL implementation and the profile configuration. The binary used is `hal_test_dshal`, invoked with the profile `Source_4K_VideoPort.yaml`.

---

## Pre-conditions

### Pre-condition 1: VTS Package Installed

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Read VTS Base Path | Check the device config file for `VTS_BASE_PATH`. If set (e.g., `VTS_BASE_PATH = /opt/VTS_Package/`), that path is used as the base; otherwise the default `/VTS_Package/` is used | Base path is determined |
| Verify Binary and Config | Confirm the module sub-directory `device_settings/` exists under the base path and contains the required files | `<VTS_BASE_PATH>/device_settings/` exists and contains the `hal_test_dshal` binary and `Source_4K_VideoPort.yaml` config file |

### Pre-condition 2: SSH Connectivity

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Read SSH Configuration | Read SSH connection parameters from the device config file: `SSH_PORT` (default: `22`), `SSH_METHOD` (e.g., `directSSH`), `SSH_USERNAME` (e.g., `root`), `SSH_PASSWORD` (`None` if no password required) | SSH parameters are available |
| Verify SSH Access | Establish an SSH session to the DUT using the configured parameters | SSH session is established successfully |

---

## Test Cases

<a id="dsvideoportinit_pos"></a>
### TestCase Name
dsVideoPortInit_pos

### TestCase ID
dsVideoPort L1-1

### TestCase Objective
Validate that `dsVideoPortInit()` successfully initializes the video port system and can be called again after termination.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Re-initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` again | `dsVideoPortInit()` must return `dsERR_NONE` |
| Re-terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsvideoportinit_neg"></a>
### TestCase Name
dsVideoPortInit_neg

### TestCase ID
dsVideoPort L1-2

### TestCase Objective
Validate that `dsVideoPortInit()` returns the correct error code when called while already initialized.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Initialize again while already initialized | Invoke `dsVideoPortInit()` again without calling `dsVideoPortTerm()` | `dsVideoPortInit()` must return `dsERR_ALREADY_INITIALIZED` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsvideoportterm_pos"></a>
### TestCase Name
dsVideoPortTerm_pos

### TestCase ID
dsVideoPort L1-3

### TestCase Objective
Validate that `dsVideoPortTerm()` successfully terminates the video port system and the system can be re-initialized after termination.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Re-initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Re-terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsvideoportterm_neg"></a>
### TestCase Name
dsVideoPortTerm_neg

### TestCase ID
dsVideoPort L1-4

### TestCase Objective
Validate that `dsVideoPortTerm()` returns the correct error code when called without prior initialization or after already being terminated.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Terminate the module without prior initialization | Invoke `dsVideoPortTerm()` before calling `dsVideoPortInit()` | `dsVideoPortTerm()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Terminate again while module is already terminated | Invoke `dsVideoPortTerm()` again | `dsVideoPortTerm()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetvideoport_pos"></a>
### TestCase Name
dsGetVideoPort_pos

### TestCase ID
dsVideoPort L1-5

### TestCase Objective
Validate that `dsGetVideoPort()` returns valid handles for all supported video port types and indexes defined in the profile.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each entry in `kPorts` | `dsGetVideoPort()` must return `dsERR_NONE` and a non-NULL handle for each port |
| Verify handle consistency | Invoke `dsGetVideoPort()` again for the last port and compare the returned handle to the previously stored value | `dsGetVideoPort()` must return `dsERR_NONE`; handles are equal |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetvideoport_neg"></a>
### TestCase Name
dsGetVideoPort_neg

### TestCase ID
dsVideoPort L1-6

### TestCase Objective
Validate that `dsGetVideoPort()` returns the correct error codes when called without initialization, with invalid type, invalid index, or NULL handle.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the handle for a video port without prior initialization | Invoke `dsGetVideoPort(kPorts[0].type, kPorts[0].index, &handle)` before `dsVideoPortInit()` | `dsGetVideoPort()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port with invalid type | Invoke `dsGetVideoPort(dsVIDEOPORT_TYPE_MAX, index, &handle)` for each port index | `dsGetVideoPort()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port with invalid index | Invoke `dsGetVideoPort(type, -1, &handle)` for each port type | `dsGetVideoPort()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port with NULL handle pointer | Invoke `dsGetVideoPort(type, index, NULL)` for each port | `dsGetVideoPort()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the handle for a video port after module terminated | Invoke `dsGetVideoPort(kPorts[0].type, kPorts[0].index, &handle)` | `dsGetVideoPort()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsisvideoportenabled_pos"></a>
### TestCase Name
dsIsVideoPortEnabled_pos

### TestCase ID
dsVideoPort L1-7

### TestCase Objective
Validate that `dsIsVideoPortEnabled()` correctly returns the enabled status of each video port and produces consistent results across two consecutive calls.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each entry in `kPorts` | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Check whether a video port is enabled (first call) | Invoke `dsIsVideoPortEnabled(handle, &isEnabled1)` for each handle | `dsIsVideoPortEnabled()` must return `dsERR_NONE` |
| Check whether a video port is enabled (second call) | Invoke `dsIsVideoPortEnabled(handle, &isEnabled2)` for each handle | `dsIsVideoPortEnabled()` must return `dsERR_NONE` |
| Compare enabled status values | Verify `isEnabled1 == isEnabled2` for each port | Values are equal |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsisvideoportenabled_neg"></a>
### TestCase Name
dsIsVideoPortEnabled_neg

### TestCase ID
dsVideoPort L1-8

### TestCase Objective
Validate that `dsIsVideoPortEnabled()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Check whether a video port is enabled without prior initialization | Invoke `dsIsVideoPortEnabled(-1, &enabled)` before `dsVideoPortInit()` | `dsIsVideoPortEnabled()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Check whether a video port is enabled with invalid handle | Invoke `dsIsVideoPortEnabled(0, &enabled)` using invalid handle `0` | `dsIsVideoPortEnabled()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Check whether a video port is enabled with NULL output pointer | Invoke `dsIsVideoPortEnabled(handle, NULL)` for each valid handle | `dsIsVideoPortEnabled()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Check whether a video port is enabled after module terminated | Invoke `dsIsVideoPortEnabled(handle, &enabled)` | `dsIsVideoPortEnabled()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsisdisplayconnected_pos"></a>
### TestCase Name
dsIsDisplayConnected_pos

### TestCase ID
dsVideoPort L1-9

### TestCase Objective
Validate that `dsIsDisplayConnected()` correctly returns the display connection status and produces consistent results across two consecutive calls.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Check whether the video port is connected to a display (first call) | Invoke `dsIsDisplayConnected(handle, &isConnected1)` for each handle | `dsIsDisplayConnected()` must return `dsERR_NONE` |
| Check whether the video port is connected to a display (second call) | Invoke `dsIsDisplayConnected(handle, &isConnected2)` for each handle | `dsIsDisplayConnected()` must return `dsERR_NONE` |
| Compare connection status values | Verify `isConnected1 == isConnected2` for each port | Values are equal |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsisdisplayconnected_neg"></a>
### TestCase Name
dsIsDisplayConnected_neg

### TestCase ID
dsVideoPort L1-10

### TestCase Objective
Validate that `dsIsDisplayConnected()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Check whether the video port is connected to a display without prior initialization | Invoke `dsIsDisplayConnected(-1, &connected)` before `dsVideoPortInit()` | `dsIsDisplayConnected()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Check whether the video port is connected to a display with invalid handle | Invoke `dsIsDisplayConnected(0, &connected)` using invalid handle `0` | `dsIsDisplayConnected()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Check whether the video port is connected to a display with NULL output pointer | Invoke `dsIsDisplayConnected(handle, NULL)` for each valid handle | `dsIsDisplayConnected()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Check whether the video port is connected to a display after module terminated | Invoke `dsIsDisplayConnected(handle, &connected)` | `dsIsDisplayConnected()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsisdisplaysurround_pos"></a>
### TestCase Name
dsIsDisplaySurround_pos

### TestCase ID
dsVideoPort L1-11

### TestCase Objective
Validate that `dsIsDisplaySurround()` correctly returns the audio surround support status and that the value matches the profile file configuration.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Check if the connected display supports audio surround | Invoke `dsIsDisplaySurround(handle, &isSurround)` for each handle | `dsIsDisplaySurround()` must return `dsERR_NONE` |
| Compare with profile | Verify `isSurround == gDSVideoPortConfiguration[i].DisplaySurround` | Value matches profile configuration |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsisdisplaysurround_neg"></a>
### TestCase Name
dsIsDisplaySurround_neg

### TestCase ID
dsVideoPort L1-12

### TestCase Objective
Validate that `dsIsDisplaySurround()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Check if the connected display supports audio surround without prior initialization | Invoke `dsIsDisplaySurround(-1, &surround)` before `dsVideoPortInit()` | `dsIsDisplaySurround()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Check if the connected display supports audio surround with invalid handle | Invoke `dsIsDisplaySurround(0, &surround)` using invalid handle `0` | `dsIsDisplaySurround()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Check if the connected display supports audio surround with NULL output pointer | Invoke `dsIsDisplaySurround(handle, NULL)` for each valid handle | `dsIsDisplaySurround()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Check if the connected display supports audio surround after module terminated | Invoke `dsIsDisplaySurround(handle, &surround)` | `dsIsDisplaySurround()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetsurroundmode_pos"></a>
### TestCase Name
dsGetSurroundMode_pos

### TestCase ID
dsVideoPort L1-13

### TestCase Objective
Validate that `dsGetSurroundMode()` correctly returns the surround mode for source devices and `dsERR_OPERATION_NOT_SUPPORTED` for sink devices.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Get the surround mode of the video port | Invoke `dsGetSurroundMode(handle, &surroundMode)` for each handle | Source device (`gSourceType==1`): `dsGetSurroundMode()` must return `dsERR_NONE`; Sink device (`gSourceType==0`): `dsGetSurroundMode()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Compare with profile (source only) | Verify `surroundMode == gDSVideoPortConfiguration[i].SurroundMode` | Value matches profile configuration |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetsurroundmode_neg"></a>
### TestCase Name
dsGetSurroundMode_neg

### TestCase ID
dsVideoPort L1-14

### TestCase Objective
Validate that `dsGetSurroundMode()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the surround mode of the video port without prior initialization | Invoke `dsGetSurroundMode(-1, &surroundMode)` before `dsVideoPortInit()` | `dsGetSurroundMode()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the surround mode of the video port with invalid handle | Invoke `dsGetSurroundMode(0, &surroundMode)` using handle `0` | `dsGetSurroundMode()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get the surround mode of the video port with NULL output pointer | Invoke `dsGetSurroundMode(handle, NULL)` for each valid handle | `dsGetSurroundMode()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the surround mode of the video port after module terminated | Invoke `dsGetSurroundMode(handle, &surroundMode)` | `dsGetSurroundMode()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="videoformatupdateregcb_pos"></a>
### TestCase Name
VideoFormatUpdateRegCB_pos

### TestCase ID
dsVideoPort L1-15

### TestCase Objective
Validate that `dsVideoFormatUpdateRegisterCB()` successfully registers a valid video format update callback after initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Register callback for the Video Format update event | Invoke `dsVideoFormatUpdateRegisterCB(mockVideoFormatCallback)` with a valid callback function | `dsVideoFormatUpdateRegisterCB()` must return `dsERR_NONE` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="videoformatupdateregcb_neg"></a>
### TestCase Name
VideoFormatUpdateRegCB_neg

### TestCase ID
dsVideoPort L1-16

### TestCase Objective
Validate that `dsVideoFormatUpdateRegisterCB()` returns the correct error codes when called without initialization, with a NULL callback, or after termination.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Register callback for the Video Format update event without prior initialization | Invoke `dsVideoFormatUpdateRegisterCB(mockVideoFormatCallback)` before `dsVideoPortInit()` | `dsVideoFormatUpdateRegisterCB()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Register callback for the Video Format update event with NULL callback | Invoke `dsVideoFormatUpdateRegisterCB(NULL)` | `dsVideoFormatUpdateRegisterCB()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Register callback for the Video Format update event after module terminated | Invoke `dsVideoFormatUpdateRegisterCB(mockVideoFormatCallback)` | `dsVideoFormatUpdateRegisterCB()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsisvideoportactive_pos"></a>
### TestCase Name
dsIsVideoPortActive_pos

### TestCase ID
dsVideoPort L1-17

### TestCase Objective
Validate that `dsIsVideoPortActive()` correctly returns the active status of each video port and produces consistent results across two consecutive calls.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Check whether a video port is active (first call) | Invoke `dsIsVideoPortActive(handle, &isActive1)` for each handle | `dsIsVideoPortActive()` must return `dsERR_NONE` |
| Check whether a video port is active (second call) | Invoke `dsIsVideoPortActive(handle, &isActive2)` for each handle | `dsIsVideoPortActive()` must return `dsERR_NONE` |
| Compare active status values | Verify `isActive1 == isActive2` for each port | Values are equal |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsisvideoportactive_neg"></a>
### TestCase Name
dsIsVideoPortActive_neg

### TestCase ID
dsVideoPort L1-18

### TestCase Objective
Validate that `dsIsVideoPortActive()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Check whether a video port is active without prior initialization | Invoke `dsIsVideoPortActive(-1, &active)` before `dsVideoPortInit()` | `dsIsVideoPortActive()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Check whether a video port is active with invalid handle | Invoke `dsIsVideoPortActive(0, &active)` using handle `0` | `dsIsVideoPortActive()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Check whether a video port is active with NULL output pointer | Invoke `dsIsVideoPortActive(handle, NULL)` for each valid handle | `dsIsVideoPortActive()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Check whether a video port is active after module terminated | Invoke `dsIsVideoPortActive(handle, &active)` | `dsIsVideoPortActive()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsenablehdcp_pos"></a>
### TestCase Name
dsEnableHDCP_pos

### TestCase ID
dsVideoPort L1-19

### TestCase Objective
Validate that `dsEnableHDCP()` successfully enables HDCP on ports that support it, and returns `dsERR_OPERATION_NOT_SUPPORTED` for ports that do not.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Enable/Disable HDCP on a video port | Invoke `dsEnableHDCP(handle, hdcp_supported, hdcpKey, HDCP_KEY_MAX_SIZE)` for each handle | Source device with HDCP support: `dsEnableHDCP()` must return `dsERR_NONE`; Source without HDCP support or sink device: `dsEnableHDCP()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsenablehdcp_neg"></a>
### TestCase Name
dsEnableHDCP_neg

### TestCase ID
dsVideoPort L1-20

### TestCase Objective
Validate that `dsEnableHDCP()` returns the correct error codes when called without initialization, with an invalid handle, invalid key size, or NULL key pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Enable/Disable HDCP on a video port without prior initialization | Invoke `dsEnableHDCP(-1, enableHDCP, hdcpKey, HDCP_KEY_MAX_SIZE)` before `dsVideoPortInit()` | `dsEnableHDCP()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Enable/Disable HDCP on a video port with invalid handle | Invoke `dsEnableHDCP(0, enableHDCP, hdcpKey, HDCP_KEY_MAX_SIZE)` using handle `0` | `dsEnableHDCP()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Enable/Disable HDCP on a video port with oversized key | Invoke `dsEnableHDCP(handle, enableHDCP, hdcpKey, HDCP_KEY_MAX_SIZE+1)` | `dsEnableHDCP()` must return `dsERR_INVALID_PARAM` |
| Enable/Disable HDCP on a video port with NULL key pointer | Invoke `dsEnableHDCP(handle, enableHDCP, NULL, HDCP_KEY_MAX_SIZE)` | `dsEnableHDCP()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Enable/Disable HDCP on a video port after module terminated | Invoke `dsEnableHDCP(handle, enableHDCP, hdcpKey, HDCP_KEY_MAX_SIZE)` | `dsEnableHDCP()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsishdcpenabled_pos"></a>
### TestCase Name
dsIsHDCPEnabled_pos

### TestCase ID
dsVideoPort L1-21

### TestCase Objective
Validate that `dsIsHDCPEnabled()` correctly returns the HDCP enabled status for each video port consistent with the profile configuration.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Check whether a video port is HDCP protected | Invoke `dsIsHDCPEnabled(handle, &isHDCPEnabled)` for each handle | Source device: `dsIsHDCPEnabled()` must return `dsERR_NONE` (or `dsERR_OPERATION_NOT_SUPPORTED` if port doesn't support HDCP); Sink device: `dsIsHDCPEnabled()` must return `dsERR_NONE` with `isHDCPEnabled = true` |
| Compare with profile | Verify returned value matches `gDSVideoPortConfiguration[i].hdcp_supported` | Values match |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsishdcpenabled_neg"></a>
### TestCase Name
dsIsHDCPEnabled_neg

### TestCase ID
dsVideoPort L1-22

### TestCase Objective
Validate that `dsIsHDCPEnabled()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Check whether a video port is HDCP protected without prior initialization | Invoke `dsIsHDCPEnabled(-1, &contentProtected)` before `dsVideoPortInit()` | `dsIsHDCPEnabled()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Check whether a video port is HDCP protected with invalid handle | Invoke `dsIsHDCPEnabled(0, &contentProtected)` using handle `0` | `dsIsHDCPEnabled()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Check whether a video port is HDCP protected with NULL output pointer | Invoke `dsIsHDCPEnabled(handle, NULL)` for each valid handle | `dsIsHDCPEnabled()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Check whether a video port is HDCP protected after module terminated | Invoke `dsIsHDCPEnabled(handle, &contentProtected)` | `dsIsHDCPEnabled()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsenablevideoport_pos"></a>
### TestCase Name
dsEnableVideoPort_pos

### TestCase ID
dsVideoPort L1-23

### TestCase Objective
Validate that `dsEnableVideoPort()` successfully enables each video port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Enable/Disable a video port | Invoke `dsEnableVideoPort(handle, true)` for each handle | `dsEnableVideoPort()` must return `dsERR_NONE` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsenablevideoport_neg"></a>
### TestCase Name
dsEnableVideoPort_neg

### TestCase ID
dsVideoPort L1-24

### TestCase Objective
Validate that `dsEnableVideoPort()` returns the correct error codes when called without initialization, with an invalid handle, or after termination.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Enable/Disable a video port without prior initialization | Invoke `dsEnableVideoPort(-1, true)` before `dsVideoPortInit()` | `dsEnableVideoPort()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Enable/Disable a video port with invalid handle | Invoke `dsEnableVideoPort(0, true)` using handle `0` | `dsEnableVideoPort()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Enable/Disable a video port after module terminated | Invoke `dsEnableVideoPort(handle, true)` | `dsEnableVideoPort()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dssetresolution_pos"></a>
### TestCase Name
dsSetResolution_pos

### TestCase ID
dsVideoPort L1-25

### TestCase Objective
Validate that `dsSetResolution()` successfully sets each supported resolution on each video port for source devices.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Set the display resolution of the video port | Invoke `dsSetResolution(handle, &supportedResolutions[j])` for each supported resolution per port | Source device: `dsSetResolution()` must return `dsERR_NONE`; Sink device: `dsSetResolution()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetresolution_neg"></a>
### TestCase Name
dsSetResolution_neg

### TestCase ID
dsVideoPort L1-26

### TestCase Objective
Validate that `dsSetResolution()` returns the correct error codes when called without initialization, with an invalid handle, a NULL resolution pointer, or out-of-range resolution parameters.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set the display resolution of the video port without prior initialization | Invoke `dsSetResolution(-1, &resolution)` before `dsVideoPortInit()` | `dsSetResolution()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Set the display resolution of the video port with invalid handle | Invoke `dsSetResolution(0, &resolution)` using handle `0` | `dsSetResolution()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Set the display resolution of the video port with NULL pointer | Invoke `dsSetResolution(handle, NULL)` | `dsSetResolution()` must return `dsERR_INVALID_PARAM` |
| Set the display resolution of the video port with invalid parameters | Invoke `dsSetResolution(handle, &resolution)` where resolution has `pixelResolution = dsVIDEO_PIXELRES_MAX`, `aspectRatio = dsVIDEO_ASPECT_RATIO_MAX`, `frameRate = dsVIDEO_FRAMERATE_MAX`, `stereoScopicMode = dsVIDEO_SSMODE_MAX` | `dsSetResolution()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Set the display resolution of the video port after module terminated | Invoke `dsSetResolution(handle, &resolution)` | `dsSetResolution()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetresolution_pos"></a>
### TestCase Name
dsGetResolution_pos

### TestCase ID
dsVideoPort L1-27

### TestCase Objective
Validate that `dsGetResolution()` successfully retrieves the current resolution of each video port and that the returned values match the default resolution from the profile.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Get the display resolution of the video port | Invoke `dsGetResolution(handle, &resolution)` for each handle | `dsGetResolution()` must return `dsERR_NONE` |
| Compare with profile default | Verify `resolution.pixelResolution`, `aspectRatio`, `stereoScopicMode`, `frameRate`, and `interlaced` match the default resolution entry in `supportedResolutions[]` | Values match profile default resolution |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetresolution_neg"></a>
### TestCase Name
dsGetResolution_neg

### TestCase ID
dsVideoPort L1-28

### TestCase Objective
Validate that `dsGetResolution()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the display resolution of the video port without prior initialization | Invoke `dsGetResolution(-1, &resolution)` before `dsVideoPortInit()` | `dsGetResolution()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the display resolution of the video port with invalid handle | Invoke `dsGetResolution(0, &resolution)` using handle `0` | `dsGetResolution()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get the display resolution of the video port with NULL output pointer | Invoke `dsGetResolution(handle, NULL)` for each valid handle | `dsGetResolution()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the display resolution of the video port after module terminated | Invoke `dsGetResolution(handle, &resolution)` | `dsGetResolution()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsregisterhdcpstatuscb_pos"></a>
### TestCase Name
dsRegisterHdcpStatusCB_pos

### TestCase ID
dsVideoPort L1-29

### TestCase Objective
Validate that `dsRegisterHdcpStatusCallback()` successfully registers a valid HDCP status change callback for each video port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Register callback for the HDCP status change event | Invoke `dsRegisterHdcpStatusCallback(handle, myHdcpStatusCallbackFunction)` for each handle | `dsRegisterHdcpStatusCallback()` must return `dsERR_NONE` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsregisterhdcpstatuscb_neg"></a>
### TestCase Name
dsRegisterHdcpStatusCB_neg

### TestCase ID
dsVideoPort L1-30

### TestCase Objective
Validate that `dsRegisterHdcpStatusCallback()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL callback.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Register callback for the HDCP status change event without prior initialization | Invoke `dsRegisterHdcpStatusCallback(-1, validCallback)` before `dsVideoPortInit()` | `dsRegisterHdcpStatusCallback()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Register callback for the HDCP status change event with invalid handle | Invoke `dsRegisterHdcpStatusCallback(0, validCallback)` using handle `0` | `dsRegisterHdcpStatusCallback()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Register callback for the HDCP status change event with NULL callback | Invoke `dsRegisterHdcpStatusCallback(handle, NULL)` for each valid handle | `dsRegisterHdcpStatusCallback()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Register callback for the HDCP status change event after module terminated | Invoke `dsRegisterHdcpStatusCallback(handle, validCallback)` | `dsRegisterHdcpStatusCallback()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgethdcpstatus_pos"></a>
### TestCase Name
dsGetHDCPStatus_pos

### TestCase ID
dsVideoPort L1-31

### TestCase Objective
Validate that `dsGetHDCPStatus()` correctly returns the HDCP authentication status based on display connectivity and HDCP support.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Enable HDCP if display connected | Invoke `dsDisplayInit()`, then `dsIsDisplayConnected(handle, &isConnected)`. If connected, invoke `dsEnableHDCP(handle, true, hdcpKey, keySize)` | `dsERR_NONE` |
| Get the current HDCP status of the video port | Invoke `dsGetHDCPStatus(handle, &hdcpStatus)` for each handle | Source device with HDCP support: `dsGetHDCPStatus()` must return `dsERR_NONE`; Source without HDCP or sink: `dsGetHDCPStatus()` must return `dsERR_OPERATION_NOT_SUPPORTED` or `dsERR_NONE` |
| Terminate display and video port | Invoke `dsDisplayTerm()`, then `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgethdcpstatus_neg"></a>
### TestCase Name
dsGetHDCPStatus_neg

### TestCase ID
dsVideoPort L1-32

### TestCase Objective
Validate that `dsGetHDCPStatus()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the current HDCP status of the video port without prior initialization | Invoke `dsGetHDCPStatus(-1, &hdcpStatus)` before `dsVideoPortInit()` | `dsGetHDCPStatus()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the current HDCP status of the video port with invalid handle | Invoke `dsGetHDCPStatus(0, &hdcpStatus)` using handle `0` | `dsGetHDCPStatus()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get the current HDCP status of the video port with NULL output pointer | Invoke `dsGetHDCPStatus(handle, NULL)` for each valid handle | `dsGetHDCPStatus()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the current HDCP status of the video port after module terminated | Invoke `dsGetHDCPStatus(handle, &hdcpStatus)` | `dsGetHDCPStatus()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgethdcpprotocol_pos"></a>
### TestCase Name
dsGetHDCPProtocol_pos

### TestCase ID
dsVideoPort L1-33

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsGetHDCPProtocol (REFPLTV-2542).

### TestCase Objective
Validate that `dsGetHDCPProtocol()` correctly retrieves the HDCP protocol version and that the value matches the profile configuration.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Get the HDCP protocol version of the device | Invoke `dsGetHDCPProtocol(handle, &protocolVersion)` for each handle | `dsGetHDCPProtocol()` must return `dsERR_NONE` |
| Compare with profile | Verify `protocolVersion == gDSVideoPortConfiguration[i].hdcp_protocol_version` | Value matches profile |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgethdcpprotocol_neg"></a>
### TestCase Name
dsGetHDCPProtocol_neg

### TestCase ID
dsVideoPort L1-34

### TestCase Objective
Validate that `dsGetHDCPProtocol()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the HDCP protocol version of the device without prior initialization | Invoke `dsGetHDCPProtocol(-1, &protocolVersion)` before `dsVideoPortInit()` | `dsGetHDCPProtocol()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the HDCP protocol version of the device with invalid handle | Invoke `dsGetHDCPProtocol(0, &protocolVersion)` using handle `0` | `dsGetHDCPProtocol()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get the HDCP protocol version of the device with NULL output pointer | Invoke `dsGetHDCPProtocol(handle, NULL)` for each valid handle | `dsGetHDCPProtocol()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the HDCP protocol version of the device after module terminated | Invoke `dsGetHDCPProtocol(handle, &protocolVersion)` | `dsGetHDCPProtocol()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="gethdcpreceiverprotocol_pos"></a>
### TestCase Name
GetHDCPReceiverProtocol_pos

### TestCase ID
dsVideoPort L1-35

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsGetHDCPReceiverProtocol (REFPLTV-2542).

### TestCase Objective
Validate that `dsGetHDCPReceiverProtocol()` correctly retrieves the sink device HDCP protocol version and that the value matches the profile configuration.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Get the HDCP protocol version of the connected sink device | Invoke `dsGetHDCPReceiverProtocol(handle, &protocolVersion)` for each handle | `dsGetHDCPReceiverProtocol()` must return `dsERR_NONE` |
| Compare with profile | Verify `protocolVersion == gDSVideoPortConfiguration[i].hdcp_protocol_version` | Value matches profile |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="gethdcpreceiverprotocol_neg"></a>
### TestCase Name
GetHDCPReceiverProtocol_neg

### TestCase ID
dsVideoPort L1-36

### TestCase Objective
Validate that `dsGetHDCPReceiverProtocol()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the HDCP protocol version of the connected sink device without prior initialization | Invoke `dsGetHDCPReceiverProtocol(-1, &protocolVersion)` before `dsVideoPortInit()` | `dsGetHDCPReceiverProtocol()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the HDCP protocol version of the connected sink device with invalid handle | Invoke `dsGetHDCPReceiverProtocol(0, &protocolVersion)` using handle `0` | `dsGetHDCPReceiverProtocol()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get the HDCP protocol version of the connected sink device with NULL output pointer | Invoke `dsGetHDCPReceiverProtocol(handle, NULL)` for each valid handle | `dsGetHDCPReceiverProtocol()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the HDCP protocol version of the connected sink device after module terminated | Invoke `dsGetHDCPReceiverProtocol(handle, &protocolVersion)` | `dsGetHDCPReceiverProtocol()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="gethdcpcurrentprotocol_pos"></a>
### TestCase Name
GetHDCPCurrentProtocol_pos

### TestCase ID
dsVideoPort L1-37

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsGetHDCPCurrentProtocol (REFPLTV-2542).

### TestCase Objective
Validate that `dsGetHDCPCurrentProtocol()` correctly retrieves the current negotiated HDCP protocol version and that the value matches the profile configuration.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Get the current negotiated HDCP protocol version | Invoke `dsGetHDCPCurrentProtocol(handle, &currentProtocol)` for each handle | `dsGetHDCPCurrentProtocol()` must return `dsERR_NONE` |
| Compare with profile | Verify `currentProtocol == gDSVideoPortConfiguration[i].hdcp_protocol_version` | Value matches profile |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="gethdcpcurrentprotocol_neg"></a>
### TestCase Name
GetHDCPCurrentProtocol_neg

### TestCase ID
dsVideoPort L1-38

### TestCase Objective
Validate that `dsGetHDCPCurrentProtocol()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the current negotiated HDCP protocol version without prior initialization | Invoke `dsGetHDCPCurrentProtocol(-1, &currentProtocol)` before `dsVideoPortInit()` | `dsGetHDCPCurrentProtocol()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the current negotiated HDCP protocol version with invalid handle | Invoke `dsGetHDCPCurrentProtocol(0, &currentProtocol)` using handle `0` | `dsGetHDCPCurrentProtocol()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get the current negotiated HDCP protocol version with NULL output pointer | Invoke `dsGetHDCPCurrentProtocol(handle, NULL)` for each valid handle | `dsGetHDCPCurrentProtocol()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the current negotiated HDCP protocol version after module terminated | Invoke `dsGetHDCPCurrentProtocol(handle, &currentProtocol)` | `dsGetHDCPCurrentProtocol()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgettvhdrcapabilities_pos"></a>
### TestCase Name
dsGetTVHDRCapabilities_pos

### TestCase ID
dsVideoPort L1-39

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsGetTVHDRCapabilities (REFPLTV-2576).

### TestCase Objective
Validate that `dsGetTVHDRCapabilities()` correctly retrieves the TV HDR capabilities, returning `dsHDRSTANDARD_SDR` when no display is connected or the profile-configured value when connected.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Get the HDR capabilities of the TV/display device | Invoke `dsGetTVHDRCapabilities(handle, &capabilities)` for each handle | `dsGetTVHDRCapabilities()` must return `dsERR_NONE` |
| Check display connection and compare | Invoke `dsDisplayInit()`, `dsIsDisplayConnected(handle, &isConnected)`. If not connected: verify `capabilities == dsHDRSTANDARD_SDR`; if connected: verify `capabilities == gDSVideoPortConfiguration[i].hdr_capabilities` | Values match expected |
| Terminate display and video port | Invoke `dsDisplayTerm()`, then `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgettvhdrcapabilities_neg"></a>
### TestCase Name
dsGetTVHDRCapabilities_neg

### TestCase ID
dsVideoPort L1-40

### TestCase Objective
Validate that `dsGetTVHDRCapabilities()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the HDR capabilities of the TV/display device without prior initialization | Invoke `dsGetTVHDRCapabilities(-1, &capabilities)` before `dsVideoPortInit()` | `dsGetTVHDRCapabilities()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the HDR capabilities of the TV/display device with invalid handle | Invoke `dsGetTVHDRCapabilities(0, &capabilities)` using handle `0` | `dsGetTVHDRCapabilities()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get the HDR capabilities of the TV/display device with NULL output pointer | Invoke `dsGetTVHDRCapabilities(handle, NULL)` for each valid handle | `dsGetTVHDRCapabilities()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the HDR capabilities of the TV/display device after module terminated | Invoke `dsGetTVHDRCapabilities(handle, &capabilities)` | `dsGetTVHDRCapabilities()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dssupportedtvresolutions_pos"></a>
### TestCase Name
dsSupportedTvResolutions_pos

### TestCase ID
dsVideoPort L1-41

### TestCase Objective
Validate that `dsSupportedTvResolutions()` correctly returns the supported TV resolutions, returning `dsTV_RESOLUTION_480p` when no display is connected or the profile value when connected.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Get the supported resolutions of the TV | Invoke `dsSupportedTvResolutions(handle, &resolutions)` for each handle | `dsSupportedTvResolutions()` must return `dsERR_NONE` |
| Check display connection and compare | Invoke `dsDisplayInit()`, `dsIsDisplayConnected(handle, &isConnected)`. If not connected: verify `resolutions == dsTV_RESOLUTION_480p`; if connected: verify `resolutions == gDSVideoPortConfiguration[i].Supported_tv_resolutions_capabilities` | Values match expected |
| Terminate display and video port | Invoke `dsDisplayTerm()`, then `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dssupportedtvresolutions_neg"></a>
### TestCase Name
dsSupportedTvResolutions_neg

### TestCase ID
dsVideoPort L1-42

### TestCase Objective
Validate that `dsSupportedTvResolutions()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the supported resolutions of the TV without prior initialization | Invoke `dsSupportedTvResolutions(-1, &resolutions)` before `dsVideoPortInit()` | `dsSupportedTvResolutions()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the supported resolutions of the TV with invalid handle | Invoke `dsSupportedTvResolutions(0, &resolutions)` using handle `0` | `dsSupportedTvResolutions()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get the supported resolutions of the TV with NULL output pointer | Invoke `dsSupportedTvResolutions(handle, NULL)` for each valid handle | `dsSupportedTvResolutions()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the supported resolutions of the TV after module terminated | Invoke `dsSupportedTvResolutions(handle, &resolutions)` | `dsSupportedTvResolutions()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="setforcedisable4ksupport_pos"></a>
### TestCase Name
SetForceDisable4KSupport_pos

### TestCase ID
dsVideoPort L1-43

### TestCase Objective
Validate that `dsSetForceDisable4KSupport()` returns `dsERR_OPERATION_NOT_SUPPORTED` for all ports (this operation is not supported in the current HAL implementation).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Set the ForceDisable 4K support variable | Invoke `dsSetForceDisable4KSupport(handle, true)` for each handle | `dsSetForceDisable4KSupport()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="setforcedisable4ksupport_neg"></a>
### TestCase Name
SetForceDisable4KSupport_neg

### TestCase ID
dsVideoPort L1-44

### TestCase Objective
Validate that `dsSetForceDisable4KSupport()` returns the correct error codes when called without initialization, with an invalid handle, or after termination.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set the ForceDisable 4K support variable without prior initialization | Invoke `dsSetForceDisable4KSupport(-1, true)` before `dsVideoPortInit()` | `dsSetForceDisable4KSupport()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Set the ForceDisable 4K support variable with invalid handle | Invoke `dsSetForceDisable4KSupport(0, true)` using handle `0` | `dsSetForceDisable4KSupport()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Set the ForceDisable 4K support variable after module terminated | Invoke `dsSetForceDisable4KSupport(handle, true)` | `dsSetForceDisable4KSupport()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="getforcedisable4ksupport_pos"></a>
### TestCase Name
GetForceDisable4KSupport_pos

### TestCase ID
dsVideoPort L1-45

### TestCase Objective
Validate that `dsGetForceDisable4KSupport()` returns `dsERR_OPERATION_NOT_SUPPORTED` consistently across two calls for all ports.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Get the ForceDisable 4K support variable (first call) | Invoke `dsGetForceDisable4KSupport(handle, &disable4K1)` for each handle | `dsGetForceDisable4KSupport()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Get the ForceDisable 4K support variable (second call) | Invoke `dsGetForceDisable4KSupport(handle, &disable4K2)` for each handle | `dsGetForceDisable4KSupport()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Compare values | Verify `disable4K1 == disable4K2` | Values are equal |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="getforcedisable4ksupport_neg"></a>
### TestCase Name
GetForceDisable4KSupport_neg

### TestCase ID
dsVideoPort L1-46

### TestCase Objective
Validate that `dsGetForceDisable4KSupport()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the ForceDisable 4K support variable without prior initialization | Invoke `dsGetForceDisable4KSupport(-1, &disable4K)` before `dsVideoPortInit()` | `dsGetForceDisable4KSupport()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the ForceDisable 4K support variable with invalid handle | Invoke `dsGetForceDisable4KSupport(0, &disable4K)` using handle `0` | `dsGetForceDisable4KSupport()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get the ForceDisable 4K support variable with NULL output pointer | Invoke `dsGetForceDisable4KSupport(handle, NULL)` for each valid handle | `dsGetForceDisable4KSupport()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the ForceDisable 4K support variable after module terminated | Invoke `dsGetForceDisable4KSupport(handle, &disable4K)` | `dsGetForceDisable4KSupport()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetvideoeotf_pos"></a>
### TestCase Name
dsGetVideoEOTF_pos

### TestCase ID
dsVideoPort L1-47

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsGetVideoEOTF.

### TestCase Objective
Validate that `dsGetVideoEOTF()` correctly retrieves the Electro-Optical Transfer Function (EOTF) value and produces consistent results across two consecutive calls.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Get the current video EOTF value (first call) | Invoke `dsGetVideoEOTF(handle, &eotf1)` for each handle | `dsGetVideoEOTF()` must return `dsERR_NONE` |
| Get the current video EOTF value (second call) | Invoke `dsGetVideoEOTF(handle, &eotf2)` for each handle | `dsGetVideoEOTF()` must return `dsERR_NONE` |
| Compare EOTF values | Verify `eotf1 == eotf2` | Values are equal |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetvideoeotf_neg"></a>
### TestCase Name
dsGetVideoEOTF_neg

### TestCase ID
dsVideoPort L1-48

### TestCase Objective
Validate that `dsGetVideoEOTF()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the current video EOTF value without prior initialization | Invoke `dsGetVideoEOTF(-1, &eotf)` before `dsVideoPortInit()` | `dsGetVideoEOTF()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the current video EOTF value with invalid handle | Invoke `dsGetVideoEOTF(0, &eotf)` using handle `0` | `dsGetVideoEOTF()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get the current video EOTF value with NULL output pointer | Invoke `dsGetVideoEOTF(handle, NULL)` for each valid handle | `dsGetVideoEOTF()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the current video EOTF value after module terminated | Invoke `dsGetVideoEOTF(handle, &eotf)` | `dsGetVideoEOTF()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetmatrixcoefficients_pos"></a>
### TestCase Name
dsGetMatrixCoefficients_pos

### TestCase ID
dsVideoPort L1-49

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsGetMatrixCoefficients.

### TestCase Objective
Validate that `dsGetMatrixCoefficients()` correctly retrieves the matrix coefficients and that the value matches the profile configuration.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Get the current matrix coefficients value | Invoke `dsGetMatrixCoefficients(handle, &matrixCoefficients)` for each handle | `dsGetMatrixCoefficients()` must return `dsERR_NONE` |
| Compare with profile | Verify `matrixCoefficients == gDSVideoPortConfiguration[i].matrix_coefficients` | Value matches profile |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetmatrixcoefficients_neg"></a>
### TestCase Name
dsGetMatrixCoefficients_neg

### TestCase ID
dsVideoPort L1-50

### TestCase Objective
Validate that `dsGetMatrixCoefficients()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the current matrix coefficients value without prior initialization | Invoke `dsGetMatrixCoefficients(-1, &matrixCoefficients)` before `dsVideoPortInit()` | `dsGetMatrixCoefficients()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the current matrix coefficients value with invalid handle | Invoke `dsGetMatrixCoefficients(0, &matrixCoefficients)` using handle `0` | `dsGetMatrixCoefficients()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get the current matrix coefficients value with NULL output pointer | Invoke `dsGetMatrixCoefficients(handle, NULL)` for each valid handle | `dsGetMatrixCoefficients()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the current matrix coefficients value after module terminated | Invoke `dsGetMatrixCoefficients(handle, &matrixCoefficients)` | `dsGetMatrixCoefficients()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetcolordepth_pos"></a>
### TestCase Name
dsGetColorDepth_pos

### TestCase ID
dsVideoPort L1-51

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsGetColorDepth.

### TestCase Objective
Validate that `dsGetColorDepth()` correctly retrieves the current color depth, returning the default value when no display is connected or the profile value when connected.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Get the color depth value of the video port | Invoke `dsGetColorDepth(handle, &colorDepth)` for each handle | `dsGetColorDepth()` must return `dsERR_NONE` |
| Check display connection and compare | Invoke `dsDisplayInit()`, `dsIsDisplayConnected(handle, &isConnected)`. If not connected: verify `colorDepth == DS_VIDEO_PORT_DEFAULT_COLORDEPTH`; if connected: verify `colorDepth == gDSvideoport_color_depth` | Values match expected |
| Terminate display and video port | Invoke `dsDisplayTerm()`, then `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetcolordepth_neg"></a>
### TestCase Name
dsGetColorDepth_neg

### TestCase ID
dsVideoPort L1-52

### TestCase Objective
Validate that `dsGetColorDepth()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the color depth value of the video port without prior initialization | Invoke `dsGetColorDepth(-1, &colorDepth)` before `dsVideoPortInit()` | `dsGetColorDepth()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the color depth value of the video port with invalid handle | Invoke `dsGetColorDepth(0, &colorDepth)` using handle `0` | `dsGetColorDepth()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get the color depth value of the video port with NULL output pointer | Invoke `dsGetColorDepth(handle, NULL)` for each valid handle | `dsGetColorDepth()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the color depth value of the video port after module terminated | Invoke `dsGetColorDepth(handle, &colorDepth)` | `dsGetColorDepth()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetcolorspace_pos"></a>
### TestCase Name
dsGetColorSpace_pos

### TestCase ID
dsVideoPort L1-53

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsGetColorSpace.

### TestCase Objective
Validate that `dsGetColorSpace()` correctly retrieves the current color space setting and that the value matches the profile configuration.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Get the color space setting of the video port | Invoke `dsGetColorSpace(handle, &colorSpace)` for each handle | `dsGetColorSpace()` must return `dsERR_NONE` |
| Compare with profile | Verify `colorSpace == gDSVideoPortConfiguration[i].colorspaces` | Value matches profile |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetcolorspace_neg"></a>
### TestCase Name
dsGetColorSpace_neg

### TestCase ID
dsVideoPort L1-54

### TestCase Objective
Validate that `dsGetColorSpace()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the color space setting of the video port without prior initialization | Invoke `dsGetColorSpace(-1, &colorSpace)` before `dsVideoPortInit()` | `dsGetColorSpace()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the color space setting of the video port with invalid handle | Invoke `dsGetColorSpace(0, &colorSpace)` using handle `0` | `dsGetColorSpace()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get the color space setting of the video port with NULL output pointer | Invoke `dsGetColorSpace(handle, NULL)` for each valid handle | `dsGetColorSpace()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the color space setting of the video port after module terminated | Invoke `dsGetColorSpace(handle, &colorSpace)` | `dsGetColorSpace()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetquantizationrange_pos"></a>
### TestCase Name
dsGetQuantizationRange_pos

### TestCase ID
dsVideoPort L1-55

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsGetQuantizationRange.

### TestCase Objective
Validate that `dsGetQuantizationRange()` correctly retrieves the current quantization range and that the value matches the profile configuration.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Get the quantization range of the video port | Invoke `dsGetQuantizationRange(handle, &quantizationRange)` for each handle | `dsGetQuantizationRange()` must return `dsERR_NONE` |
| Compare with profile | Verify `quantizationRange == gDSVideoPortConfiguration[i].quantization_ranges` | Value matches profile |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetquantizationrange_neg"></a>
### TestCase Name
dsGetQuantizationRange_neg

### TestCase ID
dsVideoPort L1-56

### TestCase Objective
Validate that `dsGetQuantizationRange()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the quantization range of the video port without prior initialization | Invoke `dsGetQuantizationRange(-1, &quantizationRange)` before `dsVideoPortInit()` | `dsGetQuantizationRange()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the quantization range of the video port with invalid handle | Invoke `dsGetQuantizationRange(0, &quantizationRange)` using handle `0` | `dsGetQuantizationRange()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get the quantization range of the video port with NULL output pointer | Invoke `dsGetQuantizationRange(handle, NULL)` for each valid handle | `dsGetQuantizationRange()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the quantization range of the video port after module terminated | Invoke `dsGetQuantizationRange(handle, &quantizationRange)` | `dsGetQuantizationRange()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetcurrentoutputsettings_pos"></a>
### TestCase Name
dsGetCurrentOutputSettings_pos

### TestCase ID
dsVideoPort L1-57

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsGetCurrentOutputSettings.

### TestCase Objective
Validate that `dsGetCurrentOutputSettings()` correctly retrieves all output settings (EOTF, matrix coefficients, color space, color depth, quantization range) and produces consistent results across two consecutive calls.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Get current output settings of the video port (first call) | Invoke `dsGetCurrentOutputSettings(handle, &eotf1, &matrixCoef1, &colorSpace1, &colorDepth1, &quantRange1)` | `dsGetCurrentOutputSettings()` must return `dsERR_NONE` |
| Get current output settings of the video port (second call) | Invoke `dsGetCurrentOutputSettings(handle, &eotf2, &matrixCoef2, &colorSpace2, &colorDepth2, &quantRange2)` | `dsGetCurrentOutputSettings()` must return `dsERR_NONE` |
| Compare values | Verify all paired values are equal: `eotf1==eotf2`, `matrixCoef1==matrixCoef2`, `colorSpace1==colorSpace2`, `colorDepth1==colorDepth2`, `quantRange1==quantRange2` | All values are equal |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetcurrentoutputsettings_neg"></a>
### TestCase Name
dsGetCurrentOutputSettings_neg

### TestCase ID
dsVideoPort L1-58

### TestCase Objective
Validate that `dsGetCurrentOutputSettings()` returns the correct error codes when called without initialization, with an invalid handle, or with any NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get current output settings without prior initialization | Invoke `dsGetCurrentOutputSettings(-1, &eotf, &matrixCoef, &colorSpace, &colorDepth, &quantRange)` before `dsVideoPortInit()` | `dsGetCurrentOutputSettings()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get current output settings with invalid handle | Invoke `dsGetCurrentOutputSettings(0, &eotf, &matrixCoef, &colorSpace, &colorDepth, &quantRange)` using handle `0` | `dsGetCurrentOutputSettings()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get current output settings with NULL eotf pointer | Invoke `dsGetCurrentOutputSettings(handle, NULL, &matrixCoef, &colorSpace, &colorDepth, &quantRange)` | `dsGetCurrentOutputSettings()` must return `dsERR_INVALID_PARAM` |
| Get current output settings with NULL matrix coefficients pointer | Invoke `dsGetCurrentOutputSettings(handle, &eotf, NULL, &colorSpace, &colorDepth, &quantRange)` | `dsGetCurrentOutputSettings()` must return `dsERR_INVALID_PARAM` |
| Get current output settings with NULL color space pointer | Invoke `dsGetCurrentOutputSettings(handle, &eotf, &matrixCoef, NULL, &colorDepth, &quantRange)` | `dsGetCurrentOutputSettings()` must return `dsERR_INVALID_PARAM` |
| Get current output settings with NULL color depth pointer | Invoke `dsGetCurrentOutputSettings(handle, &eotf, &matrixCoef, &colorSpace, NULL, &quantRange)` | `dsGetCurrentOutputSettings()` must return `dsERR_INVALID_PARAM` |
| Get current output settings with NULL quantization range pointer | Invoke `dsGetCurrentOutputSettings(handle, &eotf, &matrixCoef, &colorSpace, &colorDepth, NULL)` | `dsGetCurrentOutputSettings()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get current output settings after module terminated | Invoke `dsGetCurrentOutputSettings(handle, &eotf, &matrixCoef, &colorSpace, &colorDepth, &quantRange)` | `dsGetCurrentOutputSettings()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsisoutputhdr_pos"></a>
### TestCase Name
dsIsOutputHDR_pos

### TestCase ID
dsVideoPort L1-59

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsIsOutputHDR.

### TestCase Objective
Validate that `dsIsOutputHDR()` correctly returns the HDR output status and produces consistent results across two consecutive calls.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Check if video output is HDR (first call) | Invoke `dsIsOutputHDR(handle, &hdr1)` for each handle | `dsIsOutputHDR()` must return `dsERR_NONE` |
| Check if video output is HDR (second call) | Invoke `dsIsOutputHDR(handle, &hdr2)` for each handle | `dsIsOutputHDR()` must return `dsERR_NONE` |
| Compare HDR status values | Verify `hdr1 == hdr2` | Values are equal |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsisoutputhdr_neg"></a>
### TestCase Name
dsIsOutputHDR_neg

### TestCase ID
dsVideoPort L1-60

### TestCase Objective
Validate that `dsIsOutputHDR()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Check if video output is HDR without prior initialization | Invoke `dsIsOutputHDR(-1, &hdrStatus)` before `dsVideoPortInit()` | `dsIsOutputHDR()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Check if video output is HDR with invalid handle | Invoke `dsIsOutputHDR(0, &hdrStatus)` using handle `0` | `dsIsOutputHDR()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Check if video output is HDR with NULL output pointer | Invoke `dsIsOutputHDR(handle, NULL)` for each valid handle | `dsIsOutputHDR()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Check if video output is HDR after module terminated | Invoke `dsIsOutputHDR(handle, &hdrStatus)` | `dsIsOutputHDR()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsresetoutputtosdr_pos"></a>
### TestCase Name
dsResetOutputToSDR_pos

### TestCase ID
dsVideoPort L1-61

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsResetOutputToSDR.

### TestCase Objective
Validate that `dsResetOutputToSDR()` successfully resets the video output to SDR on source devices and returns `dsERR_OPERATION_NOT_SUPPORTED` on sink devices.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Reset Video Output to SDR | Invoke `dsResetOutputToSDR()` | Source device (`gSourceType==1`): `dsResetOutputToSDR()` must return `dsERR_NONE`; Sink device (`gSourceType==0`): `dsResetOutputToSDR()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsresetoutputtosdr_neg"></a>
### TestCase Name
dsResetOutputToSDR_neg

### TestCase ID
dsVideoPort L1-62

### TestCase Objective
Validate that `dsResetOutputToSDR()` returns the correct error code when called without initialization or after termination.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Reset Video Output to SDR without prior initialization | Invoke `dsResetOutputToSDR()` before `dsVideoPortInit()` | `dsResetOutputToSDR()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Reset Video Output to SDR after module terminated | Invoke `dsResetOutputToSDR()` | `dsResetOutputToSDR()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dssethdmipreference_pos"></a>
### TestCase Name
dsSetHdmiPreference_pos

### TestCase ID
dsVideoPort L1-63

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsSetHdmiPreference.

### TestCase Objective
Validate that `dsSetHdmiPreference()` successfully sets the HDMI preference (HDCP protocol version) for each video port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Set the preferred HDMI Protocol of the video port | Invoke `dsSetHdmiPreference(handle, &gDSVideoPortConfiguration[i].hdcp_protocol_version)` for each handle | `dsSetHdmiPreference()` must return `dsERR_NONE` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dssethdmipreference_neg"></a>
### TestCase Name
dsSetHdmiPreference_neg

### TestCase ID
dsVideoPort L1-64

### TestCase Objective
Validate that `dsSetHdmiPreference()` returns the correct error codes when called without initialization, with an invalid handle, or with an out-of-range HDCP protocol value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set the preferred HDMI Protocol without prior initialization | Invoke `dsSetHdmiPreference(-1, &dsHDCP_VERSION_1X)` before `dsVideoPortInit()` | `dsSetHdmiPreference()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Set the preferred HDMI Protocol with invalid handle | Invoke `dsSetHdmiPreference(0, &dsHDCP_VERSION_1X)` using handle `0` | `dsSetHdmiPreference()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Set the preferred HDMI Protocol with out-of-range protocol value | Invoke `dsSetHdmiPreference(handle, &dsHDCP_VERSION_MAX)` for each valid handle | `dsSetHdmiPreference()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Set the preferred HDMI Protocol after module terminated | Invoke `dsSetHdmiPreference(handle, &dsHDCP_VERSION_1X)` | `dsSetHdmiPreference()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgethdmipreference_pos"></a>
### TestCase Name
dsGetHdmiPreference_pos

### TestCase ID
dsVideoPort L1-65

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsGetHdmiPreference.

### TestCase Objective
Validate that `dsGetHdmiPreference()` correctly retrieves the HDMI preference and that the value matches the profile configuration.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Get the preferred HDMI Protocol version of the video port | Invoke `dsGetHdmiPreference(handle, &hdcpCurrentProtocol)` for each handle | `dsGetHdmiPreference()` must return `dsERR_NONE` |
| Compare with profile | Verify `hdcpCurrentProtocol == gDSVideoPortConfiguration[i].hdcp_protocol_version` | Value matches profile |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgethdmipreference_neg"></a>
### TestCase Name
dsGetHdmiPreference_neg

### TestCase ID
dsVideoPort L1-66

### TestCase Objective
Validate that `dsGetHdmiPreference()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the preferred HDMI Protocol version without prior initialization | Invoke `dsGetHdmiPreference(-1, &hdcpCurrentProtocol)` before `dsVideoPortInit()` | `dsGetHdmiPreference()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the preferred HDMI Protocol version with invalid handle | Invoke `dsGetHdmiPreference(0, &hdcpCurrentProtocol)` using handle `0` | `dsGetHdmiPreference()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get the preferred HDMI Protocol version with NULL output pointer | Invoke `dsGetHdmiPreference(handle, NULL)` for each valid handle | `dsGetHdmiPreference()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the preferred HDMI Protocol version after module terminated | Invoke `dsGetHdmiPreference(handle, &hdcpCurrentProtocol)` | `dsGetHdmiPreference()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetignoreedidstatus_pos"></a>
### TestCase Name
dsGetIgnoreEDIDStatus_pos

### TestCase ID
dsVideoPort L1-67

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsGetIgnoreEDIDStatus.

### TestCase Objective
Validate that `dsGetIgnoreEDIDStatus()` correctly retrieves the IgnoreEDID status on source devices and produces consistent results across two consecutive calls.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Get the IgnoreEDID status variable (first call) | Invoke `dsGetIgnoreEDIDStatus(handle, &ignoreEDIDStatus1)` for each handle | Source device: `dsGetIgnoreEDIDStatus()` must return `dsERR_NONE`; Sink device: `dsGetIgnoreEDIDStatus()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Get the IgnoreEDID status variable (second call, source only) | Invoke `dsGetIgnoreEDIDStatus(handle, &ignoreEDIDStatus2)` for source ports | `dsGetIgnoreEDIDStatus()` must return `dsERR_NONE` |
| Compare values (source only) | Verify `ignoreEDIDStatus1 == ignoreEDIDStatus2` | Values are equal |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetignoreedidstatus_neg"></a>
### TestCase Name
dsGetIgnoreEDIDStatus_neg

### TestCase ID
dsVideoPort L1-68

### TestCase Objective
Validate that `dsGetIgnoreEDIDStatus()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the IgnoreEDID status variable without prior initialization | Invoke `dsGetIgnoreEDIDStatus(-1, &ignoreEDIDStatus)` before `dsVideoPortInit()` | `dsGetIgnoreEDIDStatus()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the IgnoreEDID status variable with invalid handle | Invoke `dsGetIgnoreEDIDStatus(0, &ignoreEDIDStatus)` using handle `0` | `dsGetIgnoreEDIDStatus()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get the IgnoreEDID status variable with NULL output pointer | Invoke `dsGetIgnoreEDIDStatus(handle, NULL)` for each valid handle | `dsGetIgnoreEDIDStatus()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the IgnoreEDID status variable after module terminated | Invoke `dsGetIgnoreEDIDStatus(handle, &ignoreEDIDStatus)` | `dsGetIgnoreEDIDStatus()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dssetbackgroundcolor_pos"></a>
### TestCase Name
dsSetBackgroundColor_pos

### TestCase ID
dsVideoPort L1-69

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsSetBackgroundColor.

### TestCase Objective
Validate that `dsSetBackgroundColor()` successfully sets each valid background color on source devices and returns `dsERR_OPERATION_NOT_SUPPORTED` on sink devices.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Set the background color of the video port | Invoke `dsSetBackgroundColor(handle, color)` for each color in `dsVideoBackgroundColor_t` enum (`dsVIDEO_BGCOLOR_BLUE` through `dsVIDEO_BGCOLOR_MAX-1`) | Source device: `dsSetBackgroundColor()` must return `dsERR_NONE`; Sink device: `dsSetBackgroundColor()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetbackgroundcolor_neg"></a>
### TestCase Name
dsSetBackgroundColor_neg

### TestCase ID
dsVideoPort L1-70

### TestCase Objective
Validate that `dsSetBackgroundColor()` returns the correct error codes when called without initialization, with an invalid handle, or with an invalid color value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set the background color of the video port without prior initialization | Invoke `dsSetBackgroundColor(-1, dsVIDEO_BGCOLOR_BLUE)` before `dsVideoPortInit()` | `dsSetBackgroundColor()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Set the background color of the video port with invalid handle | Invoke `dsSetBackgroundColor(0, dsVIDEO_BGCOLOR_BLUE)` using handle `0` | `dsSetBackgroundColor()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Set the background color of the video port with invalid color value | Invoke `dsSetBackgroundColor(handle, dsVIDEO_BGCOLOR_MAX)` for each valid handle | `dsSetBackgroundColor()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Set the background color of the video port after module terminated | Invoke `dsSetBackgroundColor(handle, dsVIDEO_BGCOLOR_BLACK)` | `dsSetBackgroundColor()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dssetforcehdrmode_pos"></a>
### TestCase Name
dsSetForceHDRMode_pos

### TestCase ID
dsVideoPort L1-71

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsSetForceHDRMode.

### TestCase Objective
Validate that `dsSetForceHDRMode()` successfully sets the HDR mode on source devices and returns `dsERR_OPERATION_NOT_SUPPORTED` on sink devices.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Set/Reset the force HDR mode | Invoke `dsSetForceHDRMode(handle, gDSVideoPortConfiguration[i].hdr_capabilities)` for each handle | Source device: `dsSetForceHDRMode()` must return `dsERR_NONE`; Sink device: `dsSetForceHDRMode()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetforcehdrmode_neg"></a>
### TestCase Name
dsSetForceHDRMode_neg

### TestCase ID
dsVideoPort L1-72

### TestCase Objective
Validate that `dsSetForceHDRMode()` returns the correct error codes when called without initialization, with an invalid handle, or with an invalid HDR mode value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set/Reset the force HDR mode without prior initialization | Invoke `dsSetForceHDRMode(-1, mode)` before `dsVideoPortInit()` | `dsSetForceHDRMode()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Set/Reset the force HDR mode with invalid handle | Invoke `dsSetForceHDRMode(0, mode)` using handle `0` | `dsSetForceHDRMode()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Set/Reset the force HDR mode with invalid mode value | Invoke `dsSetForceHDRMode(handle, dsHDRSTANDARD_Invalid)` for each valid handle | `dsSetForceHDRMode()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Set/Reset the force HDR mode after module terminated | Invoke `dsSetForceHDRMode(handle, mode)` | `dsSetForceHDRMode()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dscolordepthcapb_pos"></a>
### TestCase Name
dsColorDepthCapb_pos

### TestCase ID
dsVideoPort L1-73

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsColorDepthCapabilities.

### TestCase Objective
Validate that `dsColorDepthCapabilities()` correctly retrieves the color depth capabilities on source devices and returns `dsERR_OPERATION_NOT_SUPPORTED` on sink devices.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Get the color depth capabilities of the video port | Invoke `dsColorDepthCapabilities(handle, &colorDepthCapability)` for each handle | Source device: `dsColorDepthCapabilities()` must return `dsERR_NONE`; Sink device: `dsColorDepthCapabilities()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Compare with profile (source only) | Verify `colorDepthCapability == gDSvideoport_color_depth` | Value matches profile |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dscolordepthcapb_neg"></a>
### TestCase Name
dsColorDepthCapb_neg

### TestCase ID
dsVideoPort L1-74

### TestCase Objective
Validate that `dsColorDepthCapabilities()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the color depth capabilities of the video port without prior initialization | Invoke `dsColorDepthCapabilities(-1, &colorDepthCapability)` before `dsVideoPortInit()` | `dsColorDepthCapabilities()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the color depth capabilities of the video port with invalid handle | Invoke `dsColorDepthCapabilities(0, &colorDepthCapability)` using handle `0` | `dsColorDepthCapabilities()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get the color depth capabilities of the video port with NULL output pointer | Invoke `dsColorDepthCapabilities(handle, NULL)` for each valid handle | `dsColorDepthCapabilities()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the color depth capabilities of the video port after module terminated | Invoke `dsColorDepthCapabilities(handle, &colorDepthCapability)` | `dsColorDepthCapabilities()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetpreferredcolordepth_pos"></a>
### TestCase Name
dsGetPreferredColorDepth_pos

### TestCase ID
dsVideoPort L1-75

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsGetPreferredColorDepth.

### TestCase Objective
Validate that `dsGetPreferredColorDepth()` correctly retrieves the preferred color depth on source devices and returns `dsERR_OPERATION_NOT_SUPPORTED` on sink devices.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Get the preferred color depth value | Invoke `dsGetPreferredColorDepth(handle, &colorDepth)` for each handle | Source device: `dsGetPreferredColorDepth()` must return `dsERR_NONE` with `colorDepth == gDSvideoport_color_depth`; Sink device: `dsGetPreferredColorDepth()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetpreferredcolordepth_neg"></a>
### TestCase Name
dsGetPreferredColorDepth_neg

### TestCase ID
dsVideoPort L1-76

### TestCase Objective
Validate that `dsGetPreferredColorDepth()` returns the correct error codes when called without initialization, with an invalid handle, or with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get the preferred color depth value without prior initialization | Invoke `dsGetPreferredColorDepth(-1, &colorDepth)` before `dsVideoPortInit()` | `dsGetPreferredColorDepth()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the preferred color depth value with invalid handle | Invoke `dsGetPreferredColorDepth(0, &colorDepth)` using handle `0` | `dsGetPreferredColorDepth()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Get the preferred color depth value with NULL output pointer | Invoke `dsGetPreferredColorDepth(handle, NULL)` for each valid handle | `dsGetPreferredColorDepth()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Get the preferred color depth value after module terminated | Invoke `dsGetPreferredColorDepth(handle, &colorDepth)` | `dsGetPreferredColorDepth()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dssetpreferredcolordepth_pos"></a>
### TestCase Name
dsSetPreferredColorDepth_pos

### TestCase ID
dsVideoPort L1-77

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — RPI doesn't support dsSetPreferredColorDepth.

### TestCase Objective
Validate that `dsSetPreferredColorDepth()` successfully sets the preferred color depth on source devices and returns `dsERR_OPERATION_NOT_SUPPORTED` on sink devices.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` with valid handles |
| Set the preferred color depth for the video port | Invoke `dsSetPreferredColorDepth(handle, gDSvideoport_color_depth)` for each handle | Source device: `dsSetPreferredColorDepth()` must return `dsERR_NONE`; Sink device: `dsSetPreferredColorDepth()` must return `dsERR_OPERATION_NOT_SUPPORTED` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetpreferredcolordepth_neg"></a>
### TestCase Name
dsSetPreferredColorDepth_neg

### TestCase ID
dsVideoPort L1-78

### TestCase Objective
Validate that `dsSetPreferredColorDepth()` returns the correct error codes when called without initialization, with an invalid handle, or with an unsupported color depth value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set the preferred color depth for the video port without prior initialization | Invoke `dsSetPreferredColorDepth(-1, dsDISPLAY_COLORDEPTH_8BIT)` before `dsVideoPortInit()` | `dsSetPreferredColorDepth()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the underlying Video Port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Set the preferred color depth for the video port with invalid handle | Invoke `dsSetPreferredColorDepth(0, dsDISPLAY_COLORDEPTH_8BIT)` using handle `0` | `dsSetPreferredColorDepth()` must return `dsERR_INVALID_PARAM` |
| Get the handle for a video port | Invoke `dsGetVideoPort(type, index, &handle)` for each port | `dsGetVideoPort()` must return `dsERR_NONE` |
| Set the preferred color depth for the video port with unsupported value | Invoke `dsSetPreferredColorDepth(handle, 0x60)` (unsupported value) for each valid handle | `dsSetPreferredColorDepth()` must return `dsERR_INVALID_PARAM` |
| Terminate the underlying Video Port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |
| Set the preferred color depth for the video port after module terminated | Invoke `dsSetPreferredColorDepth(handle, dsDISPLAY_COLORDEPTH_12BIT)` | `dsSetPreferredColorDepth()` must return `dsERR_NOT_INITIALIZED` |

---

## Post-conditions

- The `hal_test_dshal` binary exits cleanly after all test cases complete.
- `dsVideoPortTerm()` is called at the end of each test case, restoring the video port system to its uninitialized default state.

---

## Test Attributes

| Attribute | Value |
| --- | --- |
| Supported Models | Video_Accelerator, RPI-Client |
| Estimated Duration | 80 minutes |
| Priority | High |
| TDK Release Version | M134 |
