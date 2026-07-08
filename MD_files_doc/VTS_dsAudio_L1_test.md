## TestScript Name
VTS_dsAudio_L1_test

## TestScript ID
VTS_Test_04

## Table of Contents

1. [Objective](#objective)
2. [Pre-conditions](#pre-conditions)
3. [Test Cases](#test-cases)
   - [dsAudioPortInit_pos](#dsaudioportinit_pos)
   - [dsAudioPortInit_neg](#dsaudioportinit_neg)
   - [dsAudioPortTerm_pos](#dsaudioportterm_pos)
   - [dsAudioPortTerm_neg](#dsaudioportterm_neg)
   - [dsGetAudioPort_pos](#dsgetaudioport_pos)
   - [dsGetAudioPort_neg](#dsgetaudioport_neg)
   - [dsGetAudioFormat_pos](#dsgetaudioformat_pos)
   - [dsGetAudioFormat_neg](#dsgetaudioformat_neg)
   - [dsGetAudioCompression_pos](#dsgetaudiocompression_pos)
   - [dsGetAudioCompression_neg](#dsgetaudiocompression_neg)
   - [dsSetAudioCompression_pos](#dssetaudiocompression_pos)
   - [dsSetAudioCompression_neg](#dssetaudiocompression_neg)
   - [dsGetDialogEnhance_pos](#dsgetdialogenhance_pos)
   - [dsGetDialogEnhance_neg](#dsgetdialogenhance_neg)
   - [dsSetDialogEnhance_pos](#dssetdialogenhance_pos)
   - [dsSetDialogEnhance_neg](#dssetdialogenhance_neg)
   - [dsGetDolbyVolumeMode_pos](#dsgetdolbyvolumemode_pos)
   - [dsGetDolbyVolumeMode_neg](#dsgetdolbyvolumemode_neg)
   - [dsSetDolbyVolumeMode_pos](#dssetdolbyvolumemode_pos)
   - [dsSetDolbyVolumeMode_neg](#dssetdolbyvolumemode_neg)
   - [dsGetIntelliEqMode_pos](#dsgetintelleqmode_pos)
   - [dsGetIntelliEqMode_neg](#dsgetintelleqmode_neg)
   - [dsSetIntelliEqMode_pos](#dssetintelleqmode_pos)
   - [dsSetIntelliEqMode_neg](#dssetintelleqmode_neg)
   - [dsGetVolumeLeveller_pos](#dsgetvolumeleveller_pos)
   - [dsGetVolumeLeveller_neg](#dsgetvolumeleveller_neg)
   - [dsSetVolumeLeveller_pos](#dssetvolumeleveller_pos)
   - [dsSetVolumeLeveller_neg](#dssetvolumeleveller_neg)
   - [dsGetBassEnhancer_pos](#dsgetbassenhancer_pos)
   - [dsGetBassEnhancer_neg](#dsgetbassenhancer_neg)
   - [dsSetBassEnhancer_pos](#dssetbassenhancer_pos)
   - [dsSetBassEnhancer_neg](#dssetbassenhancer_neg)
   - [dsIsSurroundDecoderEnabled_pos](#dsissurrounddecoderenabledpos)
   - [dsIsSurroundDecoderEnabled_neg](#dsissurrounddecoderenablednneg)
   - [dsEnableSurroundDecoder_pos](#dsenablesurrounddecoder_pos)
   - [dsEnableSurroundDecoder_neg](#dsenablesurrounddecoder_neg)
   - [dsGetDRCMode_pos](#dsgetdrcmode_pos)
   - [dsGetDRCMode_neg](#dsgetdrcmode_neg)
   - [dsSetDRCMode_pos](#dssetdrcmode_pos)
   - [dsSetDRCMode_neg](#dssetdrcmode_neg)
   - [dsGetSurroundVirt_pos](#dsgetsurroundvirt_pos)
   - [dsGetSurroundVirt_neg](#dsgetsurroundvirt_neg)
   - [dsSetSurroundVirt_pos](#dssetsurroundvirt_pos)
   - [dsSetSurroundVirt_neg](#dssetsurroundvirt_neg)
   - [dsGetMISteering_pos](#dsgetmisteering_pos)
   - [dsGetMISteering_neg](#dsgetmisteering_neg)
   - [dsSetMISteering_pos](#dssetmisteering_pos)
   - [dsSetMISteering_neg](#dssetmisteering_neg)
   - [dsGetGraphicEqMode_pos](#dsgetgraphiceqmode_pos)
   - [dsGetGraphicEqMode_neg](#dsgetgraphiceqmode_neg)
   - [dsSetGraphicEqMode_pos](#dssetgraphiceqmode_pos)
   - [dsSetGraphicEqMode_neg](#dssetgraphiceqmode_neg)
   - [dsGetMS12AudioProfList_pos](#dsgetms12audioproflist_pos)
   - [dsGetMS12AudioProfList_neg](#dsgetms12audioproflist_neg)
   - [dsGetMS12AudioProf_pos](#dsgetms12audioprof_pos)
   - [dsGetMS12AudioProf_neg](#dsgetms12audioprof_neg)
   - [dsGetStereoMode_pos](#dsgetstereomode_pos)
   - [dsGetStereoMode_neg](#dsgetstereomode_neg)
   - [dsSetStereoMode_pos](#dssetstereomode_pos)
   - [dsSetStereoMode_neg](#dssetstereomode_neg)
   - [dsGetStereoAuto_pos](#dsgetsteroauto_pos)
   - [dsGetStereoAuto_neg](#dsgetsteroauto_neg)
   - [dsSetStereoAuto_pos](#dssetsteroauto_pos)
   - [dsSetStereoAuto_neg](#dssetsteroauto_neg)
   - [dsGetAudioGain_pos](#dsgetaudiogain_pos)
   - [dsGetAudioGain_neg](#dsgetaudiogain_neg)
   - [dsSetAudioGain_pos](#dssetaudiogain_pos)
   - [dsSetAudioGain_neg](#dssetaudiogain_neg)
   - [dsGetAudioLevel_pos](#dsgetaudiolevel_pos)
   - [dsGetAudioLevel_neg](#dsgetaudiolevel_neg)
   - [dsSetAudioLevel_pos](#dssetaudiolevel_pos)
   - [dsSetAudioLevel_neg](#dssetaudiolevel_neg)
   - [dsGetAudioDelay_pos](#dsgetaudiodelay_pos)
   - [dsGetAudioDelay_neg](#dsgetaudiodelay_neg)
   - [dsSetAudioDelay_pos](#dssetaudiodelay_pos)
   - [dsSetAudioDelay_neg](#dssetaudiodelay_neg)
   - [dsSetAudioAtmosOutMode_pos](#dssetaudioatmosoutmode_pos)
   - [dsSetAudioAtmosOutMode_neg](#dssetaudioatmosoutmode_neg)
   - [dsGetSinkDeviceAtmosCap_pos](#dsgetsinkdeviceatmoscap_pos)
   - [dsGetSinkDeviceAtmosCap_neg](#dsgetsinkdeviceatmoscap_neg)
   - [dsIsAudioMute_pos](#dsisaudiomute_pos)
   - [dsIsAudioMute_neg](#dsisaudiomute_neg)
   - [dsIsAudioPortEnabled_pos](#dsisaudioportenabled_pos)
   - [dsIsAudioPortEnabled_neg](#dsisaudioportenabled_neg)
   - [dsEnableAudioPort_pos](#dsenableaudioport_pos)
   - [dsEnableAudioPort_neg](#dsenableaudioport_neg)
   - [dsEnableLEConfig_pos](#dsenableleconfig_pos)
   - [dsEnableLEConfig_neg](#dsenableleconfig_neg)
   - [dsGetLEConfig_pos](#dsgetleconfig_pos)
   - [dsGetLEConfig_neg](#dsgetleconfig_neg)
   - [dsSetMS12AudioProf_pos](#dssetms12audioprof_pos)
   - [dsSetMS12AudioProf_neg](#dssetms12audioprof_neg)
   - [dsSetAudioMute_pos](#dssetaudiomute_pos)
   - [dsSetAudioMute_neg](#dssetaudiomute_neg)
   - [dsIsAudioMSDecode_pos](#dsisaudiomsdecode_pos)
   - [dsIsAudioMSDecode_neg](#dsisaudiomsdecode_neg)
   - [dsIsAudioMS12Decode_pos](#dsisaudioms12decode_pos)
   - [dsIsAudioMS12Decode_neg](#dsisaudioms12decode_neg)
   - [dsAudioOutIsConn_pos](#dsaudiooutisconn_pos)
   - [dsAudioOutIsConn_neg](#dsaudiooutisconn_neg)
   - [dsAudioOutRegConnCB_pos](#dsaudiooutregconncb_pos)
   - [dsAudioOutRegConnCB_neg](#dsaudiooutregconncb_neg)
   - [dsAudioFmtUpdateRegCB_pos](#dsaudiofmtupdateregcb_pos)
   - [dsAudioFmtUpdateRegCB_neg](#dsaudiofmtupdateregcb_neg)
   - [dsGetAudioCaps_pos](#dsgetaudiocaps_pos)
   - [dsGetAudioCaps_neg](#dsgetaudiocaps_neg)
   - [dsGetMS12Caps_pos](#dsgetms12caps_pos)
   - [dsGetMS12Caps_neg](#dsgetms12caps_neg)
   - [dsSetAssocAudioMixing_pos](#dssetassocaudiomixing_pos)
   - [dsSetAssocAudioMixing_neg](#dssetassocaudiomixing_neg)
   - [dsGetAssocAudioMixing_pos](#dsgetassocaudiomixing_pos)
   - [dsGetAssocAudioMixing_neg](#dsgetassocaudiomixing_neg)
   - [dsSetFaderControl_pos](#dssetfadercontrol_pos)
   - [dsSetFaderControl_neg](#dssetfadercontrol_neg)
   - [dsGetFaderControl_pos](#dsgetfadercontrol_pos)
   - [dsGetFaderControl_neg](#dsgetfadercontrol_neg)
   - [dsSetPrimaryLang_pos](#dssetprimarylang_pos)
   - [dsSetPrimaryLang_neg](#dssetprimarylang_neg)
   - [dsGetPrimaryLang_pos](#dsgetprimarylang_pos)
   - [dsGetPrimaryLang_neg](#dsgetprimarylang_neg)
   - [dsSetSecondaryLang_pos](#dssetsecondarylang_pos)
   - [dsSetSecondaryLang_neg](#dssetsecondarylang_neg)
   - [dsGetSecondaryLang_pos](#dsgetsecondarylang_pos)
   - [dsGetSecondaryLang_neg](#dsgetsecondarylang_neg)
   - [dsSetAudioMixLevels_pos](#dssetaudiomixlevels_pos)
   - [dsSetAudioMixLevels_neg](#dssetaudiomixlevels_neg)
   - [dsAudioAtmosCapsRegCB_pos](#dsaudioatmoscapsregcb_pos)
   - [dsAudioAtmosCapsRegCB_neg](#dsaudioatmoscapsregcb_neg)
   - [dsGetSupportedARCTypes_pos](#dsgetsupportedarctypes_pos)
   - [dsGetSupportedARCTypes_neg](#dsgetsupportedarctypes_neg)
   - [dsAudioSetSAD_pos](#dsaudiosetsad_pos)
   - [dsAudioSetSAD_neg](#dsaudiosetsad_neg)
   - [dsAudioEnableARC_pos](#dsaudioenablearc_pos)
   - [dsAudioEnableARC_neg](#dsaudioenablearc_neg)
4. [Post-conditions](#post-conditions)
5. [Test Attributes](#test-attributes)

---

## Objective

This script executes VTS L1 (Level 1) test cases for the Device Settings Audio Port HAL module (`dsAudio`). L1 tests validate individual HAL API functions in isolation — each test exercises a single API with valid (positive) or invalid (negative) inputs. No external stimulus is required; tests operate solely through the HAL interface. The binary used is `hal_test_dshal`, invoked with the profile `Source_AudioSettings.yaml`.

---

## Pre-conditions

### Pre-condition 1: VTS Package Installed

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Read VTS Base Path | Check the device config file for `VTS_BASE_PATH`. If set (e.g., `VTS_BASE_PATH = /opt/VTS_Package/`), that path is used as the base; otherwise the default `/VTS_Package/` is used | Base path is determined |
| Verify Binary and Config | Confirm the module sub-directory `device_settings/` exists under the base path and contains the required files | `<VTS_BASE_PATH>/device_settings/` exists and contains the `hal_test_dshal` binary and `Source_AudioSettings.yaml` config file |

### Pre-condition 2: SSH Connectivity

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Read SSH Configuration | Read SSH connection parameters from the device config file: `SSH_PORT` (default: `22`), `SSH_METHOD` (e.g., `directSSH`), `SSH_USERNAME` (e.g., `root`), `SSH_PASSWORD` (`None` if no password required) | SSH parameters are available |
| Verify SSH Access | Establish an SSH session to the DUT using the configured parameters | SSH session is established successfully |

---

## Test Cases

<a id="dsaudioportinit_pos"></a>
### TestCase Name
dsAudioPortInit_pos

### TestCase ID
dsAudio L1-1

### TestCase Objective
Validate that `dsAudioPortInit()` succeeds when called for the first time.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsaudioportinit_neg"></a>
### TestCase Name
dsAudioPortInit_neg

### TestCase ID
dsAudio L1-2

### TestCase Objective
Validate that `dsAudioPortInit()` returns an error when called again while already initialized.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Initialize again while already initialized | Invoke `dsAudioPortInit()` a second time | `dsAudioPortInit()` must return `dsERR_ALREADY_INITIALIZED` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsaudioportterm_pos"></a>
### TestCase Name
dsAudioPortTerm_pos

### TestCase ID
dsAudio L1-3

### TestCase Objective
Validate that `dsAudioPortTerm()` succeeds when called after a successful initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsaudioportterm_neg"></a>
### TestCase Name
dsAudioPortTerm_neg

### TestCase ID
dsAudio L1-4

### TestCase Objective
Validate that `dsAudioPortTerm()` returns an error when called without prior initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Terminate the audio port sub-system without prior initialization | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetaudioport_pos"></a>
### TestCase Name
dsGetAudioPort_pos

### TestCase ID
dsAudio L1-5

### TestCase Objective
Validate that `dsGetAudioPort()` returns a valid handle for each supported audio port type and index combination.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each valid port type and index from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and `handle` must be non-null |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetaudioport_neg"></a>
### TestCase Name
dsGetAudioPort_neg

### TestCase ID
dsAudio L1-6

### TestCase Objective
Validate that `dsGetAudioPort()` returns an error when called without prior initialization or with an invalid port type.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get audio port without prior initialization | Invoke `dsGetAudioPort(dsAUDIOPORT_TYPE_HDMI, 0, &handle)` | `dsGetAudioPort()` must return `dsERR_NOT_INITIALIZED` |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port with invalid type | Invoke `dsGetAudioPort(dsAUDIOPORT_TYPE_MAX, 0, &handle)` | `dsGetAudioPort()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetaudioformat_pos"></a>
### TestCase Name
dsGetAudioFormat_pos

### TestCase ID
dsAudio L1-7

### TestCase Objective
Validate that `dsGetAudioFormat()` succeeds and returns the current audio format for each valid audio port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get audio format | Invoke `dsGetAudioFormat(handle, &audioFormat)` | `dsGetAudioFormat()` must return `dsERR_NONE` and `audioFormat` must be a valid `dsAudioFormat_t` value |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetaudioformat_neg"></a>
### TestCase Name
dsGetAudioFormat_neg

### TestCase ID
dsAudio L1-8

### TestCase Objective
Validate that `dsGetAudioFormat()` returns an error when called with an invalid handle or a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio format with NULL output pointer | Invoke `dsGetAudioFormat(handle, NULL)` | `dsGetAudioFormat()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetaudiocompression_pos"></a>
### TestCase Name
dsGetAudioCompression_pos

### TestCase ID
dsAudio L1-9

### TestCase Objective
Validate that `dsGetAudioCompression()` succeeds and returns the current audio compression value for each valid audio port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get audio compression | Invoke `dsGetAudioCompression(handle, &compression)` | `dsGetAudioCompression()` must return `dsERR_NONE` and `compression` must be a valid value in range [0, 10] |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetaudiocompression_neg"></a>
### TestCase Name
dsGetAudioCompression_neg

### TestCase ID
dsAudio L1-10

### TestCase Objective
Validate that `dsGetAudioCompression()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get audio compression with NULL output pointer | Invoke `dsGetAudioCompression(handle, NULL)` | `dsGetAudioCompression()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetaudiocompression_pos"></a>
### TestCase Name
dsSetAudioCompression_pos

### TestCase ID
dsAudio L1-11

### TestCase Objective
Validate that `dsSetAudioCompression()` succeeds when called with a valid compression value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set audio compression | Invoke `dsSetAudioCompression(handle, 5)` | `dsSetAudioCompression()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetaudiocompression_neg"></a>
### TestCase Name
dsSetAudioCompression_neg

### TestCase ID
dsAudio L1-12

### TestCase Objective
Validate that `dsSetAudioCompression()` returns an error when called with an out-of-range compression value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set audio compression with invalid value | Invoke `dsSetAudioCompression(handle, 11)` | `dsSetAudioCompression()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetdialogenhance_pos"></a>
### TestCase Name
dsGetDialogEnhance_pos

### TestCase ID
dsAudio L1-13

### TestCase Objective
Validate that `dsGetDialogEnhancement()` succeeds and returns the current dialog enhancement level for each valid audio port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get dialog enhancement level | Invoke `dsGetDialogEnhancement(handle, &level)` | `dsGetDialogEnhancement()` must return `dsERR_NONE` and `level` must be in range [0, 16] |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetdialogenhance_neg"></a>
### TestCase Name
dsGetDialogEnhance_neg

### TestCase ID
dsAudio L1-14

### TestCase Objective
Validate that `dsGetDialogEnhancement()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get dialog enhancement with NULL output pointer | Invoke `dsGetDialogEnhancement(handle, NULL)` | `dsGetDialogEnhancement()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetdialogenhance_pos"></a>
### TestCase Name
dsSetDialogEnhance_pos

### TestCase ID
dsAudio L1-15

### TestCase Objective
Validate that `dsSetDialogEnhancement()` succeeds when called with a valid dialog enhancement level.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set dialog enhancement level | Invoke `dsSetDialogEnhancement(handle, 5)` | `dsSetDialogEnhancement()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetdialogenhance_neg"></a>
### TestCase Name
dsSetDialogEnhance_neg

### TestCase ID
dsAudio L1-16

### TestCase Objective
Validate that `dsSetDialogEnhancement()` returns an error when called with an out-of-range level value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set dialog enhancement with invalid value | Invoke `dsSetDialogEnhancement(handle, 17)` | `dsSetDialogEnhancement()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetdolbyvolumemode_pos"></a>
### TestCase Name
dsGetDolbyVolumeMode_pos

### TestCase ID
dsAudio L1-17

### TestCase Objective
Validate that `dsGetDolbyVolumeMode()` succeeds and returns the current Dolby volume mode for each valid audio port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get Dolby volume mode | Invoke `dsGetDolbyVolumeMode(handle, &mode)` | `dsGetDolbyVolumeMode()` must return `dsERR_NONE` and `mode` must be a valid boolean value |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetdolbyvolumemode_neg"></a>
### TestCase Name
dsGetDolbyVolumeMode_neg

### TestCase ID
dsAudio L1-18

### TestCase Objective
Validate that `dsGetDolbyVolumeMode()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get Dolby volume mode with NULL output pointer | Invoke `dsGetDolbyVolumeMode(handle, NULL)` | `dsGetDolbyVolumeMode()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetdolbyvolumemode_pos"></a>
### TestCase Name
dsSetDolbyVolumeMode_pos

### TestCase ID
dsAudio L1-19

### TestCase Objective
Validate that `dsSetDolbyVolumeMode()` succeeds when called with a valid mode value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set Dolby volume mode | Invoke `dsSetDolbyVolumeMode(handle, true)` | `dsSetDolbyVolumeMode()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetdolbyvolumemode_neg"></a>
### TestCase Name
dsSetDolbyVolumeMode_neg

### TestCase ID
dsAudio L1-20

### TestCase Objective
Validate that `dsSetDolbyVolumeMode()` returns an error when called without prior initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set Dolby volume mode without prior initialization | Invoke `dsSetDolbyVolumeMode(handle, true)` with a null/invalid handle | `dsSetDolbyVolumeMode()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetintelleqmode_pos"></a>
### TestCase Name
dsGetIntelliEqMode_pos

### TestCase ID
dsAudio L1-21

### TestCase Objective
Validate that `dsGetIntelligentEqualizerMode()` succeeds and returns the current intelligent equalizer mode for each valid audio port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get intelligent equalizer mode | Invoke `dsGetIntelligentEqualizerMode(handle, &mode)` | `dsGetIntelligentEqualizerMode()` must return `dsERR_NONE` and `mode` must be in range [0, 6] |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetintelleqmode_neg"></a>
### TestCase Name
dsGetIntelliEqMode_neg

### TestCase ID
dsAudio L1-22

### TestCase Objective
Validate that `dsGetIntelligentEqualizerMode()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get intelligent equalizer mode with NULL output pointer | Invoke `dsGetIntelligentEqualizerMode(handle, NULL)` | `dsGetIntelligentEqualizerMode()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetintelleqmode_pos"></a>
### TestCase Name
dsSetIntelliEqMode_pos

### TestCase ID
dsAudio L1-23

### TestCase Objective
Validate that `dsSetIntelligentEqualizerMode()` succeeds when called with a valid mode value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set intelligent equalizer mode | Invoke `dsSetIntelligentEqualizerMode(handle, 3)` | `dsSetIntelligentEqualizerMode()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetintelleqmode_neg"></a>
### TestCase Name
dsSetIntelliEqMode_neg

### TestCase ID
dsAudio L1-24

### TestCase Objective
Validate that `dsSetIntelligentEqualizerMode()` returns an error when called with an out-of-range mode value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set intelligent equalizer mode with invalid value | Invoke `dsSetIntelligentEqualizerMode(handle, 7)` | `dsSetIntelligentEqualizerMode()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetvolumeleveller_pos"></a>
### TestCase Name
dsGetVolumeLeveller_pos

### TestCase ID
dsAudio L1-25

### TestCase Objective
Validate that `dsGetVolumeLeveller()` succeeds and returns the current volume leveller settings for each valid audio port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get volume leveller | Invoke `dsGetVolumeLeveller(handle, &volLeveller)` | `dsGetVolumeLeveller()` must return `dsERR_NONE` and `volLeveller` must be populated |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetvolumeleveller_neg"></a>
### TestCase Name
dsGetVolumeLeveller_neg

### TestCase ID
dsAudio L1-26

### TestCase Objective
Validate that `dsGetVolumeLeveller()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get volume leveller with NULL output pointer | Invoke `dsGetVolumeLeveller(handle, NULL)` | `dsGetVolumeLeveller()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetvolumeleveller_pos"></a>
### TestCase Name
dsSetVolumeLeveller_pos

### TestCase ID
dsAudio L1-27

### TestCase Objective
Validate that `dsSetVolumeLeveller()` succeeds when called with valid volume leveller settings.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set volume leveller | Invoke `dsSetVolumeLeveller(handle, volLeveller)` with valid mode and level | `dsSetVolumeLeveller()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetvolumeleveller_neg"></a>
### TestCase Name
dsSetVolumeLeveller_neg

### TestCase ID
dsAudio L1-28

### TestCase Objective
Validate that `dsSetVolumeLeveller()` returns an error when called with invalid leveller settings.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set volume leveller with invalid level value | Invoke `dsSetVolumeLeveller(handle, volLeveller)` with level out of range | `dsSetVolumeLeveller()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetbassenhancer_pos"></a>
### TestCase Name
dsGetBassEnhancer_pos

### TestCase ID
dsAudio L1-29

### TestCase Objective
Validate that `dsGetBassEnhancer()` succeeds and returns the current bass enhancer boost value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get bass enhancer boost | Invoke `dsGetBassEnhancer(handle, &boost)` | `dsGetBassEnhancer()` must return `dsERR_NONE` and `boost` must be in range [0, 100] |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetbassenhancer_neg"></a>
### TestCase Name
dsGetBassEnhancer_neg

### TestCase ID
dsAudio L1-30

### TestCase Objective
Validate that `dsGetBassEnhancer()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get bass enhancer with NULL output pointer | Invoke `dsGetBassEnhancer(handle, NULL)` | `dsGetBassEnhancer()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetbassenhancer_pos"></a>
### TestCase Name
dsSetBassEnhancer_pos

### TestCase ID
dsAudio L1-31

### TestCase Objective
Validate that `dsSetBassEnhancer()` succeeds when called with a valid boost value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set bass enhancer boost | Invoke `dsSetBassEnhancer(handle, 50)` | `dsSetBassEnhancer()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetbassenhancer_neg"></a>
### TestCase Name
dsSetBassEnhancer_neg

### TestCase ID
dsAudio L1-32

### TestCase Objective
Validate that `dsSetBassEnhancer()` returns an error when called with an out-of-range boost value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set bass enhancer with invalid value | Invoke `dsSetBassEnhancer(handle, 101)` | `dsSetBassEnhancer()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsissurrounddecoderenabledpos"></a>
### TestCase Name
dsIsSurroundDecoderEnabled_pos

### TestCase ID
dsAudio L1-33

### TestCase Objective
Validate that `dsIsSurroundDecoderEnabled()` succeeds and returns the current surround decoder enabled state.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Check if surround decoder is enabled | Invoke `dsIsSurroundDecoderEnabled(handle, &enabled)` | `dsIsSurroundDecoderEnabled()` must return `dsERR_NONE` and `enabled` must be a valid boolean value |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsissurrounddecoderenablednneg"></a>
### TestCase Name
dsIsSurroundDecoderEnabled_neg

### TestCase ID
dsAudio L1-34

### TestCase Objective
Validate that `dsIsSurroundDecoderEnabled()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Check surround decoder enabled with NULL pointer | Invoke `dsIsSurroundDecoderEnabled(handle, NULL)` | `dsIsSurroundDecoderEnabled()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsenablesurrounddecoder_pos"></a>
### TestCase Name
dsEnableSurroundDecoder_pos

### TestCase ID
dsAudio L1-35

### TestCase Objective
Validate that `dsEnableSurroundDecoder()` succeeds when called with a valid enable value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Enable surround decoder | Invoke `dsEnableSurroundDecoder(handle, true)` | `dsEnableSurroundDecoder()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsenablesurrounddecoder_neg"></a>
### TestCase Name
dsEnableSurroundDecoder_neg

### TestCase ID
dsAudio L1-36

### TestCase Objective
Validate that `dsEnableSurroundDecoder()` returns an error when called without prior initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Enable surround decoder without prior initialization | Invoke `dsEnableSurroundDecoder(handle, true)` with a null/invalid handle | `dsEnableSurroundDecoder()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetdrcmode_pos"></a>
### TestCase Name
dsGetDRCMode_pos

### TestCase ID
dsAudio L1-37

### TestCase Objective
Validate that `dsGetDRCMode()` succeeds and returns the current DRC (Dynamic Range Control) mode.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get DRC mode | Invoke `dsGetDRCMode(handle, &mode)` | `dsGetDRCMode()` must return `dsERR_NONE` and `mode` must be a valid value (0 or 1) |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetdrcmode_neg"></a>
### TestCase Name
dsGetDRCMode_neg

### TestCase ID
dsAudio L1-38

### TestCase Objective
Validate that `dsGetDRCMode()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get DRC mode with NULL output pointer | Invoke `dsGetDRCMode(handle, NULL)` | `dsGetDRCMode()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetdrcmode_pos"></a>
### TestCase Name
dsSetDRCMode_pos

### TestCase ID
dsAudio L1-39

### TestCase Objective
Validate that `dsSetDRCMode()` succeeds when called with a valid DRC mode.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set DRC mode | Invoke `dsSetDRCMode(handle, 1)` | `dsSetDRCMode()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetdrcmode_neg"></a>
### TestCase Name
dsSetDRCMode_neg

### TestCase ID
dsAudio L1-40

### TestCase Objective
Validate that `dsSetDRCMode()` returns an error when called with an invalid mode value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set DRC mode with invalid value | Invoke `dsSetDRCMode(handle, 2)` | `dsSetDRCMode()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetsurroundvirt_pos"></a>
### TestCase Name
dsGetSurroundVirt_pos

### TestCase ID
dsAudio L1-41

### TestCase Objective
Validate that `dsGetSurroundVirtualizer()` succeeds and returns the current surround virtualizer settings.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get surround virtualizer | Invoke `dsGetSurroundVirtualizer(handle, &virtualizer)` | `dsGetSurroundVirtualizer()` must return `dsERR_NONE` and `virtualizer` must be populated |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetsurroundvirt_neg"></a>
### TestCase Name
dsGetSurroundVirt_neg

### TestCase ID
dsAudio L1-42

### TestCase Objective
Validate that `dsGetSurroundVirtualizer()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get surround virtualizer with NULL output pointer | Invoke `dsGetSurroundVirtualizer(handle, NULL)` | `dsGetSurroundVirtualizer()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetsurroundvirt_pos"></a>
### TestCase Name
dsSetSurroundVirt_pos

### TestCase ID
dsAudio L1-43

### TestCase Objective
Validate that `dsSetSurroundVirtualizer()` succeeds when called with valid surround virtualizer settings.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set surround virtualizer | Invoke `dsSetSurroundVirtualizer(handle, virtualizer)` with valid mode and boost | `dsSetSurroundVirtualizer()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetsurroundvirt_neg"></a>
### TestCase Name
dsSetSurroundVirt_neg

### TestCase ID
dsAudio L1-44

### TestCase Objective
Validate that `dsSetSurroundVirtualizer()` returns an error when called with invalid settings.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set surround virtualizer with invalid boost value | Invoke `dsSetSurroundVirtualizer(handle, virtualizer)` with boost out of range | `dsSetSurroundVirtualizer()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetmisteering_pos"></a>
### TestCase Name
dsGetMISteering_pos

### TestCase ID
dsAudio L1-45

### TestCase Objective
Validate that `dsGetMISteering()` succeeds and returns the current media intelligent steering state.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get MI steering state | Invoke `dsGetMISteering(handle, &enabled)` | `dsGetMISteering()` must return `dsERR_NONE` and `enabled` must be a valid boolean value |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetmisteering_neg"></a>
### TestCase Name
dsGetMISteering_neg

### TestCase ID
dsAudio L1-46

### TestCase Objective
Validate that `dsGetMISteering()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get MI steering with NULL output pointer | Invoke `dsGetMISteering(handle, NULL)` | `dsGetMISteering()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetmisteering_pos"></a>
### TestCase Name
dsSetMISteering_pos

### TestCase ID
dsAudio L1-47

### TestCase Objective
Validate that `dsSetMISteering()` succeeds when called with a valid enable value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set MI steering | Invoke `dsSetMISteering(handle, true)` | `dsSetMISteering()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetmisteering_neg"></a>
### TestCase Name
dsSetMISteering_neg

### TestCase ID
dsAudio L1-48

### TestCase Objective
Validate that `dsSetMISteering()` returns an error when called without prior initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set MI steering without prior initialization | Invoke `dsSetMISteering(handle, true)` with a null/invalid handle | `dsSetMISteering()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetgraphiceqmode_pos"></a>
### TestCase Name
dsGetGraphicEqMode_pos

### TestCase ID
dsAudio L1-49

### TestCase Objective
Validate that `dsGetGraphicEqualizerMode()` succeeds and returns the current graphic equalizer mode.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get graphic equalizer mode | Invoke `dsGetGraphicEqualizerMode(handle, &mode)` | `dsGetGraphicEqualizerMode()` must return `dsERR_NONE` and `mode` must be in range [0, 3] |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetgraphiceqmode_neg"></a>
### TestCase Name
dsGetGraphicEqMode_neg

### TestCase ID
dsAudio L1-50

### TestCase Objective
Validate that `dsGetGraphicEqualizerMode()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get graphic equalizer mode with NULL output pointer | Invoke `dsGetGraphicEqualizerMode(handle, NULL)` | `dsGetGraphicEqualizerMode()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetgraphiceqmode_pos"></a>
### TestCase Name
dsSetGraphicEqMode_pos

### TestCase ID
dsAudio L1-51

### TestCase Objective
Validate that `dsSetGraphicEqualizerMode()` succeeds when called with a valid mode value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set graphic equalizer mode | Invoke `dsSetGraphicEqualizerMode(handle, 2)` | `dsSetGraphicEqualizerMode()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetgraphiceqmode_neg"></a>
### TestCase Name
dsSetGraphicEqMode_neg

### TestCase ID
dsAudio L1-52

### TestCase Objective
Validate that `dsSetGraphicEqualizerMode()` returns an error when called with an out-of-range mode value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set graphic equalizer mode with invalid value | Invoke `dsSetGraphicEqualizerMode(handle, 4)` | `dsSetGraphicEqualizerMode()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetms12audioproflist_pos"></a>
### TestCase Name
dsGetMS12AudioProfList_pos

### TestCase ID
dsAudio L1-53

### TestCase Objective
Validate that `dsGetMS12AudioProfileList()` succeeds and returns the list of available MS12 audio profiles.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get MS12 audio profile list | Invoke `dsGetMS12AudioProfileList(handle, &profileList)` | `dsGetMS12AudioProfileList()` must return `dsERR_NONE` and `profileList` must be populated |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetms12audioproflist_neg"></a>
### TestCase Name
dsGetMS12AudioProfList_neg

### TestCase ID
dsAudio L1-54

### TestCase Objective
Validate that `dsGetMS12AudioProfileList()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get MS12 audio profile list with NULL output pointer | Invoke `dsGetMS12AudioProfileList(handle, NULL)` | `dsGetMS12AudioProfileList()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetms12audioprof_pos"></a>
### TestCase Name
dsGetMS12AudioProf_pos

### TestCase ID
dsAudio L1-55

### TestCase Objective
Validate that `dsGetMS12AudioProfile()` succeeds and returns the current MS12 audio profile name.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get current MS12 audio profile | Invoke `dsGetMS12AudioProfile(handle, &profile)` | `dsGetMS12AudioProfile()` must return `dsERR_NONE` and `profile` must be a valid non-empty string |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetms12audioprof_neg"></a>
### TestCase Name
dsGetMS12AudioProf_neg

### TestCase ID
dsAudio L1-56

### TestCase Objective
Validate that `dsGetMS12AudioProfile()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get MS12 audio profile with NULL output pointer | Invoke `dsGetMS12AudioProfile(handle, NULL)` | `dsGetMS12AudioProfile()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetstereomode_pos"></a>
### TestCase Name
dsGetStereoMode_pos

### TestCase ID
dsAudio L1-57

### TestCase Objective
Validate that `dsGetStereoMode()` succeeds and returns the current stereo mode for each valid audio port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get stereo mode | Invoke `dsGetStereoMode(handle, &stereoMode)` | `dsGetStereoMode()` must return `dsERR_NONE` and `stereoMode` must be a valid `dsAudioStereoMode_t` value |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetstereomode_neg"></a>
### TestCase Name
dsGetStereoMode_neg

### TestCase ID
dsAudio L1-58

### TestCase Objective
Validate that `dsGetStereoMode()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get stereo mode with NULL output pointer | Invoke `dsGetStereoMode(handle, NULL)` | `dsGetStereoMode()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetstereomode_pos"></a>
### TestCase Name
dsSetStereoMode_pos

### TestCase ID
dsAudio L1-59

### TestCase Objective
Validate that `dsSetStereoMode()` succeeds when called with a valid stereo mode value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set stereo mode | Invoke `dsSetStereoMode(handle, dsAUDIO_STEREO_STEREO)` | `dsSetStereoMode()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetstereomode_neg"></a>
### TestCase Name
dsSetStereoMode_neg

### TestCase ID
dsAudio L1-60

### TestCase Objective
Validate that `dsSetStereoMode()` returns an error when called with an invalid stereo mode value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set stereo mode with invalid value | Invoke `dsSetStereoMode(handle, dsAUDIO_STEREO_MAX)` | `dsSetStereoMode()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetsteroauto_pos"></a>
### TestCase Name
dsGetStereoAuto_pos

### TestCase ID
dsAudio L1-61

### TestCase Objective
Validate that `dsGetStereoAuto()` succeeds and returns the current stereo auto mode setting.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get stereo auto mode | Invoke `dsGetStereoAuto(handle, &autoMode)` | `dsGetStereoAuto()` must return `dsERR_NONE` and `autoMode` must be a valid boolean value |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetsteroauto_neg"></a>
### TestCase Name
dsGetStereoAuto_neg

### TestCase ID
dsAudio L1-62

### TestCase Objective
Validate that `dsGetStereoAuto()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get stereo auto mode with NULL output pointer | Invoke `dsGetStereoAuto(handle, NULL)` | `dsGetStereoAuto()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetsteroauto_pos"></a>
### TestCase Name
dsSetStereoAuto_pos

### TestCase ID
dsAudio L1-63

### TestCase Objective
Validate that `dsSetStereoAuto()` succeeds when called with a valid auto mode value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set stereo auto mode | Invoke `dsSetStereoAuto(handle, 1)` | `dsSetStereoAuto()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetsteroauto_neg"></a>
### TestCase Name
dsSetStereoAuto_neg

### TestCase ID
dsAudio L1-64

### TestCase Objective
Validate that `dsSetStereoAuto()` returns an error when called without prior initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set stereo auto mode without prior initialization | Invoke `dsSetStereoAuto(handle, 1)` with a null/invalid handle | `dsSetStereoAuto()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetaudiogain_pos"></a>
### TestCase Name
dsGetAudioGain_pos

### TestCase ID
dsAudio L1-65

### TestCase Objective
Validate that `dsGetAudioGain()` succeeds and returns the current audio gain value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get audio gain | Invoke `dsGetAudioGain(handle, &gain)` | `dsGetAudioGain()` must return `dsERR_NONE` and `gain` must be in range [-2080.0, 480.0] |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetaudiogain_neg"></a>
### TestCase Name
dsGetAudioGain_neg

### TestCase ID
dsAudio L1-66

### TestCase Objective
Validate that `dsGetAudioGain()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get audio gain with NULL output pointer | Invoke `dsGetAudioGain(handle, NULL)` | `dsGetAudioGain()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetaudiogain_pos"></a>
### TestCase Name
dsSetAudioGain_pos

### TestCase ID
dsAudio L1-67

### TestCase Objective
Validate that `dsSetAudioGain()` succeeds when called with a valid gain value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set audio gain | Invoke `dsSetAudioGain(handle, 0.0)` | `dsSetAudioGain()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetaudiogain_neg"></a>
### TestCase Name
dsSetAudioGain_neg

### TestCase ID
dsAudio L1-68

### TestCase Objective
Validate that `dsSetAudioGain()` returns an error when called with an out-of-range gain value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set audio gain with out-of-range value | Invoke `dsSetAudioGain(handle, 481.0)` | `dsSetAudioGain()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetaudiolevel_pos"></a>
### TestCase Name
dsGetAudioLevel_pos

### TestCase ID
dsAudio L1-69

### TestCase Objective
Validate that `dsGetAudioLevel()` succeeds and returns the current audio level value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get audio level | Invoke `dsGetAudioLevel(handle, &level)` | `dsGetAudioLevel()` must return `dsERR_NONE` and `level` must be in range [0.0, 100.0] |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetaudiolevel_neg"></a>
### TestCase Name
dsGetAudioLevel_neg

### TestCase ID
dsAudio L1-70

### TestCase Objective
Validate that `dsGetAudioLevel()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get audio level with NULL output pointer | Invoke `dsGetAudioLevel(handle, NULL)` | `dsGetAudioLevel()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetaudiolevel_pos"></a>
### TestCase Name
dsSetAudioLevel_pos

### TestCase ID
dsAudio L1-71

### TestCase Objective
Validate that `dsSetAudioLevel()` succeeds when called with a valid level value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set audio level | Invoke `dsSetAudioLevel(handle, 50.0)` | `dsSetAudioLevel()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetaudiolevel_neg"></a>
### TestCase Name
dsSetAudioLevel_neg

### TestCase ID
dsAudio L1-72

### TestCase Objective
Validate that `dsSetAudioLevel()` returns an error when called with an out-of-range level value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set audio level with out-of-range value | Invoke `dsSetAudioLevel(handle, 101.0)` | `dsSetAudioLevel()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetaudiodelay_pos"></a>
### TestCase Name
dsGetAudioDelay_pos

### TestCase ID
dsAudio L1-73

### TestCase Objective
Validate that `dsGetAudioDelay()` succeeds and returns the current audio delay in milliseconds.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get audio delay | Invoke `dsGetAudioDelay(handle, &delay)` | `dsGetAudioDelay()` must return `dsERR_NONE` and `delay` must be a valid value in range [0, 200] ms |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetaudiodelay_neg"></a>
### TestCase Name
dsGetAudioDelay_neg

### TestCase ID
dsAudio L1-74

### TestCase Objective
Validate that `dsGetAudioDelay()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get audio delay with NULL output pointer | Invoke `dsGetAudioDelay(handle, NULL)` | `dsGetAudioDelay()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetaudiodelay_pos"></a>
### TestCase Name
dsSetAudioDelay_pos

### TestCase ID
dsAudio L1-75

### TestCase Objective
Validate that `dsSetAudioDelay()` succeeds when called with a valid delay value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set audio delay | Invoke `dsSetAudioDelay(handle, 100)` | `dsSetAudioDelay()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetaudiodelay_neg"></a>
### TestCase Name
dsSetAudioDelay_neg

### TestCase ID
dsAudio L1-76

### TestCase Objective
Validate that `dsSetAudioDelay()` returns an error when called with an out-of-range delay value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set audio delay with out-of-range value | Invoke `dsSetAudioDelay(handle, 201)` | `dsSetAudioDelay()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetaudioatmosoutmode_pos"></a>
### TestCase Name
dsSetAudioAtmosOutMode_pos

### TestCase ID
dsAudio L1-77

### TestCase Objective
Validate that `dsSetAudioAtmosOutputMode()` succeeds when called with a valid Atmos output mode.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set audio Atmos output mode | Invoke `dsSetAudioAtmosOutputMode(handle, true)` | `dsSetAudioAtmosOutputMode()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetaudioatmosoutmode_neg"></a>
### TestCase Name
dsSetAudioAtmosOutMode_neg

### TestCase ID
dsAudio L1-78

### TestCase Objective
Validate that `dsSetAudioAtmosOutputMode()` returns an error when called without prior initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set audio Atmos output mode without prior initialization | Invoke `dsSetAudioAtmosOutputMode(handle, true)` with a null/invalid handle | `dsSetAudioAtmosOutputMode()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetsinkdeviceatmoscap_pos"></a>
### TestCase Name
dsGetSinkDeviceAtmosCap_pos

### TestCase ID
dsAudio L1-79

### TestCase Objective
Validate that `dsGetSinkDeviceAtmosCapability()` succeeds and returns the Atmos capability of the connected sink device.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get sink device Atmos capability | Invoke `dsGetSinkDeviceAtmosCapability(handle, &capability)` | `dsGetSinkDeviceAtmosCapability()` must return `dsERR_NONE` and `capability` must be a valid `dsATMOSCapability_t` value |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetsinkdeviceatmoscap_neg"></a>
### TestCase Name
dsGetSinkDeviceAtmosCap_neg

### TestCase ID
dsAudio L1-80

### TestCase Objective
Validate that `dsGetSinkDeviceAtmosCapability()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get sink device Atmos capability with NULL output pointer | Invoke `dsGetSinkDeviceAtmosCapability(handle, NULL)` | `dsGetSinkDeviceAtmosCapability()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsisaudiomute_pos"></a>
### TestCase Name
dsIsAudioMute_pos

### TestCase ID
dsAudio L1-81

### TestCase Objective
Validate that `dsIsAudioMute()` succeeds and returns the current mute state for each valid audio port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Check if audio is muted | Invoke `dsIsAudioMute(handle, &muted)` | `dsIsAudioMute()` must return `dsERR_NONE` and `muted` must be a valid boolean value |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsisaudiomute_neg"></a>
### TestCase Name
dsIsAudioMute_neg

### TestCase ID
dsAudio L1-82

### TestCase Objective
Validate that `dsIsAudioMute()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Check if audio is muted with NULL output pointer | Invoke `dsIsAudioMute(handle, NULL)` | `dsIsAudioMute()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsisaudioportenabled_pos"></a>
### TestCase Name
dsIsAudioPortEnabled_pos

### TestCase ID
dsAudio L1-83

### TestCase Objective
Validate that `dsIsAudioPortEnabled()` succeeds and returns whether the audio port is currently enabled.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Check if audio port is enabled | Invoke `dsIsAudioPortEnabled(handle, &enabled)` | `dsIsAudioPortEnabled()` must return `dsERR_NONE` and `enabled` must be a valid boolean value |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsisaudioportenabled_neg"></a>
### TestCase Name
dsIsAudioPortEnabled_neg

### TestCase ID
dsAudio L1-84

### TestCase Objective
Validate that `dsIsAudioPortEnabled()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Check if audio port is enabled with NULL output pointer | Invoke `dsIsAudioPortEnabled(handle, NULL)` | `dsIsAudioPortEnabled()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsenableaudioport_pos"></a>
### TestCase Name
dsEnableAudioPort_pos

### TestCase ID
dsAudio L1-85

### TestCase Objective
Validate that `dsEnableAudioPort()` succeeds when called to enable or disable an audio port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Enable audio port | Invoke `dsEnableAudioPort(handle, true)` | `dsEnableAudioPort()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsenableaudioport_neg"></a>
### TestCase Name
dsEnableAudioPort_neg

### TestCase ID
dsAudio L1-86

### TestCase Objective
Validate that `dsEnableAudioPort()` returns an error when called without prior initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Enable audio port without prior initialization | Invoke `dsEnableAudioPort(handle, true)` with a null/invalid handle | `dsEnableAudioPort()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsenableleconfig_pos"></a>
### TestCase Name
dsEnableLEConfig_pos

### TestCase ID
dsAudio L1-87

### TestCase Objective
Validate that `dsEnableLEConfig()` succeeds when called with a valid enable value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Enable LE (Loudness Equivalence) config | Invoke `dsEnableLEConfig(handle, true)` | `dsEnableLEConfig()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsenableleconfig_neg"></a>
### TestCase Name
dsEnableLEConfig_neg

### TestCase ID
dsAudio L1-88

### TestCase Objective
Validate that `dsEnableLEConfig()` returns an error when called without prior initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Enable LE config without prior initialization | Invoke `dsEnableLEConfig(handle, true)` with a null/invalid handle | `dsEnableLEConfig()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetleconfig_pos"></a>
### TestCase Name
dsGetLEConfig_pos

### TestCase ID
dsAudio L1-89

### TestCase Objective
Validate that `dsGetLEConfig()` succeeds and returns the current LE (Loudness Equivalence) configuration state.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get LE config | Invoke `dsGetLEConfig(handle, &enabled)` | `dsGetLEConfig()` must return `dsERR_NONE` and `enabled` must be a valid boolean value |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetleconfig_neg"></a>
### TestCase Name
dsGetLEConfig_neg

### TestCase ID
dsAudio L1-90

### TestCase Objective
Validate that `dsGetLEConfig()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get LE config with NULL output pointer | Invoke `dsGetLEConfig(handle, NULL)` | `dsGetLEConfig()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetms12audioprof_pos"></a>
### TestCase Name
dsSetMS12AudioProf_pos

### TestCase ID
dsAudio L1-91

### TestCase Objective
Validate that `dsSetMS12AudioProfile()` succeeds when called with a valid profile name.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get MS12 audio profile list | Invoke `dsGetMS12AudioProfileList(handle, &profileList)` to retrieve available profiles | `dsGetMS12AudioProfileList()` must return `dsERR_NONE` |
| Set MS12 audio profile | Invoke `dsSetMS12AudioProfile(handle, profileList.profiles[0])` with a valid profile name from the list | `dsSetMS12AudioProfile()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetms12audioprof_neg"></a>
### TestCase Name
dsSetMS12AudioProf_neg

### TestCase ID
dsAudio L1-92

### TestCase Objective
Validate that `dsSetMS12AudioProfile()` returns an error when called with an invalid profile name.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set MS12 audio profile with invalid name | Invoke `dsSetMS12AudioProfile(handle, "InvalidProfile")` | `dsSetMS12AudioProfile()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetaudiomute_pos"></a>
### TestCase Name
dsSetAudioMute_pos

### TestCase ID
dsAudio L1-93

### TestCase Objective
Validate that `dsSetAudioMute()` succeeds when called with a valid mute state.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set audio mute | Invoke `dsSetAudioMute(handle, true)` | `dsSetAudioMute()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetaudiomute_neg"></a>
### TestCase Name
dsSetAudioMute_neg

### TestCase ID
dsAudio L1-94

### TestCase Objective
Validate that `dsSetAudioMute()` returns an error when called without prior initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set audio mute without prior initialization | Invoke `dsSetAudioMute(handle, true)` with a null/invalid handle | `dsSetAudioMute()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsisaudiomsdecode_pos"></a>
### TestCase Name
dsIsAudioMSDecode_pos

### TestCase ID
dsAudio L1-95

### TestCase Objective
Validate that `dsIsAudioMSDecode()` succeeds and returns whether MS (Multi-stream) decode is supported.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Check if audio MS decode is supported | Invoke `dsIsAudioMSDecode(handle, &supported)` | `dsIsAudioMSDecode()` must return `dsERR_NONE` and `supported` must be a valid boolean value |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsisaudiomsdecode_neg"></a>
### TestCase Name
dsIsAudioMSDecode_neg

### TestCase ID
dsAudio L1-96

### TestCase Objective
Validate that `dsIsAudioMSDecode()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Check if audio MS decode is supported with NULL pointer | Invoke `dsIsAudioMSDecode(handle, NULL)` | `dsIsAudioMSDecode()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsisaudioms12decode_pos"></a>
### TestCase Name
dsIsAudioMS12Decode_pos

### TestCase ID
dsAudio L1-97

### TestCase Objective
Validate that `dsIsAudioMS12Decode()` succeeds and returns whether MS12 decode is supported.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Check if audio MS12 decode is supported | Invoke `dsIsAudioMS12Decode(handle, &supported)` | `dsIsAudioMS12Decode()` must return `dsERR_NONE` and `supported` must be a valid boolean value |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsisaudioms12decode_neg"></a>
### TestCase Name
dsIsAudioMS12Decode_neg

### TestCase ID
dsAudio L1-98

### TestCase Objective
Validate that `dsIsAudioMS12Decode()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Check if audio MS12 decode is supported with NULL pointer | Invoke `dsIsAudioMS12Decode(handle, NULL)` | `dsIsAudioMS12Decode()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsaudiooutisconn_pos"></a>
### TestCase Name
dsAudioOutIsConn_pos

### TestCase ID
dsAudio L1-99

### TestCase Objective
Validate that `dsAudioOutIsConnected()` succeeds and returns the connection status of the audio output port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Check if audio output is connected | Invoke `dsAudioOutIsConnected(handle, &connected)` | `dsAudioOutIsConnected()` must return `dsERR_NONE` and `connected` must be a valid boolean value |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsaudiooutisconn_neg"></a>
### TestCase Name
dsAudioOutIsConn_neg

### TestCase ID
dsAudio L1-100

### TestCase Objective
Validate that `dsAudioOutIsConnected()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Check audio output connection with NULL pointer | Invoke `dsAudioOutIsConnected(handle, NULL)` | `dsAudioOutIsConnected()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsaudiooutregconncb_pos"></a>
### TestCase Name
dsAudioOutRegConnCB_pos

### TestCase ID
dsAudio L1-101

### TestCase Objective
Validate that `dsAudioOutRegisterConnectCB()` succeeds when called with a valid callback function.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Register audio output connection callback | Invoke `dsAudioOutRegisterConnectCB(connectCBFunc)` with a valid callback | `dsAudioOutRegisterConnectCB()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsaudiooutregconncb_neg"></a>
### TestCase Name
dsAudioOutRegConnCB_neg

### TestCase ID
dsAudio L1-102

### TestCase Objective
Validate that `dsAudioOutRegisterConnectCB()` returns an error when called with a NULL callback.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Register audio output connection callback with NULL | Invoke `dsAudioOutRegisterConnectCB(NULL)` | `dsAudioOutRegisterConnectCB()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsaudiofmtupdateregcb_pos"></a>
### TestCase Name
dsAudioFmtUpdateRegCB_pos

### TestCase ID
dsAudio L1-103

### TestCase Objective
Validate that `dsAudioFormatUpdateRegisterCB()` succeeds when called with a valid callback function.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Register audio format update callback | Invoke `dsAudioFormatUpdateRegisterCB(formatUpdateCBFunc)` with a valid callback | `dsAudioFormatUpdateRegisterCB()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsaudiofmtupdateregcb_neg"></a>
### TestCase Name
dsAudioFmtUpdateRegCB_neg

### TestCase ID
dsAudio L1-104

### TestCase Objective
Validate that `dsAudioFormatUpdateRegisterCB()` returns an error when called with a NULL callback.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Register audio format update callback with NULL | Invoke `dsAudioFormatUpdateRegisterCB(NULL)` | `dsAudioFormatUpdateRegisterCB()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetaudiocaps_pos"></a>
### TestCase Name
dsGetAudioCaps_pos

### TestCase ID
dsAudio L1-105

### TestCase Objective
Validate that `dsGetAudioCapabilities()` succeeds and returns the audio capabilities for each valid audio port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get audio capabilities | Invoke `dsGetAudioCapabilities(handle, &capabilities)` | `dsGetAudioCapabilities()` must return `dsERR_NONE` and `capabilities` must be a valid bitmask |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetaudiocaps_neg"></a>
### TestCase Name
dsGetAudioCaps_neg

### TestCase ID
dsAudio L1-106

### TestCase Objective
Validate that `dsGetAudioCapabilities()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get audio capabilities with NULL output pointer | Invoke `dsGetAudioCapabilities(handle, NULL)` | `dsGetAudioCapabilities()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetms12caps_pos"></a>
### TestCase Name
dsGetMS12Caps_pos

### TestCase ID
dsAudio L1-107

### TestCase Objective
Validate that `dsGetMS12Capabilities()` succeeds and returns the MS12 capabilities bitmask for each valid audio port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get MS12 capabilities | Invoke `dsGetMS12Capabilities(handle, &capabilities)` | `dsGetMS12Capabilities()` must return `dsERR_NONE` and `capabilities` must be a valid bitmask |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetms12caps_neg"></a>
### TestCase Name
dsGetMS12Caps_neg

### TestCase ID
dsAudio L1-108

### TestCase Objective
Validate that `dsGetMS12Capabilities()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get MS12 capabilities with NULL output pointer | Invoke `dsGetMS12Capabilities(handle, NULL)` | `dsGetMS12Capabilities()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetassocaudiomixing_pos"></a>
### TestCase Name
dsSetAssocAudioMixing_pos

### TestCase ID
dsAudio L1-109

### TestCase Objective
Validate that `dsSetAssociatedAudioMixing()` succeeds when called with a valid mixing enable value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set associated audio mixing | Invoke `dsSetAssociatedAudioMixing(handle, true)` | `dsSetAssociatedAudioMixing()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetassocaudiomixing_neg"></a>
### TestCase Name
dsSetAssocAudioMixing_neg

### TestCase ID
dsAudio L1-110

### TestCase Objective
Validate that `dsSetAssociatedAudioMixing()` returns an error when called without prior initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set associated audio mixing without prior initialization | Invoke `dsSetAssociatedAudioMixing(handle, true)` with a null/invalid handle | `dsSetAssociatedAudioMixing()` must return `dsERR_NOT_INITIALIZED` |

---

<a id="dsgetassocaudiomixing_pos"></a>
### TestCase Name
dsGetAssocAudioMixing_pos

### TestCase ID
dsAudio L1-111

### TestCase Objective
Validate that `dsGetAssociatedAudioMixing()` succeeds and returns the current associated audio mixing state.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get associated audio mixing state | Invoke `dsGetAssociatedAudioMixing(handle, &mixing)` | `dsGetAssociatedAudioMixing()` must return `dsERR_NONE` and `mixing` must be a valid boolean value |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetassocaudiomixing_neg"></a>
### TestCase Name
dsGetAssocAudioMixing_neg

### TestCase ID
dsAudio L1-112

### TestCase Objective
Validate that `dsGetAssociatedAudioMixing()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get associated audio mixing with NULL output pointer | Invoke `dsGetAssociatedAudioMixing(handle, NULL)` | `dsGetAssociatedAudioMixing()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetfadercontrol_pos"></a>
### TestCase Name
dsSetFaderControl_pos

### TestCase ID
dsAudio L1-113

### TestCase Objective
Validate that `dsSetFaderControl()` succeeds when called with a valid mixer balance value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set fader control | Invoke `dsSetFaderControl(handle, 0)` | `dsSetFaderControl()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetfadercontrol_neg"></a>
### TestCase Name
dsSetFaderControl_neg

### TestCase ID
dsAudio L1-114

### TestCase Objective
Validate that `dsSetFaderControl()` returns an error when called with an out-of-range balance value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set fader control with out-of-range value | Invoke `dsSetFaderControl(handle, 101)` | `dsSetFaderControl()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetfadercontrol_pos"></a>
### TestCase Name
dsGetFaderControl_pos

### TestCase ID
dsAudio L1-115

### TestCase Objective
Validate that `dsGetFaderControl()` succeeds and returns the current mixer balance value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get fader control value | Invoke `dsGetFaderControl(handle, &mixerBalance)` | `dsGetFaderControl()` must return `dsERR_NONE` and `mixerBalance` must be in range [-100, 100] |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetfadercontrol_neg"></a>
### TestCase Name
dsGetFaderControl_neg

### TestCase ID
dsAudio L1-116

### TestCase Objective
Validate that `dsGetFaderControl()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get fader control with NULL output pointer | Invoke `dsGetFaderControl(handle, NULL)` | `dsGetFaderControl()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetprimarylang_pos"></a>
### TestCase Name
dsSetPrimaryLang_pos

### TestCase ID
dsAudio L1-117

### TestCase Objective
Validate that `dsSetPrimaryLanguage()` succeeds when called with a valid ISO 639-3 language code.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set primary language | Invoke `dsSetPrimaryLanguage(handle, "eng")` | `dsSetPrimaryLanguage()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetprimarylang_neg"></a>
### TestCase Name
dsSetPrimaryLang_neg

### TestCase ID
dsAudio L1-118

### TestCase Objective
Validate that `dsSetPrimaryLanguage()` returns an error when called with a NULL language string.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set primary language with NULL string | Invoke `dsSetPrimaryLanguage(handle, NULL)` | `dsSetPrimaryLanguage()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetprimarylang_pos"></a>
### TestCase Name
dsGetPrimaryLang_pos

### TestCase ID
dsAudio L1-119

### TestCase Objective
Validate that `dsGetPrimaryLanguage()` succeeds and returns the current primary language code.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get primary language | Invoke `dsGetPrimaryLanguage(handle, &lang)` | `dsGetPrimaryLanguage()` must return `dsERR_NONE` and `lang` must be a valid 3-character ISO 639-3 language code |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetprimarylang_neg"></a>
### TestCase Name
dsGetPrimaryLang_neg

### TestCase ID
dsAudio L1-120

### TestCase Objective
Validate that `dsGetPrimaryLanguage()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get primary language with NULL output pointer | Invoke `dsGetPrimaryLanguage(handle, NULL)` | `dsGetPrimaryLanguage()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetsecondarylang_pos"></a>
### TestCase Name
dsSetSecondaryLang_pos

### TestCase ID
dsAudio L1-121

### TestCase Objective
Validate that `dsSetSecondaryLanguage()` succeeds when called with a valid ISO 639-3 language code.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set secondary language | Invoke `dsSetSecondaryLanguage(handle, "spa")` | `dsSetSecondaryLanguage()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetsecondarylang_neg"></a>
### TestCase Name
dsSetSecondaryLang_neg

### TestCase ID
dsAudio L1-122

### TestCase Objective
Validate that `dsSetSecondaryLanguage()` returns an error when called with a NULL language string.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set secondary language with NULL string | Invoke `dsSetSecondaryLanguage(handle, NULL)` | `dsSetSecondaryLanguage()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetsecondarylang_pos"></a>
### TestCase Name
dsGetSecondaryLang_pos

### TestCase ID
dsAudio L1-123

### TestCase Objective
Validate that `dsGetSecondaryLanguage()` succeeds and returns the current secondary language code.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get secondary language | Invoke `dsGetSecondaryLanguage(handle, &lang)` | `dsGetSecondaryLanguage()` must return `dsERR_NONE` and `lang` must be a valid 3-character ISO 639-3 language code |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetsecondarylang_neg"></a>
### TestCase Name
dsGetSecondaryLang_neg

### TestCase ID
dsAudio L1-124

### TestCase Objective
Validate that `dsGetSecondaryLanguage()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get secondary language with NULL output pointer | Invoke `dsGetSecondaryLanguage(handle, NULL)` | `dsGetSecondaryLanguage()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetaudiomixlevels_pos"></a>
### TestCase Name
dsSetAudioMixLevels_pos

### TestCase ID
dsAudio L1-125

### TestCase Objective
Validate that `dsSetAudioMixLevels()` succeeds when called with valid primary and secondary mix levels.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set audio mix levels | Invoke `dsSetAudioMixLevels(handle, 100, 0)` with valid primary and secondary levels | `dsSetAudioMixLevels()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dssetaudiomixlevels_neg"></a>
### TestCase Name
dsSetAudioMixLevels_neg

### TestCase ID
dsAudio L1-126

### TestCase Objective
Validate that `dsSetAudioMixLevels()` returns an error when called with out-of-range mix level values.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set audio mix levels with out-of-range value | Invoke `dsSetAudioMixLevels(handle, 101, 0)` | `dsSetAudioMixLevels()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsaudioatmoscapsregcb_pos"></a>
### TestCase Name
dsAudioAtmosCapsRegCB_pos

### TestCase ID
dsAudio L1-127

### TestCase Objective
Validate that `dsAudioAtmosCapsChangeRegisterCB()` succeeds when called with a valid callback function.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Register Atmos capabilities change callback | Invoke `dsAudioAtmosCapsChangeRegisterCB(atmosCapsCBFunc)` with a valid callback | `dsAudioAtmosCapsChangeRegisterCB()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsaudioatmoscapsregcb_neg"></a>
### TestCase Name
dsAudioAtmosCapsRegCB_neg

### TestCase ID
dsAudio L1-128

### TestCase Objective
Validate that `dsAudioAtmosCapsChangeRegisterCB()` returns an error when called with a NULL callback.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Register Atmos capabilities change callback with NULL | Invoke `dsAudioAtmosCapsChangeRegisterCB(NULL)` | `dsAudioAtmosCapsChangeRegisterCB()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetsupportedarctypes_pos"></a>
### TestCase Name
dsGetSupportedARCTypes_pos

### TestCase ID
dsAudio L1-129

### TestCase Objective
Validate that `dsGetSupportedARCTypes()` succeeds and returns the supported ARC types bitmask for each valid audio port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get supported ARC types | Invoke `dsGetSupportedARCTypes(handle, &types)` | `dsGetSupportedARCTypes()` must return `dsERR_NONE` and `types` must be a valid bitmask of `dsAudioARCTypes_t` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsgetsupportedarctypes_neg"></a>
### TestCase Name
dsGetSupportedARCTypes_neg

### TestCase ID
dsAudio L1-130

### TestCase Objective
Validate that `dsGetSupportedARCTypes()` returns an error when called with a NULL output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Get supported ARC types with NULL output pointer | Invoke `dsGetSupportedARCTypes(handle, NULL)` | `dsGetSupportedARCTypes()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsaudiosetsad_pos"></a>
### TestCase Name
dsAudioSetSAD_pos

### TestCase ID
dsAudio L1-131

### TestCase Objective
Validate that `dsAudioSetSAD()` succeeds when called with a valid SAD (Short Audio Descriptor) list.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set SAD list | Invoke `dsAudioSetSAD(handle, &sad)` with a valid SAD list | `dsAudioSetSAD()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsaudiosetsad_neg"></a>
### TestCase Name
dsAudioSetSAD_neg

### TestCase ID
dsAudio L1-132

### TestCase Objective
Validate that `dsAudioSetSAD()` returns an error when called with a NULL SAD pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Set SAD list with NULL pointer | Invoke `dsAudioSetSAD(handle, NULL)` | `dsAudioSetSAD()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsaudioenablearc_pos"></a>
### TestCase Name
dsAudioEnableARC_pos

### TestCase ID
dsAudio L1-133

### TestCase Objective
Validate that `dsAudioEnableARC()` succeeds when called with a valid ARC type and enable value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Enable ARC | Invoke `dsAudioEnableARC(handle, arcType, true)` with a valid ARC type | `dsAudioEnableARC()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="dsaudioenablearc_neg"></a>
### TestCase Name
dsAudioEnableARC_neg

### TestCase ID
dsAudio L1-134

### TestCase Objective
Validate that `dsAudioEnableARC()` returns an error when called with an invalid ARC type.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle | Invoke `dsGetAudioPort(type, index, &handle)` | `dsGetAudioPort()` must return `dsERR_NONE` |
| Enable ARC with invalid type | Invoke `dsAudioEnableARC(handle, dsAUDIO_ARC_TYPE_MAX, true)` | `dsAudioEnableARC()` must return `dsERR_INVALID_PARAM` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

## Post-conditions

1. The `hal_test_dshal` binary exits cleanly after completing all test cases in the `[L1 dsAudio]` suite.
2. The DS Audio Port HAL module is terminated (via `dsAudioPortTerm()`) at the end of each test case, restoring the uninitialized default state.

---

## Test Attributes

| Attribute | Value |
| --- | --- |
| Supported Models | Video_Accelerator, RPI-Client |
| Estimated Duration | 60 minutes |
| Priority | High |
| TDK Release Version | M134 |
