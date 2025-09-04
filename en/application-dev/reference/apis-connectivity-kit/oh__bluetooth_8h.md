# oh_bluetooth.h

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->

## Overview

Defines the API for obtaining the Bluetooth switch state.

**Library**: libbluetooth_ndk.so

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Since**: 13

**Related module**: [Bluetooth](_bluetooth.md)


## Summary


### Types

| Name| Description| 
| -------- | -------- |
| typedef enum [Bluetooth_SwitchState](_bluetooth.md#bluetooth_switchstate) [Bluetooth_SwitchState](_bluetooth.md#bluetooth_switchstate) | Enumerates the Bluetooth switch states.| 
| typedef enum [Bluetooth_ResultCode](_bluetooth.md#bluetooth_resultcode) [Bluetooth_ResultCode](_bluetooth.md#bluetooth_resultcode) | Enumerates the error codes returned by Bluetooth APIs.| 


### Enums

| Name| Description| 
| -------- | -------- |
| [Bluetooth_SwitchState](_bluetooth.md#bluetooth_switchstate) {<br>BLUETOOTH_STATE_OFF = 0,<br>BLUETOOTH_STATE_TURNING_ON = 1,<br>BLUETOOTH_STATE_ON = 2,<br>BLUETOOTH_STATE_TURNING_OFF = 3,<br>BLUETOOTH_STATE_BLE_TURNING_ON = 4,<br>BLUETOOTH_STATE_BLE_ON = 5,<br>BLUETOOTH_STATE_BLE_TURNING_OFF = 6<br>} | Enumerates the Bluetooth switch states.| 
| [Bluetooth_ResultCode](_bluetooth.md#bluetooth_resultcode) {<br>BLUETOOTH_SUCCESS = 0,<br>BLUETOOTH_INVALID_PARAM = 401<br>} | Enumerates the error codes returned by Bluetooth APIs.| 

### Functions

| Name| Description| 
| -------- | -------- |
| [Bluetooth_ResultCode](_bluetooth.md#bluetooth_resultcode) [OH_Bluetooth_GetBluetoothSwitchState](_bluetooth.md#oh_bluetooth_getbluetoothswitchstate) ([Bluetooth_SwitchState](_bluetooth.md#bluetooth_switchstate) \*state) | Obtains the Bluetooth state.| 
