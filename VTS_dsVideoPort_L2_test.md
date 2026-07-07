## TestScript Name
VTS_dsVideoPort_L2_test

## TestScript ID
VTS_Test_06

## Table of Contents

1. [Objective](#objective)
2. [Pre-conditions](#pre-conditions)
3. [Test Cases](#test-cases)
   - [EnableDisabledVideoPorts](#enabledisabledvideoports)
   - [VerifyDisplayAndPortStatus](#verifydisplayandportstatus)
   - [RetrieveVerifySurroundModeCapb](#retrieveverifysurroundmodecapb)
   - [VerifySupportedTvRes](#verifysupportedtvres)
   - [GetHDRCapabilities](#gethdrcapabilities)
   - [GetHDCPStatus](#gethdcpstatus)
   - [VerifyHDCPProtocolStatus](#verifyhdcpprotocolstatus)
   - [SetAndGetHdmiPreference](#setandgethdmipreference)
   - [GetColorSpace](#getcolorspace)
   - [GetColorDepth](#getcolordepth)
   - [GetQuantizationRange](#getquantizationrange)
   - [GetMatrixCoefficients](#getmatrixcoefficients)
   - [SetAndGetResolution_src](#setandgetresolution_src)
   - [SetAndGetPreferredColorDepth_src](#setandgetpreferredcolordepth_src)
   - [CheckColorDepthCapb_src](#checkcolordepthcapb_src)
4. [Post-conditions](#post-conditions)
5. [Test Attributes](#test-attributes)

---

## Objective

This script executes VTS L2 (Level 2) test cases for the Device Settings Video Port HAL module (`dsVideoPort`). L2 tests validate end-to-end workflows that exercise sequences of HAL APIs and compare results against the device profile configuration to verify functional correctness on source platforms. No external stimulus is required; the tests rely on the HAL implementation and the profile configuration. The binary used is `hal_test_dshal`, invoked with the profile `Source_4K_VideoPort.yaml`.

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

<a id="enabledisabledvideoports"></a>
### TestCase Name
EnableDisabledVideoPorts

### TestCase ID
dsVideoPort L2-1

### TestCase Objective
Validate that `dsEnableVideoPort()` and `dsIsVideoPortEnabled()` work correctly together — that enabling and disabling video ports can be verified through the status query API.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the video port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get video port handle for each supported port | Invoke `dsGetVideoPort(type, index, &handle)` for each port from the profile | `dsGetVideoPort()` must return `dsERR_NONE` and a valid handle |
| Enable the video port | Invoke `dsEnableVideoPort(handle, true)` | `dsEnableVideoPort()` must return `dsERR_NONE` |
| Verify video port is enabled | Invoke `dsIsVideoPortEnabled(handle, &enabled)` | `dsIsVideoPortEnabled()` must return `dsERR_NONE` and `enabled` must be `true` |
| Disable the video port | Invoke `dsEnableVideoPort(handle, false)` | `dsEnableVideoPort()` must return `dsERR_NONE` |
| Verify video port is disabled | Invoke `dsIsVideoPortEnabled(handle, &enabled)` | `dsIsVideoPortEnabled()` must return `dsERR_NONE` and `enabled` must be `false` |
| Terminate the video port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="verifydisplayandportstatus"></a>
### TestCase Name
VerifyDisplayAndPortStatus

### TestCase ID
dsVideoPort L2-2

### TestCase Objective
Validate that `dsIsDisplayConnected()` and `dsIsVideoPortActive()` correctly report the display connection and port active status for all video ports on source platforms (display not connected for source).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the video port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get video port handle for each supported port | Invoke `dsGetVideoPort(type, index, &handle)` for each port from the profile | `dsGetVideoPort()` must return `dsERR_NONE` and a valid handle |
| Check if display is connected (source) | Invoke `dsIsDisplayConnected(handle, &connected)` | `dsIsDisplayConnected()` must return `dsERR_NONE` and `connected` must be `false` for source platforms |
| Check if video port is active (source) | Invoke `dsIsVideoPortActive(handle, &active)` | `dsIsVideoPortActive()` must return `dsERR_NONE` and `active` must be `false` for source platforms |
| Terminate the video port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="retrieveverifysurroundmodecapb"></a>
### TestCase Name
RetrieveVerifySurroundModeCapb

### TestCase ID
dsVideoPort L2-3

### TestCase Objective
Validate that `dsIsDisplaySurround()` returns `false` and `dsGetSurroundMode()` returns `dsSURROUNDMODE_NONE` for source platforms without a connected display.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the video port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get video port handle for each supported port | Invoke `dsGetVideoPort(type, index, &handle)` for each port from the profile | `dsGetVideoPort()` must return `dsERR_NONE` and a valid handle |
| Check if display is in surround mode (source) | Invoke `dsIsDisplaySurround(handle, &surround)` | `dsIsDisplaySurround()` must return `dsERR_NONE` and `surround` must be `false` |
| Get surround mode (source) | Invoke `dsGetSurroundMode(handle, &surroundMode)` | `dsGetSurroundMode()` must return `dsERR_NONE` and `surroundMode` must equal `dsSURROUNDMODE_NONE` |
| Terminate the video port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="verifysupportedtvres"></a>
### TestCase Name
VerifySupportedTvRes

### TestCase ID
dsVideoPort L2-4

### TestCase Objective
Validate that `dsSupportedTvResolutions()` returns the correct supported TV resolution capabilities for each video port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the video port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get video port handle for each supported port | Invoke `dsGetVideoPort(type, index, &handle)` for each port from the profile | `dsGetVideoPort()` must return `dsERR_NONE` and a valid handle |
| Get supported TV resolutions | Invoke `dsSupportedTvResolutions(handle, &resolutions)` | `dsSupportedTvResolutions()` must return `dsERR_NONE` and when display is not connected, `resolutions` must equal `dsTV_RESOLUTION_480p` |
| Terminate the video port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="gethdrcapabilities"></a>
### TestCase Name
GetHDRCapabilities

### TestCase ID
dsVideoPort L2-5

### TestCase Objective
Validate that `dsGetTVHDRCapabilities()` returns the correct HDR capabilities for each video port; when display is not connected, returns `dsHDRSTANDARD_SDR`.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI (REFPLTV-2576).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the video port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get video port handle for each supported port | Invoke `dsGetVideoPort(type, index, &handle)` for each port from the profile | `dsGetVideoPort()` must return `dsERR_NONE` and a valid handle |
| Get TV HDR capabilities | Invoke `dsGetTVHDRCapabilities(handle, &capabilities)` | `dsGetTVHDRCapabilities()` must return `dsERR_NONE` and when display is not connected, `capabilities` must equal `dsHDRSTANDARD_SDR` |
| Terminate the video port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="gethdcpstatus"></a>
### TestCase Name
GetHDCPStatus

### TestCase ID
dsVideoPort L2-6

### TestCase Objective
Validate that `dsGetHDCPStatus()` returns the correct HDCP status for each video port; when display is not connected, returns `dsHDCP_STATUS_UNPOWERED`.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI (REFPLTV-2542).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the video port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get video port handle for each supported port | Invoke `dsGetVideoPort(type, index, &handle)` for each port from the profile | `dsGetVideoPort()` must return `dsERR_NONE` and a valid handle |
| Get HDCP status | Invoke `dsGetHDCPStatus(handle, &status)` | `dsGetHDCPStatus()` must return `dsERR_NONE` and when display is not connected, `status` must equal `dsHDCP_STATUS_UNPOWERED` |
| Terminate the video port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="verifyhdcpprotocolstatus"></a>
### TestCase Name
VerifyHDCPProtocolStatus

### TestCase ID
dsVideoPort L2-7

### TestCase Objective
Validate that `dsGetHDCPProtocol()` returns the HDCP protocol version matching the expected value from the device profile configuration.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the video port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get video port handle for each supported port | Invoke `dsGetVideoPort(type, index, &handle)` for each port from the profile | `dsGetVideoPort()` must return `dsERR_NONE` and a valid handle |
| Get HDCP protocol version | Invoke `dsGetHDCPProtocol(handle, &protocolVersion)` | `dsGetHDCPProtocol()` must return `dsERR_NONE` and `protocolVersion` must equal `hdcp_protocol_version` from the profile |
| Terminate the video port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="setandgethdmipreference"></a>
### TestCase Name
SetAndGetHdmiPreference

### TestCase ID
dsVideoPort L2-8

### TestCase Objective
Validate that `dsSetHdmiPreference()` and `dsGetHdmiPreference()` work correctly together — the HDCP protocol preference written can be read back with the same value.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the video port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get video port handle for each supported port | Invoke `dsGetVideoPort(type, index, &handle)` for each port from the profile | `dsGetVideoPort()` must return `dsERR_NONE` and a valid handle |
| Get HDCP protocol version | Invoke `dsGetHDCPProtocol(handle, &protocolVersion)` | `dsGetHDCPProtocol()` must return `dsERR_NONE` |
| Set HDMI preference for each HDCP version | Invoke `dsSetHdmiPreference(handle, &version)` for each version from `dsHDCP_VERSION_1X` to `protocolVersion` | `dsSetHdmiPreference()` must return `dsERR_NONE` |
| Verify HDMI preference was set | Invoke `dsGetHdmiPreference(handle, &hdcpCurrentProtocolGet)` after each set call | `dsGetHdmiPreference()` must return `dsERR_NONE` and `hdcpCurrentProtocolGet` must equal the version that was set |
| Terminate the video port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="getcolorspace"></a>
### TestCase Name
GetColorSpace

### TestCase ID
dsVideoPort L2-9

### TestCase Objective
Validate that `dsGetColorSpace()` returns the color space matching the expected value from the device profile configuration.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the video port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get video port handle for each supported port | Invoke `dsGetVideoPort(type, index, &handle)` for each port from the profile | `dsGetVideoPort()` must return `dsERR_NONE` and a valid handle |
| Get color space | Invoke `dsGetColorSpace(handle, &colorSpace)` | `dsGetColorSpace()` must return `dsERR_NONE` and `colorSpace` must equal `colorspaces` from the profile |
| Terminate the video port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="getcolordepth"></a>
### TestCase Name
GetColorDepth

### TestCase ID
dsVideoPort L2-10

### TestCase Objective
Validate that `dsGetColorDepth()` returns the color depth; when display is not connected, returns the default color depth value.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the video port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get video port handle for each supported port | Invoke `dsGetVideoPort(type, index, &handle)` for each port from the profile | `dsGetVideoPort()` must return `dsERR_NONE` and a valid handle |
| Get color depth | Invoke `dsGetColorDepth(handle, &colorDepth)` | `dsGetColorDepth()` must return `dsERR_NONE` and when display is not connected, `colorDepth` must equal the default color depth (`DS_VIDEO_PORT_DEFAULT_COLORDEPTH`) |
| Terminate the video port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="getquantizationrange"></a>
### TestCase Name
GetQuantizationRange

### TestCase ID
dsVideoPort L2-11

### TestCase Objective
Validate that `dsGetQuantizationRange()` returns `dsDISPLAY_QUANTIZATIONRANGE_UNKNOWN` for source platforms without a connected display.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the video port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get video port handle for each supported port | Invoke `dsGetVideoPort(type, index, &handle)` for each port from the profile | `dsGetVideoPort()` must return `dsERR_NONE` and a valid handle |
| Get quantization range (source) | Invoke `dsGetQuantizationRange(handle, &quantizationRange)` | `dsGetQuantizationRange()` must return `dsERR_NONE` and `quantizationRange` must equal `dsDISPLAY_QUANTIZATIONRANGE_UNKNOWN` |
| Terminate the video port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="getmatrixcoefficients"></a>
### TestCase Name
GetMatrixCoefficients

### TestCase ID
dsVideoPort L2-12

### TestCase Objective
Validate that `dsGetMatrixCoefficients()` returns `dsDISPLAY_MATRIXCOEFFICIENT_UNKNOWN` for source platforms without a connected display.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the video port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get video port handle for each supported port | Invoke `dsGetVideoPort(type, index, &handle)` for each port from the profile | `dsGetVideoPort()` must return `dsERR_NONE` and a valid handle |
| Get matrix coefficients (source) | Invoke `dsGetMatrixCoefficients(handle, &matrixCoefficients)` | `dsGetMatrixCoefficients()` must return `dsERR_NONE` and `matrixCoefficients` must equal `dsDISPLAY_MATRIXCOEFFICIENT_UNKNOWN` |
| Terminate the video port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="setandgetresolution_src"></a>
### TestCase Name
SetAndGetResolution_src

### TestCase ID
dsVideoPort L2-13

### TestCase Objective
Validate that `dsSetResolution()` and `dsGetResolution()` work correctly together on source platforms — that the resolution set can be read back with matching values.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the video port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get video port handle for each supported port | Invoke `dsGetVideoPort(type, index, &handle)` for each port from the profile | `dsGetVideoPort()` must return `dsERR_NONE` and a valid handle |
| Set resolution for each supported resolution | Invoke `dsSetResolution(handle, &pSetResolution)` for each supported resolution from the profile | `dsSetResolution()` must return `dsERR_NONE` |
| Verify resolution was set | Invoke `dsGetResolution(handle, &getResolution)` after each set call | `dsGetResolution()` must return `dsERR_NONE` and `getResolution` fields (name, pixelResolution, aspectRatio, stereoScopicMode, frameRate, interlaced) must match `pSetResolution` |
| Terminate the video port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="setandgetpreferredcolordepth_src"></a>
### TestCase Name
SetAndGetPreferredColorDepth_src

### TestCase ID
dsVideoPort L2-14

### TestCase Objective
Validate that `dsSetPreferredColorDepth()` and `dsGetPreferredColorDepth()` work correctly together on source platforms.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the video port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get video port handle for each supported port | Invoke `dsGetVideoPort(type, index, &handle)` for each port from the profile | `dsGetVideoPort()` must return `dsERR_NONE` and a valid handle |
| Set preferred color depth for each valid value | Invoke `dsSetPreferredColorDepth(handle, colorDepthSet)` for each value from `dsDISPLAY_COLORDEPTH_8BIT` to `dsDISPLAY_COLORDEPTH_AUTO` | `dsSetPreferredColorDepth()` must return `dsERR_NONE` |
| Verify preferred color depth | Invoke `dsGetPreferredColorDepth(handle, &colorDepthGet)` after each set call | `dsGetPreferredColorDepth()` must return `dsERR_NONE` and `colorDepthGet` must equal `dsDISPLAY_COLORDEPTH_UNKNOWN` (source behavior) |
| Terminate the video port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

<a id="checkcolordepthcapb_src"></a>
### TestCase Name
CheckColorDepthCapb_src

### TestCase ID
dsVideoPort L2-15

### TestCase Objective
Validate that `dsColorDepthCapabilities()` returns the color depth capability equal to `dsDISPLAY_COLORDEPTH_8BIT` for source platforms.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the video port sub-system | Invoke `dsVideoPortInit()` | `dsVideoPortInit()` must return `dsERR_NONE` |
| Get video port handle for each supported port | Invoke `dsGetVideoPort(type, index, &handle)` for each port from the profile | `dsGetVideoPort()` must return `dsERR_NONE` and a valid handle |
| Get color depth capabilities (source) | Invoke `dsColorDepthCapabilities(handle, &colorDepthCapability)` | `dsColorDepthCapabilities()` must return `dsERR_NONE` and `colorDepthCapability` must equal `dsDISPLAY_COLORDEPTH_8BIT` |
| Terminate the video port sub-system | Invoke `dsVideoPortTerm()` | `dsVideoPortTerm()` must return `dsERR_NONE` |

---

## Post-conditions

1. The `hal_test_dshal` binary exits cleanly after completing all test cases in the `[L2 dsVideoPort - Source]` suite.
2. The DS Video Port HAL module is terminated (via `dsVideoPortTerm()`) at the end of each test case, restoring the uninitialized default state.

---

## Test Attributes

| Attribute | Value |
| --- | --- |
| Supported Models | Video_Accelerator, RPI-Client |
| Estimated Duration | 15 minutes |
| Priority | High |
| TDK Release Version | M134 |
