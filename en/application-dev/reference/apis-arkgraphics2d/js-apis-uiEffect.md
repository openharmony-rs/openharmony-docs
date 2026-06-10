# @ohos.graphics.uiEffect (Cascading Effect)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hanamaru-->
<!--Designer: @gaoweihua-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

The uiEffect module provides basic capabilities to apply an effect, for example, blur, pixel stretch, and brightness, to a component. Effects are classified into filters and visual effects. Effects of the same category can be cascaded in an effect instance of the corresponding category. In actual development, the blur effect can be used for background blurring, and the brightness effect can be used for screen-on display.

- [Filter](#filter): applies a filter to a component.
- [VisualEffect](#visualeffect): applies a visual effect to a component.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { uiEffect } from "@kit.ArkGraphics2D";
```

## uiEffect.createFilter
createFilter(): Filter

Creates a **Filter** instance, which can be used to apply multiple filters to a component.

**System capability**: SystemCapability.Graphics.Drawing

**Return value**

| Type             | Description                |
| ------------------| ------------------- |
| [Filter](#filter) | Head node of the filter.|

**Example**

```ts
let filter : uiEffect.Filter = uiEffect.createFilter()
```

## uiEffect.createEffect
createEffect(): VisualEffect

Creates a **VisualEffect** instance, which can be used to apply multiple visual effects to a component.

**Widget capability**: This API can be used in ArkTS widgets since API version 24.

**System capability**: SystemCapability.Graphics.Drawing

**Return value**

| Type                         | Description                      |
| ----------------------------- | ------------------------- |
| [VisualEffect](#visualeffect) | Head node of the visual effect.|

**Example**

```ts
let visualEffect : uiEffect.VisualEffect = uiEffect.createEffect()
```

## Filter
A class that can apply a filter to a component. Before calling any API in **Filter**, you must use [createFilter](#uieffectcreatefilter) to create a **Filter** instance.

### blur
blur(blurRadius: number): Filter

Applies the blur effect to the component.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**
| Name      | Type  | Mandatory| Description      |
| ----------- | -------| ---- | --------- |
| blurRadius  | number | Yes  | Blur radius.<br>The value must be greater than or equal to 0. The larger the radius is, the more blurred the content is.<br>If the value is 0, the content is not blurred.|

**Return value**

| Type              | Description                      |
| ----------------- | -------------------------- |
| [Filter](#filter) | **Filter** instance with the blur effect.|

**Example**

```ts
// xxx.ts
import { uiEffect } from '@kit.ArkGraphics2D';

let filter: uiEffect.Filter = uiEffect.createFilter();
filter.blur(10);

@Entry
@Component
struct UIEffectFilterExample {
    build(){
        Column({ space: 15 }) {
            Text('UIEffectFilter').fontSize(20).width('75%').fontColor('#DCDCDC')
            Image($r('app.media.foreground'))
                .width(100)
                .height(100)
                .backgroundImage($r('app.media.background'))
                .backgroundImagePosition(Alignment.Center)
                .backgroundImageSize({ width: 90, height: 90 })
                .backgroundFilter(filter)
        }
        .height('100%')
        .width('100%')
    }
}
```
![image_UIEffect_blur.png](figures/image_UIEffect_blur.png)

### hdrBrightnessRatio<sup>24+</sup>
hdrBrightnessRatio(ratio: number): Filter

Applies an HDR brightness effect to a component. Nesting is not recommended. Forcible nesting may cause overexposure.

The brightness effect takes effect only when the HDR rendering pipeline is enabled. In some scenarios, HDR cannot be enabled even if the HDR rendering pipeline is triggered. For example, the device hardware does not support HDR.

The maximum supported brightness boost multiple is calculated as the device's current maximum brightness divided by its SDR reference white luminance.

>  **NOTE**
>
> Using the HDR brightness boost effect may cause certain performance and power consumption overheads. It is recommended that this effect be used in scenarios where HDR images or videos are already available.

**Required permissions**: ohos.permission.HDR_BRIGHTNESS
<!--Del-->System applications do not need to apply for this permission.<!--DelEnd-->

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**
| Name        | Type                 | Mandatory| Description                      |
| ------------- | --------------------- | ---- | ------------------------- |
| ratio  | number         | Yes  | Brightness boost multiple. Value range: [1.0, maximum supported brightness boost multiple of the device]. Values less than **1.0** default to **1.0**. Values equal to **1.0** trigger no processing. Values greater than **1.0** will attempt to trigger the HDR rendering pipeline. Values exceeding the device's maximum supported brightness boost multiple will be clamped to this maximum value.|

**Return value**

| Type             | Description                              |
| ----------------- | --------------------------------- |
| [Filter](#filter) | Returns a filter with the HDR brightness effect.|

**Error codes:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| Error Code| Error Message|
| ------- | --------------------------------------------|
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
filter.hdrBrightnessRatio(2.0)
```

## VisualEffect
A class that can apply a visual effect to a component. Before calling any API in **VisualEffect**, you must use [createEffect](#uieffectcreateeffect) to create a **VisualEffect** instance.
