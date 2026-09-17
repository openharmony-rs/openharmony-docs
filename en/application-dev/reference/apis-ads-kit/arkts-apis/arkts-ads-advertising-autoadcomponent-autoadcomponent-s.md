# AutoAdComponent

The AutoAdComponent module provides the capability of displaying carousel ads.

**Since:** 11

**Decorator:** @Component

**System capability:** SystemCapability.Advertising.Ads

## Modules to Import

```TypeScript
import { AutoAdComponent } from '@kit.AdsKit';
```

## build

```TypeScript
build(): void
```

A constructor used to create an **AutoAdComponent** object.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## adOptions

```TypeScript
adOptions: advertising.AdOptions
```

Ad configuration options.

**Type:** [advertising.AdOptions](arkts-ads-advertising-adoptions-i.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## adParam

```TypeScript
adParam: advertising.AdRequestParams
```

Ad request parameters.

**Type:** [advertising.AdRequestParams](arkts-ads-advertising-adrequestparams-i.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## displayOptions

```TypeScript
displayOptions: advertising.AdDisplayOptions
```

Ad display parameters.

**Type:** [advertising.AdDisplayOptions](arkts-ads-advertising-addisplayoptions-i.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## interactionListener

```TypeScript
interactionListener: advertising.AdInteractionListener
```

Ad status change callback.

**Type:** [advertising.AdInteractionListener](arkts-ads-advertising-adinteractionlistener-i.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads
