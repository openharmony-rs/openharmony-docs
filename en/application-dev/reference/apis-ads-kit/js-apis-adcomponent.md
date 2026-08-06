# @ohos.advertising.AdComponent (Ad Component)

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @SukiEvas-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=ea2d8082679fb01eb444ae8d25a7681c82490ad7 translatedAt=2026-05-25T06:57:04.051Z pushedAt=2026-05-27T13:09:59.116Z -->

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

| **Parameter Name** | **Type** | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| ads | advertising.[Advertisement](js-apis-advertising.md#advertisement)[] | Yes | Array of ad objects.<br/>NOTE: For non-roll ad types, the component only displays the first data in the array.<br/>Atomic service API: This API can be used in atomic services since API version 12. |
| displayOptions | advertising.[AdDisplayOptions](js-apis-advertising.md#addisplayoptions) | Yes | Ad display parameters.<br/>Atomic service API: This API can be used in atomic services since API version 12. |
| interactionListener | advertising.[AdInteractionListener](js-apis-advertising.md#adinteractionlistener) | Yes | Callback for ad status changes.<br/>Atomic service API: This API can be used in atomic services since API version 12. |
| adRenderer<sup>12+</sup> | () =&gt; void | No | Application self-rendered ad style. The application self-rendered ad style is a restricted capability. For details, please consult [Traffic Monetization Official Website Customer Support](https://developer.huawei.com/consumer/en/doc/monetize/support-0000001061434261).<br/>Atomic service API: This API can be used in atomic services since API version 20.<br/>Decorator type: \@BuilderParam |
| rollPlayState<sup>15+</sup> | number | No | Used to provide the playback status of roll ads externally. Set to 1 for playing and 2 for paused. The default value is 2. Other values are invalid and do not change the previous playback status. The page where the roll ad is located needs to be associated with the property through \@State. For usage methods, refer to the [sample code](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ads-publisher-service-roll#section4281165885118).<br/>Atomic service API: This API can be used in atomic services since API version 20.<br/>Decorator type: \@Prop |

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