# @ohos.bluetooth.pbap (Bluetooth PBAP Module)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=8a0e36109bea79cc35522d2aee4c1b8ad683b256 translatedAt=2026-11-18T04:11:05.651Z pushedAt=2026-11-20T09:25:10.483Z nl=1 -->

This module implements phone book access capabilities based on the [Phone Book Access Profile (PBAP)](../../connectivity/bluetooth/terminology.md#pbap). It allows you to create a [PSE](../../connectivity/bluetooth/terminology.md#pse) server instance and obtain the connection status of the Bluetooth phonebook service between devices. This module is applicable to scenarios where the local device functions as a PSE to provide phonebook access services for external devices. It helps you quickly implement Bluetooth phonebook sharing and connection management.

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { pbap } from '@kit.ConnectivityKit';
```

## BaseProfile

type BaseProfile = baseProfile.BaseProfile

**BaseProfile** class, which provides public capabilities such as obtaining the connection status and listening for connection status changes.

**System capability**: SystemCapability.Communication.Bluetooth.Core

| Type                            | Description         |
| ----------------------------- | ---------- |
| [baseProfile.BaseProfile](js-apis-bluetooth-baseProfile.md#baseprofile) | **BaseProfile** API definition. |

## pbap.createPbapServerProfile

createPbapServerProfile(): PbapServerProfile

Creates a [PSE](../../connectivity/bluetooth/terminology.md#pse) instance. Through this instance, you can use the local device as the PSE and implement functions such as obtaining the phone book service connection status between the local device and other devices. Typical use scenarios include the Bluetooth car kit accessing the phone book of a mobile phone and cross-device contacts synchronization, where the local device needs to function as the phone book server.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Return value**

| Type                            | Description         |
| ----------------------------- | ---------- |
|PbapServerProfile | PSE instance.<br>- The **PbapServerProfile** class is inherited from [BaseProfile](#baseprofile). Therefore, you can use the APIs in its parent class.<br>- The counterpart of the PSE role is the [PCE](../../connectivity/bluetooth/terminology.md#pce) role. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
|401 | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed.                 |
|801 | Capability not supported.          |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let pbapServerProfile = pbap.createPbapServerProfile();
    console.info('pbapServer success');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## pbap.createPbapClientProfile

createPbapClientProfile(): PbapClientProfile

Creates a [PCE](../../connectivity/bluetooth/terminology.md#pce) instance in the Phone Book Access Protocol. Through this instance, the local device can act as a PCE device and use the APIs provided, such as obtaining the phone book synchronization status and subscribing to phone book synchronization status change events. Typical use scenarios include an in-vehicle Bluetooth system acting as a PCE to access the phone book on a mobile device, cross-device contact synchronization, etc.

**Since:** 26.0.1

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type                            | Description         |
| ----------------------------- | ---------- |
|PbapClientProfile | PCE instance.<br>- This class inherits from [BaseProfile](#baseprofile). Therefore, methods from its parent class can be used.<br>- The counterpart of the PCE role is the [PSE](../../connectivity/bluetooth/terminology.md#pse) role. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
|801 | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported.        |

**Example**

```js
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let pbapClientProfile = pbap.createPbapClientProfile();
    console.info('pbapClient success');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```