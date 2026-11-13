# ProgressButtonV2
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangwentao96-->
<!--Designer: @song-song-song-->
<!--Tester: @ybhou1993-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=42500bbbc602d56c8fbfa6bd5fe37a6d7cf3a324 translatedAt=2026-11-03T01:32:45.447Z pushedAt=2026-11-13T01:05:59.872Z nl=1 -->


The **ProgressButtonV2** component is a text-based download button with a progress indicator that shows the download progress.

This component is implemented based on [state management V2](../../../ui/state-management/arkts-state-management-overview.md#state-management-v2). Compared with [state management V1](../../../ui/state-management/arkts-state-management-overview.md#state-management-v1), V2 offers a higher level of observation and management over data objects beyond the component level. You can now more easily manage download button data and states with greater flexibility, leading to faster UI updates.


> **NOTE**
>
> - This component is supported since API version 18. Newly added content in later versions will be marked with a superscript to indicate the version in which it was introduced.
>
> - The APIs of this module can be used only in the stage model.
>
> - If [universal attributes](ts-component-general-attributes.md) or [universal events](ts-component-general-events.md) are set for **ProgressButtonV2**, the compilation toolchain additionally generates a node named **\_\_Common\_\_** and mounts the universal attributes or universal events on **\_\_Common\_\_** instead of applying them directly to **ProgressButtonV2** itself. This may cause the universal attributes or universal events set by developers to not take effect or to behave unexpectedly. Therefore, it is not recommended to set universal attributes and universal events for **ProgressButtonV2**.


## Modules to Import

``` ts
import { ColorMetrics, LengthMetrics, ProgressButtonV2, ProgressButtonV2Color } from '@kit.ArkUI';
```

## ProgressButtonV2

ProgressButtonV2({progress: number, content: ResourceStr, progressButtonWidth?: LengthMetrics, onClicked: ClickCallback, isEnabled: boolean, colorOptions?: ProgressButtonV2Color, progressButtonRadius?: LengthMetrics})

Creates a text-based download button with a progress indicator that shows the download progress.

**Decorator**: \@ComponentV2

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name                               | Type                                                           | Mandatory| Decorator                 | Description                                                                        |
|-----------------------------------|---------------------------------------------------------------|----|------------------------|----------------------------------------------------------------------------|
| progress                          | number                                                        | Yes | \@Require <br>\@Param | Current download progress.<br>The value range is [0, 100]. Values less than 0 are adjusted to **0**, and values greater than 100 are capped at **100**.<br>Default value: **0**      |
| content                           | [ResourceStr](ts-types.md#resourcestr)                        | Yes | \@Require <br>\@Param | Button text.                                                                  |
| progressButtonWidth               | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No | \@Param <br>\@Once  | Width of the button.<br>Default value: **44vp**                                                     |
| onClicked                         | [ClickCallback](#clickcallback)                               | Yes | \@Param                | Callback invoked when the button is clicked.                                                                |
| isEnabled                         | boolean                                                       | Yes | \@Param                | Whether the button can be clicked.<br> **true**: yes<br> **false**: no      |
| colorOptions                      | [ProgressButtonV2Color](#progressbuttonv2color)               | No | \@Param                | Color options for the button.                                                     |
| progressButtonRadius | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No  | \@Param                | Corner radius of the download button (percentage setting is not supported).<br/>Value range: [0, height/2]<br/>Default value: height/2<br/>If an invalid value is set, the default value is used. |

## ClickCallback

type ClickCallback = () => void

Callback invoked when the button is clicked.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

## ProgressButtonV2Color
Defines the color options for the download button.

**Decorator type**: \@ObservedV2

### Properties

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name             | Type          | Read-Only| Optional| Description                        |
|-----------------|--------------|---|----|----------------------------|
| progressColor   | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12) | No| Yes| Color of the progress indicator.<br>Default value: **#330A59F7**<br>Decorator type: @Trace |
| borderColor     | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12) | No| Yes| Border color of the button.<br>Default value: **#330A59F7**<br>Decorator type: @Trace|
| textColor       | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12) | No| Yes| Text color of the button.<br>Default value: system default value **#CE000000**<br>Decorator type: @Trace|
| backgroundColor | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12) | No| Yes| Background color of the button.<br>Default value: **\$r('sys.color.ohos_id_color_foreground_contrary')**<br>Decorator type: @Trace|

### constructor
constructor(options: ProgressButtonV2ColorOptions);

A constructor used to create a **ProgressButtonV2Color** object.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name      | Type                                                           | Mandatory| Description   |
|---------|---------------------------------------------------------------|----|-------|
| options | [ProgressButtonV2ColorOptions](#progressbuttonv2coloroptions) | Yes | Color settings.|

## ProgressButtonV2ColorOptions

Provides options for customizing the color of the download button.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name             | Type          | Read-Only| Optional| Description                                                                |
|-----------------|--------------|---|---|--------------------------------------------------------------------|
| progressColor   | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)| No| Yes| Color of the progress indicator.<br>Default value: **#330A59F7**                                          |
| borderColor     | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)| No| Yes| Border color of the button.<br>Default value: **#330A59F7**                                         |
| textColor       | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)| No| Yes| Text color of the button.<br>Default value: system default value **#CE000000**                                  |
| backgroundColor | [ColorMetrics](../js-apis-arkui-graphics.md#colormetrics12)| No| Yes| Background color of the button.<br>Default value: **\$r('sys.color.ohos_id_color_foreground_contrary')**|

## Example

This example demonstrates how to create a simple download button with a progress indicator that shows the loading status of a text file.
```ts
import { LengthMetrics, ProgressButtonV2 } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local progressIndex: number = 0;
  @Local textState: string = 'Download';
  @Local buttonWidth: LengthMetrics = LengthMetrics.vp(200);
  @Local isRunning: boolean = false;
  @Local enableState: boolean = true;

  build() {
    Column() {
      Scroll() {
        Column({ space: 20 }) {
          ProgressButtonV2({
            progress: this.progressIndex,
            progressButtonWidth: this.buttonWidth,
            content: this.textState,
            isEnabled: this.enableState,
            onClicked: () => {
              if (this.textState && !this.isRunning && this.progressIndex < 100) {
                this.textState = 'Continue';
              }
              this.isRunning = !this.isRunning;
              let timer = setInterval(() => {
                if (this.isRunning) {
                  if (this.progressIndex === 100) {
                    clearInterval(timer);
                  } else {
                    this.progressIndex++;
                    if (this.progressIndex === 100) {
                      this.textState = 'Completed';
                      this.enableState = false;
                    }
                  }
                } else {
                  clearInterval(timer);
                }
              }, 20);
            }
          })
        }.alignItems(HorizontalAlign.Center).width('100%').margin({ top: 20 });
      }
    }
  }
}
```


<!--Del--> <!--DelEnd-->