## TestScript Name
VTS_dsAudio_L2_test

## TestScript ID
VTS_Test_08

## Table of Contents

1. [Objective](#objective)
2. [Pre-conditions](#pre-conditions)
3. [Test Cases](#test-cases)
   - [EnableDisableVerifyPortStatus](#enabledisableverifyportstatus)
   - [GetAndVerifyMS12Capabilities](#getandverifyms12capabilities)
   - [SetAndGetAudioCompression](#setandgetaudiocompression)
   - [SetAndGetDialogEnhancement](#setandgetdialogenhancement)
   - [SetAndGetDolbyVolumeMode](#setandgetdolbyvolumemode)
   - [SetAndGetIntelligentEqualizerMode](#setandgetintelligentequalizermode)
   - [SetAndGetVolumeLeveller](#setandgetvolumeleveller)
   - [SetAndGetBassEnhancer](#setandgetbassenhancer)
   - [EnableAndVerifySurroundDecoder](#enableandverifysurrounddecoder)
   - [SetAndGetDRCMode](#setandgetdrcmode)
   - [SetAndGetSurroundVirtualizer](#setandgetsurroundvirtualizer)
   - [SetAndGetMISteering](#setandgetmisteering)
   - [SetAndGetGraphicEqualizerMode](#setandgetgraphicequalizermode)
   - [EnableDisableAndRetrieveLEConfig](#enabledisableandretrieveleconfig)
   - [CheckMS12DecodeSupport](#checkms12decodesupport)
   - [CheckMS11DecodeSupport](#checkms11decodesupport)
   - [SetAndGetStereoMode](#setandgetstereomode)
   - [AudioMuteVerification](#audiomuteverification)
   - [SetAndGetAudioDelay](#setandgetaudiodelay)
   - [GetAudioCapabilities](#getaudiocapabilities)
   - [EnableDisableRetrieveAudioMixing](#enabledisableretrieveaudiomixing)
   - [AudioPortControl](#audioportcontrol)
   - [SetAndGetPrimaryLanguage](#setandgetprimarylanguage)
   - [SetAndGetSecondaryLanguage](#setandgetsecondarylanguage)
4. [Post-conditions](#post-conditions)
5. [Test Attributes](#test-attributes)

---

## Objective

This script executes VTS L2 (Level 2) test cases for the Device Settings Audio Port HAL module (`dsAudio`). L2 tests validate end-to-end workflows that exercise sequences of HAL APIs and compare results against the device profile configuration to verify functional correctness on source platforms. No external stimulus is required; the tests rely on the HAL implementation and the profile configuration. The binary used is `hal_test_dshal`, invoked with the profile `Source_AudioSettings.yaml`.

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

<a id="enabledisableverifyportstatus"></a>
### TestCase Name
EnableDisableVerifyPortStatus

### TestCase ID
dsAudio L2-1

### TestCase Objective
Validate that `dsEnableAudioPort()` and `dsIsAudioPortEnabled()` work correctly together — that enabling and disabling audio ports can be verified for each supported port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Enable the audio port | Invoke `dsEnableAudioPort(handle, true)` | `dsEnableAudioPort()` must return `dsERR_NONE` |
| Verify audio port is enabled | Invoke `dsIsAudioPortEnabled(handle, &enabled)` | `dsIsAudioPortEnabled()` must return `dsERR_NONE` and `enabled` must be `true` |
| Disable the audio port | Invoke `dsEnableAudioPort(handle, false)` | `dsEnableAudioPort()` must return `dsERR_NONE` |
| Verify audio port is disabled | Invoke `dsIsAudioPortEnabled(handle, &enabled)` | `dsIsAudioPortEnabled()` must return `dsERR_NONE` and `enabled` must be `false` |
| Re-enable the audio port | Invoke `dsEnableAudioPort(handle, true)` | `dsEnableAudioPort()` must return `dsERR_NONE` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="getandverifyms12capabilities"></a>
### TestCase Name
GetAndVerifyMS12Capabilities

### TestCase ID
dsAudio L2-2

### TestCase Objective
Validate that `dsGetMS12Capabilities()` returns MS12 capabilities matching the expected values from the device profile for each supported audio port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Get MS12 capabilities | Invoke `dsGetMS12Capabilities(handle, &capabilities)` | `dsGetMS12Capabilities()` must return `dsERR_NONE` and `capabilities` must match `ms12Capabilities` from the profile |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="setandgetaudiocompression"></a>
### TestCase Name
SetAndGetAudioCompression

### TestCase ID
dsAudio L2-3

### TestCase Objective
Validate that `dsSetAudioCompression()` and `dsGetAudioCompression()` work correctly together — that the compression value written can be read back with the same value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Set audio compression for each valid value | Invoke `dsSetAudioCompression(handle, compressionSet)` for each value in range [0, 10] | `dsSetAudioCompression()` must return `dsERR_NONE` |
| Verify audio compression was set | Invoke `dsGetAudioCompression(handle, &compressionGet)` after each set call | `dsGetAudioCompression()` must return `dsERR_NONE` and `compressionGet` must equal `compressionSet` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="setandgetdialogenhancement"></a>
### TestCase Name
SetAndGetDialogEnhancement

### TestCase ID
dsAudio L2-4

### TestCase Objective
Validate that `dsSetDialogEnhancement()` and `dsGetDialogEnhancement()` work correctly together — that the dialog enhancement level written can be read back with the same value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Set dialog enhancement for each valid level | Invoke `dsSetDialogEnhancement(handle, levelSet)` for each value in range [0, 16] | `dsSetDialogEnhancement()` must return `dsERR_NONE` |
| Verify dialog enhancement was set | Invoke `dsGetDialogEnhancement(handle, &levelGet)` after each set call | `dsGetDialogEnhancement()` must return `dsERR_NONE` and `levelGet` must equal `levelSet` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="setandgetdolbyvolumemode"></a>
### TestCase Name
SetAndGetDolbyVolumeMode

### TestCase ID
dsAudio L2-5

### TestCase Objective
Validate that `dsSetDolbyVolumeMode()` and `dsGetDolbyVolumeMode()` work correctly together — that the Dolby volume mode written can be read back with the same value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Enable Dolby volume mode | Invoke `dsSetDolbyVolumeMode(handle, true)` | `dsSetDolbyVolumeMode()` must return `dsERR_NONE` |
| Verify Dolby volume mode is enabled | Invoke `dsGetDolbyVolumeMode(handle, &modeGet)` | `dsGetDolbyVolumeMode()` must return `dsERR_NONE` and `modeGet` must be `true` |
| Disable Dolby volume mode | Invoke `dsSetDolbyVolumeMode(handle, false)` | `dsSetDolbyVolumeMode()` must return `dsERR_NONE` |
| Verify Dolby volume mode is disabled | Invoke `dsGetDolbyVolumeMode(handle, &modeGet)` | `dsGetDolbyVolumeMode()` must return `dsERR_NONE` and `modeGet` must be `false` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="setandgetintelligentequalizermode"></a>
### TestCase Name
SetAndGetIntelligentEqualizerMode

### TestCase ID
dsAudio L2-6

### TestCase Objective
Validate that `dsSetIntelligentEqualizerMode()` and `dsGetIntelligentEqualizerMode()` work correctly together — that the mode written can be read back with the same value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Set intelligent equalizer mode for each valid value | Invoke `dsSetIntelligentEqualizerMode(handle, modeSet)` for each value in range [0, 6] | `dsSetIntelligentEqualizerMode()` must return `dsERR_NONE` |
| Verify intelligent equalizer mode was set | Invoke `dsGetIntelligentEqualizerMode(handle, &modeGet)` after each set call | `dsGetIntelligentEqualizerMode()` must return `dsERR_NONE` and `modeGet` must equal `modeSet` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="setandgetvolumeleveller"></a>
### TestCase Name
SetAndGetVolumeLeveller

### TestCase ID
dsAudio L2-7

### TestCase Objective
Validate that `dsSetVolumeLeveller()` and `dsGetVolumeLeveller()` work correctly together — that the volume leveller settings written can be read back with the same values.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Set volume leveller for each valid mode and level combination | Invoke `dsSetVolumeLeveller(handle, volLevellerSet)` for each valid mode/level combination from the profile | `dsSetVolumeLeveller()` must return `dsERR_NONE` |
| Verify volume leveller was set | Invoke `dsGetVolumeLeveller(handle, &volLevellerGet)` after each set call | `dsGetVolumeLeveller()` must return `dsERR_NONE` and `volLevellerGet.mode` and `volLevellerGet.level` must equal the set values |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="setandgetbassenhancer"></a>
### TestCase Name
SetAndGetBassEnhancer

### TestCase ID
dsAudio L2-8

### TestCase Objective
Validate that `dsSetBassEnhancer()` and `dsGetBassEnhancer()` work correctly together — that the bass boost value written can be read back with the same value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Set bass enhancer for each valid boost value | Invoke `dsSetBassEnhancer(handle, boostSet)` for each valid value in range [0, 100] | `dsSetBassEnhancer()` must return `dsERR_NONE` |
| Verify bass enhancer was set | Invoke `dsGetBassEnhancer(handle, &boostGet)` after each set call | `dsGetBassEnhancer()` must return `dsERR_NONE` and `boostGet` must equal `boostSet` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="enableandverifysurrounddecoder"></a>
### TestCase Name
EnableAndVerifySurroundDecoder

### TestCase ID
dsAudio L2-9

### TestCase Objective
Validate that `dsEnableSurroundDecoder()` and `dsIsSurroundDecoderEnabled()` work correctly together — that enabling and disabling the surround decoder can be verified.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Enable surround decoder | Invoke `dsEnableSurroundDecoder(handle, true)` | `dsEnableSurroundDecoder()` must return `dsERR_NONE` |
| Verify surround decoder is enabled | Invoke `dsIsSurroundDecoderEnabled(handle, &enabled)` | `dsIsSurroundDecoderEnabled()` must return `dsERR_NONE` and `enabled` must be `true` |
| Disable surround decoder | Invoke `dsEnableSurroundDecoder(handle, false)` | `dsEnableSurroundDecoder()` must return `dsERR_NONE` |
| Verify surround decoder is disabled | Invoke `dsIsSurroundDecoderEnabled(handle, &enabled)` | `dsIsSurroundDecoderEnabled()` must return `dsERR_NONE` and `enabled` must be `false` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="setandgetdrcmode"></a>
### TestCase Name
SetAndGetDRCMode

### TestCase ID
dsAudio L2-10

### TestCase Objective
Validate that `dsSetDRCMode()` and `dsGetDRCMode()` work correctly together — that the DRC mode written can be read back with the same value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Set DRC mode for each valid value | Invoke `dsSetDRCMode(handle, modeSet)` for each value (0 and 1) | `dsSetDRCMode()` must return `dsERR_NONE` |
| Verify DRC mode was set | Invoke `dsGetDRCMode(handle, &modeGet)` after each set call | `dsGetDRCMode()` must return `dsERR_NONE` and `modeGet` must equal `modeSet` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="setandgetsurroundvirtualizer"></a>
### TestCase Name
SetAndGetSurroundVirtualizer

### TestCase ID
dsAudio L2-11

### TestCase Objective
Validate that `dsSetSurroundVirtualizer()` and `dsGetSurroundVirtualizer()` work correctly together — that the surround virtualizer settings written can be read back with the same values.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Set surround virtualizer for each valid mode/boost combination | Invoke `dsSetSurroundVirtualizer(handle, virtSet)` for each valid combination from the profile | `dsSetSurroundVirtualizer()` must return `dsERR_NONE` |
| Verify surround virtualizer was set | Invoke `dsGetSurroundVirtualizer(handle, &virtGet)` after each set call | `dsGetSurroundVirtualizer()` must return `dsERR_NONE` and `virtGet.mode` and `virtGet.boost` must equal the set values |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="setandgetmisteering"></a>
### TestCase Name
SetAndGetMISteering

### TestCase ID
dsAudio L2-12

### TestCase Objective
Validate that `dsSetMISteering()` and `dsGetMISteering()` work correctly together — that the MI steering state written can be read back with the same value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Enable MI steering | Invoke `dsSetMISteering(handle, true)` | `dsSetMISteering()` must return `dsERR_NONE` |
| Verify MI steering is enabled | Invoke `dsGetMISteering(handle, &enabledGet)` | `dsGetMISteering()` must return `dsERR_NONE` and `enabledGet` must be `true` |
| Disable MI steering | Invoke `dsSetMISteering(handle, false)` | `dsSetMISteering()` must return `dsERR_NONE` |
| Verify MI steering is disabled | Invoke `dsGetMISteering(handle, &enabledGet)` | `dsGetMISteering()` must return `dsERR_NONE` and `enabledGet` must be `false` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="setandgetgraphicequalizermode"></a>
### TestCase Name
SetAndGetGraphicEqualizerMode

### TestCase ID
dsAudio L2-13

### TestCase Objective
Validate that `dsSetGraphicEqualizerMode()` and `dsGetGraphicEqualizerMode()` work correctly together — that the graphic equalizer mode written can be read back with the same value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Set graphic equalizer mode for each valid value | Invoke `dsSetGraphicEqualizerMode(handle, modeSet)` for each value in range [0, 3] | `dsSetGraphicEqualizerMode()` must return `dsERR_NONE` |
| Verify graphic equalizer mode was set | Invoke `dsGetGraphicEqualizerMode(handle, &modeGet)` after each set call | `dsGetGraphicEqualizerMode()` must return `dsERR_NONE` and `modeGet` must equal `modeSet` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="enabledisableandretrieveleconfig"></a>
### TestCase Name
EnableDisableAndRetrieveLEConfig

### TestCase ID
dsAudio L2-14

### TestCase Objective
Validate that `dsEnableLEConfig()` and `dsGetLEConfig()` work correctly together — that enabling and disabling LE (Loudness Equivalence) configuration can be verified.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Enable LE config | Invoke `dsEnableLEConfig(handle, true)` | `dsEnableLEConfig()` must return `dsERR_NONE` |
| Verify LE config is enabled | Invoke `dsGetLEConfig(handle, &enabledGet)` | `dsGetLEConfig()` must return `dsERR_NONE` and `enabledGet` must be `true` |
| Disable LE config | Invoke `dsEnableLEConfig(handle, false)` | `dsEnableLEConfig()` must return `dsERR_NONE` |
| Verify LE config is disabled | Invoke `dsGetLEConfig(handle, &enabledGet)` | `dsGetLEConfig()` must return `dsERR_NONE` and `enabledGet` must be `false` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="checkms12decodesupport"></a>
### TestCase Name
CheckMS12DecodeSupport

### TestCase ID
dsAudio L2-15

### TestCase Objective
Validate that `dsIsAudioMS12Decode()` returns the MS12 decode support status matching the expected value from the device profile.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Check MS12 decode support | Invoke `dsIsAudioMS12Decode(handle, &supported)` | `dsIsAudioMS12Decode()` must return `dsERR_NONE` and `supported` must match `MS12Decode` from the profile |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="checkms11decodesupport"></a>
### TestCase Name
CheckMS11DecodeSupport

### TestCase ID
dsAudio L2-16

### TestCase Objective
Validate that `dsIsAudioMSDecode()` returns the MS11 decode support status matching the expected value from the device profile.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Check MS11 decode support | Invoke `dsIsAudioMSDecode(handle, &supported)` | `dsIsAudioMSDecode()` must return `dsERR_NONE` and `supported` must match `MS11Decode` from the profile |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="setandgetstereomode"></a>
### TestCase Name
SetAndGetStereoMode

### TestCase ID
dsAudio L2-17

### TestCase Objective
Validate that `dsSetStereoMode()` and `dsGetStereoMode()` work correctly together — that each supported stereo mode written can be read back with the same value.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI (REFPLTV-2543).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Set stereo mode for each supported mode | Invoke `dsSetStereoMode(handle, modeSet)` for each supported stereo mode from the profile | `dsSetStereoMode()` must return `dsERR_NONE` |
| Verify stereo mode was set | Invoke `dsGetStereoMode(handle, &modeGet)` after each set call | `dsGetStereoMode()` must return `dsERR_NONE` and `modeGet` must equal `modeSet` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="audiomuteverification"></a>
### TestCase Name
AudioMuteVerification

### TestCase ID
dsAudio L2-18

### TestCase Objective
Validate that `dsSetAudioMute()` and `dsIsAudioMute()` work correctly together — that muting and unmuting the audio port can be verified.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Mute the audio port | Invoke `dsSetAudioMute(handle, true)` | `dsSetAudioMute()` must return `dsERR_NONE` |
| Verify audio port is muted | Invoke `dsIsAudioMute(handle, &muted)` | `dsIsAudioMute()` must return `dsERR_NONE` and `muted` must be `true` |
| Unmute the audio port | Invoke `dsSetAudioMute(handle, false)` | `dsSetAudioMute()` must return `dsERR_NONE` |
| Verify audio port is unmuted | Invoke `dsIsAudioMute(handle, &muted)` | `dsIsAudioMute()` must return `dsERR_NONE` and `muted` must be `false` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="setandgetaudiodelay"></a>
### TestCase Name
SetAndGetAudioDelay

### TestCase ID
dsAudio L2-19

### TestCase Objective
Validate that `dsSetAudioDelay()` and `dsGetAudioDelay()` work correctly together — that the audio delay value written can be read back with the same value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Set audio delay for each test value | Invoke `dsSetAudioDelay(handle, delaySet)` for each valid delay value from the profile | `dsSetAudioDelay()` must return `dsERR_NONE` |
| Verify audio delay was set | Invoke `dsGetAudioDelay(handle, &delayGet)` after each set call | `dsGetAudioDelay()` must return `dsERR_NONE` and `delayGet` must equal `delaySet` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="getaudiocapabilities"></a>
### TestCase Name
GetAudioCapabilities

### TestCase ID
dsAudio L2-20

### TestCase Objective
Validate that `dsGetAudioCapabilities()` returns audio capabilities matching the expected values from the device profile for each supported audio port.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Get audio capabilities | Invoke `dsGetAudioCapabilities(handle, &capabilities)` | `dsGetAudioCapabilities()` must return `dsERR_NONE` and `capabilities` must match `AudioCapabilities` from the profile |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="enabledisableretrieveaudiomixing"></a>
### TestCase Name
EnableDisableRetrieveAudioMixing

### TestCase ID
dsAudio L2-21

### TestCase Objective
Validate that `dsSetAssociatedAudioMixing()` and `dsGetAssociatedAudioMixing()` work correctly together — that enabling and disabling associated audio mixing can be verified.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Enable associated audio mixing | Invoke `dsSetAssociatedAudioMixing(handle, true)` | `dsSetAssociatedAudioMixing()` must return `dsERR_NONE` |
| Verify associated audio mixing is enabled | Invoke `dsGetAssociatedAudioMixing(handle, &mixingGet)` | `dsGetAssociatedAudioMixing()` must return `dsERR_NONE` and `mixingGet` must be `true` |
| Disable associated audio mixing | Invoke `dsSetAssociatedAudioMixing(handle, false)` | `dsSetAssociatedAudioMixing()` must return `dsERR_NONE` |
| Verify associated audio mixing is disabled | Invoke `dsGetAssociatedAudioMixing(handle, &mixingGet)` | `dsGetAssociatedAudioMixing()` must return `dsERR_NONE` and `mixingGet` must be `false` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="audioportcontrol"></a>
### TestCase Name
AudioPortControl

### TestCase ID
dsAudio L2-22

### TestCase Objective
Validate the audio port control workflow — that the port can be enabled, its connected state queried, and the port level set and retrieved correctly.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Enable the audio port | Invoke `dsEnableAudioPort(handle, true)` | `dsEnableAudioPort()` must return `dsERR_NONE` |
| Set audio level | Invoke `dsSetAudioLevel(handle, levelSet)` with a valid level value | `dsSetAudioLevel()` must return `dsERR_NONE` |
| Get audio level | Invoke `dsGetAudioLevel(handle, &levelGet)` | `dsGetAudioLevel()` must return `dsERR_NONE` and `levelGet` must equal `levelSet` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="setandgetprimarylanguage"></a>
### TestCase Name
SetAndGetPrimaryLanguage

### TestCase ID
dsAudio L2-23

### TestCase Objective
Validate that `dsSetPrimaryLanguage()` and `dsGetPrimaryLanguage()` work correctly together — that the primary language code written can be read back with the same value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Set primary language | Invoke `dsSetPrimaryLanguage(handle, "eng")` | `dsSetPrimaryLanguage()` must return `dsERR_NONE` |
| Verify primary language was set | Invoke `dsGetPrimaryLanguage(handle, &langGet)` | `dsGetPrimaryLanguage()` must return `dsERR_NONE` and `langGet` must equal `"eng"` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

<a id="setandgetsecondarylanguage"></a>
### TestCase Name
SetAndGetSecondaryLanguage

### TestCase ID
dsAudio L2-24

### TestCase Objective
Validate that `dsSetSecondaryLanguage()` and `dsGetSecondaryLanguage()` work correctly together — that the secondary language code written can be read back with the same value.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the audio port sub-system | Invoke `dsAudioPortInit()` | `dsAudioPortInit()` must return `dsERR_NONE` |
| Get audio port handle for each supported port | Invoke `dsGetAudioPort(type, index, &handle)` for each port from the profile | `dsGetAudioPort()` must return `dsERR_NONE` and a valid handle |
| Set secondary language | Invoke `dsSetSecondaryLanguage(handle, "spa")` | `dsSetSecondaryLanguage()` must return `dsERR_NONE` |
| Verify secondary language was set | Invoke `dsGetSecondaryLanguage(handle, &langGet)` | `dsGetSecondaryLanguage()` must return `dsERR_NONE` and `langGet` must equal `"spa"` |
| Terminate the audio port sub-system | Invoke `dsAudioPortTerm()` | `dsAudioPortTerm()` must return `dsERR_NONE` |

---

## Post-conditions

1. The `hal_test_dshal` binary exits cleanly after completing all test cases in the `[L2 dsAudio - Source]` suite.
2. The DS Audio Port HAL module is terminated (via `dsAudioPortTerm()`) at the end of each test case, restoring the uninitialized default state.

---

## Test Attributes

| Attribute | Value |
| --- | --- |
| Supported Models | Video_Accelerator, RPI-Client |
| Estimated Duration | 20 minutes |
| Priority | High |
| TDK Release Version | M134 |
