# @ohos.bluetooth.baseProfile (Bluetooth baseProfile Module) (System API)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=1275b89181ca8fc1862130ee865235369b412dd3 translatedAt=2026-09-15T02:24:10.720Z pushedAt=2026-09-15T09:03:59.007Z -->

The **baseProfile** module provides common methods for basic Bluetooth [profiles](../../connectivity/bluetooth/terminology.md#profile), including setting and obtaining connection strategies. These methods are inherited by Bluetooth profile modules (such as [A2DP](../../connectivity/bluetooth/terminology.md#a2dp) and [HFP](../../connectivity/bluetooth/terminology.md#hfp)) to help you manage connection strategies for Bluetooth devices.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.bluetooth.baseProfile (Bluetooth baseProfile Module)](js-apis-bluetooth-baseProfile.md).


## Modules to Import

```js
import { baseProfile } from '@kit.ConnectivityKit';
```


## ConnectionStrategy

Enumerates the profile connection strategies.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.Bluetooth.Core

| Name                            | Value     | Description           |
| -------------------------------- | ------ | --------------- |
| CONNECTION_STRATEGY_UNSUPPORTED   | 0 | Default connection strategy to use when the device is not paired.<br>This API is a system API. |
| CONNECTION_STRATEGY_ALLOWED  | 1 |  Connection strategy to use when the device is allowed to accept or initiate pairing.<br>This API is a system API. |
| CONNECTION_STRATEGY_FORBIDDEN  | 2 | Connection strategy to use when the device is not allowed to accept or initiate pairing.<br>This API is a system API.  |



## baseProfile.setConnectionStrategy

setConnectionStrategy(deviceId: string, strategy: ConnectionStrategy, callback: AsyncCallback&lt;void&gt;): void

Sets the profile connection strategy for this device. This API uses an asynchronous callback to return the result. For example, when managing Bluetooth devices, you can call this API to set the connection strategy for a specific device to allow or prevent it from automatically initiating or accepting pairing requests.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name     | Type    | Mandatory  | Description                                 |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes   | Address of the device to pair, for example, XX:XX:XX:XX:XX:XX.|
| strategy | [ConnectionStrategy](#connectionstrategy)   | Yes   |Profile connection strategy to set.|
| callback | AsyncCallback&lt;void&gt;  | Yes   | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.|

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
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
import { a2dp } from '@kit.ConnectivityKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    a2dpSrc.setConnectionStrategy('XX:XX:XX:XX:XX:XX', 0, (err: BusinessError) => {
        console.info('setConnectionStrategy, err: ' + JSON.stringify(err));
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## baseProfile.setConnectionStrategy

setConnectionStrategy(deviceId: string, strategy: ConnectionStrategy): Promise&lt;void&gt;

Sets the profile connection strategy for this device. This API uses a promise to return the result. For example, when managing Bluetooth devices, you can call this API to set the connection strategy for a specific device to allow or prevent it from automatically initiating or accepting pairing requests.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name     | Type    | Mandatory  | Description                                 |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes   | Address of the device to pair, for example, XX:XX:XX:XX:XX:XX.|
| strategy | [ConnectionStrategy](#connectionstrategy)   | Yes   |Profile connection strategy to set.|

**Return value**

| Type                 | Description           |
| ------------------- | ------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

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
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
import { a2dp } from '@kit.ConnectivityKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    a2dpSrc.setConnectionStrategy('XX:XX:XX:XX:XX:XX', 1).then(() => {
        console.info('setConnectionStrategy');
    }, (err: BusinessError) => {
        console.error('setConnectionStrategy errCode: ' + err.code + ', errMessage: ' + err.message);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## baseProfile.getConnectionStrategy

getConnectionStrategy(deviceId: string, callback: AsyncCallback&lt;ConnectionStrategy&gt;): void

Obtains the profile connection strategy. This API uses an asynchronous callback to return the result. For example, in Bluetooth device management, you can call this API to query the connection strategy of the current device to display the strategy status or determine subsequent connection operations.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name     | Type    | Mandatory  | Description                                 |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes   | Address of the device to pair, for example, XX:XX:XX:XX:XX:XX.|
| callback | AsyncCallback&lt;[ConnectionStrategy](#connectionstrategy)&gt; | Yes | Callback used to return the result. If the connection strategy is obtained successfully, **err** is **undefined** and data is the connection strategy obtained. Otherwise, **err** is an error object. |

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
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
import { a2dp } from '@kit.ConnectivityKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    a2dpSrc.getConnectionStrategy('XX:XX:XX:XX:XX:XX', (err: BusinessError, data: baseProfile.ConnectionStrategy) => {
        console.info('getConnectionStrategy, err: ' + JSON.stringify(err) + ', data: ' + JSON.stringify(data));
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## baseProfile.getConnectionStrategy

getConnectionStrategy(deviceId: string): Promise&lt;ConnectionStrategy&gt;

Obtains the profile connection strategy. This API uses a promise to return the result. For example, in Bluetooth device management, you can call this API to query the connection strategy of the current device to display the strategy status or determine subsequent connection operations.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name     | Type    | Mandatory  | Description                                 |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes   | Address of the device to pair, for example, XX:XX:XX:XX:XX:XX.|

**Return value**

| Type                 | Description           |
| ------------------- | ------------- |
|   Promise&lt;[ConnectionStrategy](#connectionstrategy)&gt; | Promise used to return the connection strategy obtained. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID| Error Message|
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.               |
|2900003 | Bluetooth disabled.                 |
|2900004 | Profile not supported.                |
|2900099 | Operation failed.                        |

**Example**

```js
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
import { a2dp } from '@kit.ConnectivityKit';
try {
    let a2dpSrc = a2dp.createA2dpSrcProfile();
    a2dpSrc.getConnectionStrategy('XX:XX:XX:XX:XX:XX').then((data: baseProfile.ConnectionStrategy) => {
        console.info('getConnectionStrategy');
    }, (err: BusinessError) => {
        console.error('getConnectionStrategy errCode: ' + err.code + ', errMessage: ' + err.message);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```