# RespCallback

```TypeScript
export interface RespCallback
```

Ad request callback.

**Since:** 11

<!--Device-unnamed-export interface RespCallback--><!--Device-unnamed-export interface RespCallback-End-->

**System capability:** SystemCapability.Advertising.Ads

## Modules to Import

```TypeScript
import { AdsServiceExtensionAbility, RespCallback } from '@kit.AdsKit';
```

## [[Call]]

```TypeScript
(respData: Map<string, Array<advertising.Advertisement>>): void
```

Data in the ad request callback.

**Since:** 11

<!--Device-RespCallback-(respData: Map<string, Array<advertising.Advertisement>>): void--><!--Device-RespCallback-(respData: Map<string, Array<advertising.Advertisement>>): void-End-->

**System capability:** SystemCapability.Advertising.Ads

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| respData | Map&lt;string, Array&lt;[advertising.Advertisement](arkts-ads-advertising-advertisement-t.md)&gt;&gt; | Yes | Callback data of ad requests. It is a mapping collection that takes ad unit ID as the key and stores acquired ad content. |

**Examples**

```TypeScript
import { advertising, RespCallback } from '@kit.AdsKit';

function setRespCallback(respCallback: RespCallback) {
  const respData: Map<string, Array<advertising.Advertisement>> = new Map();
  // Set the returned ad data.
  // ...
  respCallback(respData);
}
```
