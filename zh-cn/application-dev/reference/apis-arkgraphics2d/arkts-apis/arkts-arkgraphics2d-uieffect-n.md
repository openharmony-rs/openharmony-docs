# uiEffect

本模块提供组件效果的一些基础能力，包括模糊、提亮等。效果被分为Filter和VisualEffect大类，同类效果可以级联在一个效果大类的实例下。 使用该模块可以快速实现复杂的视觉效果，无需开发者掌握底层的图像处理算法，降低了开发复杂度，提升了用户体验。 在实际开发中，模糊可用于背景虚化，提亮可用于亮屏显示等。 - [Filter](arkts-arkgraphics2d-uieffect-filter-i.md#Filter)：用于添加指定Filter效果到组件上。 - [VisualEffect](arkts-arkgraphics2d-uieffect-visualeffect-i-sys.md#VisualEffect)：用于添加指定VisualEffect效果到组件上。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace uiEffect--><!--Device-unnamed-declare namespace uiEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createFilter](arkts-arkgraphics2d-uieffect-createfilter-f.md#createFilter) | 创建Filter实例用于给组件添加多种Filter效果。 |
| [createEffect](arkts-arkgraphics2d-uieffect-createeffect-f.md#createEffect) | 创建VisualEffect实例用于给组件添加多种VisualEffect效果。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createBrightnessBlender](arkts-arkgraphics2d-uieffect-createbrightnessblender-f-sys.md#createBrightnessBlender) | 创建BrightnessBlender实例用于给组件添加提亮效果。 |
| [createHdrBrightnessBlender](arkts-arkgraphics2d-uieffect-createhdrbrightnessblender-f-sys.md#createHdrBrightnessBlender) | 创建HdrBrightnessBlender实例用于给组件添加支持HDR的提亮效果。 |
| [createHdrDarkenBlender](arkts-arkgraphics2d-uieffect-createhdrdarkenblender-f-sys.md#createHdrDarkenBlender) | 创建HdrDarkenBlender实例用于HDR图层的压暗混合效果。 |
<!--DelEnd-->

<!--Del-->
### 类（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | Mask效果类，作为Filter以及VisualEffect的输入使用。不同类型的Mask提供不同的灰度分布模式，如波环遮罩、径向渐变、像素图遮罩等。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Filter效果类，用于将模糊、边缘像素扩展、水波纹等效果添加到组件上。在调用Filter的方法前， 需要先通过[createFilter](arkts-arkgraphics2d-uieffect-createfilter-f.md#createFilter)创建一个Filter实例。 |
| [HdrBrightnessBlender](arkts-arkgraphics2d-uieffect-hdrbrightnessblender-i.md) | 支持HDR的提亮混合器（继承自BrightnessBlender），用于将提亮效果添加到指定的组件上。 在调用HdrBrightnessBlender前，需要先通过createHdrBrightnessBlender创建一个HdrBrightnessBlender实例。 该混合器参数可参考BrightnessBlender。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i-sys.md) | Filter效果类，用于将模糊、边缘像素扩展、水波纹等效果添加到组件上。在调用Filter的方法前， 需要先通过[createFilter](arkts-arkgraphics2d-uieffect-createfilter-f.md#createFilter)创建一个Filter实例。 |
| [VisualEffect](arkts-arkgraphics2d-uieffect-visualeffect-i-sys.md) | VisualEffect效果类，用于将背景颜色混合、边框光照、颜色渐变等效果添加到组件上。 在调用VisualEffect的方法前，需要先通过[createEffect](arkts-arkgraphics2d-uieffect-createeffect-f.md#createEffect)创建一个VisualEffect实例。 |
| [BrightnessParam](arkts-arkgraphics2d-uieffect-brightnessparam-i-sys.md) | 材质提亮参数的详细说明。 |
| [HeatDistortionEffectParam](arkts-arkgraphics2d-uieffect-heatdistortioneffectparam-i-sys.md) | 热浪扭曲效果的参数。 |
| [BlurBubblesRiseEffectParam](arkts-arkgraphics2d-uieffect-blurbubblesriseeffectparam-i-sys.md) | 模糊气泡上升效果的参数。 |
| [LiquidMaterialEffectParam](arkts-arkgraphics2d-uieffect-liquidmaterialeffectparam-i-sys.md) | 材质效果参数，用于控制材质的折射、反射、扰动和叠加颜色等显示属性。 |
| [BrightnessBlender](arkts-arkgraphics2d-uieffect-brightnessblender-i-sys.md) | 提亮混合器，用于将提亮效果添加到指定的组件上。 在调用BrightnessBlender前，需要先通过createBrightnessBlender创建一个BrightnessBlender实例。 |
| [HdrDarkenBlender](arkts-arkgraphics2d-uieffect-hdrdarkenblender-i-sys.md) | 支持HDR的压暗混合器，用于将压暗效果添加到指定的组件上。 在调用HdrDarkenBlender前，需要先通过createHdrDarkenBlender创建一个HdrDarkenBlender实例。 |
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

