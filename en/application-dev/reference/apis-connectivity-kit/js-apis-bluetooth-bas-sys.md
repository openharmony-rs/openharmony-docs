# @ohos.bluetooth.bas (Bluetooth BAS Module) (System API)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=2ad35b82ef90103e0aea46340195e6b86af251c2 translatedAt=2026-08-25T10:02:28.079Z pushedAt=2026-08-25T12:10:16.772Z -->

The BAS module provides APIs for battery services, including reading the battery level and listening for changes in the battery level of a peer device.

**Since**: 26.0.0

## Modules to Import

```js
import { bas } from '@kit.ConnectivityKit';
```

## bas.isBasSupported

isBasSupported(): boolean

Checks whether the local device can obtain the battery level of a peer device.

**Since**: 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type    | Description                                                        |
| ------- | ------------------------------------------------------------------ |
| boolean | The value **true** indicates that the local device supports obtaining the battery level of a peer device. The value **false** indicates otherwise. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Information |
| -------- | ---------------------------- |
|202 | Non-system applications are not allowed to use system APIs.                 |
|2900099 | Operation failed.                        |

**Example**

```js
try {
    let isSupported: boolean = bas.isBasSupported();
    console.info('isBasSupported: ' + isSupported);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## bas.getRemoteDeviceBatteryInfo

getRemoteDeviceBatteryInfo(deviceId: BluetoothAddress): Promise&lt;BatteryInfo&gt;

Queries the battery level of a peer device.

- Before using this API, you are advised to use [isBasSupported](#basisbassupported) to check whether the local device supports obtaining the battery level of a peer device.

- Only BLE peripheral devices that support the battery service (with UUID of **0000180F-0000-1000-8000-00805F9B34FB**) defined by the Bluetooth protocol can obtain the battery level.

- You can obtain the battery level of the peer Bluetooth device from the callback of [onBatteryChange](#basonbatterychange).

- This API can be used to obtain the battery level of the peer Bluetooth device based on the actual and random MAC addresses of the peer device.

**Since**: 26.0.0

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------------- | --------------------------------------- | ---- | ------------------- |
| deviceId | [BluetoothAddress](js-apis-bluetooth-common.md#bluetoothaddress) | Yes | Address of the peer device.<br>- **address**, **addressType**, and **rawAddressType** in **BluetoothAddress** are mandatory. |

**Return value**

| Type | Description |
| ---------------------------------------- | -------------------------- |
| Promise&lt;[BatteryInfo](#batteryinfo)&gt; | Promise used to return the battery level of the peer device. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Information |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.             |
|2900003 | Bluetooth disabled.                |
|2900004 | Remote device profile not supported.                |
|2900099 | Operation failed. Possible causes: 1. Unregistered bas observer. 2. Bas observers exceeds the limit. 3. Bas request busy.                 |
|2901003 | Connection not established.                |

**Example**

```js
import { common } from '@kit.ConnectivityKit';

let deviceId: common.BluetoothAddress = {
    address:"11:22:33:44:55:66",
    addressType:common.BluetoothAddressType.REAL,
    rawAddressType:common.BluetoothRawAddressType.PUBLIC
}
try {
    bas.getRemoteDeviceBatteryInfo(deviceId).then((batteryInfo: bas.BatteryInfo) => {
        console.info('getRemoteDeviceBatteryInfo, batteryInfo: [address: ' + batteryInfo.deviceId.address +
            ', batteryLevel: ' + batteryInfo.batteryLevel + ']');
    });
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## bas.onBatteryChange

onBatteryChange(callback: Callback&lt;BatteryInfo&gt;): void

Subscribes to battery level change events of a peer device.

- Only BLE peripheral devices that support the battery service (with UUID of **0000180F-0000-1000-8000-00805F9B34FB**) defined by the Bluetooth protocol can report the battery level. This API cannot be used together with [connection.on('batteryChange')](js-apis-bluetooth-connection.md#connectiononbatterychange12).

- When this API is called, the latest valid battery level of the device connected to the battery service is reported immediately. Subsequently, the battery level is reported only when it changes on the peer device.

**Since**: 26.0.0

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name            | Type                                      | Mandatory   | Description                  |
| -------------- | --------------------------------------- | ---- | ------------------- |
| callback | Callback&lt;[BatteryInfo](#batteryinfo)&gt; | Yes    | Callback used to return the battery level. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Information |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs.                 |
|801 | Capability not supported.          |
|2900099 | Operation failed.                        |

**Example**

```js
let onReceiveEvent: (data: bas.BatteryInfo) => void = (data: bas.BatteryInfo) => {
    console.info(`address: ${data.deviceId.address}, batteryLevel: ${data.batteryLevel}`);
}
try {
    bas.onBatteryChange(onReceiveEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## bas.offBatteryChange

offBatteryChange(callback?: Callback&lt;BatteryInfo&gt;): void

Unsubscribes from battery level change events of a peer device.

This API cannot be used together with [connection.off('batteryChange')](js-apis-bluetooth-connection.md#connectionoffbatterychange12).

**Since**: 26.0.0

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------------- | --------------------------------------- | ---- | ------------------- |
| callback | Callback&lt;[BatteryInfo](#batteryinfo)&gt; | No | Callback used to return the result.<br>If this parameter is specified, it must be the same as the callback in [bas.onBatteryChange](#basonbatterychange). If this parameter is not specified, all callbacks for battery level changes are unregistered. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Information |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs.                 |
|801 | Capability not supported.          |
|2900099 | Operation failed.                        |

**Example**

```js
let onReceiveEvent: (data: bas.BatteryInfo) => void = (data: bas.BatteryInfo) => {
    console.info(`address: ${data.deviceId.address}, batteryLevel: ${data.batteryLevel}`);
}
try {
    bas.onBatteryChange(onReceiveEvent);
    bas.offBatteryChange(onReceiveEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## BatteryInfo

Describes the battery information of a device.

**Since**: 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction**: This API can be used only in the stage model.

| Name       | Type   | Read-Only   | Optional   | Description          |
| -------- | ------ | ---- | ---- | ----------- |
| deviceId | [BluetoothAddress](js-apis-bluetooth-common.md#bluetoothaddress) | No    | No    | Address of the peer device. |
| batteryLevel | number | No    | No    | Battery level. The value range is [–1, 100], in percentage. The value **–1** indicates that there is no battery level information. |