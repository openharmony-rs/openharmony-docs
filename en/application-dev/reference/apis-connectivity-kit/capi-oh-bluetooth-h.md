# oh_bluetooth.h

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=1ea8aa0626dcbea629ef512eb27ca07c34ff3ad2 translatedAt=2026-10-09T12:34:21.385Z pushedAt=2026-10-10T06:56:38.680Z -->

## Overview

Provides APIs for obtaining the Bluetooth switch state. You can obtain the Bluetooth switch state, including enabled, disabling, enabling, and BLE only. This is applicable to scenarios where the current Bluetooth switch state needs to be detected for service processing.

**File to include**: <ConnectivityKit/bluetooth/oh_bluetooth.h>

**Library**: libbluetooth_ndk.so

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Since**: 13

**Related module**: [Bluetooth](capi-bluetooth.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [Bluetooth_SwitchState](#bluetooth_switchstate) | Bluetooth_SwitchState | Enumerates the Bluetooth switch states.|
| [Bluetooth_ResultCode](#bluetooth_resultcode) | Bluetooth_ResultCode | Defines the Bluetooth return value.|

### Functions

| Name| Description|
| -- | -- |
| [Bluetooth_ResultCode OH_Bluetooth_GetBluetoothSwitchState(Bluetooth_SwitchState *state)](#oh_bluetooth_getbluetoothswitchstate) | Obtains the Bluetooth state.|

## Enum Description

### Bluetooth_SwitchState

```c
enum Bluetooth_SwitchState
```

**Description**

Enumerates the Bluetooth switch states.

**Since**: 13

| Enum Item| Description|
| -- | -- |
| BLUETOOTH_STATE_OFF = 0 | Bluetooth is turned off.|
| BLUETOOTH_STATE_TURNING_ON = 1 | Bluetooth is being turned on.|
| BLUETOOTH_STATE_ON = 2 | Bluetooth is turned on and ready for use.|
| BLUETOOTH_STATE_TURNING_OFF = 3 | Bluetooth is being turned off.|
| BLUETOOTH_STATE_BLE_TURNING_ON = 4 | The BLE only mode is being turned on.|
| BLUETOOTH_STATE_BLE_ON = 5 | The BLE only mode is turned on.|
| BLUETOOTH_STATE_BLE_TURNING_OFF = 6 | The BLE only mode is being turned off.|

### Bluetooth_ResultCode

```c
enum Bluetooth_ResultCode
```

**Description**

Defines the Bluetooth return value.

**Since**: 13

| Enum Item| Description|
| -- | -- |
| BLUETOOTH_SUCCESS = 0 | Operation success.|
| BLUETOOTH_INVALID_PARAM = 401 | Invalid parameter. Possible causes: 1. The input parameter is a null pointer. 2. The parameter value exceeds the value range.|


## Function Description

### OH_Bluetooth_GetBluetoothSwitchState()

```c
Bluetooth_ResultCode OH_Bluetooth_GetBluetoothSwitchState(Bluetooth_SwitchState *state)
```

**Description**

Obtains the Bluetooth state.

**Since**: 13


**Parameters**

| Name| Description|
| -- | -- |
| [Bluetooth_SwitchState](#bluetooth_switchstate) *state | Pointer to the Bluetooth state obtained. A null pointer is prohibited. If a null pointer is passed in, an error is returned. For details, see [Bluetooth_SwitchState](#bluetooth_switchstate). |

**Returns**

| Type| Description|
| -- | -- |
| [Bluetooth_ResultCode](#bluetooth_resultcode) | Bluetooth switch state enumerated by [Bluetooth_ResultCode](capi-oh-bluetooth-h.md#bluetooth_resultcode).<br>     For details, see [Bluetooth_ResultCode](#bluetooth_resultcode).<br>     [BLUETOOTH_SUCCESS](#bluetooth_resultcode) indicates that the operation is successful.<br>     [BLUETOOTH_INVALID_PARAM](#bluetooth_resultcode) indicates that the input parameter is a null pointer. |


