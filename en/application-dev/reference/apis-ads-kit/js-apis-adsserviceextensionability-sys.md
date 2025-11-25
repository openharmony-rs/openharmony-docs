# @ohos.advertising.AdsServiceExtensionAbility (ExtensionAbility for Ads) (System API)

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @SukiEvas-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->

The AdsServiceExtensionAbility module provides ExtensionAbilities for the ads service. Device vendors can implement the service logic of requesting one or multiple ads.

> **NOTE**<br>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.<br>
> - The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { AdsServiceExtensionAbility } from '@kit.AdsKit';
```

## AdsServiceExtensionAbility.onLoadAd

onLoadAd(adParam: advertising.AdRequestParams, adOptions: advertising.AdOptions, respCallback: RespCallback)

Called when the media application starts to load an ad. The device vendor needs to implement the ad request service logic in this API and send the result to the media application through a call back.

**System API**: This is a system API.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| Name      | Type                                                                 | Mandatory| Description         |
|--------------|-----------------------------------------------------------------------|-----|-------------|
| adParam      | advertising.[AdRequestParams](js-apis-advertising.md#adrequestparams) | Yes  | Ad request parameters.|
| adOptions    | advertising.[AdOptions](js-apis-advertising.md#adoptions)             | Yes  | Ad configuration options.|
| respCallback | [RespCallback](js-apis-adsserviceextensionability.md#respcallback)    | Yes  | Ad request callback.|

**Example**

```ts
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

## AdsServiceExtensionAbility.onLoadAdWithMultiSlots

onLoadAdWithMultiSlots(adParams: advertising.AdRequestParams[], adOptions: advertising.AdOptions, respCallback: RespCallback)

Called when the media application starts to load multiple ads. The device vendor needs to implement the ad request service logic in this API and send the result to the media application through a call back.

**System API**: This is a system API.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| Name      | Type                                                                   | Mandatory| Description         |
|--------------|-------------------------------------------------------------------------|-----|-------------|
| adParams     | advertising.[AdRequestParams](js-apis-advertising.md#adrequestparams)[] | Yes  | Ad request parameters.|
| adOptions    | advertising.[AdOptions](js-apis-advertising.md#adoptions)               | Yes  | Ad configuration options.|
| respCallback | [RespCallback](js-apis-adsserviceextensionability.md#respcallback)      | Yes  | Ad request callback.|

**Example**

```ts
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
