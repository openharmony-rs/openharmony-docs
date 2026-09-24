# oh_bluetooth.h

## Overview

Define interfaces for querying bluetooth switch status.

**Library**: libbluetooth_ndk.so

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Since**: 13

**Related module**: [Bluetooth](capi-bluetooth.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [Bluetooth_SwitchState](#bluetooth_switchstate) | Bluetooth_SwitchState | Enumeration state of bluetooth switch. |
| [Bluetooth_ResultCode](#bluetooth_resultcode) | Bluetooth_ResultCode | Enumeration the bluetooth result codes. |

### Function

| Name | Description |
| -- | -- |
| [Bluetooth_ResultCode OH_Bluetooth_GetBluetoothSwitchState(Bluetooth_SwitchState *state)](#oh_bluetooth_getbluetoothswitchstate) | Get the bluetooth switch state. |

## Enum type description

### Bluetooth_SwitchState

```c
enum Bluetooth_SwitchState
```

**Description**

Enumeration state of bluetooth switch.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Since**: 13

| Enum item | Description |
| -- | -- |
| BLUETOOTH_STATE_OFF = 0 | Indicates the local bluetooth is off. |
| BLUETOOTH_STATE_TURNING_ON = 1 | Indicates the local bluetooth is turning on. |
| BLUETOOTH_STATE_ON = 2 | Indicates the local bluetooth is on, and ready for use. |
| BLUETOOTH_STATE_TURNING_OFF = 3 | Indicates the local bluetooth is turning off. |
| BLUETOOTH_STATE_BLE_TURNING_ON = 4 | Indicates the local bluetooth is turning LE mode on. |
| BLUETOOTH_STATE_BLE_ON = 5 | Indicates the local bluetooth is in LE only mode. |
| BLUETOOTH_STATE_BLE_TURNING_OFF = 6 | Indicates the local bluetooth is turning off LE only mode. |

### Bluetooth_ResultCode

```c
enum Bluetooth_ResultCode
```

**Description**

Enumeration the bluetooth result codes.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Since**: 13

| Enum item | Description |
| -- | -- |
| BLUETOOTH_SUCCESS = 0 | The operation is successful. |
| BLUETOOTH_INVALID_PARAM = 401 | Parameter error. Possible reasons: 1. The input parameter is a null pointer; 2. Parameter values exceed the defined range. |


## Function description

### OH_Bluetooth_GetBluetoothSwitchState()

```c
Bluetooth_ResultCode OH_Bluetooth_GetBluetoothSwitchState(Bluetooth_SwitchState *state)
```

**Description**

Get the bluetooth switch state.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| [Bluetooth_SwitchState](capi-oh-bluetooth-h.md#bluetooth_switchstate) *state | - It is a pointer used to receive bluetooth switch status values. The caller needs to pass in a non empty boolean pointer, otherwise an error will be returned. For a detailed definition, please refer to [Bluetooth_SwitchState](capi-oh-bluetooth-h.md#bluetooth_switchstate). |

**Returns**:

| Type | Description |
| -- | -- |
| [Bluetooth_ResultCode](capi-oh-bluetooth-h.md#bluetooth_resultcode) | Bluetooth functions result code.      For a detailed definition, please refer to [Bluetooth_ResultCode](capi-oh-bluetooth-h.md#bluetooth_resultcode).      [BLUETOOTH_SUCCESS](capi-oh-bluetooth-h.md#bluetooth_resultcode) Successfully obtained the bluetooth switch status.      [BLUETOOTH_INVALID_PARAM](capi-oh-bluetooth-h.md#bluetooth_resultcode) The input parameter enabled is a null pointer. |


