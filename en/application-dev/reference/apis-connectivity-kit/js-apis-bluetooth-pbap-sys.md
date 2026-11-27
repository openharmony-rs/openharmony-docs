# @ohos.bluetooth.pbap (Bluetooth PBAP Module) (System API)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=0c35e2da2a6ef71cfecc03dfb2bbc3c0f3345833 translatedAt=2026-11-18T04:07:55.900Z pushedAt=2026-11-20T09:24:44.326Z nl=1 -->

The **pbap** module provides APIs for accessing the phone book of a device using the Bluetooth Phone Book Access Profile (PBAP).

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.bluetooth.pbap (Bluetooth PBAP Module)](js-apis-bluetooth-pbap.md).


## Modules to Import

```js
import { pbap } from '@kit.ConnectivityKit';
```

## PbapServerProfile

Provides APIs for accessing the phone book of a device. Before using any API of **PbapServerProfile**, you need to create an instance of this class by using **createPbapServerProfile()**.

### disconnect

disconnect(deviceId: string): void

Disconnects the PBAP service for a device.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name    | Type    | Mandatory  | Description     |
| ------ | ------ | ---- | ------- |
| deviceId | string | Yes   | Address of the remote device, for example, XX:XX:XX:XX:XX:XX. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
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
    let pbapServerProfile = pbap.createPbapServerProfile();
    pbapServerProfile.disconnect('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### setShareType

setShareType(deviceId: string, type: ShareType, callback: AsyncCallback&lt;void&gt;): void

Sets the share type of the phone book information for a device. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name     | Type    | Mandatory  | Description                                 |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes   | Address of the remote device, for example, XX:XX:XX:XX:XX:XX. |
| type | [ShareType](#sharetype) | Yes   | Share type to set. |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result.<br> If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
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
    let pbapServerProfile = pbap.createPbapServerProfile();
    pbapServerProfile.setShareType('XX:XX:XX:XX:XX:XX', 0, (err: BusinessError) => {
       console.info('setShareType'); 
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### setShareType

setShareType(deviceId: string, type: ShareType): Promise&lt;void&gt;

Sets the share type of the phone book information for a device. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name     | Type    | Mandatory  | Description                                 |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes   | Address of the remote device, for example, XX:XX:XX:XX:XX:XX. |
| type | [ShareType](#sharetype) | Yes   | Share type to set. |

**Return value**

| Type                                             | Description               |
| ------------------------------------------------- | ------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
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
    let pbapServerProfile = pbap.createPbapServerProfile();
    pbapServerProfile.setShareType('XX:XX:XX:XX:XX:XX', 0).then(() => {
        console.info('setShareType');
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### getShareType

getShareType(deviceId: string, callback: AsyncCallback&lt;ShareType&gt;): void

Obtains the phone book share type of a device. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name     | Type    | Mandatory  | Description                                 |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes   | Address of the remote device, for example, XX:XX:XX:XX:XX:XX. |
| callback | AsyncCallback&lt;[ShareType](#sharetype)&gt; | Yes   | Callback used to return the result.<br> If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
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
    let pbapServerProfile = pbap.createPbapServerProfile();
    pbapServerProfile.getShareType('XX:XX:XX:XX:XX:XX', (err, type) => {
        console.info('getShareType ' + type);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### getShareType

getShareType(deviceId: string): Promise&lt;ShareType&gt;

Obtains the phone book share type of a device. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name     | Type    | Mandatory  | Description                                 |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes   | Address of the remote device, for example, XX:XX:XX:XX:XX:XX. |

**Return value**

| Type                                             | Description               |
| ------------------------------------------------- | ------------------- |
| Promise&lt;[ShareType](#sharetype)&gt; | Promise used to return the share type of phone book information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
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
    let pbapServerProfile = pbap.createPbapServerProfile();
    pbapServerProfile.getShareType('XX:XX:XX:XX:XX:XX').then((type) => {
        console.info('getShareType ' + type);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### setPhoneBookAccessAuthorization

setPhoneBookAccessAuthorization(deviceId: string, authorization: AccessAuthorization, callback: AsyncCallback&lt;void&gt;): void

Sets the phone book access authorization for a device. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name     | Type    | Mandatory  | Description                                 |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes   | Address of the remote device, for example, XX:XX:XX:XX:XX:XX. |
| authorization | [AccessAuthorization](js-apis-bluetooth-constant-sys.md#accessauthorization11) | Yes   | Phone book access authorization to set. |
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result.<br> If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
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
    let pbapServerProfile = pbap.createPbapServerProfile();
    pbapServerProfile.setPhoneBookAccessAuthorization('XX:XX:XX:XX:XX:XX', 0, (err: BusinessError) => {
       console.info('setPhoneBookAccessAuthorization'); 
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### setPhoneBookAccessAuthorization

setPhoneBookAccessAuthorization(deviceId: string, authorization: AccessAuthorization): Promise&lt;void&gt;

Sets the phone book access authorization for a device. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name     | Type    | Mandatory  | Description                                 |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes   | Address of the remote device, for example, XX:XX:XX:XX:XX:XX. |
| authorization | [AccessAuthorization](js-apis-bluetooth-constant-sys.md#accessauthorization11) | Yes   | Phone book access authorization to set. |

**Return value**

| Type                                             | Description               |
| ------------------------------------------------- | ------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
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
    let pbapServerProfile = pbap.createPbapServerProfile();
    pbapServerProfile.setPhoneBookAccessAuthorization('XX:XX:XX:XX:XX:XX', 0).then(() => {
        console.info('setPhoneBookAccessAuthorization');
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### getPhoneBookAccessAuthorization

getPhoneBookAccessAuthorization(deviceId: string, callback: AsyncCallback&lt;AccessAuthorization&gt;): void

Obtains the phone book access authorization of a device. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name     | Type    | Mandatory  | Description                                 |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes   | Address of the remote device, for example, XX:XX:XX:XX:XX:XX. |
| callback | AsyncCallback&lt;[AccessAuthorization](js-apis-bluetooth-constant-sys.md#accessauthorization11)&gt; | Yes   | Callback used to return the result.<br> If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
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
    let pbapServerProfile = pbap.createPbapServerProfile();
    pbapServerProfile.getPhoneBookAccessAuthorization('XX:XX:XX:XX:XX:XX', (err, authorization) => {
        console.info('authorization ' + authorization);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

### getPhoneBookAccessAuthorization

getPhoneBookAccessAuthorization(deviceId: string): Promise&lt;AccessAuthorization&gt;

Obtains the phone book access authorization of a device. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name     | Type    | Mandatory  | Description                                 |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes   | Address of the remote device, for example, XX:XX:XX:XX:XX:XX. |

**Return value**

| Type                                             | Description               |
| ------------------------------------------------- | ------------------- |
| Promise&lt;[AccessAuthorization](js-apis-bluetooth-constant-sys.md#accessauthorization11)&gt; | Promise used to return the access permission of phone book information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
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
    let pbapServerProfile = pbap.createPbapServerProfile();
    pbapServerProfile.getPhoneBookAccessAuthorization('XX:XX:XX:XX:XX:XX').then((authorization) => {
        console.info('authorization ' + authorization);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## ShareType

Enumerates the phone book share types.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.Bluetooth.Core

| Name                 | Value  | Description     |
| ------------------ | ---- | ------ |
| SHARE_NAME_AND_PHONE_NUMBER | 0    | Share the name and number.<br>This is a system API. |
| SHARE_ALL | 1    | Share all information.<br>This is a system API.  |
| SHARE_NOTHING  | 2    | Share nothing.<br>This is a system API.   |


## PbapClientProfile

Manages the PBAP client profile.

**Since:** 26.0.1

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction**: This API can be used only in the stage model.


### connect

connect(deviceId: string): void

Connects the PBAP client to the remote device.

**Since:** 26.0.1

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name    | Type    | Mandatory  | Description     |
| ------ | ------ | ---- | ------- |
| deviceId | string | Yes   | Address of the remote device, for example, XX:XX:XX:XX:XX:XX. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API. |
|202 | Permission verification failed. A non-system application calls a system API. |
|801 | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
|2900003 | Bluetooth disabled. |
|2900004 | Profile not supported. |
|2900099 | Internal system error. For example, IPC error. Detailed error messages can be used to assist in locating the problem. |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let pbapClientProfile = pbap.createPbapClientProfile();
    pbapClientProfile.connect('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### disconnect

disconnect(deviceId: string): void

Disconnects the PBAP client from the remote device.

**Since:** 26.0.1

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name    | Type    | Mandatory  | Description     |
| ------ | ------ | ---- | ------- |
| deviceId | string | Yes   | Address of the remote device, for example, XX:XX:XX:XX:XX:XX. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API. |
|202 | Permission verification failed. A non-system application calls a system API. |
|801 | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
|2900003 | Bluetooth disabled. |
|2900004 | Profile not supported. |
|2900099 | Internal system error. For example, IPC error. Detailed error messages can be used to assist in locating the problem. |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let pbapClientProfile = pbap.createPbapClientProfile();
    pbapClientProfile.disconnect('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### getSyncState

getSyncState(deviceId: string): SyncStateType

Obtains the PBAP phone book synchronization status, and only reports the synchronization substatus.

**Since:** 26.0.1

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name    | Type    | Mandatory  | Description     |
| ------ | ------ | ---- | ------- |
| deviceId | string | Yes   | Address of the remote device, for example, XX:XX:XX:XX:XX:XX. |

**Return value**

| Type                           | Description        |
| ----------------------------- | ---------- |
| [SyncStateType](#syncstatetype) | Returns the phone book synchronization status. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API. |
|202 | Permission verification failed. A non-system application calls a system API. |
|801 | Capability not supported. |
|2900003 | Bluetooth disabled. |
|2900004 | Profile not supported. |
|2900099 | Internal system error. For example, IPC error. Detailed error messages can be used to assist in locating the problem. |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let pbapClientProfile = pbap.createPbapClientProfile();
    let state = pbapClientProfile.getSyncState('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### onSyncStateChange

onSyncStateChange(callback: Callback&lt;SyncStateChangeParam&gt;): void

Subscribes to the phone book synchronization status change event. Only the synchronization substatus is reported.

**Since:** 26.0.1

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name    | Type    | Mandatory  | Description     |
| ------ | ------ | ---- | ------- |
| callback | Callback&lt;[SyncStateChangeParam](#syncstatechangeparam)&gt; | Yes   | Callback function, returns the phone book synchronization status change information. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API. |
|202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let pbapClientProfile = pbap.createPbapClientProfile();
    pbapClientProfile.onSyncStateChange((data: pbap.SyncStateChangeParam) => {
        console.info('deviceId: ' + data.deviceId + ', state: ' + data.state);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### offSyncStateChange

offSyncStateChange(callback?: Callback&lt;SyncStateChangeParam&gt;): void

Unsubscribes from the phone book synchronization status change event.

**Since:** 26.0.1

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name    | Type    | Mandatory  | Description     |
| ------ | ------ | ---- | ------- |
| callback | Callback&lt;[SyncStateChangeParam](#syncstatechangeparam)&gt; | No   | Specifies the callback function notification to unsubscribe from.<br>If a parameter is passed, it must be the same as the callback function in [onSyncStateChange](#onsyncstatechange); if no parameter is passed, all callback function notifications of this event are unsubscribed from. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission verification failed. The application does not have the permission required to call the API. |
|202 | Permission verification failed. A non-system application calls a system API. |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let pbapClientProfile = pbap.createPbapClientProfile();
    pbapClientProfile.offSyncStateChange((data: pbap.SyncStateChangeParam) => {
        console.info('deviceId: ' + data.deviceId + ', state: ' + data.state);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## SyncStateChangeParam

Phone book synchronization status change information.

**Since:** 26.0.1

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction**: This API can be used only in the stage model.

| Name     | Type    | Read-Only  | Optional  | Description                                 |
| -------- | ------ | ---- | ---- | ----------------------------------- |
| deviceId | string | No   | No   | Address of the target device. |
| state | [SyncStateType](#syncstatetype) | No   | No   | Phone book synchronization status. |


## SyncStateType

Enumerates the phone book synchronization status types.

**Since:** 26.0.1

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction**: This API can be used only in the stage model.

| Name               | Value   | Description     |
| ----------------- | ------ | ------- |
| PHONEBOOK_STATE_IDLE | 0 | The phone book synchronization is in the idle state (not started, for example, connected but not downloaded). |
| PHONEBOOK_STATE_DOWNLOADING | 1 | The phone book is being downloaded. |
| PHONEBOOK_STATE_DOWNLOADED | 2 | The phone book download is complete. |
| PHONEBOOK_STATE_DOWNLOAD_ERROR | 3 | A phone book download error occurs. |