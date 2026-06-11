# Advertisement

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @SukiEvas-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=ea2d8082679fb01eb444ae8d25a7681c82490ad7 translatedAt=2026-05-25T06:56:43.151Z pushedAt=2026-05-27T13:10:03.735Z -->

This module provides the requested ad content.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```typescript
import { advertising } from '@kit.AdsKit';
```

## Advertisement

The requested ad content.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

| Name              | Type                     | Read-Only| Optional| Description                                                                                                                   |
|--------------------|---------------------------|-----|-----|-----------------------------------------------------------------------------------------------------------------------|
| adType | number | No | No | Ad type.<br/>- 1: Splash ad.<br/>- 3: Native ad.<br/>- 7: Rewarded ad.<br/>- 8: Banner ad.<br/>- 12: Interstitial ad.<br/>- 60: Roll ad.<br/>If not filled, the default is native ad type. |
| uniqueId           | string                    | No  | No  | Unique ID of the ad.                                                                                                          |
| rewarded           | boolean                   | No  | No  | Whether users get rewarded for watching or clicking the ad.<br>- **true**: Users get rewarded.<br>- **false**: Users do not get rewarded.                                                       |
| shown              | boolean                   | No  | No  | Whether the ad is shown.<br>- **true**: The ad is shown.<br>- **false**: The ad is not shown.                                                                     |
| clicked            | boolean                   | No  | No  | Whether the ad is clicked.<br>- **true**: The ad is clicked.<br>- **false**: The ad is not clicked.                                                               |
| rewardVerifyConfig | Map&lt;string, string&gt; | No | No | Server verification parameters.<br/>{<br/>customData: "test",<br/>userId: "12345"<br/>} |
| [key: string] | Object | No | Yes | Custom parameters.<br/><!--RP1--><!--RP1End--> |