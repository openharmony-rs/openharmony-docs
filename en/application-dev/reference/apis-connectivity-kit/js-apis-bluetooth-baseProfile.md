# @ohos.bluetooth.baseProfile (Bluetooth baseProfile Module)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->

The **baseProfile** module provides APIs for using basic Bluetooth profiles.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.



## Modules to Import

```js
import { baseProfile } from '@kit.ConnectivityKit';
```


## ProfileConnectionState

type ProfileConnectionState = constant.ProfileConnectionState

Defines the profile connection status of the Bluetooth device.

**System capability**: SystemCapability.Communication.Bluetooth.Core

| Type                 | Description                 |
| ------------------- | ------------------- |
| [constant.ProfileConnectionState](js-apis-bluetooth-constant.md#profileconnectionstate) | Profile connection status of the Bluetooth device.|


## StateChangeParam

Represents the profile state change parameters.

**System capability**: SystemCapability.Communication.Bluetooth.Core

| Name    | Type                          | Read-Only| Optional| Description                           |
| -------- | ----------------------------- | ---- | ---- | ------------------------------- |
| deviceId | string                        | No  | No  | Address of the Bluetooth device, for example, XX:XX:XX:XX:XX:XX.  |
| state    | [ProfileConnectionState](js-apis-bluetooth-constant.md#profileconnectionstate)        | No  | No  | Defines the profile connection status of the Bluetooth device.|
| cause<sup>12+</sup>| [DisconnectCause](#disconnectcause12) | No| No| Reason for disconnection.|


## DisconnectCause<sup>12+</sup>

Enumerates the reasons for disconnection.

**System capability**: SystemCapability.Communication.Bluetooth.Core

| Name                | Value | Description    |
| ------------------ | ---- | ------ |
| USER_DISCONNECT            | 0    | The user proactively disconnects the connection.|
| CONNECT_FROM_KEYBOARD      | 1    | The connection should be initiated from a keyboard.|
| CONNECT_FROM_MOUSE         | 2    | The connection should be initiated from a mouse device.|
| CONNECT_FROM_CAR           | 3    | The connection should be initiated from a head unit side.|
| TOO_MANY_CONNECTED_DEVICES | 4    | The number of connections exceeds the limit.|
| CONNECT_FAIL_INTERNAL      | 5    | Internal error.|


## BaseProfile.getConnectedDevices

getConnectedDevices(): Array&lt;string&gt;

Obtains the connected devices.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Return value**

| Type                 | Description                 |
| ------------------- | ------------------- |
| Array&lt;string&gt; | Addresses of the connected devices. For security purposes, the device addresses obtained are random MAC addresses.<br> The random MAC address remains unchanged after a device is paired successfully.<br> The random address changes if the paired device is unpaired and scanned again or the Bluetooth service is turned off.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID| Error Message|
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900004 | Profile not supported.                |
|2900099 | Operation failed.                        |

**Example**

```js
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
import { a2dp } from '@kit.ConnectivityKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    let retArray = a2dpSrc.getConnectedDevices();
} catch (err) {
    console.error("errCode:" + (err as BusinessError).code + ",errMessage:" + (err as BusinessError).message);
}
```


## BaseProfile.getConnectionState

getConnectionState(deviceId: string): ProfileConnectionState

Obtains the profile connection state of a device.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name   | Type    | Mandatory  | Description     |
| ------ | ------ | ---- | ------- |
| deviceId | string | Yes   | Address of the remote device, for example, XX:XX:XX:XX:XX:XX.|

**Return value**

| Type                                             | Description                   |
| ------------------------------------------------- | ----------------------- |
| [ProfileConnectionState](js-apis-bluetooth-constant.md#profileconnectionstate) | Profile connection state obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID| Error Message|
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900004 | Profile not supported.                |
|2900099 | Operation failed.                        |

**Example**

```js
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
import { a2dp } from '@kit.ConnectivityKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    let ret = a2dpSrc.getConnectionState('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## BaseProfile.on('connectionStateChange')

on(type: 'connectionStateChange', callback: Callback&lt;StateChangeParam&gt;): void

Subscribes to profile connection state changes. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name     | Type                                      | Mandatory  | Description                                      |
| -------- | ---------------------------------------- | ---- | ---------------------------------------- |
| type     | string                                   | Yes   | Event type. The value **connectionStateChange** indicates a connection state change event.<br>This event is triggered when the connection state changes.|
| callback | Callback&lt;[StateChangeParam](#statechangeparam)&gt; | Yes   | Callback used to return the Bluetooth profile connection state.                       |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |

**Example**

```js
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
import { a2dp } from '@kit.ConnectivityKit';
function onReceiveEvent(data: baseProfile.StateChangeParam) {
    console.info('a2dp state = '+ JSON.stringify(data));
}
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    a2dpSrc.on('connectionStateChange', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## BaseProfile.off('connectionStateChange')

off(type: 'connectionStateChange', callback?: Callback&lt;[StateChangeParam](#statechangeparam)&gt;): void

Unsubscribes from profile connection state changes.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name     | Type                                      | Mandatory  | Description                                      |
| -------- | ---------------------------------------- | ---- | ---------------------------------------- |
| type     | string                                   | Yes   | Event type. The value **connectionStateChange** indicates a connection state change event.|
| callback | Callback&lt;[StateChangeParam](#statechangeparam)&gt; | No   | Callback to unregister.<br>If this parameter is specified, it must be the same as the callback in [BaseProfile.on('connectionStateChange')](#baseprofileonconnectionstatechange). If this parameter is not specified, all callbacks corresponding to the event type are unregistered.                              |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |

**Example**

```js
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
import { a2dp } from '@kit.ConnectivityKit';
function onReceiveEvent(data: baseProfile.StateChangeParam) {
    console.info('a2dp state = '+ JSON.stringify(data));
}
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    a2dpSrc.on('connectionStateChange', onReceiveEvent);
    a2dpSrc.off('connectionStateChange', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
