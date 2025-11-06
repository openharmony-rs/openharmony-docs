# @ohos.advertising.AdsServiceExtensionAbility (ExtensionAbility for Ads)

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @SukiEvas-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->

The AdsServiceExtensionAbility module provides ExtensionAbilities for the ads service. Device vendors can implement the callbacks for ads requests.

> **NOTE**<br>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { RespCallback } from '@kit.AdsKit';
```

## RespCallback

### (respData: Map&lt;string, Array&lt;advertising.Advertisement&gt;&gt;)

(respData: Map&lt;string, Array&lt;advertising.Advertisement&gt;&gt;): void

Ad request callback.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| Name  | Type                                                                                             | Mandatory| Description             |
|----------|---------------------------------------------------------------------------------------------------|-----|-----------------|
| respData | Map&lt;string, Array&lt;advertising.[Advertisement](js-apis-advertising.md#advertisement)&gt;&gt; | Yes  | Data in the ad request callback.|

**Example**

```ts
import { advertising, RespCallback } from '@kit.AdsKit';

function setRespCallback(respCallback: RespCallback) {
  const respData: Map<string, Array<advertising.Advertisement>> = new Map();
  // Set the returned ad data.
  // ...
  respCallback(respData);
}
```
