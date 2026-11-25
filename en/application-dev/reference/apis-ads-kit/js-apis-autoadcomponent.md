# @ohos.advertising.AutoAdComponent (Carousel Ad Component)
<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @ctssss-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=3be691bf73bee527113c7ef6168ff4e2f7d57541 translatedAt=2026-11-23T09:12:46.529Z pushedAt=2026-11-24T09:09:27.614Z nl=1 -->


The AutoAdComponent module provides the capability of displaying carousel ads.


> **NOTE**
> 
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```typescript
import { AutoAdComponent } from '@kit.AdsKit';
```


## AutoAdComponent

```typescript
AutoAdComponent({
  adParam: advertising.AdRequestParams,
  adOptions: advertising.AdOptions,
  displayOptions: advertising.AdDisplayOptions,  
  interactionListener: advertising.AdInteractionListener  
})  
```
Component used to display carousel ads.

**Decorator**: \@Component

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| **Name** | **Type** | Mandatory | **Decorator** | Description | 
| -------- | -------- | -------- | -------- | -------- |
| adParam | advertising.[AdRequestParams](js-apis-advertising.md#adrequestparams) | Yes | - | Ad request parameters. | 
| adOptions | advertising.[AdOptions](js-apis-advertising.md#adoptions) | Yes | - | Ad configuration parameters. | 
| displayOptions | advertising.[AdDisplayOptions](js-apis-advertising.md#addisplayoptions) | Yes | - | Ad display parameters. | 
| interactionListener | advertising.[AdInteractionListener](js-apis-advertising.md#adinteractionlistener) | Yes | - | Callback for ad status changes. |

### build

build(): void

A constructor used to create an **AutoAdComponent** object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

## Example

```typescript
import { advertising, AutoAdComponent } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  // Ad request parameter.
  private adRequestParams: advertising.AdRequestParams = {
    // Ad slot ID.
    adId: 'h5xkz3mbr2',
    // Ad type.
    adType: 8,
    // Ad slot width, unit vp.
    adWidth: 360,
    // Ad slot height, unit vp.
    adHeight: 57
  };
  // Ad configuration parameter.
  private adOptions: advertising.AdOptions = {};
  // Ad display parameter.
  private adDisplayOptions: advertising.AdDisplayOptions = {
    // Ad carousel time interval, unit ms, value range [30000, 120000].
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
