# AdsServiceExtensionAbility (System API)

```TypeScript
export default class AdsServiceExtensionAbility
```

Provides the capability of integrating advertising services with vendors.

**Since:** 11

<!--Device-unnamed-export default class AdsServiceExtensionAbility--><!--Device-unnamed-export default class AdsServiceExtensionAbility-End-->

**System capability:** SystemCapability.Advertising.Ads

**System API:** This is a system API.

## ExtensionAbility Usage Restrictions

To ensure system security and stability, AdsServiceExtensionAbility is restricted from abusing system resources. The system controls its capabilities and does not support referencing some modules. For details, see [Appendix](#appendix).

## Modules to Import

```TypeScript
import { AdsServiceExtensionAbility, RespCallback } from '@kit.AdsKit';
```

## onLoadAd

```TypeScript
onLoadAd(adParam: advertising.AdRequestParams, adOptions: advertising.AdOptions, respCallback: RespCallback)
```

Called when the media application starts to load an ad. The device vendor needs to implement the ad request service logic in this API and send the result to the media application through a call back.

**Since:** 11

<!--Device-AdsServiceExtensionAbility-onLoadAd(adParam: advertising.AdRequestParams, adOptions: advertising.AdOptions, respCallback: RespCallback)--><!--Device-AdsServiceExtensionAbility-onLoadAd(adParam: advertising.AdRequestParams, adOptions: advertising.AdOptions, respCallback: RespCallback)-End-->

**System capability:** SystemCapability.Advertising.Ads

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| adParam | [advertising.AdRequestParams](arkts-ads-advertising-adrequestparams-i.md) | Yes | Ad request parameters. |
| adOptions | [advertising.AdOptions](arkts-ads-advertising-adoptions-i.md) | Yes | Ad configuration options. |
| respCallback | [RespCallback](arkts-ads-advertising-adsserviceextensionability-respcallback-i.md) | Yes | Ad request callback. |

<!--Del-->
**Examples**

```TypeScript
import { AdsServiceExtensionAbility, advertising, RespCallback } from '@kit.AdsKit';

export default class AdsExtensionAbility extends AdsServiceExtensionAbility {
  onLoadAd(adParam: advertising.AdRequestParams, adOptions: advertising.AdOptions, respCallback: RespCallback) {
    const respData: Map<string, Array<advertising.Advertisement>> = new Map();
    // Set the returned ad data.
    // ...
    respCallback(respData);
  }
}
```

<!--DelEnd-->

## onLoadAdWithMultiSlots

```TypeScript
onLoadAdWithMultiSlots(adParams: advertising.AdRequestParams[], adOptions: advertising.AdOptions, 
    respCallback: RespCallback)
```

Called when the media application starts to load multiple ads. The device vendor needs to implement the ad request service logic in this API and send the result to the media application through a call back.

**Since:** 11

<!--Device-AdsServiceExtensionAbility-onLoadAdWithMultiSlots(adParams: advertising.AdRequestParams[], adOptions: advertising.AdOptions,     respCallback: RespCallback)--><!--Device-AdsServiceExtensionAbility-onLoadAdWithMultiSlots(adParams: advertising.AdRequestParams[], adOptions: advertising.AdOptions,     respCallback: RespCallback)-End-->

**System capability:** SystemCapability.Advertising.Ads

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| adParams | [advertising.AdRequestParams](arkts-ads-advertising-adrequestparams-i.md)[] | Yes | Ad request parameters. |
| adOptions | [advertising.AdOptions](arkts-ads-advertising-adoptions-i.md) | Yes | Ad configuration options. |
| respCallback | [RespCallback](arkts-ads-advertising-adsserviceextensionability-respcallback-i.md) | Yes | Ad request callback. |

<!--Del-->
**Examples**

```TypeScript
import { AdsServiceExtensionAbility, advertising, RespCallback } from '@kit.AdsKit';

export default class AdsExtensionAbility extends AdsServiceExtensionAbility {
  onLoadAdWithMultiSlots(adParams: advertising.AdRequestParams[], adOptions: advertising.AdOptions,
    respCallback: RespCallback) {
    const respData: Map<string, Array<advertising.Advertisement>> = new Map();
    // Set the returned ad data.
    // ...
    respCallback(respData);
  }
}
```

<!--DelEnd-->

## Appendix

AdsServiceExtensionAbility does not support referencing the following modules.

| Kit | Module |
| --- | --- |
| Camera Kit | [@ohos.multimedia.camera](../../apis-camera-kit/arkts-apis/arkts-camera-multimedia-camera.md) |
| Telephony Kit | [@ohos.telephony.sim](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sim.md) |
| Telephony Kit | [@ohos.telephony.sms](../../apis-telephony-kit/arkts-apis/arkts-telephony-telephony-sms.md) |
| Contacts Kit | [@ohos.contact](../../apis-contacts-kit/arkts-apis/arkts-contacts-contact.md) |
