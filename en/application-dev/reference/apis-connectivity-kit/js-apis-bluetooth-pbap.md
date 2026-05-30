# @ohos.bluetooth.pbap (Bluetooth PBAP Module)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @chengguohong; @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->

The **pbap** module implements phone book access capabilities based on the [Phone Book Access Profile (PBAP)](../../connectivity/terminology.md#pbap), such as obtaining the phone book service connection status.

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

| Type                           | Description        |
| ----------------------------- | ---------- |
| [baseProfile.BaseProfile](js-apis-bluetooth-baseProfile.md#baseprofile) | **BaseProfile** API definition.|

## pbap.createPbapServerProfile

createPbapServerProfile(): PbapServerProfile

Creates a [PSE](../../connectivity/terminology.md#pse) instance. Through this instance, you can use the local device as the PSE and implement functions such as obtaining the phone book service connection status.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Return value**

| Type                           | Description        |
| ----------------------------- | ---------- |
|PbapServerProfile | PSE instance.<br>- The **PbapServerProfile** class is inherited from [BaseProfile](#baseprofile). Therefore, you can use the APIs in its parent class.<br>- The counterpart of the PSE role is the [PCE](../../connectivity/terminology.md#pce) role.|

**Error codes**

For details about the error codes, see [Bluetooth Error Codes](errorcode-bluetoothManager.md).

| ID| Error Message|
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
