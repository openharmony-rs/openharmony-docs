# @ohos.bluetooth.hfp (Bluetooth HFP Module) (System API)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=1275b89181ca8fc1862130ee865235369b412dd3 translatedAt=2026-09-15T02:41:22.980Z pushedAt=2026-09-16T03:13:13.907Z -->

The **hfp** module provides APIs for using the Bluetooth Hands-Free Profile (HFP) and supports operations such as connecting and disconnecting [HFP](../../connectivity/bluetooth/terminology.md#hfp). This module is applicable to scenarios where the Bluetooth call audio connection needs to be established between devices.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.bluetooth.hfp (Bluetooth HFP Module)](js-apis-bluetooth-hfp.md).


## Modules to Import

```js
import { hfp } from '@kit.ConnectivityKit';
```


## HandsFreeAudioGatewayProfile

Represents the [HFP AG](../../connectivity/bluetooth/terminology.md#hfp-ag) role in Bluetooth call audio.
- This class is inherited from [BaseProfile](js-apis-bluetooth-hfp.md#baseprofile). Therefore, you can use the APIs in its parent class.
- Before using the APIs of this class, you need to construct an HFP AG instance by calling [createHfpAgProfile](js-apis-bluetooth-hfp.md#hfpcreatehfpagprofile).
- The counterpart of the HFP AG role is the [HF](../../connectivity/bluetooth/terminology.md#hf) role.

**System capability**: SystemCapability.Communication.Bluetooth.Core


### connect

connect(deviceId: string): void

Connects to the HFP service of a device. For example, in hands-free call scenarios such as in-vehicle calls and calls using Bluetooth earphones, this API can be used to proactively establish an HFP connection with the remote device.

You need to register the callback using the [BaseProfile.on('connectionStateChange')](js-apis-bluetooth-baseProfile.md#baseprofileonconnectionstatechange) API to detect the connection status change of the HFP profile of the device.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name   | Type    | Mandatory  | Description     |
| ------ | ------ | ---- | ------- |
| deviceId | string | Yes | MAC address of the remote device, for example, "XX:XX:XX:XX:XX:XX". |

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
    let hfpAg = hfp.createHfpAgProfile();
    hfpAg.connect('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


### disconnect

disconnect(deviceId: string): void

Disconnects the HFP connection of a device. For example, this API is used when a user proactively disconnects a hands-free call using Bluetooth earphones or an in-vehicle hands-free call.

You need to register the callback using the [BaseProfile.on('connectionStateChange')](js-apis-bluetooth-baseProfile.md#baseprofileonconnectionstatechange) API to detect the connection status change of the HFP profile of the device.

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Parameters**

| Name    | Type     | Mandatory  | Description      |
| ------ | ------ | ---- | ------- |
| deviceId | string | Yes    | MAC address of the remote device, for example, "XX:XX:XX:XX:XX:XX". |

**Error codes**:

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
    let hfpAg = hfp.createHfpAgProfile();
    hfpAg.disconnect('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## HandsFreeHfProfile

Represents the [HF](../../connectivity/bluetooth/terminology.md#hf) role in Bluetooth call audio.
- This class is inherited from [BaseProfile](js-apis-bluetooth-hfp.md#baseprofile). Therefore, you can use the APIs in its parent class.
- Before using the APIs of this class, you need to construct an instance of this class by calling [createHfpHfProfile](js-apis-bluetooth-hfp.md#hfpcreatehfphfprofile).
- The counterpart of the HF role is the [HFP AG](../../connectivity/bluetooth/terminology.md#hfp-ag) role.

**Since:** 26.0.0

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.


### connect

connect(deviceId: string): void

Connects to the HFP service of a device. For example, this API is used when you need to proactively connect Bluetooth earphones or an in-vehicle device to a phone for a hands-free call.

You need to register the callback using the [BaseProfile.on('connectionStateChange')](js-apis-bluetooth-baseProfile.md#baseprofileonconnectionstatechange) API to detect the connection status change of the HFP profile of the device.

**Since:** 26.0.0

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| ------ | ------ | ---- | ------- |
| deviceId | string | Yes | MAC address of the remote device, for example, "XX:XX:XX:XX:XX:XX". |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID | Error Message |
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900004 | Profile not supported.                |
|2900099 | Internal system error. For example, IPC error.     |

**Example**

```js
try {
    let hf = hfp.createHfpHfProfile();
    hf.connect('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```


### disconnect

disconnect(deviceId: string): void

Disconnects the HFP connection of a device.

You need to register the callback using the [BaseProfile.on('connectionStateChange')](js-apis-bluetooth-baseProfile.md#baseprofileonconnectionstatechange) API to detect the connection status change of the HFP profile of the device.

**Since:** 26.0.0

**System API**: This is a system API.

**Required permissions**: ohos.permission.ACCESS_BLUETOOTH

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Parameters**

| Name   | Type    | Mandatory  | Description     |
| ------ | ------ | ---- | ------- |
| deviceId | string | Yes | MAC address of the remote device, for example, "XX:XX:XX:XX:XX:XX". |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID| Error Message|
| -------- | ---------------------------- |
|201 | Permission denied.                 |
|202 | Non-system applications are not allowed to use system APIs. |
|801 | Capability not supported.          |
|2900001 | Service stopped.                         |
|2900003 | Bluetooth disabled.                 |
|2900004 | Profile not supported.                |
|2900099 | Internal system error. For example, IPC error.          |

**Example**

```js
try {
    let hf = hfp.createHfpHfProfile();
    hf.disconnect('XX:XX:XX:XX:XX:XX');
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```