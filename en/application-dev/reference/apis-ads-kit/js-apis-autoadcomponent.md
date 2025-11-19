# @ohos.advertising.AutoAdComponent (Carousel Ad Component)

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @SukiEvas-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->

The AutoAdComponent module provides the capability of displaying carousel ads.

> **NOTE**<br>
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { AutoAdComponent } from '@kit.AdsKit';
```

## AutoAdComponent

AutoAdComponent({adParam: advertising.AdRequestParams, adOptions: advertising.AdOptions, displayOptions: advertising.AdDisplayOptions, interactionListener: advertising.AdInteractionListener})

**Decorator**: @Component

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| Name               | Type                                                                             | Mandatory| Description             |
|---------------------|-----------------------------------------------------------------------------------|-----|-----------------|
| adParam             | advertising.[AdRequestParams](js-apis-advertising.md#adrequestparams)             | Yes  | Ad request parameters.    |
| adOptions           | advertising.[AdOptions](js-apis-advertising.md#adoptions)                         | Yes  | Ad configuration options.    |
| displayOptions      | advertising.[AdDisplayOptions](js-apis-advertising.md#addisplayoptions)           | Yes  | Ad display parameters.    |
| interactionListener | advertising.[AdInteractionListener](js-apis-advertising.md#adinteractionlistener) | Yes  | Ad status change callback.|

### build

build(): void

A constructor used to create an **AutoAdComponent** object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

## Example

The sample code shows how to display a carousel ad.

```ts
import { advertising, AutoAdComponent } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  // Ad request parameters.
  private adRequestParams: advertising.AdRequestParams = {
    // Ad ID.
    adId: 'testw6vs28auh3',
    // Ad type.
    adType: 8
  };
  // Ad configuration options.
  private adOptions: advertising.AdOptions = {};
  // Ad display parameters.
  private adDisplayOptions: advertising.AdDisplayOptions = {
    // Interval at which the carousel items rotate, in ms. The value range is [30000, 120000].
    refreshTime: 30000
  };

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
        .height('100%')
    }
    .width('100%')
    .height('100%')
  }
}
```
