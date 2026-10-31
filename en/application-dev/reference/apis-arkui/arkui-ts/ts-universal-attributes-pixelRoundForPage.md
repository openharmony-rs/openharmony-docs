# Page-Level Pixel Rounding
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangwentao96-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=75a7d62c0702c21a06ca0119552a942305a023cc translatedAt=2026-09-02T12:00:41.151Z -->

Page-level pixel rounding is a pixel alignment mechanism that rounds the calculated component sizes and positions to resolve display blurring or edge aliasing caused by floating-point pixel values. Page-level pixel rounding sets the pixel rounding mode as a context property of the page, so as to uniformly control pixel alignment at the page level and improve the clarity and consistency of UI display. It is suitable for scenarios that require precise control of pixel alignment, such as high-quality image rendering and fine-grained animation effects.

>  **NOTE**
>
> - This module is supported since API version 18. New APIs added in later versions are marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - If pixel rounding [issues](ts-universal-attributes-pixelRoundForComponent.md#faqs) occur and cannot be resolved by [component-level pixel rounding](./ts-universal-attributes-pixelRoundForComponent.md), you are advised to try the PIXEL_ROUND_AFTER_MEASURE mode.
>
> - In PIXEL_ROUND_AFTER_MEASURE mode, a component is rounded at the end of measurement, which means that the final size may be 1 px larger than that in PIXEL_ROUND_ON_LAYOUT_FINISH mode.
>
> - The difference between page-level pixel rounding and component-level pixel rounding is that page-level pixel rounding adjusts the pixel rounding timing of the entire page, whereas component-level pixel rounding adjusts the pixel rounding alignment of a specific component in a specific direction.

## setPixelRoundMode

setPixelRoundMode(mode: PixelRoundMode): void

Sets the pixel rounding mode of the current page, which affects the pixel rounding timing of the entire page. When [component-level pixel rounding](./ts-universal-attributes-pixelRoundForComponent.md) cannot resolve pixel rounding issues, you can try the PIXEL_ROUND_AFTER_MEASURE mode.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type        | Mandatory  | Description  |
| -------- | ---------- | ---- | ---- |
| mode | [PixelRoundMode](./ts-appendix-enums.md#pixelroundmode18)| Yes    | Pixel rounding mode. Available values:<br>- PIXEL_ROUND_ON_LAYOUT_FINISH: Performs pixel rounding after layout is complete. This mode is suitable for most scenarios.<br>- PIXEL_ROUND_AFTER_MEASURE: Performs pixel rounding at the end of component measurement. This mode is suitable for pixel rounding scenarios that cannot be resolved by component-level pixel rounding, but the final size may be 1px larger than that in PIXEL_ROUND_ON_LAYOUT_FINISH mode.<br>If an invalid value is set, the PixelRoundMode.PIXEL_ROUND_ON_LAYOUT_FINISH mode is used. |

**Example**

<!--code_no_check-->
```ts
// EntryAbility.ets
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

onWindowStageCreate(windowStage: window.WindowStage) {
   windowStage.loadContent('pages/Index', (err, data) => {
      // Obtain the UIContext instance.
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      // Set the pixel rounding mode to PIXEL_ROUND_AFTER_MEASURE.
      uiContext.setPixelRoundMode(PixelRoundMode.PIXEL_ROUND_AFTER_MEASURE);
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
```

## getPixelRoundMode

getPixelRoundMode(): PixelRoundMode

Obtains the pixel rounding mode for this page.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type        | Description  |
| ---------- | ---- |
| [PixelRoundMode](./ts-appendix-enums.md#pixelroundmode18)| Pixel rounding mode of the current page. The value can be:<br>- PIXEL_ROUND_ON_LAYOUT_FINISH (value: 0): pixel rounding is performed after layout is complete.<br>- PIXEL_ROUND_AFTER_MEASURE (value: 1): pixel rounding is performed at the end of component measurement. |

**Example**

<!--code_no_check-->
```ts
// EntryAbility.ets
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.loadContent('pages/Index', (err, data) => {
      // Obtain the UIContext instance.
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      // Obtain and print the current pixel rounding mode.
      console.info("pixelRoundMode : " + uiContext.getPixelRoundMode().valueOf());
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
```