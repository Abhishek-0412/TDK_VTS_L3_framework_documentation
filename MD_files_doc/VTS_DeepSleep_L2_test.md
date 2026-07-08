## TestScript Name
VTS_DeepSleep_L2_test

## TestScript ID
VTS_Test_16

## Table of Contents

1. [Objective](#objective)
2. [Pre-conditions](#pre-conditions)
3. [Test Cases](#test-cases)
   - [SetDsAndVerifyWakeup1sec](#setdsandverifywakeup1sec)
   - [SetDsAndVerifyWakeup10sec](#setdsandverifywakeup10sec)
4. [Post-conditions](#post-conditions)
5. [Test Attributes](#test-attributes)

---

## Objective

This script executes VTS L2 (Level 2) test cases for the **Deep Sleep Manager HAL** module (`deepSleepMgr`). L2 tests validate end-to-end workflows that exercise sequences of HAL APIs to verify combined functional behaviour. Each test puts the device into actual deep sleep for a specified timeout and verifies the wakeup reason upon return. No external stimulus is required beyond the HAL implementation and the platform profile configuration. The binary used is `hal_test_iarmmgrs-deepsleep-hal`, invoked with the profile `deepsleepmanagerExtendedEnumsNotSupported.yaml`.

---

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

---

## Test Cases

<a id="setdsandverifywakeup1sec"></a>
### TestCase Name
SetDsAndVerifyWakeup1sec

### TestCase ID
deepSleepMgr L2-1

### TestCase Objective
Validate the end-to-end deep sleep workflow by setting a 1-second deep sleep timeout and verifying that the wakeup reason is `DEEPSLEEP_WAKEUPREASON_TIMER` upon return.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI (REFPLTV-2526).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the Deep Sleep Management module | Invoke `PLAT_DS_INIT()` | `PLAT_DS_INIT()` must return `DEEPSLEEPMGR_SUCCESS` |
| Set CPE power state to Deep Sleep | Invoke `PLAT_DS_SetDeepSleep(1, false, 0)` | Device enters deep sleep; `PLAT_DS_SetDeepSleep()` returns after wakeup with `DEEPSLEEPMGR_SUCCESS` |
| Configure platform status after deep sleep wake-up | Invoke `PLAT_DS_DeepSleepWakeup()` | `PLAT_DS_DeepSleepWakeup()` must return `DEEPSLEEPMGR_SUCCESS` |
| Get the CPE's last wakeup reason | Invoke `PLAT_DS_GetLastWakeupReason(&wakeupReason)` | `PLAT_DS_GetLastWakeupReason()` must return `DEEPSLEEPMGR_SUCCESS` and `wakeupReason` must equal `DEEPSLEEP_WAKEUPREASON_TIMER` |
| Terminate the CPE Deep Sleep Management module | Invoke `PLAT_DS_TERM()` | `PLAT_DS_TERM()` must return `DEEPSLEEPMGR_SUCCESS` |

---

<a id="setdsandverifywakeup10sec"></a>
### TestCase Name
SetDsAndVerifyWakeup10sec

### TestCase ID
deepSleepMgr L2-2

### TestCase Objective
Validate the end-to-end deep sleep workflow by setting a 10-second deep sleep timeout and verifying that the wakeup reason is `DEEPSLEEP_WAKEUPREASON_TIMER` upon return.

> **Note — Platform Skip:** This test case is **skipped on RPI-Client** — Not applicable for RPI (REFPLTV-2526).

### Test Steps

| Step Name | Description | Expected Result |
| --- | --- | --- |
| Initialize the Deep Sleep Management module | Invoke `PLAT_DS_INIT()` | `PLAT_DS_INIT()` must return `DEEPSLEEPMGR_SUCCESS` |
| Set CPE power state to Deep Sleep | Invoke `PLAT_DS_SetDeepSleep(10, false, 0)` | Device enters deep sleep; `PLAT_DS_SetDeepSleep()` returns after wakeup with `DEEPSLEEPMGR_SUCCESS` |
| Configure platform status after deep sleep wake-up | Invoke `PLAT_DS_DeepSleepWakeup()` | `PLAT_DS_DeepSleepWakeup()` must return `DEEPSLEEPMGR_SUCCESS` |
| Get the CPE's last wakeup reason | Invoke `PLAT_DS_GetLastWakeupReason(&wakeupReason)` | `PLAT_DS_GetLastWakeupReason()` must return `DEEPSLEEPMGR_SUCCESS` and `wakeupReason` must equal `DEEPSLEEP_WAKEUPREASON_TIMER` |
| Terminate the CPE Deep Sleep Management module | Invoke `PLAT_DS_TERM()` | `PLAT_DS_TERM()` must return `DEEPSLEEPMGR_SUCCESS` |

---

## Post-conditions

1. The `hal_test_iarmmgrs-deepsleep-hal` binary exits cleanly after completing all test cases in the `L2 deepSleepMgr` suite.
2. The Deep Sleep Manager HAL module is terminated via `PLAT_DS_TERM()` at the end of each test case, restoring the module to its uninitialized default state.

---

## Test Attributes

| Attribute | Value |
| --- | --- |
| Supported Models | Video_Accelerator, RPI-Client |
| Estimated Duration | 8 minutes |
| Priority | High |
| TDK Release Version | M134 |
