# uiEffect

**起始版本：** 12

<!--Device-unnamed-declare namespace uiEffect--><!--Device-unnamed-declare namespace uiEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createFilter](arkts-arkgraphics2d-uieffect-createfilter-f.md#createfilter) | 创建Filter实例用于给组件添加多种filter效果。 |
| [createEffect](arkts-arkgraphics2d-uieffect-createeffect-f.md#createeffect) | 创建VisualEffect实例用于给组件添加多种effect效果。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createBrightnessBlender](arkts-arkgraphics2d-uieffect-createbrightnessblender-f-sys.md#createbrightnessblender) | 创建BrightnessBlender实例用于给组件添加提亮效果。 |
| [createHdrBrightnessBlender](arkts-arkgraphics2d-uieffect-createhdrbrightnessblender-f-sys.md#createhdrbrightnessblender) | 创建HdrBrightnessBlender实例用于给组件添加支持HDR的提亮效果。 |
| [createHdrDarkenBlender](arkts-arkgraphics2d-uieffect-createhdrdarkenblender-f-sys.md#createhdrdarkenblender) | 创建HdrDarkenBlender实例用于HDR图层的压暗混合效果。 |
<!--DelEnd-->

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | Mask效果类，作为Filter以及VisualEffect的输入使用。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) |  |
| [HdrBrightnessBlender](arkts-arkgraphics2d-uieffect-hdrbrightnessblender-i.md) | 支持HDR的提亮混合器（继承自BrightnessBlender），用于将提亮效果添加到指定的组件上。在调用HdrBrightnessBlender前，需要先通过createHdrBrightnessBlender创建一个HdrBrightnessBlender实例。该混合器参数可参考BrightnessBlender。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i-sys.md) |  |
| [VisualEffect](arkts-arkgraphics2d-uieffect-visualeffect-i-sys.md) | VisualEffect效果类，用于将相应的效果添加到指定的组件上。在调用VisualEffect的方法前，需要先通过createEffect创建一个VisualEffect实例。 |
| [BrightnessParam](arkts-arkgraphics2d-uieffect-brightnessparam-i-sys.md) | 材质提亮参数的详细说明。 |
| [HeatDistortionEffectParam](arkts-arkgraphics2d-uieffect-heatdistortioneffectparam-i-sys.md) | 热浪扭曲效果的参数。 |
| [BlurBubblesRiseEffectParam](arkts-arkgraphics2d-uieffect-blurbubblesriseeffectparam-i-sys.md) | 模糊气泡上升效果的参数。 |
| [LiquidMaterialEffectParam](arkts-arkgraphics2d-uieffect-liquidmaterialeffectparam-i-sys.md) | 材质的各项参数及其用途的详细说明。 |
| [BrightnessBlender](arkts-arkgraphics2d-uieffect-brightnessblender-i-sys.md) | 提亮混合器，用于将提亮效果添加到指定的组件上。在调用BrightnessBlender前，需要先通过createBrightnessBlender创建一个BrightnessBlender实例。 |
| [HdrDarkenBlender](arkts-arkgraphics2d-uieffect-hdrdarkenblender-i-sys.md) | 支持HDR的压暗混合器，用于将压暗效果添加到指定的组件上。在调用HdrDarkenBlender前，需要先通过createHdrDarkenBlender创建一个HdrDarkenBlender实例。 |
| [Color](arkts-arkgraphics2d-uieffect-color-i-sys.md) | RGBA格式的颜色描述。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [TileMode](arkts-arkgraphics2d-uieffect-tilemode-e-sys.md) | 像素填充模式枚举。 |
| [WaterRippleMode](arkts-arkgraphics2d-uieffect-waterripplemode-e-sys.md) | 水波纹场景模式枚举。 |
| [FlyMode](arkts-arkgraphics2d-uieffect-flymode-e-sys.md) | 飞入飞出形变场景模式枚举。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Blender](arkts-arkgraphics2d-uieffect-blender-t-sys.md) | 混合器类型，用于描述混合效果。 |
<!--DelEnd-->

