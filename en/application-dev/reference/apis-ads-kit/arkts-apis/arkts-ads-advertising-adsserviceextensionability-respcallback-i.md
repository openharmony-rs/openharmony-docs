# RespCallback

Ad request callback.

**Since:** 11

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

**System capability:** SystemCapability.Advertising.Ads

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| respData | Map&lt;string, Array&lt;[advertising.Advertisement](arkts-ads-advertising-advertisement-t.md)&gt;&gt; | Yes | Callback data of ad requests. It is a mapping collection that takes ad unit ID as the key and stores acquired ad content. |
