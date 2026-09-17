# AdsServiceExtensionAbility (System API)

Provides the capability of integrating advertising services with vendors.

**Since:** 11

**System capability:** SystemCapability.Advertising.Ads

**System API:** This is a system API.

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

**System capability:** SystemCapability.Advertising.Ads

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| adParam | [advertising.AdRequestParams](arkts-ads-advertising-adrequestparams-i.md) | Yes | Ad request parameters. |
| adOptions | [advertising.AdOptions](arkts-ads-advertising-adoptions-i.md) | Yes | Ad configuration options. |
| respCallback | [RespCallback](arkts-ads-advertising-adsserviceextensionability-respcallback-i.md) | Yes | Ad request callback. |

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

## onLoadAdWithMultiSlots

```TypeScript
onLoadAdWithMultiSlots(adParams: advertising.AdRequestParams[], adOptions: advertising.AdOptions, 
    respCallback: RespCallback)
```

Called when the media application starts to load multiple ads. The device vendor needs to implement the ad request service logic in this API and send the result to the media application through a call back.

**Since:** 11

**System capability:** SystemCapability.Advertising.Ads

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| adParams | [advertising.AdRequestParams](arkts-ads-advertising-adrequestparams-i.md)[] | Yes | Ad request parameters. |
| adOptions | [advertising.AdOptions](arkts-ads-advertising-adoptions-i.md) | Yes | Ad configuration options. |
| respCallback | [RespCallback](arkts-ads-advertising-adsserviceextensionability-respcallback-i.md) | Yes | Ad request callback. |

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
