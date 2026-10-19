# @ohos.bluetooth.map (Bluetooth MAP Module) (System API)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=1275b89181ca8fc1862130ee865235369b412dd3 translatedAt=2026-09-15T02:47:25.706Z pushedAt=2026-09-16T07:46:03.721Z -->

The **map** module provides the capability of accessing Bluetooth messages (such as SMS and email) on remote devices based on [Message Access Profile (MAP)](../../connectivity/bluetooth/terminology.md#map), and supports functions such as disconnecting the MAP service and setting and obtaining permissions to access messages. This module is applicable to scenarios where message data needs to be exchanged with a remote device via Bluetooth.

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.bluetooth.map (Bluetooth MAP Module)](js-apis-bluetooth-map.md).


## Modules to Import

```js
import { map } from '@kit.ConnectivityKit';
```


### disconnect

disconnect(deviceId: string): void

Disconnects the MAP service for a device. This method is applicable to scenarios such as switchover, connection recovery, and termination of Bluetooth message synchronization initiated by the user.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name   | Type    | Mandatory  | Description     |
| ------ | ------ | ---- | ------- |
| deviceId | string | Yes   | Address of the remote device, for example, XX:XX:XX:XX:XX:XX.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID| Error Message|
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900004 | Profile not supported.                |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let mapMseProfile = map.createMapMseProfile();
    mapMseProfile.disconnect('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### setMessageAccessAuthorization

setMessageAccessAuthorization(deviceId: string, authorization: AccessAuthorization): Promise&lt;void&gt;

Sets the message access authorization for a device. This API uses a promise to return the result. This API is applicable to scenarios where permissions to access messages are granted or revoked before Bluetooth message synchronization, for example, when the user manages permissions to read Bluetooth messages on vehicle-mounted devices or wearables.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name     | Type    | Mandatory  | Description                                 |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes   | Address of the remote device, for example, XX:XX:XX:XX:XX:XX.|
| authorization | [AccessAuthorization](js-apis-bluetooth-constant-sys.md#accessauthorization11) | Yes | Authorization status of message access permissions, for example, **ACCESS_ALLOWED** or **ACCESS_DENIED**. For details about the enumerated values and their meanings, see [AccessAuthorization](js-apis-bluetooth-constant-sys.md#accessauthorization11). |

**Return value**

| Type                                             | Description               |
| ------------------------------------------------- | ------------------- |
| Promise&lt;void&gt; | Promise used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID| Error Message|
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900004 | Profile not supported.                |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let mapMseProfile = map.createMapMseProfile();
    mapMseProfile.setMessageAccessAuthorization('XX:XX:XX:XX:XX:XX', 0).then(() => {
        console.info('setMessageAccessAuthorization');
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### getMessageAccessAuthorization

getMessageAccessAuthorization(deviceId: string): Promise&lt;AccessAuthorization&gt;

Obtains the message access authorization of a device. This API uses a promise to return the result. This API can be used to check whether the device has been granted permissions to read messages before Bluetooth message synchronization.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name     | Type    | Mandatory  | Description                                 |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes   | Address of the remote device, for example, XX:XX:XX:XX:XX:XX.|

**Return value**

| Type                                             | Description               |
| ------------------------------------------------- | ------------------- |
| Promise&lt;[AccessAuthorization](js-apis-bluetooth-constant-sys.md#accessauthorization11)&gt; | Promise used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID| Error Message|
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900004 | Profile not supported.                |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let mapMseProfile = map.createMapMseProfile();
    mapMseProfile.getMessageAccessAuthorization('XX:XX:XX:XX:XX:XX').then((authorization) => {
        console.info('authorization ' + authorization);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```