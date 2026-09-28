# @ohos.advertising.AdComponent (Ad Component)

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @ctssss-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=3af2c2640a0dfa1285ceb6197505adab556ff3bb translatedAt=2026-09-02T02:13:45.817Z pushedAt=2026-09-02T09:34:14.199Z -->


This module provides the capability of displaying ads, covering native, roll, splash, and other ad styles.


> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```typescript
import { AdComponent } from '@kit.AdsKit';
```


## AdComponent

```typescript
AdComponent({
  ads: advertising.Advertisement[], 
  displayOptions: advertising.AdDisplayOptions,
  interactionListener: advertising.AdInteractionListener,
  @BuilderParam adRenderer?: () => void,   
  @Prop rollPlayState?: number
})
```

Ad display component, which provides the capability of displaying native, roll, splash, and other ads.

**Decorator type:** \@Component

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| **Name** | **Type** | Mandatory | **Decorator Type** | Description |
| -------- | -------- | -------- | -------- | -------- |
| ads | advertising.[Advertisement](js-apis-advertisement.md#advertisement)[] | Yes | - | Array of ad objects.<br/>Note: For non-roll ad types, the component displays only the first item in the array.<br/>Atomic service API: This API can be used in atomic services since API version 12. |
| displayOptions | advertising.[AdDisplayOptions](js-apis-advertising.md#addisplayoptions) | Yes | - | Ad display parameters.<br/>Atomic service API: This API can be used in atomic services since API version 12. |
| interactionListener | advertising.[AdInteractionListener](js-apis-advertising.md#adinteractionlistener) | Yes | - | Callback for ad status changes.<br/>Atomic service API: This API can be used in atomic services since API version 12. |
| adRenderer<sup>12+</sup> | () =&gt; void | No | \@BuilderParam | Application self-rendered ad style. The application self-rendered ad style is a restricted capability. For details, contact Traffic Monetization Official Website Customer Support.<br/>Atomic service API: This API can be used in atomic services since API version 20. |
| rollPlayState<sup>15+</sup> | number | No | \@Prop | Provides the roll ad playback state externally. Set 1 for playing and 2 for paused. The default value is 2. Other values are invalid and do not change the previous playback state. On the page where the roll ad is located, associate the attribute through \@State. For usage, refer to [Sample Code](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ads-publisher-service-roll#displaying-an-ad).<br/>Atomic service API: This API can be used in atomic services since API version 20. |

> **NOTE**
>
> To ensure that ads can be displayed correctly, this API must be used in conjunction with the ad request API. For effects and usage methods, refer to [Native Ads](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ads-publisher-service-native), [Roll Ads](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ads-publisher-service-roll), and [Splash Ads](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ads-publisher-service-splash) integration and display.

**Example:**

```typescript
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


### build


build(): void


A constructor used to create an **AdComponent** object.


**Atomic service API:** This API can be used in atomic services since API version 12.


**System capability**: SystemCapability.Advertising.Ads
