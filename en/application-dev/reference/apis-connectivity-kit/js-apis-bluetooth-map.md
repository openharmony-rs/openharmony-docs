# @ohos.bluetooth.map (Bluetooth MAP Module)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=4f824c67b9f4e04b01e793c0dcb9c04799653b39 translatedAt=2026-09-15T02:48:42.628Z pushedAt=2026-09-16T07:55:59.699Z -->

This module provides Bluetooth message access capability based on [Message Access Profile (MAP)](../../connectivity/bluetooth/terminology.md#map), and supports functions such as creating MSE instances and obtaining and subscribing to the Bluetooth message service connection status between devices. This module is applicable to scenarios where the Bluetooth protocol is used for message access and connection management.

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { map } from '@kit.ConnectivityKit';
```

## BaseProfile

type BaseProfile = baseProfile.BaseProfile

**BaseProfile** class, which provides public capabilities such as obtaining the connection status and listening for connection status changes.

**System capability**: SystemCapability.Communication.Bluetooth.Core

| Type                           | Description        |
| ----------------------------- | ---------- |
| [baseProfile.BaseProfile](js-apis-bluetooth-baseProfile.md#baseprofile) | **BaseProfile** API definition.|

## map.createMapMseProfile

createMapMseProfile(): MapMseProfile

Creates a [Message Server Equipment (MSE)](../../connectivity/bluetooth/terminology.md#mse) instance. Through this instance, you can use API provided when the local device is used as the MSE and implement functions such as obtaining the Bluetooth message service connection status of the local device. This API is applicable to scenarios such as Bluetooth message synchronization and viewing messages of the Bluetooth car kit.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Return value**

| Type                           | Description        |
| ----------------------------- | ---------- |
| [MapMseProfile](#mapmseprofile) | **MapMseProfile** instance. This instance can be used by the local device as an MSE to access Bluetooth messages. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | ---------------------------- |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let mapMseProfile = map.createMapMseProfile();
    console.info('MapMse success');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```

## MapMseProfile

Represents the [MSE](../../connectivity/bluetooth/terminology.md#mse) role in MAP.
- The **MapMseProfile** class is inherited from [BaseProfile](#baseprofile). Therefore, you can use the APIs in its parent class.
- Before using the APIs of this class, you need to construct an MSE instance by calling [createMapMseProfile](#mapcreatemapmseprofile).
- The counterpart of the MSE role is the [MCE](../../connectivity/bluetooth/terminology.md#mce) role.
