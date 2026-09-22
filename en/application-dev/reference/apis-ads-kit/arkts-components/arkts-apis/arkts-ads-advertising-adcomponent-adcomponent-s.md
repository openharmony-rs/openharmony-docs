# AdComponent

```TypeScript
declare struct AdComponent
```

This module provides the capability of displaying ads, covering native, roll, splash, and other ad styles.

> **NOTE:** 
> 
> To ensure that ads can be displayed correctly, this API must be used in conjunction with the ad request API.
> For effects and usage methods, refer to
> [Native Ads](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ads-publisher-service-native),
> [Roll Ads](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ads-publisher-service-roll),
> and [Splash Ads](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ads-publisher-service-splash)
> integration and display.

**Since:** 11

**Decorator:** @Component

**System capability:** SystemCapability.Advertising.Ads

## Modules to Import

```TypeScript
import { AdComponent } from '@kit.AdsKit';
```

## adRenderer

```TypeScript
adRenderer?: () => void
```

Application self-rendered ad style. The application self-rendered ad style is a restricted capability. For details, please consult [Traffic Monetization Official Website Customer Support](https://developer.huawei.com/consumer/en/doc/monetize/ support-0000001061434261).

**Since:** 12

**Decorator:** @BuilderParam

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Advertising.Ads

## build

```TypeScript
build(): void
```

A constructor used to create an **AdComponent** object.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## ads

```TypeScript
ads: advertising.Advertisement[]
```

Array of ad objects.

NOTE: For non-roll ad types, the component only displays the first data in the array.

**Type:** [advertising.Advertisement](arkts-ads-advertising-advertisement-t.md)[]

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

Callback for ad status changes.

**Type:** [advertising.AdInteractionListener](arkts-ads-advertising-adinteractionlistener-i.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Advertising.Ads

## rollPlayState

```TypeScript
rollPlayState?: number
```

Used to provide the playback status of roll ads externally. Set to 1 for playing and 2 for paused. The default value is 2. Other values are invalid and do not change the previous playback status. The page where the roll ad is located needs to be associated with the property through @State. For usage methods, refer to the [sample code](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ ads-publisher-service-roll#section4281165885118).

**Type:** number

**Since:** 15

**Decorator:** @Prop

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Advertising.Ads

**Examples**

```TypeScript
import { AdComponent, advertising } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  // Requested ad content
  private ads: advertising.Advertisement[] = [];
  // Ad display parameters
  private adDisplayOptions: advertising.AdDisplayOptions = {};

  build() {
    Column() {
      AdComponent({
        ads: this.ads,
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
        .height('100%')
    }
    .width('100%')
    .height('100%')
  }
}
```
