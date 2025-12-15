# @ohos.advertising.AdComponent (Ad Component)

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @SukiEvas-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->

This module provides the capability of displaying ads.

> **NOTE**<br>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { AdComponent } from '@kit.AdsKit';
```

## AdComponent

AdComponent({ads: advertising.Advertisement[], displayOptions: advertising.AdDisplayOptions, interactionListener: advertising.AdInteractionListener, @BuilderParam adRenderer?: () => void, @Prop rollPlayState?: number})

**Decorator**: @Component

**System capability**: SystemCapability.Advertising.Ads

**Parameters**

| Name                       | Type                                                                             | Mandatory| Decorator   | Description                                                                                                                                                                                                 |
|-----------------------------|-----------------------------------------------------------------------------------|------|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ads                         | advertising.[Advertisement](js-apis-advertising.md#advertisement)[]               | Yes  | -             | Array of ad objects.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                                                                           |
| displayOptions              | advertising.[AdDisplayOptions](js-apis-advertising.md#addisplayoptions)           | Yes  | -             | Ad display parameters.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                                                                           |
| interactionListener         | advertising.[AdInteractionListener](js-apis-advertising.md#adinteractionlistener) | Yes  | -             | Ad status change callback.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                                                                                                       |
| adRenderer<sup>12+</sup>    | () => void                                                                        | No  | @BuilderParam | Ad self-rendering.<br>**Atomic service API**: This API can be used in atomic services since API version 20.                                                                                                     |
| rollPlayState<sup>15+</sup> | number                                                                            | No  | @Prop         | Roll ad state. The value **1** means that the roll ad is playing, and the value **2** (default) means that the roll ad is paused. Other values are invalid and the previous playback state is not changed.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

### build

build(): void

A constructor used to create an **AdComponent** object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Advertising.Ads

## Example

The sample code shows how to display an ad.

```ts
import { AdComponent, advertising } from '@kit.AdsKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

@Entry
@Component
struct Index {
  // Requested ad content.
  private ads: advertising.Advertisement[] = [];
  // Ad display parameters.
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
