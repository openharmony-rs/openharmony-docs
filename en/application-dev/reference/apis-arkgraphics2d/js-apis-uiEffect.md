# @ohos.graphics.uiEffect (Cascading Effect)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hanamaru-->
<!--Designer: @chensiyi_CE-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=83ae349e9ef332979a7fb594747f69da60439d0b translatedAt=2026-09-09T03:23:33.488Z pushedAt=2026-09-09T04:04:32.372Z -->

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

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

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
| blurRadius  | number | Yes   | Blur Radius, in px.<br/>The value must be greater than or equal to 0. A larger blur radius produces a stronger blur effect.<br/>A blur radius of 0 produces no blur effect. |

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

### hdrBrightnessRatio<sup>24+</sup>
hdrBrightnessRatio(ratio: number): Filter

Adds an HDR (High Dynamic Range) brightening effect to the component content. Nesting is not recommended, as forced nesting may cause overexposure.

The brightening effect requires the HDR rendering pipeline to be enabled to take effect. In some scenarios, HDR cannot be enabled even if an attempt is made to trigger the HDR rendering pipeline, for example, when the device hardware specifications do not support HDR.

The maximum supported brightness boost multiple is calculated as the device's current maximum brightness divided by its SDR reference white luminance.

>  **NOTE**
>
> Using the HDR brightening effect incurs certain performance and power consumption overhead. It is recommended to use it in scenarios where HDR images or videos already exist.

**Required permissions:** ohos.permission.HDR_BRIGHTNESS
<!--Del-->System applications do not need to apply for this permission.<!--DelEnd-->

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**
| Name         | Type                  | Required | Description                       |
| ------------- | --------------------- | ---- | ------------------------- |
| ratio  | number         | Yes   | Brightening multiplier, with a value range of [1.0, the maximum brightening multiplier currently supported by the device]. If a value less than 1.0 is set, it is processed as 1.0. If the value equals 1.0, no processing is performed. If the value is greater than 1.0, the HDR rendering pipeline is triggered. If a value greater than the maximum brightening multiplier currently supported by the device is set, it is processed as the maximum brightening multiplier currently supported by the device.|

**Return value**

| Type              | Description                               |
| ----------------- | --------------------------------- |
| [Filter](#filter) | Returns the Filter with the HDR brightening effect attached. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message |
| ------- | --------------------------------------------|
| 201 | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
filter.hdrBrightnessRatio(2.0)
```

## VisualEffect
A class that can apply a visual effect to a component. Before calling any API in **VisualEffect**, you must use [createEffect](#uieffectcreateeffect) to create a **VisualEffect** instance.