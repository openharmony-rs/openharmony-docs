# AdRequestParams

```TypeScript
export interface AdRequestParams
```

Defines the ad request parameters.

**Since:** 11

**System capability:** SystemCapability.Advertising.Ads

## Modules to Import

```TypeScript
import { advertising } from '@kit.AdsKit';
```

## [key: string]

```TypeScript
[key: string]: number | boolean | string | undefined
```

Custom parameter.

&lt;!--RP2--&gt;&lt;!--RP2End--&gt;

**Type:** number &#124; boolean &#124; string &#124; undefined

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## adCount

```TypeScript
adCount?: number
```

Number of ads requested. If not set, the business logic prevails.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## adHeight

```TypeScript
adHeight?: number
```

Expected creative height when requesting an ad, in vp (mandatory for banner ads). If not set, the business logic prevails.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## adId

```TypeScript
adId: string
```

Ad slot ID.

Note: The getAdRequestBody API can omit this parameter.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## adSearchKeyword

```TypeScript
adSearchKeyword?: string
```

Ad keyword. Defaults to "" if not set.

Note: Not supported for use currently.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## adType

```TypeScript
adType?: number
```

Requested ad type.

- 1: Splash ad.  
- 3: Native ad.  
- 7: Rewarded ad.  
- 8: Banner ad.  
- 12: Interstitial ad  
- 60: Roll ad.

If not set, the default is the native ad type.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## adWidth

```TypeScript
adWidth?: number
```

Expected creative width when requesting an ad, in vp (mandatory for banner ads). If not set, the business logic prevails.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads
