## TestScript Name
VTS_DeepSleep_L1_test

## TestScript ID
VTS_Test_15

## Table of Contents

1. [Objective](#objective)
2. [Pre-conditions](#pre-conditions)
3. [Test Cases](#test-cases)
   - [PLAT_INIT_pos](#plat_init_pos)
   - [PLAT_INIT_neg](#plat_init_neg)
   - [PLAT_TERM_pos](#plat_term_pos)
   - [PLAT_TERM_neg](#plat_term_neg)
   - [PLAT_DeepSleepWakeup_pos](#plat_deepsleeepwakeup_pos)
   - [PLAT_DeepSleepWakeup_neg](#plat_deepsleeepwakeup_neg)
   - [PLAT_SetDeepSleep_pos](#plat_setdeepsleep_pos)
   - [PLAT_SetDeepSleep_neg](#plat_setdeepsleep_neg)
   - [PLAT_GetLastWakeupReason_pos](#plat_getlastwakeupreason_pos)
   - [PLAT_GetLastWakeupReason_neg](#plat_getlastwakeupreason_neg)
   - [PLAT_GetLastWakeupKeyCode_pos](#plat_getlastwakeupkeycode_pos)
   - [PLAT_GetLastWakeupKeyCode_neg](#plat_getlastwakeupkeycode_neg)
4. [Post-conditions](#post-conditions)
5. [Test Attributes](#test-attributes)

## Objective

This script executes all **L1 (Component Function)** test cases for the **Deep Sleep Manager HAL** module. L1 tests verify that every individual HAL API function behaves correctly when called with valid inputs (positive tests) and invalid/boundary inputs (negative tests), without requiring any external stimulus or hardware wake-up sources. The tests are run by invoking the `hal_test_iarmmgrs-deepsleep-hal` binary on the DUT via the TDK framework.

## Pre-conditions

### Pre-condition 1: VTS Package Installed

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Read VTS Base Path | Check the device config file for `VTS_BASE_PATH`. If set (e.g., `VTS_BASE_PATH = /opt/VTS_Package/`), that path is used as the base; otherwise the default `/VTS_Package/` is used | Base path is determined |
| Verify Binary and Config | Confirm the module sub-directory `deepsleep_manager/` exists under the base path and contains the required files | `<VTS_BASE_PATH>/deepsleep_manager/` exists and contains `hal_test_iarmmgrs-deepsleep-hal` and `deepsleepmanagerExtendedEnumsNotSupported.yaml` |

### Pre-condition 2: SSH Connectivity

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Read SSH Configuration | Read SSH connection parameters from the device config file: `SSH_PORT` (default: `22`), `SSH_METHOD` (e.g., `directSSH`), `SSH_USERNAME` (e.g., `root`), `SSH_PASSWORD` (`None` if no password required) | SSH parameters are available |
| Verify SSH Access | Establish an SSH session to the DUT using the configured parameters | SSH session is established successfully |

## Test Cases

---

<a id="plat_init_pos"></a>
### TestCase Name
PLAT_INIT_pos

### TestCase ID
DeepSleep_L1_01

### TestCase Objective
Verify that `PLAT_DS_INIT()` initializes the Deep Sleep Manager successfully and can be called, terminated, and re-initialized in sequence — each call returning `DEEPSLEEPMGR_SUCCESS`.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize | Call `PLAT_DS_INIT()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Terminate | Call `PLAT_DS_TERM()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Re-Initialize | Call `PLAT_DS_INIT()` again | Returns `DEEPSLEEPMGR_SUCCESS` |
| Re-Terminate | Call `PLAT_DS_TERM()` again | Returns `DEEPSLEEPMGR_SUCCESS` |

---

<a id="plat_init_neg"></a>
### TestCase Name
PLAT_INIT_neg

### TestCase ID
DeepSleep_L1_02

### TestCase Objective
Verify that calling `PLAT_DS_INIT()` when the module is already initialized returns `DEEPSLEEPMGR_ALREADY_INITIALIZED`.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize | Call `PLAT_DS_INIT()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Double Initialize | Call `PLAT_DS_INIT()` again while already initialized | Returns `DEEPSLEEPMGR_ALREADY_INITIALIZED` |
| Terminate | Call `PLAT_DS_TERM()` | Returns `DEEPSLEEPMGR_SUCCESS` |

---

<a id="plat_term_pos"></a>
### TestCase Name
PLAT_TERM_pos

### TestCase ID
DeepSleep_L1_03

### TestCase Objective
Verify that `PLAT_DS_TERM()` terminates the Deep Sleep Manager successfully after a valid initialization and returns `DEEPSLEEPMGR_SUCCESS`.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize | Call `PLAT_DS_INIT()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Terminate | Call `PLAT_DS_TERM()` | Returns `DEEPSLEEPMGR_SUCCESS` |

---

<a id="plat_term_neg"></a>
### TestCase Name
PLAT_TERM_neg

### TestCase ID
DeepSleep_L1_04

### TestCase Objective
Verify that `PLAT_DS_TERM()` returns `DEEPSLEEPMGR_NOT_INITIALIZED` when called before initialization or after an already-completed termination.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Terminate Without Init | Call `PLAT_DS_TERM()` before any `PLAT_DS_INIT()` | Returns `DEEPSLEEPMGR_NOT_INITIALIZED` |
| Initialize | Call `PLAT_DS_INIT()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Terminate | Call `PLAT_DS_TERM()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Double Terminate | Call `PLAT_DS_TERM()` again after already terminated | Returns `DEEPSLEEPMGR_NOT_INITIALIZED` |

---

<a id="plat_deepsleeepwakeup_pos"></a>
### TestCase Name
PLAT_DeepSleepWakeup_pos

### TestCase ID
DeepSleep_L1_05

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Deep sleep is not applicable for RPI (REFPLTV-2526).

### TestCase Objective
Verify that `PLAT_DS_DeepSleepWakeup()` completes post-wakeup processing successfully and returns `DEEPSLEEPMGR_SUCCESS` when called after initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize | Call `PLAT_DS_INIT()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Trigger Wakeup Processing | Call `PLAT_DS_DeepSleepWakeup()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Terminate | Call `PLAT_DS_TERM()` | Returns `DEEPSLEEPMGR_SUCCESS` |

---

<a id="plat_deepsleeepwakeup_neg"></a>
### TestCase Name
PLAT_DeepSleepWakeup_neg

### TestCase ID
DeepSleep_L1_06

### TestCase Objective
Verify that `PLAT_DS_DeepSleepWakeup()` returns `DEEPSLEEPMGR_NOT_INITIALIZED` when called before initialization or after termination.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Wakeup Before Init | Call `PLAT_DS_DeepSleepWakeup()` without prior `PLAT_DS_INIT()` | Returns `DEEPSLEEPMGR_NOT_INITIALIZED` |
| Initialize | Call `PLAT_DS_INIT()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Terminate | Call `PLAT_DS_TERM()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Wakeup After Term | Call `PLAT_DS_DeepSleepWakeup()` after `PLAT_DS_TERM()` | Returns `DEEPSLEEPMGR_NOT_INITIALIZED` |

---

<a id="plat_setdeepsleep_pos"></a>
### TestCase Name
PLAT_SetDeepSleep_pos

### TestCase ID
DeepSleep_L1_07

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Deep sleep is not applicable for RPI (REFPLTV-2526).

### TestCase Objective
Verify that `PLAT_DS_SetDeepSleep()` accepts valid timeout and `networkStandby` parameters (both `false` and `true`) and returns `DEEPSLEEPMGR_SUCCESS`. `PLAT_DS_DeepSleepWakeup()` is called after each sleep cycle to complete wakeup processing.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize | Call `PLAT_DS_INIT()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Set Deep Sleep (networkStandby=false) | Call `PLAT_DS_SetDeepSleep(deep_sleep_timeout=30, *isGPIOWakeup=false, networkStandby=false)` | Returns `DEEPSLEEPMGR_SUCCESS`; device enters deep sleep |
| Post-Wakeup (1st) | Call `PLAT_DS_DeepSleepWakeup()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Set Deep Sleep (networkStandby=true) | Call `PLAT_DS_SetDeepSleep(deep_sleep_timeout=30, *isGPIOWakeup=false, networkStandby=true)` | Returns `DEEPSLEEPMGR_SUCCESS`; device enters deep sleep with network standby enabled |
| Post-Wakeup (2nd) | Call `PLAT_DS_DeepSleepWakeup()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Terminate | Call `PLAT_DS_TERM()` | Returns `DEEPSLEEPMGR_SUCCESS` |

---

<a id="plat_setdeepsleep_neg"></a>
### TestCase Name
PLAT_SetDeepSleep_neg

### TestCase ID
DeepSleep_L1_08

### TestCase Objective
Verify that `PLAT_DS_SetDeepSleep()` returns `DEEPSLEEPMGR_NOT_INITIALIZED` when called before initialization or after termination, `DEEPSLEEPMGR_INVALID_ARGUMENT` when passed a `NULL` pointer for `isGPIOWakeup` or an out-of-range `deep_sleep_timeout` value (max valid = 604800 seconds).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Call Before Init | Call `PLAT_DS_SetDeepSleep(deep_sleep_timeout=60, *isGPIOWakeup=false, networkStandby=false)` without prior `PLAT_DS_INIT()` | Returns `DEEPSLEEPMGR_NOT_INITIALIZED` |
| Initialize | Call `PLAT_DS_INIT()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Null Pointer for isGPIOWakeup | Call `PLAT_DS_SetDeepSleep(deep_sleep_timeout=30, isGPIOWakeup=NULL, networkStandby=false)` | Returns `DEEPSLEEPMGR_INVALID_ARGUMENT` |
| Out-of-Range Timeout | Call `PLAT_DS_SetDeepSleep(deep_sleep_timeout=604801, *isGPIOWakeup=false, networkStandby=false)` — max valid value is 604800 | Returns `DEEPSLEEPMGR_INVALID_ARGUMENT` |
| Terminate | Call `PLAT_DS_TERM()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Call After Term | Call `PLAT_DS_SetDeepSleep(deep_sleep_timeout=60, *isGPIOWakeup=false, networkStandby=false)` after `PLAT_DS_TERM()` | Returns `DEEPSLEEPMGR_NOT_INITIALIZED` |

---

<a id="plat_getlastwakeupreason_pos"></a>
### TestCase Name
PLAT_GetLastWakeupReason_pos

### TestCase ID
DeepSleep_L1_09

### TestCase Objective
Verify that `PLAT_DS_GetLastWakeupReason()` retrieves a valid `DeepSleep_WakeupReason_t` value when called with a valid output pointer after initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize | Call `PLAT_DS_INIT()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Get Last Wakeup Reason | Call `PLAT_DS_GetLastWakeupReason(wakeupReason=<valid DeepSleep_WakeupReason_t*>)` | Returns `DEEPSLEEPMGR_SUCCESS`; `wakeupReason` is populated with a valid `DeepSleep_WakeupReason_t` enum value |
| Terminate | Call `PLAT_DS_TERM()` | Returns `DEEPSLEEPMGR_SUCCESS` |

---

<a id="plat_getlastwakeupreason_neg"></a>
### TestCase Name
PLAT_GetLastWakeupReason_neg

### TestCase ID
DeepSleep_L1_10

### TestCase Objective
Verify that `PLAT_DS_GetLastWakeupReason()` returns `DEEPSLEEPMGR_NOT_INITIALIZED` when called without initialization or after termination, and `DEEPSLEEPMGR_INVALID_ARGUMENT` when passed a `NULL` output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Call Without Init | Call `PLAT_DS_GetLastWakeupReason(wakeupReason=<valid DeepSleep_WakeupReason_t*>)` without prior `PLAT_DS_INIT()` | Returns `DEEPSLEEPMGR_NOT_INITIALIZED` |
| Initialize | Call `PLAT_DS_INIT()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Null Output Pointer | Call `PLAT_DS_GetLastWakeupReason(wakeupReason=NULL)` | Returns `DEEPSLEEPMGR_INVALID_ARGUMENT` |
| Terminate | Call `PLAT_DS_TERM()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Call After Term | Call `PLAT_DS_GetLastWakeupReason(wakeupReason=<valid DeepSleep_WakeupReason_t*>)` after `PLAT_DS_TERM()` | Returns `DEEPSLEEPMGR_NOT_INITIALIZED` |

---

<a id="plat_getlastwakeupkeycode_pos"></a>
### TestCase Name
PLAT_GetLastWakeupKeyCode_pos

### TestCase ID
DeepSleep_L1_11

### TestCase Objective
Verify that `PLAT_DS_GetLastWakeupKeyCode()` retrieves a valid `DeepSleepMgr_WakeupKeyCode_Param_t` value when called with a valid output pointer after initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize | Call `PLAT_DS_INIT()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Get Last Wakeup Key Code | Call `PLAT_DS_GetLastWakeupKeyCode(wakeupKeyCode=<valid DeepSleepMgr_WakeupKeyCode_Param_t*>)` | Returns `DEEPSLEEPMGR_SUCCESS`; `wakeupKeyCode` is populated with the last key code that triggered wakeup |
| Terminate | Call `PLAT_DS_TERM()` | Returns `DEEPSLEEPMGR_SUCCESS` |

---

<a id="plat_getlastwakeupkeycode_neg"></a>
### TestCase Name
PLAT_GetLastWakeupKeyCode_neg

### TestCase ID
DeepSleep_L1_12

### TestCase Objective
Verify that `PLAT_DS_GetLastWakeupKeyCode()` returns `DEEPSLEEPMGR_NOT_INITIALIZED` when called without initialization or after termination, and `DEEPSLEEPMGR_INVALID_ARGUMENT` when passed a `NULL` output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Call Without Init | Call `PLAT_DS_GetLastWakeupKeyCode(wakeupKeyCode=<valid DeepSleepMgr_WakeupKeyCode_Param_t*>)` without prior `PLAT_DS_INIT()` | Returns `DEEPSLEEPMGR_NOT_INITIALIZED` |
| Initialize | Call `PLAT_DS_INIT()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Null Output Pointer | Call `PLAT_DS_GetLastWakeupKeyCode(wakeupKeyCode=NULL)` | Returns `DEEPSLEEPMGR_INVALID_ARGUMENT` |
| Terminate | Call `PLAT_DS_TERM()` | Returns `DEEPSLEEPMGR_SUCCESS` |
| Call After Term | Call `PLAT_DS_GetLastWakeupKeyCode(wakeupKeyCode=<valid DeepSleepMgr_WakeupKeyCode_Param_t*>)` after `PLAT_DS_TERM()` | Returns `DEEPSLEEPMGR_NOT_INITIALIZED` |

---

## Post-conditions

On completion of all test cases, the `hal_test_iarmmgrs-deepsleep-hal` binary exits cleanly. The Deep Sleep Manager is terminated via `PLAT_DS_TERM()`, restoring the module to its uninitialized default state.

## Test Attributes

| Attribute | Value |
| --- | --- |
| Supported Models | Video Accelerator, RPI-Client |
| Estimated Duration | 15 minutes |
| Priority | High |
| TDK Release Version | M134 |