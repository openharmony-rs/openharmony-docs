# AdOptions

Defines the ad configuration.

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

Custom parameters.

&lt;!--RP1--&gt;&lt;!--RP1End--&gt;

**Type:** number &#124; boolean &#124; string &#124; undefined

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## adContentClassification

```TypeScript
adContentClassification?: string
```

Sets the maximum ad content rating.

W: ages 3+, all audiences. PI: ages 7+, parental guidance. J: ages 12+, teen. A: ages 16+/18+, adult audience.

If not set, the business logic prevails.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## nonPersonalizedAd

```TypeScript
nonPersonalizedAd?: number
```

Sets whether to request only non-personalized ads.

0: Request both personalized and non-personalized ads. 1: Request only non-personalized ads.

If not set, the business logic prevails.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## tagForChildProtection

```TypeScript
tagForChildProtection?: number
```

Whether you want your content to be treated as child-directed for purposes of COPPA.

-1: Default value, unspecified. 0: No. 1: Yes.

The default value is -1.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads
