# @ohos.bluetooth.pan (Bluetooth PAN Module) (System API)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=1275b89181ca8fc1862130ee865235369b412dd3 translatedAt=2026-09-15T02:50:39.070Z pushedAt=2026-09-16T08:29:36.754Z -->

The PAN module provides methods for accessing [Personal Area Networking (PAN)](../../connectivity/bluetooth/terminology.md#pan). It supports the two roles of [personal area network user (PANU)](../../connectivity/bluetooth/terminology.md#panu) and [network access point (NAP)](../../connectivity/bluetooth/terminology.md#nap). A PANU device can initiate a connection to an NAP device to achieve network sharing.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.bluetooth.pan (Bluetooth PAN Module)](js-apis-bluetooth-pan.md).


## Modules to Import

```js
import { pan } from '@kit.ConnectivityKit';
```

## PanProfile

Before using any API of **PanProfile**, you need to create an instance of this class by calling [createPanProfile](js-apis-bluetooth-pan.md#pancreatepanprofile).

### connect

connect(deviceId: string): void

Sends a PAN service connection request to a specified device when the local device acts as a PANU. Ensure that the peer device has enabled the network access point (NAP) capability. This method is applicable when the local device needs to connect to a remote NAP device through the Bluetooth PAN to access the network. For example, devices share an Internet connection via Bluetooth.
- You can call [on('connectionStateChange')](js-apis-bluetooth-baseProfile.md#baseprofileonconnectionstatechange) to subscribe to connection status change events.
- If the connection is no longer needed, call [disconnect](#disconnect) for disconnection.

**Since**: 26.0.0

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name   | Type    | Mandatory  | Description     |
| ------ | ------ | ---- | ------- |
| deviceId | string | Yes | MAC address of the remote device. For example: "XX:XX:XX:XX:XX:XX". |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID| Error Message|
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|801 | Capability not supported.          |
|2900003 | Bluetooth disabled.                 |
|2900004 | Profile not supported.                |
|2900099 | Operation failed.                        |

**Example**

```js
try {
    let panProfile: pan.PanProfile = pan.createPanProfile();
    panProfile.connect('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```

### disconnect

disconnect(deviceId: string): void

Disconnects from the PAN service of the currently connected device and releases related resources when the local device acts as a PANU. This method is applicable when you need to disconnect from the Bluetooth PAN when network services are no longer needed to be obtained through the Bluetooth PAN.
- You can call [on('connectionStateChange')](js-apis-bluetooth-baseProfile.md#baseprofileonconnectionstatechange) to subscribe to connection status change events and check whether the disconnection is successful.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name   | Type    | Mandatory  | Description     |
| ------ | ------ | ---- | ------- |
| deviceId | string | Yes | Address of the peer device, for example, "XX:XX:XX:XX:XX:XX". |

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
try {
    let panProfile: pan.PanProfile = pan.createPanProfile();
    panProfile.disconnect('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
```


### setTethering

setTethering(enable: boolean): void

Sets the tethering status when the local device is used as the network access point (NAP).
- When tethering is not enabled for the local device, the PAN service of the local device cannot be connected by using the peer device as the PANU.
- Before calling this API, you are advised to call [isTetheringOn](js-apis-bluetooth-pan.md#istetheringon) to check the current tethering status.
- After tethering is enabled, you can subscribe to the [on('connectionStateChange')](js-apis-bluetooth-baseProfile.md#baseprofileonconnectionstatechange) event to detect the connection of the peer device as the PANU.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH and ohos.permission.MANAGE_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name    | Type     | Mandatory   | Description      |
| ------ | ------ | ---- | ------- |
| enable | boolean | Yes    | Whether to enable network sharing. The value **true** means to enable network sharing, and **false** means the opposite. |

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
try {
    let panProfile: pan.PanProfile = pan.createPanProfile();
    panProfile.setTethering(false);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
```