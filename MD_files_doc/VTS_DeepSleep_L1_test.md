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
deepSleepMgr L1-1

### TestCase Objective
Verify that `PLAT_DS_INIT()` initializes the Deep Sleep Manager successfully and can be called, terminated, and re-initialized in sequence — each call returning `DEEPSLEEPMGR_SUCCESS`.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the Deep Sleep Management module | Invoke `PLAT_DS_INIT()` | `PLAT_DS_INIT()` must return `DEEPSLEEPMGR_SUCCESS` |
| Terminate the Deep Sleep Management module | Invoke `PLAT_DS_TERM()` | `PLAT_DS_TERM()` must return `DEEPSLEEPMGR_SUCCESS` |
| Re-initialize the Deep Sleep Management module | Invoke `PLAT_DS_INIT()` again | `PLAT_DS_INIT()` must return `DEEPSLEEPMGR_SUCCESS` |
| Re-terminate the Deep Sleep Management module | Invoke `PLAT_DS_TERM()` again | `PLAT_DS_TERM()` must return `DEEPSLEEPMGR_SUCCESS` |

---

<a id="plat_init_neg"></a>
### TestCase Name
PLAT_INIT_neg

### TestCase ID
deepSleepMgr L1-2

### TestCase Objective
Verify that calling `PLAT_DS_INIT()` when the module is already initialized returns `DEEPSLEEPMGR_ALREADY_INITIALIZED`.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the Deep Sleep Management module | Invoke `PLAT_DS_INIT()` | `PLAT_DS_INIT()` must return `DEEPSLEEPMGR_SUCCESS` |
| Initialize again while module is already initialized | Invoke `PLAT_DS_INIT()` again while module is already initialized | `PLAT_DS_INIT()` must return `DEEPSLEEPMGR_ALREADY_INITIALIZED` |
| Terminate the Deep Sleep Management module | Invoke `PLAT_DS_TERM()` | `PLAT_DS_TERM()` must return `DEEPSLEEPMGR_SUCCESS` |

---

<a id="plat_term_pos"></a>
### TestCase Name
PLAT_TERM_pos

### TestCase ID
deepSleepMgr L1-3

### TestCase Objective
Verify that `PLAT_DS_TERM()` terminates the Deep Sleep Manager successfully after a valid initialization and returns `DEEPSLEEPMGR_SUCCESS`.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the Deep Sleep Management module | Invoke `PLAT_DS_INIT()` | `PLAT_DS_INIT()` must return `DEEPSLEEPMGR_SUCCESS` |
| Terminate the Deep Sleep Management module | Invoke `PLAT_DS_TERM()` | `PLAT_DS_TERM()` must return `DEEPSLEEPMGR_SUCCESS` |

---

<a id="plat_term_neg"></a>
### TestCase Name
PLAT_TERM_neg

### TestCase ID
deepSleepMgr L1-4

### TestCase Objective
Verify that `PLAT_DS_TERM()` returns `DEEPSLEEPMGR_NOT_INITIALIZED` when called before initialization or after an already-completed termination.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Terminate the module without prior initialization | Invoke `PLAT_DS_TERM()` before any `PLAT_DS_INIT()` | `PLAT_DS_TERM()` must return `DEEPSLEEPMGR_NOT_INITIALIZED` |
| Initialize the Deep Sleep Management module | Invoke `PLAT_DS_INIT()` | `PLAT_DS_INIT()` must return `DEEPSLEEPMGR_SUCCESS` |
| Terminate the Deep Sleep Management module | Invoke `PLAT_DS_TERM()` | `PLAT_DS_TERM()` must return `DEEPSLEEPMGR_SUCCESS` |
| Terminate again after module is already terminated | Invoke `PLAT_DS_TERM()` again after module is already terminated | `PLAT_DS_TERM()` must return `DEEPSLEEPMGR_NOT_INITIALIZED` |

---

<a id="plat_deepsleeepwakeup_pos"></a>
### TestCase Name
PLAT_DeepSleepWakeup_pos

### TestCase ID
deepSleepMgr L1-5

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Deep sleep is not applicable for RPI (REFPLTV-2526).

### TestCase Objective
Verify that `PLAT_DS_DeepSleepWakeup()` completes post-wakeup processing successfully and returns `DEEPSLEEPMGR_SUCCESS` when called after initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the Deep Sleep Management module | Invoke `PLAT_DS_INIT()` | `PLAT_DS_INIT()` must return `DEEPSLEEPMGR_SUCCESS` |
| Configure platform status after deep sleep wake-up | Invoke `PLAT_DS_DeepSleepWakeup()` | `PLAT_DS_DeepSleepWakeup()` must return `DEEPSLEEPMGR_SUCCESS` |
| Terminate the Deep Sleep Management module | Invoke `PLAT_DS_TERM()` | `PLAT_DS_TERM()` must return `DEEPSLEEPMGR_SUCCESS` |

---

<a id="plat_deepsleeepwakeup_neg"></a>
### TestCase Name
PLAT_DeepSleepWakeup_neg

### TestCase ID
deepSleepMgr L1-6

### TestCase Objective
Verify that `PLAT_DS_DeepSleepWakeup()` returns `DEEPSLEEPMGR_NOT_INITIALIZED` when called before initialization or after termination.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Configure platform wake-up status without prior initialization | Invoke `PLAT_DS_DeepSleepWakeup()` without prior `PLAT_DS_INIT()` | `PLAT_DS_DeepSleepWakeup()` must return `DEEPSLEEPMGR_NOT_INITIALIZED` |
| Initialize the Deep Sleep Management module | Invoke `PLAT_DS_INIT()` | `PLAT_DS_INIT()` must return `DEEPSLEEPMGR_SUCCESS` |
| Terminate the Deep Sleep Management module | Invoke `PLAT_DS_TERM()` | `PLAT_DS_TERM()` must return `DEEPSLEEPMGR_SUCCESS` |
| Configure platform wake-up status after module terminated | Invoke `PLAT_DS_DeepSleepWakeup()` after `PLAT_DS_TERM()` | `PLAT_DS_DeepSleepWakeup()` must return `DEEPSLEEPMGR_NOT_INITIALIZED` |

---

<a id="plat_setdeepsleep_pos"></a>
### TestCase Name
PLAT_SetDeepSleep_pos

### TestCase ID
deepSleepMgr L1-7

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Deep sleep is not applicable for RPI (REFPLTV-2526).

### TestCase Objective
Verify that `PLAT_DS_SetDeepSleep()` accepts valid timeout and `networkStandby` parameters (both `false` and `true`) and returns `DEEPSLEEPMGR_SUCCESS`. `PLAT_DS_DeepSleepWakeup()` is called after each sleep cycle to complete wakeup processing.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the Deep Sleep Management module | Invoke `PLAT_DS_INIT()` | `PLAT_DS_INIT()` must return `DEEPSLEEPMGR_SUCCESS` |
| Set CPE power state to Deep Sleep with network standby disabled | Invoke `PLAT_DS_SetDeepSleep(deep_sleep_timeout=30, *isGPIOWakeup=false, networkStandby=false)` | `PLAT_DS_SetDeepSleep()` must return `DEEPSLEEPMGR_SUCCESS`; device enters deep sleep |
| Configure platform status after first wake-up | Invoke `PLAT_DS_DeepSleepWakeup()` | `PLAT_DS_DeepSleepWakeup()` must return `DEEPSLEEPMGR_SUCCESS` |
| Set CPE power state to Deep Sleep with network standby enabled | Invoke `PLAT_DS_SetDeepSleep(deep_sleep_timeout=30, *isGPIOWakeup=false, networkStandby=true)` | `PLAT_DS_SetDeepSleep()` must return `DEEPSLEEPMGR_SUCCESS`; device enters deep sleep with network standby enabled |
| Configure platform status after second wake-up | Invoke `PLAT_DS_DeepSleepWakeup()` | `PLAT_DS_DeepSleepWakeup()` must return `DEEPSLEEPMGR_SUCCESS` |
| Terminate the Deep Sleep Management module | Invoke `PLAT_DS_TERM()` | `PLAT_DS_TERM()` must return `DEEPSLEEPMGR_SUCCESS` |

---

<a id="plat_setdeepsleep_neg"></a>
### TestCase Name
PLAT_SetDeepSleep_neg

### TestCase ID
deepSleepMgr L1-8

### TestCase Objective
Verify that `PLAT_DS_SetDeepSleep()` returns `DEEPSLEEPMGR_NOT_INITIALIZED` when called before initialization or after termination, `DEEPSLEEPMGR_INVALID_ARGUMENT` when passed a `NULL` pointer for `isGPIOWakeup` or an out-of-range `deep_sleep_timeout` value (max valid = 604800 seconds).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Set CPE power state to Deep Sleep without prior initialization | Invoke `PLAT_DS_SetDeepSleep(deep_sleep_timeout=60, *isGPIOWakeup=false, networkStandby=false)` without prior `PLAT_DS_INIT()` | `PLAT_DS_SetDeepSleep()` must return `DEEPSLEEPMGR_NOT_INITIALIZED` |
| Initialize the Deep Sleep Management module | Invoke `PLAT_DS_INIT()` | `PLAT_DS_INIT()` must return `DEEPSLEEPMGR_SUCCESS` |
| Set CPE power state with NULL isGPIOWakeup output pointer | Invoke `PLAT_DS_SetDeepSleep(deep_sleep_timeout=30, isGPIOWakeup=NULL, networkStandby=false)` | `PLAT_DS_SetDeepSleep()` must return `DEEPSLEEPMGR_INVALID_ARGUMENT` |
| Set CPE power state with out-of-range timeout | Invoke `PLAT_DS_SetDeepSleep(deep_sleep_timeout=604801, *isGPIOWakeup=false, networkStandby=false)` — max valid timeout is 604800 seconds | `PLAT_DS_SetDeepSleep()` must return `DEEPSLEEPMGR_INVALID_ARGUMENT` |
| Terminate the Deep Sleep Management module | Invoke `PLAT_DS_TERM()` | `PLAT_DS_TERM()` must return `DEEPSLEEPMGR_SUCCESS` |
| Set CPE power state to Deep Sleep after module terminated | Invoke `PLAT_DS_SetDeepSleep(deep_sleep_timeout=60, *isGPIOWakeup=false, networkStandby=false)` after `PLAT_DS_TERM()` | `PLAT_DS_SetDeepSleep()` must return `DEEPSLEEPMGR_NOT_INITIALIZED` |

---

<a id="plat_getlastwakeupreason_pos"></a>
### TestCase Name
PLAT_GetLastWakeupReason_pos

### TestCase ID
deepSleepMgr L1-9

### TestCase Objective
Verify that `PLAT_DS_GetLastWakeupReason()` retrieves a valid `DeepSleep_WakeupReason_t` value when called with a valid output pointer after initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the Deep Sleep Management module | Invoke `PLAT_DS_INIT()` | `PLAT_DS_INIT()` must return `DEEPSLEEPMGR_SUCCESS` |
| Get the CPE's last wakeup reason | Invoke `PLAT_DS_GetLastWakeupReason(wakeupReason=<valid DeepSleep_WakeupReason_t*>)` | `PLAT_DS_GetLastWakeupReason()` must return `DEEPSLEEPMGR_SUCCESS`; `wakeupReason` is populated with a valid `DeepSleep_WakeupReason_t` enum value |
| Terminate the Deep Sleep Management module | Invoke `PLAT_DS_TERM()` | `PLAT_DS_TERM()` must return `DEEPSLEEPMGR_SUCCESS` |

---

<a id="plat_getlastwakeupreason_neg"></a>
### TestCase Name
PLAT_GetLastWakeupReason_neg

### TestCase ID
deepSleepMgr L1-10

### TestCase Objective
Verify that `PLAT_DS_GetLastWakeupReason()` returns `DEEPSLEEPMGR_NOT_INITIALIZED` when called without initialization or after termination, and `DEEPSLEEPMGR_INVALID_ARGUMENT` when passed a `NULL` output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get last wakeup reason without prior initialization | Invoke `PLAT_DS_GetLastWakeupReason(wakeupReason=<valid DeepSleep_WakeupReason_t*>)` without prior `PLAT_DS_INIT()` | `PLAT_DS_GetLastWakeupReason()` must return `DEEPSLEEPMGR_NOT_INITIALIZED` |
| Initialize the Deep Sleep Management module | Invoke `PLAT_DS_INIT()` | `PLAT_DS_INIT()` must return `DEEPSLEEPMGR_SUCCESS` |
| Get last wakeup reason with NULL output pointer | Invoke `PLAT_DS_GetLastWakeupReason(wakeupReason=NULL)` | `PLAT_DS_GetLastWakeupReason()` must return `DEEPSLEEPMGR_INVALID_ARGUMENT` |
| Terminate the Deep Sleep Management module | Invoke `PLAT_DS_TERM()` | `PLAT_DS_TERM()` must return `DEEPSLEEPMGR_SUCCESS` |
| Get last wakeup reason after module terminated | Invoke `PLAT_DS_GetLastWakeupReason(wakeupReason=<valid DeepSleep_WakeupReason_t*>)` after `PLAT_DS_TERM()` | `PLAT_DS_GetLastWakeupReason()` must return `DEEPSLEEPMGR_NOT_INITIALIZED` |

---

<a id="plat_getlastwakeupkeycode_pos"></a>
### TestCase Name
PLAT_GetLastWakeupKeyCode_pos

### TestCase ID
deepSleepMgr L1-11

### TestCase Objective
Verify that `PLAT_DS_GetLastWakeupKeyCode()` retrieves a valid `DeepSleepMgr_WakeupKeyCode_Param_t` value when called with a valid output pointer after initialization.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the Deep Sleep Management module | Invoke `PLAT_DS_INIT()` | `PLAT_DS_INIT()` must return `DEEPSLEEPMGR_SUCCESS` |
| Get the CPE's last wakeup key code | Invoke `PLAT_DS_GetLastWakeupKeyCode(wakeupKeyCode=<valid DeepSleepMgr_WakeupKeyCode_Param_t*>)` | `PLAT_DS_GetLastWakeupKeyCode()` must return `DEEPSLEEPMGR_SUCCESS`; `wakeupKeyCode` is populated with the last key code that triggered wakeup |
| Terminate the Deep Sleep Management module | Invoke `PLAT_DS_TERM()` | `PLAT_DS_TERM()` must return `DEEPSLEEPMGR_SUCCESS` |

---

<a id="plat_getlastwakeupkeycode_neg"></a>
### TestCase Name
PLAT_GetLastWakeupKeyCode_neg

### TestCase ID
deepSleepMgr L1-12

### TestCase Objective
Verify that `PLAT_DS_GetLastWakeupKeyCode()` returns `DEEPSLEEPMGR_NOT_INITIALIZED` when called without initialization or after termination, and `DEEPSLEEPMGR_INVALID_ARGUMENT` when passed a `NULL` output pointer.

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Get last wakeup key code without prior initialization | Invoke `PLAT_DS_GetLastWakeupKeyCode(wakeupKeyCode=<valid DeepSleepMgr_WakeupKeyCode_Param_t*>)` without prior `PLAT_DS_INIT()` | `PLAT_DS_GetLastWakeupKeyCode()` must return `DEEPSLEEPMGR_NOT_INITIALIZED` |
| Initialize the Deep Sleep Management module | Invoke `PLAT_DS_INIT()` | `PLAT_DS_INIT()` must return `DEEPSLEEPMGR_SUCCESS` |
| Get last wakeup key code with NULL output pointer | Invoke `PLAT_DS_GetLastWakeupKeyCode(wakeupKeyCode=NULL)` | `PLAT_DS_GetLastWakeupKeyCode()` must return `DEEPSLEEPMGR_INVALID_ARGUMENT` |
| Terminate the Deep Sleep Management module | Invoke `PLAT_DS_TERM()` | `PLAT_DS_TERM()` must return `DEEPSLEEPMGR_SUCCESS` |
| Get last wakeup key code after module terminated | Invoke `PLAT_DS_GetLastWakeupKeyCode(wakeupKeyCode=<valid DeepSleepMgr_WakeupKeyCode_Param_t*>)` after `PLAT_DS_TERM()` | `PLAT_DS_GetLastWakeupKeyCode()` must return `DEEPSLEEPMGR_NOT_INITIALIZED` |

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