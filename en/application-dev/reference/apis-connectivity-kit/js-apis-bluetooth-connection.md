# @ohos.bluetooth.connection (Bluetooth connection Module)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=cc0fc565309f1feee1e8ea853938538a7ace0021 translatedAt=2026-09-15T02:36:10.385Z pushedAt=2026-09-16T02:07:31.164Z -->

The **connection** module provides capabilities such as Bluetooth device pairing, connection, status query, device scanning and discovery, scanning mode setting, battery level information obtaining, and event subscription. It is applicable to scenarios where Bluetooth device discovery, pairing, connection, and information query need to be implemented in an app.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.



## Modules to Import

```js
import { connection } from '@kit.ConnectivityKit';
```


## ProfileConnectionState

type ProfileConnectionState = constant.ProfileConnectionState

Connection state of the Profile protocol of a Bluetooth device. The Profile protocols include A2DP (Advanced Audio Distribution Profile), HFP (Hands-Free Profile), and HID (Human Interface Device).

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

| Type                  | Description                  |
| ------------------- | ------------------- |
| [constant.ProfileConnectionState](js-apis-bluetooth-constant.md#profileconnectionstate) | Defines the profile connection status of the Bluetooth device. |


## ProfileId

type ProfileId = constant.ProfileId

Enumerates the Bluetooth profile protocols.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

| Type                  | Description                  |
| ------------------- | ------------------- |
| [constant.ProfileId](js-apis-bluetooth-constant.md#profileid) | Enumerates the Bluetooth profile protocols. |


## ProfileUuids<sup>12+</sup>

type ProfileUuids = constant.ProfileUuids

UUID of the Bluetooth Profile protocol.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

| Type                  | Description                  |
| ------------------- | ------------------- |
| [constant.ProfileUuids](js-apis-bluetooth-constant.md#profileuuids12) | UUID of the Bluetooth Profile protocol. |


## MajorClass

type MajorClass = constant.MajorClass

Enumerates the types of Bluetooth devices. This is a standard field in the Bluetooth protocol.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

| Type                  | Description                  |
| ------------------- | ------------------- |
| [constant.MajorClass](js-apis-bluetooth-constant.md#majorclass) | Enumerates the types of Bluetooth devices. |


## MajorMinorClass

type MajorMinorClass = constant.MajorMinorClass

Subtype of the Bluetooth device, further classified based on [MajorClass](js-apis-bluetooth-constant.md#majorclass). A standard Bluetooth protocol field.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

| Type                  | Description                  |
| ------------------- | ------------------- |
| [constant.MajorMinorClass](js-apis-bluetooth-constant.md#majorminorclass) | Subtype of the Bluetooth device. |


## BluetoothAddress<sup>21+</sup>

type BluetoothAddress = common.BluetoothAddress

Defines the address information of a Bluetooth device, including the address and address type.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

| Type                  | Description                  |
| ------------------- | ------------------- |
| [common.BluetoothAddress](js-apis-bluetooth-common.md#bluetoothaddress) | Address information of the Bluetooth device. |


## connection.pairDevice

pairDevice(deviceId: string, callback: AsyncCallback&lt;void&gt;): void

Initiates the pairing process with a peer Bluetooth device. This API uses an asynchronous callback to return the result.
- If the developer does not know the [address type](js-apis-bluetooth-common.md#bluetoothaddresstype) of the target device, it is recommended to call this API to initiate pairing.
- The Bluetooth pairing state is obtained through the callback result of [on('bondStateChange')](#connectiononbondstatechange).

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name     | Type    | Mandatory | Description                                  |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes   | Address of the peer Bluetooth device to be paired, for example, "XX:XX:XX:XX:XX:XX". |
| callback | AsyncCallback&lt;void&gt;  | Yes   | Callback used to return the result. If pairing is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error Code**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
// callback
try {
    connection.pairDevice('11:22:33:44:55:66', (err: BusinessError) => {
        console.info('pairDevice, device name err:' + JSON.stringify(err));
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}

```


## connection.pairDevice

pairDevice(deviceId: string): Promise&lt;void&gt;

Initiates the pairing process with a peer Bluetooth device. This API uses a promise to return the result asynchronously.
- If the developer does not know the [address type](js-apis-bluetooth-common.md#bluetoothaddresstype) of the target device, it is recommended to call this API to initiate pairing.
- The Bluetooth pairing state is obtained through the callback result of [on('bondStateChange')](#connectiononbondstatechange).

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type     | Mandatory   | Description                                  |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes    | Address of the peer Bluetooth device to be paired, for example, "XX:XX:XX:XX:XX:XX". |

**Return value**

| Type                  | Description            |
| ------------------- | ------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error Code**:

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
// promise
try {
    connection.pairDevice('11:22:33:44:55:66').then(() => {
        console.info('pairDevice');
    }, (error: BusinessError) => {
        console.error('pairDevice: errCode:' + error.code + ',errMessage' + error.message);
    })

} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.pairDevice<sup>21+</sup>

pairDevice(deviceId: BluetoothAddress): Promise&lt;void&gt;

Initiates the pairing process with a peer Bluetooth device. This API uses a promise to return the result asynchronously.
- If the developer knows the MAC address and [address type](js-apis-bluetooth-common.md#bluetoothaddresstype) of the target device, it is recommended to call this API to initiate pairing.
- The Bluetooth pairing state is obtained through the callback result of [on('bondStateChange')](#connectiononbondstatechange).

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type     | Mandatory   | Description                                  |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | [BluetoothAddress](js-apis-bluetooth-common.md#bluetoothaddress) | Yes    | Address information of the peer Bluetooth device to be paired, including the address and address type. |

**Return value**

| Type                  | Description            |
| ------------------- | ------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error Code**:

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.ConnectivityKit';
// promise
try {
    let btAddr: common.BluetoothAddress = {
        "address": '11:22:33:44:55:66', // Actual MAC address or virtual MAC address of the target device.
        "addressType": common.BluetoothAddressType.REAL, // Corresponding address type.
    }
    connection.pairDevice(btAddr).then(() => {
        console.info('pairDevice');
    }, (error: BusinessError) => {
        console.error('errCode: ' + error.code + ', errMessage' + error.message);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.getRemoteDeviceName

getRemoteDeviceName(deviceId: string): string

Obtains the name of the peer Bluetooth device.

- Starting from API version 21, this API can be used to obtain the device name by using the actual MAC address of the peer device.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ------ | ---- | --------------------------------- |
| deviceId | string | Yes | Address of the peer device, for example, "XX:XX:XX:XX:XX:XX". |

**Return value**

| Type | Description |
| ------ | ------------- |
| string | Device name returned as a string. |

**Error Codes**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let remoteDeviceName: string = connection.getRemoteDeviceName('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.getRemoteDeviceName<sup>16+</sup>

getRemoteDeviceName(deviceId: string, alias?: boolean): string

Obtains the name of the peer Bluetooth device, where alias is an optional parameter.

- Starting from API version 21, this API can be used to obtain the device name by using the actual MAC address of the peer device.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**Atomic service API**: This API can be used in atomic services since API version 16.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type     | Mandatory   | Description                                |
| -------- | ------ | ---- | --------------------------------- |
| deviceId | string | Yes    | Address of the peer device, for example, "XX:XX:XX:XX:XX:XX". |
| alias | boolean | No    | Whether to obtain the alias of the peer Bluetooth device.<br>- If alias is carried, whether to obtain the alias of the peer Bluetooth device is determined by alias: true indicates obtaining the alias of the peer Bluetooth device, and false indicates obtaining the original name of the peer Bluetooth device.<br>- If alias is not carried, the default value is true, and the alias of the peer Bluetooth device is returned. |

**Return value**

| Type     | Description            |
| ------ | ------------- |
| string | Device name returned in string format. |

**Error codes**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Failed to obtain the name or alias of the peer Bluetooth device.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let remoteDeviceName: string = connection.getRemoteDeviceName('XX:XX:XX:XX:XX:XX', true);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.getRemoteDeviceClass

getRemoteDeviceClass(deviceId: string): DeviceClass

Obtains the class of the peer Bluetooth device.

- Starting from API version 18, this API no longer verifies the ohos.permission.ACCESS_BLUETOOTH permission.
- Starting from API version 21, this API can be used to obtain the device class information by using the actual MAC address of the peer device.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ------ | ---- | --------------------------------- |
| deviceId | string | Yes | Address of the peer device, for example, "XX:XX:XX:XX:XX:XX". |

**Return value**

| Type | Description |
| --------------------------- | -------- |
| [DeviceClass](#deviceclass) | Class of the peer device. |

**Error Code**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 |Permission denied.<br>Applicable versions: 10-17 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let remoteDeviceClass: connection.DeviceClass = connection.getRemoteDeviceClass('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## connection.getRemoteDeviceTransport<sup>20+</sup>

getRemoteDeviceTransport(deviceId: string): BluetoothTransport

Obtains the transport type of the peer Bluetooth device.

- Starting from API version 21, this API can be used to obtain the transport type of the device by using the actual MAC address of the peer device.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type     | Mandatory   | Description                                |
| -------- | ------ | ---- | --------------------------------- |
| deviceId | string | Yes    | Address of the peer device, for example, "XX:XX:XX:XX:XX:XX". |

**Return value**

| Type                          | Description       |
| --------------------------- | -------- |
| [BluetoothTransport](#bluetoothtransport) | Transport type of the peer device. |

**Error codes:**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Get transport failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let transport: connection.BluetoothTransport = connection.getRemoteDeviceTransport('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## connection.getRemoteProfileUuids<sup>12+</sup>

getRemoteProfileUuids(deviceId: string, callback: AsyncCallback&lt;Array&lt;ProfileUuids&gt;&gt;): void

Obtains the profile protocol capabilities of the peer Bluetooth device, distinguished by UUID. This API uses an asynchronous callback to return the result.
- It is recommended that this method be called only for paired devices.
- Starting from API version 21, this API can be used to obtain the profile protocol capabilities by using the actual MAC address of the peer device.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type     | Mandatory   | Description                                  |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes    | Address of the peer device, for example, "XX:XX:XX:XX:XX:XX". |
| callback | AsyncCallback&lt;Array&lt;[ProfileUuids](js-apis-bluetooth-constant.md#profileuuids12)&gt;&gt; | Yes    | Callback used to return the result. If the UUIDs are obtained successfully, **err** is **undefined** and the returned value is the set of profile protocol capabilities; otherwise, **err** is an error object. |

**Error Codes**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter.    |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    connection.getRemoteProfileUuids('XX:XX:XX:XX:XX:XX', (err: BusinessError, data: Array<connection.ProfileUuids>) => {
        console.info('getRemoteProfileUuids, err: ' + JSON.stringify(err) + ', data: ' + JSON.stringify(data));
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}

```


## connection.getRemoteProfileUuids<sup>12+</sup>

getRemoteProfileUuids(deviceId: string): Promise&lt;Array&lt;ProfileUuids&gt;&gt;

Obtains the profile protocol capabilities of the peer Bluetooth device, which are distinguished by UUID. This API uses a promise to return the result.
- It is recommended that this method be called only for paired devices.
- Starting from API version 21, this API can be used to obtain the profile protocol capabilities by using the actual MAC address of the peer device.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name     | Type   | Mandatory | Description                                  |
| -------- | ------ | --------- | -------------------------------------------- |
| deviceId | string | Yes       | Address of the peer device, for example, "XX:XX:XX:XX:XX:XX". |

**Return value**

| Type                  | Description            |
| --------------------- | ---------------------- |
| Promise&lt;Array&lt;[ProfileUuids](js-apis-bluetooth-constant.md#profileuuids12)&gt;&gt; | Promise object used to return the set of supported profile protocol capabilities. |

**Error codes**:

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter.    |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    connection.getRemoteProfileUuids('XX:XX:XX:XX:XX:XX').then(() => {
        console.info('getRemoteProfileUuids');
    }, (err: BusinessError) => {
        console.error('getRemoteProfileUuids: errCode' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.getLocalName

getLocalName(): string

Obtains the name of the local Bluetooth device.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Return value**

| Type | Description |
| ------ | --------- |
| string | Name of the local Bluetooth device. |

**Error code:**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let localName: string = connection.getLocalName();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.getPairedDevices

getPairedDevices(): Array&lt;string&gt;

Obtains the address set of paired Bluetooth devices.

**Required permissions**:
- API versions 26.0.0+: ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)
- API version 10 to 24: ohos.permission.ACCESS_BLUETOOTH

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Return value**

| Type                  | Description            |
| ------------------- | ------------- |
| Array&lt;string&gt; | Address set of paired Bluetooth devices.<br>For information security purposes, the device address obtained here is a virtual MAC address.<br>- The address of a paired device does not change.<br>- If Bluetooth is restarted on the device, the virtual address obtained again changes immediately.<br>- If pairing is canceled, the Bluetooth subsystem determines when to change the address based on its actual usage. If another application is using the address, it will not be changed immediately.<br>- To persist the address, use the [access.addPersistentDeviceId](js-apis-bluetooth-access.md#accessaddpersistentdeviceid16) method. |

**Error code:**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let devices: Array<string> = connection.getPairedDevices();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.getPairState<sup>11+</sup>

getPairState(deviceId: string): BondState

Obtains the pairing state of the peer Bluetooth device.

- Starting from API version 21, this API can be used to obtain the pairing state by using the actual MAC address of the peer device.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type     | Mandatory   | Description                                |
| -------- | ------ | ---- | --------------------------------- |
| deviceId | string | Yes    | Address of the peer device, for example, "XX:XX:XX:XX:XX:XX". |

**Return value**

| Type                          | Description       |
| --------------------------- | -------- |
| [BondState](#bondstate) | Bluetooth pairing state of the device. |

**Error Code**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let res: connection.BondState = connection.getPairState("XX:XX:XX:XX:XX:XX");
    console.info('getPairState: ' + res);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.getProfileConnectionState

getProfileConnectionState(profileId?: ProfileId): ProfileConnectionState

Obtains the connection state of a Bluetooth profile. The parameter ProfileId is optional.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

<!--Table: 10%; 10%; 10%; 70%-->
| Name       | Type        | Mandatory   | Description                                    |
| --------- | --------- | ---- | ------------------------------------- |
| profileId | [ProfileId](js-apis-bluetooth-constant.md#profileid) | No    | Enum value of the profile. If ProfileId is carried, the connection state of the specified profile is returned. If ProfileId is not carried, the connection states of all supported profiles are checked and returned in the following priority order:<br>- If a connected profile exists, [STATE_CONNECTED](js-apis-bluetooth-constant.md#profileconnectionstate) is returned.<br>- If a connecting profile exists, [STATE_CONNECTING](js-apis-bluetooth-constant.md#profileconnectionstate) is returned.<br>- If a disconnecting profile exists, [STATE_DISCONNECTING](js-apis-bluetooth-constant.md#profileconnectionstate) is returned.<br>- If none of the preceding conditions is met, [STATE_DISCONNECTED](js-apis-bluetooth-constant.md#profileconnectionstate) is returned. |

**Return value**

| Type                                              | Description                |
| ------------------------------------------------- | ------------------- |
| [ProfileConnectionState](js-apis-bluetooth-constant.md#profileconnectionstate) | Connection state of the profile. |

**Error Codes**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Incorrect parameter types.        |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900004 | Profile not supported.                |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
import { constant } from '@kit.ConnectivityKit';
try {
    let result: connection.ProfileConnectionState = connection.getProfileConnectionState(constant.ProfileId.PROFILE_A2DP_SOURCE);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.setDevicePairingConfirmation

setDevicePairingConfirmation(deviceId: string, accept: boolean): void

Confirms the result of a pairing request after receiving the pairing request event from the peer Bluetooth device.
- The pairing request from the peer Bluetooth device is obtained through the callback result of [on('pinRequired')](#connectiononpinrequired).

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH (available only to system applications)

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------- | ---- | -------------------------------- |
| deviceId | string | Yes | Address of the peer device, for example, "XX:XX:XX:XX:XX:XX". |
| accept | boolean | Yes | Whether to accept the pairing request from the peer device. The value true means to accept the request, and false means the opposite. |

**Error code**:

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
// Subscribe to the "pinRequired" pairing request event and set the pairing confirmation after receiving the peer pairing request.
function onReceivePinRequiredEvent(data: connection.PinRequiredParam) { // data is the input parameter of the pairing request, that is, the pairing request parameter.
    console.info('pin required  = '+ JSON.stringify(data));
    connection.setDevicePairingConfirmation(data.deviceId, true);
}
try {
    connection.on('pinRequired', onReceivePinRequiredEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.setDevicePinCode

setDevicePinCode(deviceId: string, code: string, callback: AsyncCallback&lt;void&gt;): void

During Bluetooth pairing, a dialog box prompts the user to enter a personal identification number (PIN). Call this API to set the PIN and complete Bluetooth pairing. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name    | Type      | Mandatory   | Description                               |
| ------ | ------- | ---- | -------------------------------- |
| deviceId | string  | Yes    | MAC address of the peer device, for example, "XX:XX:XX:XX:XX:XX". |
| code   | string  | Yes    | PIN entered by the user. The number of characters ranges from (0, 16], for example, "12345".        |
| callback   | AsyncCallback&lt;void&gt;  | Yes    | Callback used to return the result. If the PIN is set successfully, **err** is **undefined**. Otherwise, **err** is an error object.        |

**Error Code**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
// callback
try {
    connection.setDevicePinCode('11:22:33:44:55:66', '12345', (err: BusinessError) => {
        console.info('setDevicePinCode,device name err: ' + JSON.stringify(err));
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.setDevicePinCode

setDevicePinCode(deviceId: string, code: string): Promise&lt;void&gt;

Sets the PIN used to complete Bluetooth pairing. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name    | Type      | Mandatory   | Description                               |
| ------ | ------- | ---- | -------------------------------- |
| deviceId | string  | Yes    | MAC address of the peer device, for example, "XX:XX:XX:XX:XX:XX". |
| code   | string  | Yes    | PIN entered by the user. The number of characters ranges from (0, 16], for example, "12345".        |

**Return value**

| Type                  | Description            |
| ------------------- | ------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error Code**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
// promise
try {
    connection.setDevicePinCode('11:22:33:44:55:66', '12345').then(() => {
        console.info('setDevicePinCode');
    }, (error: BusinessError) => {
        console.error('setDevicePinCode: errCode:' + error.code + ',errMessage' + error.message);
    })

} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.setLocalName<sup>(deprecated)</sup>

setLocalName(name: string): void

Sets the name of the local Bluetooth device. The name cannot be an empty string; otherwise, the operation fails.

> **NOTE**<br/>
> This API is supported since API version 10 and deprecated since API version 12 for security and sensitive information concerns. No substitute is provided. To change the Bluetooth device name of the local device, you can do so in the system settings.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ------ | ---- | --------------------- |
| name | string | Yes | Bluetooth name to set. The name length ranges from (0, 248], in bytes. |

**Error Codes**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    connection.setLocalName('device_name');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.setBluetoothScanMode

setBluetoothScanMode(mode: ScanMode, duration: number): void

Sets the Bluetooth scan mode to determine whether the local device can be connected or discovered. Used together with [onScanModeChange](#connectiononscanmodechange23), this API allows real-time listening for Bluetooth scan mode change events.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | --------------------- | ---- | ---------------------------- |
| mode | [ScanMode](#scanmode) | Yes | Bluetooth scan mode to set. If the scan times out (**duration** is not **0**) when the scan mode is **SCAN_MODE_GENERAL_DISCOVERABLE**, the scan mode will be reset to **SCAN_MODE_CONNECTABLE**. |
| duration | number | Yes | Duration during which the device can be discovered, in milliseconds. If the value is set to **0**, the device can be discovered permanently. |

**Error code**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    // Set the device to connectable and discoverable so that it can be scanned and connected by the peer device.
    connection.setBluetoothScanMode(connection.ScanMode.SCAN_MODE_CONNECTABLE_GENERAL_DISCOVERABLE, 100);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.getBluetoothScanMode

getBluetoothScanMode(): ScanMode

Obtains the Bluetooth scan mode. Used together with [onScanModeChange](#connectiononscanmodechange23), this API can listen for Bluetooth scan mode change events in real time.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Return value**

| Type                    | Description      |
| --------------------- | ------- |
| [ScanMode](#scanmode) | Bluetooth scan mode. |

**Error Code**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let scanMode: connection.ScanMode = connection.getBluetoothScanMode();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.startBluetoothDiscovery

startBluetoothDiscovery(): void

Starts Bluetooth scanning to discover peer Bluetooth devices.<br>
- This API supports discovering both classic Bluetooth devices and Bluetooth Low Energy devices. The entire Bluetooth scanning process lasts about 12 seconds.<br>
- The scan results can be obtained through the callback function of [connection.on('bluetoothDeviceFind')](#connectiononbluetoothdevicefind), supported since API version 10, or [connection.on('discoveryResult')](#connectionondiscoveryresult18), supported since API version 18. It is recommended to use [connection.on('discoveryResult')](#connectionondiscoveryresult18), which can obtain more device information.<br>
- Do not call this API repeatedly during scanning. You can use [connection.isBluetoothDiscovering](#connectionisbluetoothdiscovering11) to check whether Bluetooth is currently scanning.<br>
- Calling [connection.stopBluetoothDiscovery](#connectionstopbluetoothdiscovery) stops the scanning process started by this API. Only after scanning stops can the next Bluetooth scan be started.<br>

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Error code:**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
function onReceiveEvent(data: Array<string>) {
    console.info('data length' + data.length);
}
try {
    connection.on('bluetoothDeviceFind', onReceiveEvent);
    connection.startBluetoothDiscovery();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.stopBluetoothDiscovery

stopBluetoothDiscovery(): void

Stops Bluetooth scanning.<br>
- The scanning to be stopped is triggered by [connection.startBluetoothDiscovery](#connectionstartbluetoothdiscovery).<br>
- When an application no longer needs to scan for devices, it must proactively call this method to stop scanning.<br>
- If scanning is not in progress, do not call this method repeatedly. (You can use [connection.isBluetoothDiscovering](#connectionisbluetoothdiscovering11) to check whether Bluetooth is currently scanning.)<br>

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Error codes**:

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    connection.stopBluetoothDiscovery();
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.isBluetoothDiscovering<sup>11+</sup>

isBluetoothDiscovering(): boolean

Checks whether the local Bluetooth device is in the Device Scan state.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Return value**

| Type                  | Description            |
| ------------------- | ------------- |
|   boolean           | Whether Bluetooth discovery is enabled. The value **true** indicates that a Device Scan is being initiated, and **false** indicates that no Device Scan is being initiated.  |

**Error code:**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
    let res: boolean = connection.isBluetoothDiscovering();
    console.info('isBluetoothDiscovering: ' + res);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## connection.setRemoteDeviceName<sup>12+</sup>

setRemoteDeviceName(deviceId: string, name: string): Promise&lt;void&gt;

Sets the name of the peer Bluetooth device. The name cannot be an empty string; setting it to an empty string will fail. This API uses a promise to return the result asynchronously.
- It is recommended to call this method only for paired devices.
- Since API version 21, this API supports setting the name using the actual MAC address of the peer device.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                  | Mandatory   | Description                                     |
| -------- | ----------------------------------- | ---- | -------------------------------------- |
| deviceId     | string                              | Yes    | MAC address of the peer device, for example, "XX:XX:XX:XX:XX:XX". |
| name | string | Yes    | New name of the peer device. The name length ranges from (0, 64], in bytes.    |

**Return value**

| Type                  | Description            |
| ------------------- | ------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error Code**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.            |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
// promise
try {
    connection.setRemoteDeviceName('11:22:33:44:55:66', 'RemoteDeviceName').then(() => {
        console.info('setRemoteDeviceName success');
    }, (error: BusinessError) => {
        console.error('setRemoteDeviceName: errCode: ' + error.code + ',errMessage' + error.message);
    })
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.getRemoteDeviceBatteryInfo<sup>12+</sup>

getRemoteDeviceBatteryInfo(deviceId: string): Promise&lt;BatteryInfo&gt;

Obtains the battery information of the peer Bluetooth device. This API uses a promise to return the result asynchronously.
- Changes in the battery information of the peer Bluetooth device are obtained through the callback result of [on('batteryChange')](#connectiononbatterychange12).
- Starting from API version 21, this API can be used to obtain the battery information by using the actual MAC address of the peer device.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name    | Type      | Mandatory   | Description                               |
| ------ | ------- | ---- | -------------------------------- |
| deviceId | string  | Yes    | MAC address of the peer Bluetooth device, for example, "XX:XX:XX:XX:XX:XX". |

**Return value**

| Type                  | Description         |
| ------------------- | ------------- |
| Promise&lt;[BatteryInfo](#batteryinfo12)&gt; | Promise object used to return the battery information object. |

**Error Code**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.            |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
// promise
try {
    connection.getRemoteDeviceBatteryInfo('11:22:33:AA:BB:FF').then((data: connection.BatteryInfo) => {
        console.info('getRemoteDeviceBatteryInfo success, DeviceType:' + JSON.stringify(data));
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.on('batteryChange')<sup>12+</sup>

on(type: 'batteryChange', callback: Callback&lt;BatteryInfo&gt;): void

Subscribes to the battery information change event of the peer device. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                  | Mandatory   | Description                                     |
| -------- | ----------------------------------- | ---- | -------------------------------------- |
| type     | string                              | Yes    | Event callback type. The supported event is 'batteryChange', which indicates the battery information change event of the peer device. This event is triggered when the device notifies a battery change. |
| callback | Callback&lt;[BatteryInfo](#batteryinfo12)&gt; | Yes    | Callback invoked to return the battery information.    |

**Error Code**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
let onReceiveEvent: (data: connection.BatteryInfo) => void = (data: connection.BatteryInfo) => {
    console.info('BatteryInfo = '+ JSON.stringify(data));
}
try {
    connection.on('batteryChange', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.off('batteryChange')<sup>12+</sup>

off(type: 'batteryChange', callback?: Callback&lt;BatteryInfo&gt;): void

Unsubscribes from the battery information change event of the peer device.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                  | Mandatory   | Description                                       |
| -------- | ----------------------------------- | ---- | ---------------------------------------- |
| type     | string                              | Yes    | Type of the event to unsubscribe from. The supported event is 'batteryChange', which indicates the battery information change event of the peer device.   |
| callback | Callback&lt;[BatteryInfo](#batteryinfo12)&gt; | No    | Callback for the battery information change event.<br>If this parameter is passed, it must be the same as the callback in [connection.on('batteryChange')](#connectiononbatterychange12). If this parameter is not passed, all callbacks subscribed for this type are unsubscribed. |

**Error code:**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
let onReceiveEvent: (data: connection.BatteryInfo) => void = (data: connection.BatteryInfo) => {
    console.info('BatteryInfo = '+ JSON.stringify(data));
}
try {
    connection.on('batteryChange', onReceiveEvent);
    connection.off('batteryChange', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.on('bluetoothDeviceFind')

on(type: 'bluetoothDeviceFind', callback: Callback&lt;Array&lt;string&gt;&gt;): void

Subscribes to the Bluetooth device scan result reporting event. This API uses an asynchronous callback.<br>
- The device types that can be scanned include classic Bluetooth devices and Bluetooth Low Energy devices.<br>
- This reporting method supports obtaining only the device address information.<br>
- It is recommended that you use the [connection.on('discoveryResult')](#connectionondiscoveryresult18) scan reporting method supported since API version 18, which can obtain more device information, including the device address, device signal strength, device name, and device type.

**Required permissions**:
- API versions 26.0.0+: ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)
- API version 10 to 24: ohos.permission.ACCESS_BLUETOOTH

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                  | Mandatory   | Description                                     |
| -------- | ----------------------------------- | ---- | -------------------------------------- |
| type     | string                              | Yes    | Type of the event to subscribe to. The supported event is 'bluetoothDeviceFind', which indicates the Bluetooth device scan result reporting event. After [connection.startBluetoothDiscovery](#connectionstartbluetoothdiscovery) is called, device scanning starts. If a device is scanned, this event is triggered. |
| callback | Callback&lt;Array&lt;string&gt;&gt; | Yes    | Callback invoked to return the set of scanned device addresses.<br>For information security purposes, the device address obtained here is a virtual MAC address.<br>- The address of a paired device does not change.<br>- If Bluetooth is restarted on the device, the re-obtained virtual address changes immediately.<br>- If pairing is canceled, the Bluetooth subsystem determines the subsequent change timing based on the actual usage of the address. If another application is using the address, it will not change immediately.<br>- To persist the address, use [access.addPersistentDeviceId](js-apis-bluetooth-access.md#accessaddpersistentdeviceid16).   |

**Error codes**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>Applicable versions: 10 to 24                 |
|801 | Capability not supported.          |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
function onReceiveEvent(data: Array<string>) { // data is a set of Bluetooth device addresses.
    console.info('bluetooth device find = '+ JSON.stringify(data));
}
try {
    connection.on('bluetoothDeviceFind', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.off('bluetoothDeviceFind')

off(type: 'bluetoothDeviceFind', callback?: Callback&lt;Array&lt;string&gt;&gt;): void

Unsubscribes from Bluetooth device scan result reporting events.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                  | Mandatory   | Description                                       |
| -------- | ----------------------------------- | ---- | ---------------------------------------- |
| type     | string                              | Yes    | Type of the event callback. The supported event is 'bluetoothDeviceFind', which indicates the Bluetooth device scan result reporting event.   |
| callback | Callback&lt;Array&lt;string&gt;&gt; | No    | Callback for the Bluetooth device scan result reporting event.<br>If this parameter is passed, it must be the same as the callback in [connection.on('bluetoothDeviceFind')](#connectiononbluetoothdevicefind). If this parameter is not passed, all callbacks registered for this type are unsubscribed. |

**Error code:**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
function onReceiveEvent(data: Array<string>) {
    console.info('bluetooth device find = '+ JSON.stringify(data));
}
try {
    connection.on('bluetoothDeviceFind', onReceiveEvent);
    connection.off('bluetoothDeviceFind', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.on('bondStateChange')

on(type: 'bondStateChange', callback: Callback&lt;BondStateParam&gt;): void

Subscribes to Bluetooth pairing status change events. This API uses an asynchronous callback to return the result.

**Required permissions**:
- API versions 26.0.0+: ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)
- API version 10 to 24: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                       | Mandatory   | Description                                   |
| -------- | ---------------------------------------- | ---- | ------------------------------------ |
| type     | string                                   | Yes    | Type of the event to subscribe to. The supported event is 'bondStateChange', which indicates a Bluetooth pairing status change event.<br>This event is triggered when [connection.pairDevice](#connectionpairdevice) is called to initiate pairing, or when the local device receives a pairing request from another device. |
| callback | Callback&lt;[BondStateParam](#bondstateparam)&gt; | Yes    | Callback invoked to return the pairing status result.    |

**Error Code**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>Applicable versions: 10 to 24                 |
|801 | Capability not supported.          |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
function onReceiveEvent(data: connection.BondStateParam) { // data is the input parameter of the callback function, indicating the pairing status.
    console.info('pair state = '+ JSON.stringify(data));
}
try {
    connection.on('bondStateChange', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.off('bondStateChange')

off(type: 'bondStateChange', callback?: Callback&lt;BondStateParam&gt;): void

Unsubscribes from the Bluetooth pairing state change event.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                       | Mandatory   | Description                                       |
| -------- | ---------------------------------------- | ---- | ---------------------------------------- |
| type     | string                                   | Yes    | Type of the event callback. The supported event is 'bondStateChange', which indicates the Bluetooth pairing state change event.     |
| callback | Callback&lt;[BondStateParam](#bondstateparam)&gt; | No    | Callback for the Bluetooth pairing state change event.<br>If this parameter is passed, it must be the same as the callback in [connection.on('bondStateChange')](#connectiononbondstatechange). If this parameter is not passed, all callbacks registered for this type are unsubscribed. |

**Error Code**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
function onReceiveEvent(data: connection.BondStateParam) {
    console.info('bond state = '+ JSON.stringify(data));
}
try {
    connection.on('bondStateChange', onReceiveEvent);
    connection.off('bondStateChange', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.on('pinRequired')

on(type: 'pinRequired', callback: Callback&lt;PinRequiredParam&gt;): void

Subscribes to the pairing request event. This API uses an asynchronous callback to return the result.

**Required permissions**:
- API versions 26.0.0+: ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)
- API version 10 to 24: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                       | Mandatory   | Description                               |
| -------- | ---------------------------------------- | ---- | -------------------------------- |
| type     | string                                   | Yes    | Event type. The value **pinRequired** indicates a pairing request event. This event is triggered when [connection.pairDevice](#connectionpairdevice) is called to initiate pairing or the local device receives a pairing request from another device. After receiving a pairing request, you can call [connection.setDevicePairingConfirmation](#connectionsetdevicepairingconfirmation) to accept or reject the request.     |
| callback | Callback&lt;[PinRequiredParam](#pinrequiredparam)&gt; | Yes    | Callback used to return the pairing request. |

**Error Code**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>Applicable versions: 10 to 24                 |
|801 | Capability not supported.          |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
function onReceiveEvent(data: connection.PinRequiredParam) { // data is the pairing request parameter.
    console.info('pin required = '+ JSON.stringify(data));
}
try {
    connection.on('pinRequired', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.off('pinRequired')

off(type: 'pinRequired', callback?: Callback&lt;PinRequiredParam&gt;): void

Unsubscribes from the pairing request event.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                       | Mandatory   | Description                                       |
| -------- | ---------------------------------------- | ---- | ---------------------------------------- |
| type     | string                                   | Yes    | Type of the event callback. The supported event is 'pinRequired', which indicates the pairing request event.             |
| callback | Callback&lt;[PinRequiredParam](#pinrequiredparam)&gt; | No    | Callback for the pairing request event.<br>If this parameter is passed, it must be the same as the callback in [connection.on('pinRequired')](#connectiononpinrequired). If this parameter is not passed, all callbacks for this type are unsubscribed. |

**Error code**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
function onReceiveEvent(data: connection.PinRequiredParam) {
    console.info('pin required = '+ JSON.stringify(data));
}
try {
    connection.on('pinRequired', onReceiveEvent);
    connection.off('pinRequired', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.on('discoveryResult')<sup>18+</sup>

on(type: 'discoveryResult', callback: Callback&lt;Array&lt;DiscoveryResult&gt;&gt;): void

Subscribes to the Bluetooth device scan result reporting event. This API uses an asynchronous callback to return the result.<br>
- The device types that can be scanned include classic Bluetooth devices and Bluetooth Low Energy devices.<br>
- This reporting method supports obtaining the device address, device signal strength, device name, and device type.

**Required permissions**:
- API versions 26.0.0+: ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)
- API version 18 to 24: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                  | Mandatory   | Description                                     |
| -------- | ----------------------------------- | ---- | -------------------------------------- |
| type     | string                              | Yes    | Event callback type. The supported event is 'discoveryResult', which indicates the Bluetooth device scan result reporting event. After [connection.startBluetoothDiscovery](#connectionstartbluetoothdiscovery) is called, device scan starts. If a device is scanned, this event is triggered. |
| callback | Callback&lt;Array&lt;[DiscoveryResult](#discoveryresult18)&gt;&gt; | Yes    | Callback invoked to return the set of scan results.    |

**Error Code**:

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.<br>Applicable versions: 18 to 24                 |
|801 | Capability not supported.          |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
let onReceiveEvent: (data: Array<connection.DiscoveryResult>) => void = (data: Array<connection.DiscoveryResult>) => { // data is the set of Bluetooth device scan results.
    console.info('bluetooth device find = '+ JSON.stringify(data));
}
try {
    connection.on('discoveryResult', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.off('discoveryResult')<sup>18+</sup>

off(type: 'discoveryResult', callback?: Callback&lt;Array&lt;DiscoveryResult&gt;&gt;): void

Unsubscribes from Bluetooth device scan result reporting events.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                  | Mandatory   | Description                                       |
| -------- | ----------------------------------- | ---- | ---------------------------------------- |
| type     | string                              | Yes    | Event callback type. The supported event is 'discoveryResult', which indicates the Bluetooth device scan result reporting event.   |
| callback | Callback&lt;Array&lt;[DiscoveryResult](#discoveryresult18)&gt;&gt; | No    | Callback for the Bluetooth device scan result reporting event.<br>If this parameter is passed, it must be the same as the callback in [connection.on('discoveryResult')](#connectionondiscoveryresult18). If this parameter is not passed, all callbacks corresponding to this type are unsubscribed. |

**Error Code**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
let onReceiveEvent: (data: Array<connection.DiscoveryResult>) => void = (data: Array<connection.DiscoveryResult>) => { // data is the set of Bluetooth device scan results.
    console.info('bluetooth device find = '+ JSON.stringify(data));
}
try {
    connection.on('discoveryResult', onReceiveEvent);
    connection.off('discoveryResult', onReceiveEvent);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.onScanModeChange<sup>23+</sup>

onScanModeChange(callback: Callback&lt;ScanMode&gt;): void

Subscribes to the Bluetooth scan mode change event. This API uses an asynchronous callback. After [setBluetoothScanMode](#connectionsetbluetoothscanmode) is called to change the current Bluetooth scan mode, if this event is subscribed, the callback function carrying the latest scan mode is invoked.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                       | Mandatory   | Description                               |
| -------- | ---------------------------------------- | ---- | -------------------------------- |
| callback | Callback&lt;[ScanMode](#scanmode)&gt; | Yes    | Callback invoked to return the latest Bluetooth scan mode after the change. |

**Error Code**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|2900099 | Operation failed.              |

**Example**

```js
function ScanModeChangeEvent(scanMode: connection.ScanMode) {
    console.info(`Scan mode has changed, new mode: ${scanMode}`);
}
try {
    connection.onScanModeChange(ScanModeChangeEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```


## connection.offScanModeChange<sup>23+</sup>

offScanModeChange(callback?: Callback&lt;ScanMode&gt;): void

Unsubscribes from the Bluetooth scan mode change event.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                       | Mandatory   | Description                                       |
| -------- | ---------------------------------------- | ---- | ---------------------------------------- |
| callback | Callback&lt;[ScanMode](#scanmode)&gt; | No    | Callback for the Bluetooth scan mode change event to unsubscribe from.<br>If this parameter is passed, it must be the same as the callback in [connection.onScanModeChange](#connectiononscanmodechange23). If this parameter is not passed, all callbacks for the Bluetooth scan mode change event are unsubscribed from. |

**Error code**:

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|801 | Capability not supported.          |
|2900099 | Operation failed.                        |

**Example**

```js
function ScanModeChangeEvent(scanMode: connection.ScanMode) {
    console.info(`Scan mode has changed, new mode: ${scanMode}`);
}
try {
    connection.offScanModeChange(ScanModeChangeEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```


## connection.getLastConnectionTime<sup>15+</sup>

getLastConnectionTime(deviceId: string): Promise&lt;number&gt;

Obtains the time of the last connection to the peer Bluetooth device. This API uses a promise to return the result asynchronously.

- Starting from API version 21, this API can be used to obtain the last connection time by using the actual MAC address of the peer device.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name    | Type      | Mandatory   | Description                               |
| ------ | ------- | ---- | -------------------------------- |
| deviceId | string  | Yes    | MAC address of the peer device, for example, "XX:XX:XX:XX:XX:XX". |

**Return value**

| Type                  | Description         |
| ------------------- | ------------- |
| Promise&lt;number&gt; | Promise object that returns the time of the last connection to the peer Bluetooth device, in the format of a UNIX timestamp in seconds. |

**Error codes**:

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
// promise
try {
    connection.getLastConnectionTime('11:22:33:44:55:66').then((time: number) => {
        console.info(`connectionTime: ${time}`);
    });
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## connection.connectAllowedProfiles<sup>16+</sup>

connectAllowedProfiles(deviceId: string, callback: AsyncCallback&lt;void&gt;): void

Connects to the profiles (including A2DP, HFP, HID, and PAN) supported by the peer device. The Bluetooth subsystem identifies the profile types supported by the peer device. This API uses an asynchronous callback to return the result.
- For versions earlier than API version 26.0.0, call [connection.pairDevice](#connectionpairdevice) to initiate pairing first. This API can be called only once within 30 seconds after each pairing is initiated.
- Starting from API version 26.0.0, there is no time limit for calling this API for A2DP and HFP. You can call this API at any time after calling [connection.pairDevice](#connectionpairdevice) to initiate pairing. For HID, this API still needs to be called within 30 seconds after each pairing is initiated.
- Upon successful pairing, you are advised to call [getRemoteProfileUuids](#connectiongetremoteprofileuuids12) to query the profiles supported by the target device. This API is called only if the target device supports the profile required by the application.
- This API must be used together with [connection.disconnectAllowedProfiles](#connectiondisconnectallowedprofiles).
- Starting from API version 21, this API can be used to perform profile connection using the actual MAC address of the peer device.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name     | Type    | Mandatory  | Description                                 |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes   | MAC address of the peer device to connect, for example, "XX:XX:XX:XX:XX:XX".|
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the connection is initiated successfully, **err** is **undefined**. Otherwise, **err** is an error object.  |

**Error codes**:

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID| Error Message|
| -------- | ---------------------------- |
|201     | Permission denied.                       |
|401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                       |
|801     | Capability not supported.                |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
  connection.connectAllowedProfiles('68:13:24:79:4C:8C', (err: BusinessError) => {
    if (err) {
      console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
      return;
    }
    console.info('connectAllowedProfiles');
  });
} catch (err) {
  console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## connection.connectAllowedProfiles<sup>16+</sup>

connectAllowedProfiles(deviceId: string): Promise&lt;void&gt;

Connects to the profiles (including A2DP, HFP, HID, and PAN) supported by the peer device. The Bluetooth subsystem identifies the profile types supported by the peer device. This API uses a promise to return the result.
- For versions earlier than API version 26.0.0, call [connection.pairDevice](#connectionpairdevice) to initiate pairing first. This API can be called only once within 30 seconds after each pairing is initiated.
- Starting from API version 26.0.0, there is no time limit for calling this API for A2DP and HFP. You can call this API at any time after calling [connection.pairDevice](#connectionpairdevice) to initiate pairing. For HID, this API still needs to be called within 30 seconds after each pairing is initiated.
- Upon successful pairing, you are advised to call [getRemoteProfileUuids](#connectiongetremoteprofileuuids12) to query the profiles supported by the target device. This API is called only if the target device supports the profile required by the application.
- This API must be used together with [connection.disconnectAllowedProfiles](#connectiondisconnectallowedprofiles).
- Starting from API version 21, this API can be used to perform profile connection using the actual MAC address of the peer device.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name     | Type    | Mandatory  | Description                                 |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes   | MAC address of the peer device to connect, for example, "XX:XX:XX:XX:XX:XX".|

**Return value**

| Type                                             | Description               |
| ------------------------------------------------- | ------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error Code:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID| Error Message|
| -------- | ---------------------------- |
|201     | Permission denied.                       |
|401     | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                       |
|801     | Capability not supported.                |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';
try {
  connection.connectAllowedProfiles('68:13:24:79:4C:8C').then(() => {
      console.info('connectAllowedProfiles');
    }, (err: BusinessError) => {
      console.error('connectAllowedProfiles:errCode' + err.code + ', errMessage: ' + err.message);
  });
} catch (err) {
  console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## connection.disconnectAllowedProfiles

disconnectAllowedProfiles(deviceId: string): Promise&lt;void&gt;

Disconnects the profiles supported by the peer device. This API uses a promise to return the result.
- For non-system apps, this API must be used together with [connection.connectAllowedProfiles](#connectionconnectallowedprofiles16). If this API is directly called, error code 2900099 will be returned. For non-system apps, this API can only be used to disconnect from the A2DP and HFP profiles. Other profiles involve system app functions and can only be operated by system apps.
- System apps can directly call this API to disconnect from all connected profiles, including A2DP, HFP, HID, and PAN.

**Since**: 26.0.0

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name     | Type    | Mandatory  | Description                                 |
| -------- | ------ | ---- | ----------------------------------- |
| deviceId | string | Yes   | MAC address of the peer device to disconnect, for example, "XX:XX:XX:XX:XX:XX".|

**Return value**

| Type                                             | Description               |
| ------------------------------------------------- | ------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error Codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID| Error Message|
| -------- | ---------------------------- |
|201     | Permission denied.                       |
|801     | Capability not supported. Failed to call the API when the short-range chip is not inserted on 2in1 device.               |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900099 | Operation failed.                        |

**Example**

```js
try {
  await connection.disconnectAllowedProfiles('68:13:24:79:4C:8C');
} catch (err) {
  console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## connection.getVirtualAddressByHash<sup>24+</sup>

getVirtualAddressByHash(algorithmType: HashAlgorithmType, hashValue: string): string

Obtains the corresponding [virtual MAC address](../../connectivity/bluetooth/bluetooth-overview.md#bluetooth-device-address-type) based on the hash value of the [actual MAC address](../../connectivity/bluetooth/bluetooth-overview.md#bluetooth-device-address-type) of a paired device.

When [HashAlgorithmType](#hashalgorithmtype24) is HASH_ALGORITHM_SHA256, use the uppercase actual MAC address to generate the corresponding hash value (64 hexadecimal digits) through the SHA256 algorithm, take the last 32 digits as the input, and the letters in the hash value are case-insensitive.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name     | Type    | Mandatory  | Description                                 |
| -------- | ------ | ---- | ----------------------------------- |
| algorithmType | [HashAlgorithmType](#hashalgorithmtype24) | Yes   | Hash algorithm type.|
| hashValue | string | Yes   | Hash value, for example, "c10b57deb2e1aafd255596e0d4fd6789".|

**Return value**

| Type                                             | Description               |
| ------------------------------------------------- | ------------------- |
| string | Returns the virtual MAC address of the device corresponding to the hash value, for example, "XX:XX:XX:XX:XX:XX". The returned address is in uppercase.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID| Error Message|
| -------- | ---------------------------- |
|201     | Permission denied.                       |
|801     | Capability not supported. Failed to call the API when the short-range chip is not inserted on 2in1 device.               |
|2900003 | Bluetooth disabled.                 |
|2900015 | Parameter format mismatch with specification.   |
|2900016 | Device unpaired.   |
|2900099 | Internal system error. For example, IPC error. Detailed error messages can be used to assist in locating the problem.                        |

**Example**

```js
// If the actual address to be queried is 11:22:33:44:55:AA,
// the corresponding 64-digit hash value is d2204cb9b6d3d3962cc90fa54130efb4c10b57deb2e1aafd255596e0d4fd6789,
// Take the last 32 bits of the hash value when HashAlgorithmType is HASH_ALGORITHM_SHA256.
let hashValue: string = "c10b57deb2e1aafd255596e0d4fd6789";
try {
  let addr: string = connection.getVirtualAddressByHash(connection.HashAlgorithmType.HASH_ALGORITHM_SHA256, hashValue);
} catch (err) {
  console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## connection.onAclStateChange

onAclStateChange(callback: Callback&lt;AclStateResult&gt;): void

Subscribes to the Bluetooth ACL link connection status change event. If this event is subscribed to, a callback containing the address and connection status of the corresponding device will be received when the Bluetooth ACL link is connected or disconnected.

**Since**: 26.0.0

**Required Permission:** ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                       | Mandatory   | Description                               |
| -------- | ---------------------------------------- | ---- | -------------------------------- |
| callback | Callback&lt;[AclStateResult](#aclstateresult)&gt; | Yes    | Callback used to return the Bluetooth ACL link connection status. |

**Error Code**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|801 | Capability not supported.<br>Failed to call the API when the short-range chip is not inserted on 2in1 device.       |
|2900099 | Internal system error.<br>For example, IPC error. Detailed error messages can be used to assist in locating the problem.              |

**Example**

```js
function AclStateChangeEvent(aclStateResult: connection.AclStateResult) {
    console.info('acl state changed:'+ JSON.stringify(aclStateResult));
}
try {
    connection.onAclStateChange(AclStateChangeEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## connection.offAclStateChange

offAclStateChange(callback?: Callback&lt;AclStateResult&gt;): void

Unsubscribes from the Bluetooth ACL link connection state change event.

**Since**: 26.0.0

**Required Permission:** ohos.permission.ACCESS_BLUETOOTH or (ohos.permission.ACCESS_BLUETOOTH and ohos.permission.GET_BLUETOOTH_PEERS_MAC)

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name      | Type                                       | Mandatory   | Description                                       |
| -------- | ---------------------------------------- | ---- | ---------------------------------------- |
| callback | Callback&lt;[AclStateResult](#aclstateresult)&gt; | No    | Callback for the Bluetooth ACL connection state change event.<br>If this parameter is passed, it must be the same as the callback in [connection.onAclStateChange](#connectiononaclstatechange). If this parameter is not passed, all callbacks for the Bluetooth ACL connection state change event are unsubscribed. |

**Error Code:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|801 | Capability not supported.<br>Failed to call the API when the short-range chip is not inserted on 2in1 device.|
|2900099 | Internal system error.<br>For example, IPC error. Detailed error messages can be used to assist in locating the problem.                        |

**Example**

```js
function AclStateChangeEvent(aclStateResult: connection.AclStateResult) {
    console.info('acl state changed:'+ JSON.stringify(aclStateResult));
}
try {
    connection.offAclStateChange(AclStateChangeEvent);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

## BondStateParam

Describes the parameter structure of the pairing state result.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

| Name       | Type   | Read-only | Optional   | Description          |
| -------- | ------ | ---- | ---- | ----------- |
| deviceId | string      | No    | No    | Address of the peer device. |
| state    | [BondState](#bondstate)   | No    | No    | Pairing status. |
| cause<sup>12+</sup>| [UnbondCause](#unbondcause12) | No | No | Reason why the pairing fails. |
| causeMessage | string | No | Yes | Specific reason why the pairing fails. For example, when the local service proactively deletes the pairing, **USER_REMOVED** is returned.<br> **Since:** 26.0.0  |


## PinRequiredParam

Describes the parameter structure of a pairing request.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

| Name | Type | Read-only | Optional | Description |
| -------- | ------ | ---- | ---- | ----------- |
| deviceId | string | No | No | Address of the peer device to pair. |
| pinCode | string | No | No | PIN code used in the pairing process. |



## DeviceClass

Describes the type of a Bluetooth device.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

| Name            | Type                                | Read-only | Optional | Description               |
| --------------- | ----------------------------------- | ---- | ---- | ---------------- |
| majorClass      | [MajorClass](js-apis-bluetooth-constant.md#majorclass)           | No    | No    | Main class. This is a standard field in the Bluetooth protocol.   |
| majorMinorClass | [MajorMinorClass](js-apis-bluetooth-constant.md#majorminorclass) | No    | No    | Subclass, which is further classified based on the major class. This is a standard field in the Bluetooth protocol. |
| classOfDevice   | number                              | No    | No    | Class of the Bluetooth device. This is a standard field in the Bluetooth protocol. It includes the [MajorClass](js-apis-bluetooth-constant.md#majorclass), [MajorMinorClass](js-apis-bluetooth-constant.md#majorminorclass), and supported major services.          |


## BatteryInfo<sup>12+</sup>

Describes the battery level of a device.<br>Only devices that support the specific **Attention** (AT) command (including +XEVENT and IPHONEACCEV) can report valid battery level information.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

| Name       | Type   | Read-only   | Optional   | Description          |
| -------- | ------ | ---- | ---- | ----------- |
| batteryLevel  | number | No    | No    | Battery level of the device. The value range is [0, 100], in percentage (%). If the value is **-1**, no battery level is available.   |
| leftEarBatteryLevel  | number | No    | No    | Battery level of the left earbud if the device is a Bluetooth earbud. The value range is [0, 100], in percentage (%). If the value is **-1**, no battery level is available.   |
| leftEarChargeState  | [DeviceChargeState](#devicechargestate12) | No    | No    | Charging status of the left earbud if the device is a Bluetooth earbud.   |
| rightEarBatteryLevel  | number | No    | No    | Battery level of the right earbud if the device is a Bluetooth earbud. The value range is [0, 100], in percentage (%). If the value is **-1**, no battery level is available.   |
| rightEarChargeState  | [DeviceChargeState](#devicechargestate12) | No    | No    | Charging status of the right earbud if the device is a Bluetooth earbud.   |
| boxBatteryLevel  | number | No    | No    | Battery level of the earbud compartment if the device is a Bluetooth earbud. The value range is [0, 100], in percentage (%). If the value is **-1**, no battery level is available.   |
| boxChargeState  | [DeviceChargeState](#devicechargestate12) | No    | No    | Charging status of the earbud compartment if the device is a Bluetooth earbud.   |


## BluetoothTransport

Enumerates the device transport types.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

| Name                               | Value    | Description              |
| -------------------------------- | ------ | --------------- |
| TRANSPORT_BR_EDR   | 0 | Transport mode of a classic Bluetooth (Basic Rate/Enhanced Data Rate, BR/EDR) device.  |
| TRANSPORT_LE  | 1 | Transport mode of a Bluetooth Low Energy (BLE) device.  |
| TRANSPORT_DUAL<sup>20+</sup>  | 2 | Transport mode of a dual-mode device that supports both classic Bluetooth (BR/EDR) and Bluetooth Low Energy (BLE). The device can select either classic Bluetooth (BR/EDR) or Bluetooth Low Energy (BLE) for communication as needed.  |
| TRANSPORT_UNKNOWN<sup>20+</sup>  | 3 | Unknown device transport mode.  |


## ScanMode

Enumerates the scan modes. The mode determines whether the device is discoverable or connectable.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

| Name                                       | Value  | Description              |
| ---------------------------------------- | ---- | --------------- |
| SCAN_MODE_NONE                           | 0    | Not discoverable or connectable.         |
| SCAN_MODE_CONNECTABLE                    | 1    | Connectable.        |
| SCAN_MODE_GENERAL_DISCOVERABLE           | 2    | Generally discoverable, and can be discovered for a long time.    |
| SCAN_MODE_LIMITED_DISCOVERABLE           | 3    | Limited discoverable, and discoverable for a certain period of time.    |
| SCAN_MODE_CONNECTABLE_GENERAL_DISCOVERABLE | 4    | Connectable and generally discoverable. |
| SCAN_MODE_CONNECTABLE_LIMITED_DISCOVERABLE | 5    | Connectable and limited discoverable. |


## BondState

Enumerates the bond states.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

| Name                | Value | Description |
| ------------------- | ----- | ----------- |
| BOND_STATE_INVALID | 0     | Unpaired.   |
| BOND_STATE_BONDING | 1     | Pairing.    |
| BOND_STATE_BONDED  | 2     | Paired.     |


## UnbondCause<sup>12+</sup>

Enumerates the causes of pairing failure.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

| Name                 | Value  | Description     |
| ------------------ | ---- | ------ |
| USER_REMOVED        | 0    | The user removed the device. If the pairing state [BondState](#bondstate) is bonded, it also indicates that pairing is successful.|
| REMOTE_DEVICE_DOWN  | 1    | The peer device is offline. For example, Bluetooth is disabled on the peer device.|
| AUTH_FAILURE        | 2    | Authentication failed. For example, the keys of the two devices do not match.|
| AUTH_REJECTED       | 3    | Authentication was rejected. For example, the peer device rejected the pairing request. |
| INTERNAL_ERROR      | 4    | An internal error occurred. For example, the device does not support pairing, or the pairing process timed out. |


## DeviceChargeState<sup>12+</sup>

Enumerates the current charging states of a device.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

| Name                 | Value  | Description     |
| ------------------ | ---- | ------ |
| DEVICE_NORMAL_CHARGE_NOT_CHARGED        | 0    | The device that does not support super fast charging is currently not being charged.|
| DEVICE_NORMAL_CHARGE_IN_CHARGING       | 1    | The device that does not support super fast charging is currently being charged.|
| DEVICE_SUPER_CHARGE_NOT_CHARGED        | 2    | The device that supports super fast charging is currently not being charged.|
| DEVICE_SUPER_CHARGE_IN_CHARGING       | 3    | The device that supports super fast charging is currently being charged.|

## DiscoveryResult<sup>18+</sup>

Scan result reported after a device is discovered.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

<!--Table: 15%; 15%; 10%; 10%; 50%-->
| Name       | Type   | Read-only   | Optional   | Description          |
| -------- | ------ | ---- | ---- | ----------- |
| deviceId    | string      | No    | No    | Address of the discovered device.<br>For information security purposes, the device address obtained here is a virtual MAC address.<br>- The address of a paired device does not change.<br>- If the Bluetooth switch of the device is restarted, the virtual address obtained again changes immediately.<br>- If pairing is canceled, the Bluetooth subsystem decides when to change the address later based on the actual usage of the address. If another application is using the address, it is not changed immediately.<br>- To persist this address, use the [access.addPersistentDeviceId](js-apis-bluetooth-access.md#accessaddpersistentdeviceid16) method.|
| rssi     | number      | No    | No    | Signal strength of the discovered device, in dBm.|
| deviceName     | string      | No    | No    | Name of the discovered device.|
| deviceClass     | [DeviceClass](#deviceclass)      | No    | No    | Type of the discovered device.|

## HashAlgorithmType<sup>24+</sup>

Enumerates the hash algorithm types.

A hash algorithm is a mathematical function that generates a unique, fixed-length string (that is, a hash value) by performing complex computations on the input data. It is commonly used for data integrity verification, digital signatures, and other scenarios.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

| Name                 | Value  | Description     |
| ------------------ | ---- | ------ |
| HASH_ALGORITHM_SHA256        | 0    | SHA-256. |


## AclStateResult

Describes the parameter structure of the ACL connection state.

**Since**: 26.0.0

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

| Name     | Type   | Read-only | Optional | Description          |
| -------- | ------ | ---- | ---- | ----------- |
| deviceId | string      | No    | No    | Address of the peer device, for example, "XX:XX:XX:XX:XX:XX". |
| state    | [AclState](#aclstate)   | No    | No    | Connection status. |


## AclState

Enumerates the ACL connection states.

**Since**: 26.0.0

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

| Name                 | Value  | Description     |
| ------------------ | ---- | ------ |
| STATE_CONNECTED        | 0    | The ACL link is connected.|
| STATE_DISCONNECTED        | 1    | The ACL link is disconnected.|