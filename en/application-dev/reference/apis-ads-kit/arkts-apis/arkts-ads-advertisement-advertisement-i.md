# Advertisement

```TypeScript
export interface Advertisement
```

This module provides the requested ad content.

**Since:** 11

**System capability:** SystemCapability.Advertising.Ads

## [key:string]

```TypeScript
[key:string]: Object
```

Custom parameters.

&lt;!--RP1--&gt;&lt;!--RP1End--&gt;

**Type:** Object

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## adType

```TypeScript
adType: number
```

Ad type.

- 1: Splash ad.  
- 3: Native ad.  
- 7: Rewarded ad.  
- 8: Banner ad.  
- 12: Interstitial ad.  
- 60: Roll ad.

If not filled, the default is native ad type.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## clicked

```TypeScript
clicked: boolean
```

Whether the ad is clicked.

- **true**: The ad is clicked.  
- **false**: The ad is not clicked.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## rewarded

```TypeScript
rewarded: boolean
```

Whether users get rewarded for watching or clicking the ad.

- **true**: Users get rewarded.  
- **false**: Users do not get rewarded.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## rewardVerifyConfig

```TypeScript
rewardVerifyConfig: Map<string, string>
```

Server verification parameters.

{

customData: "test",

userId: "12345"

}

**Type:** Map&lt;string, string&gt;

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

**Test API:** This API is used only in automated test scripts.

## shown

```TypeScript
shown: boolean
```

Whether the ad is shown.

- **true**: The ad is shown.  
- **false**: The ad is not shown.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## uniqueId

```TypeScript
uniqueId: string
```

Unique ID of the ad.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads
