# @ohos.bluetooth.hfp (Bluetooth HFP Module)

<!--Kit: Connectivity Kit-->
<!--Subsystem: Communication-->
<!--Owner: @enjoy_sunshine-->
<!--Designer: @tangjia15-->
<!--Tester: @wangfeng517-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=1275b89181ca8fc1862130ee865235369b412dd3 translatedAt=2026-09-15T02:44:24.831Z pushedAt=2026-09-16T03:25:18.539Z -->

This module provides the Bluetooth call audio capability based on the [Hands-Free Profile (HFP)](../../connectivity/bluetooth/terminology.md#hfp), such as creating [HFP AG](../../connectivity/bluetooth/terminology.md#hfp-ag) and [HF](../../connectivity/bluetooth/terminology.md#hf) instances and obtaining the call audio connection status. This module is applicable to scenarios where Bluetooth call audio connection management and call audio connection status monitoring need to be implemented.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { hfp } from '@kit.ConnectivityKit';
```

## BaseProfile

type BaseProfile = baseProfile.BaseProfile

**BaseProfile** class, which provides public capabilities such as obtaining the connection status and listening for connection status changes.

**System capability**: SystemCapability.Communication.Bluetooth.Core

| Type                           | Description        |
| ----------------------------- | ---------- |
| [baseProfile.BaseProfile](js-apis-bluetooth-baseProfile.md#baseprofile) | **BaseProfile** API definition.|

## hfp.createHfpAgProfile

createHfpAgProfile(): HandsFreeAudioGatewayProfile

Creates an [HFP AG](../../connectivity/bluetooth/terminology.md#hfp-ag) instance. Through this instance, you can use the local device as the HFP AG and implement functions such as obtaining the Bluetooth call audio connection status. Typical use scenarios include the Bluetooth call function of the in-vehicle infotainment (IVI) system. The local device functions as the audio gateway (AG) to manage the call audio route.

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Return value**

| Type                           | Description        |
| ----------------------------- | ---------- |
| [HandsFreeAudioGatewayProfile](#handsfreeaudiogatewayprofile) | HFP AG instance, which can be used to obtain the Bluetooth call audio connection status with other devices. |

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
    let hfpAgProfile = hfp.createHfpAgProfile();
    console.info('hfpAg success');
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```


## hfp.createHfpHfProfile

createHfpHfProfile(): HandsFreeHfProfile

Creates an [HF](../../connectivity/bluetooth/terminology.md#hf) instance. Through this instance, you can use the local device as the HF and implement functions such as obtaining the Bluetooth call audio connection status. Typical use scenarios include the hands-free call function of Bluetooth earphones and the in-vehicle hands-free call system. The local device functions as the hands-free (HF) role to receive and process call audio.

**Since:** 26.0.0

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.

**Return value**

| Type                            | Description         |
| ----------------------------- | ---------- |
| [HandsFreeHfProfile](#handsfreehfprofile) | HF instance, which can be used to obtain the Bluetooth call audio connection status with other devices. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| -------- | ---------------------------- |
|801 | Capability not supported.          |

**Example**

```js
try {
    let hfProfile = hfp.createHfpHfProfile();
    console.info('hf success');
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```


## HandsFreeAudioGatewayProfile

Represents the [HFP AG](../../connectivity/bluetooth/terminology.md#hfp-ag) role in Bluetooth call audio.
- The **HandsFreeAudioGatewayProfile** class is inherited from [BaseProfile](#baseprofile). Therefore, you can use the APIs in its parent class.
- Before using the APIs of this class, you need to construct an HFP AG instance by calling [createHfpAgProfile](#hfpcreatehfpagprofile).
- The counterpart of the HFP AG role is the [HF](../../connectivity/bluetooth/terminology.md#hf) role.

**System capability**: SystemCapability.Communication.Bluetooth.Core


## HandsFreeHfProfile

Represents the [HF](../../connectivity/bluetooth/terminology.md#hf) role in Bluetooth call audio.
- This class is inherited from [BaseProfile](#baseprofile). Therefore, you can use the APIs in its parent class.
- Before using the APIs of this class, you need to construct an instance of this class by calling [createHfpHfProfile](#hfpcreatehfphfprofile).
- The counterpart of the HF role is the [HFP AG](../../connectivity/bluetooth/terminology.md#hfp-ag) role.

**Since:** 26.0.0

**System capability**: SystemCapability.Communication.Bluetooth.Core

**Model restriction:** This API can be used only in the stage model.
