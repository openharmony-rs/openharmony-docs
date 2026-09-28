# Advertisement (Content of the Requested Ad)
<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @ctssss-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=3af2c2640a0dfa1285ceb6197505adab556ff3bb translatedAt=2026-09-02T02:13:38.204Z pushedAt=2026-09-03T07:24:13.603Z -->


This module provides the requested advertisement content.


> **NOTE**
> 
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```typescript
import { advertising } from '@kit.AdsKit';
```

## Advertisement

Requested advertisement content.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

| Name | Type | Read-Only | Optional | Description | 
| -------- | -------- | -------- | -------- | -------- |
| adType | number | No | No | Advertisement type.<br/>- 1: splash ad.<br/>- 3: native ad.<br/>- 7: rewarded ad.<br/>- 8: banner ad.<br/>- 12: interstitial ad.<br/>- 60: patch ad.<br/>If not specified, the native ad type is used by default. | 
| uniqueId | string | No | No | Unique identifier of the advertisement. | 
| rewarded | boolean | No | No | Whether the advertisement is rewarded.<br/>- true: rewarded.<br/>- false: not rewarded. | 
| shown | boolean | No | No | Whether the advertisement is displayed.<br/>- true: displayed.<br/>- false: not displayed. | 
| clicked | boolean | No | No | Whether the advertisement is clicked.<br/>- true: clicked.<br/>- false: not clicked. | 
| rewardVerifyConfig | Map&lt;string, string&gt; | No | No | Server verification parameters.<br/>{<br/>customData: "test",<br/>userId: "12345"<br/>} | 
| [key: string] | Object | No | Yes | Custom parameters.<br/><!--RP1--><!--RP1End--> | 