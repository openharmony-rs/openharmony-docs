# AutoAdComponent

```TypeScript
declare struct AutoAdComponent
```

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

**Examples**

```TypeScript
import { advertising, AutoAdComponent } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  // Ad request parameters.
  private adRequestParams: advertising.AdRequestParams = {
    // Ad ID.
    adId: 'h5xkz3mbr2',
    // Ad type.
    adType: 8,
    // Ad slot width, in vp.
    adWidth: 360,
    // Ad slot height, in vp.
    adHeight: 57
  };
  // Ad configuration options.
  private adOptions: advertising.AdOptions = {};
  // Ad display parameters.
  private adDisplayOptions: advertising.AdDisplayOptions = {
    // Interval at which the carousel items rotate, in ms. The value range is [30000, 120000].
    refreshTime: 30000
  };
  private ratio: number = -1;

  aboutToAppear() {
    if (this.adRequestParams.adWidth && this.adRequestParams.adHeight) {
      this.ratio = this.adRequestParams.adWidth / this.adRequestParams.adHeight;
    }
  }
  
  build() {
    Column() {
      AutoAdComponent({
        adParam: this.adRequestParams,
        adOptions: this.adOptions,
        displayOptions: this.adDisplayOptions,
        interactionListener: {
          onStatusChanged: (status: string, ad: advertising.Advertisement, data: string) => {
            switch (status) {
              case 'onAdOpen':
                hilog.info(0x0000, 'testTag', 'onAdOpen');
                break;
              case 'onAdClick':
                hilog.info(0x0000, 'testTag', 'onAdClick');
                break;
              case 'onAdClose':
                hilog.info(0x0000, 'testTag', 'onAdClose');
                break;
            }
          }
        }
      })
        .width('100%')
        .aspectRatio(this.ratio)
    }
    .width('100%')
    .height('100%')
  }
}
```
