# @ohos.effectKit

图像效果模块提供了处理图像的基础能力，包括亮度调节、模糊化、灰度调节和智能取色等， 适用于图片编辑应用中添加滤镜效果、应用启动页背景图模糊处理、UI主题色自动提取、图片配色分析等场景。 本模块用于离线处理image.PixelMap以获得视觉效果， 而uiEffect（UI效果服务）则实时接入渲染服务，针对屏幕帧缓存进行处理以获得动态视觉效果。 该模块提供以下图像效果相关的常用功能： - [Filter](arkts-arkgraphics2d-effectkit-filter-i.md#Filter)：效果类，用于将指定效果添加到效果链表中，通过链式调用实现多种图像效果的组合处理。 - [Color](arkts-arkgraphics2d-effectkit-color-i.md#Color)：颜色类，用于保存取色的结果。 - [ColorPicker](arkts-arkgraphics2d-effectkit-colorpicker-i.md#ColorPicker)：智能取色器。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace effectKit--><!--Device-unnamed-declare namespace effectKit-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createColorPicker](arkts-arkgraphics2d-effectkit-createcolorpicker-f.md#createColorPicker) | 通过传入的PixelMap创建ColorPicker实例，使用Promise异步回调。 |
| [createColorPicker](arkts-arkgraphics2d-effectkit-createcolorpicker-f.md#createColorPicker) | 通过传入的PixelMap创建选定取色区域的ColorPicker实例，使用Promise异步回调。 |
| [createColorPicker](arkts-arkgraphics2d-effectkit-createcolorpicker-f.md#createColorPicker) | 通过传入的PixelMap创建ColorPicker实例，使用callback异步回调。 |
| [createColorPicker](arkts-arkgraphics2d-effectkit-createcolorpicker-f.md#createColorPicker) | 通过传入的PixelMap创建选定取色区域的ColorPicker实例，使用callback异步回调。 |
| [createEffect](arkts-arkgraphics2d-effectkit-createeffect-f.md#createEffect) | 通过传入的PixelMap创建Filter实例。后续可通过链式调用添加各种图像效果， 最终通过[getEffectPixelMap](arkts-arkgraphics2d-effectkit-filter-i.md#getEffectPixelMap)获取处理后的图像。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Color](arkts-arkgraphics2d-effectkit-color-i.md) | 颜色类，用于保存取色的结果，适用于配合ColorPicker获取图像主色、占比最多颜色、饱和度最高颜色等场景， 可帮助开发者便捷地获取和传递图像取色结果。 |
| [ColorPicker](arkts-arkgraphics2d-effectkit-colorpicker-i.md) | 取色类，用于从一张图像数据中获取它的主要颜色，适用于UI主题色提取、图片配色分析、智能配色推荐等场景， 可帮助开发者基于图片内容动态生成和谐的配色方案。在调用ColorPicker的方法前，需要先通过 [createColorPicker](arkts-arkgraphics2d-effectkit-createcolorpicker-f.md#createColorPicker)创建一个ColorPicker实例。 |
| [Filter](arkts-arkgraphics2d-effectkit-filter-i.md) | 图像效果类，用于通过链式调用将指定效果添加到效果链表中，适用于图片滤镜处理、视觉效果增强、图像美化等场景。 在调用Filter的方法前，需要先通过[createEffect](arkts-arkgraphics2d-effectkit-createeffect-f.md#createEffect)创建一个Filter实例。 在添加效果后，需调用[getEffectPixelMap](arkts-arkgraphics2d-effectkit-filter-i.md#getEffectPixelMap)获取处理后的图像。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ColorPicker](arkts-arkgraphics2d-effectkit-colorpicker-i-sys.md) | 取色类，用于从一张图像数据中获取它的主要颜色，适用于UI主题色提取、图片配色分析、智能配色推荐等场景， 可帮助开发者基于图片内容动态生成和谐的配色方案。在调用ColorPicker的方法前，需要先通过 [createColorPicker](arkts-arkgraphics2d-effectkit-createcolorpicker-f.md#createColorPicker)创建一个ColorPicker实例。 |
| [Filter](arkts-arkgraphics2d-effectkit-filter-i-sys.md) | 图像效果类，用于通过链式调用将指定效果添加到效果链表中，适用于图片滤镜处理、视觉效果增强、图像美化等场景。 在调用Filter的方法前，需要先通过[createEffect](arkts-arkgraphics2d-effectkit-createeffect-f.md#createEffect)创建一个Filter实例。 在添加效果后，需调用[getEffectPixelMap](arkts-arkgraphics2d-effectkit-filter-i.md#getEffectPixelMap)获取处理后的图像。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [TileMode](arkts-arkgraphics2d-effectkit-tilemode-e.md) | 着色器效果平铺模式的枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [PictureComplexityDegree](arkts-arkgraphics2d-effectkit-picturecomplexitydegree-e-sys.md) | 图片内容复杂度的枚举。 |
| [PictureLightDegree](arkts-arkgraphics2d-effectkit-picturelightdegree-e-sys.md) | 图片颜色明亮度的枚举。 |
| [PictureShadeDegree](arkts-arkgraphics2d-effectkit-pictureshadedegree-e-sys.md) | 图片颜色深浅度的枚举。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [EllipticalMaskCenter](arkts-arkgraphics2d-effectkit-ellipticalmaskcenter-t-sys.md) | 定义椭圆形遮罩的中心点。 |
| [EllipticalMaskRadius](arkts-arkgraphics2d-effectkit-ellipticalmaskradius-t-sys.md) | 定义椭圆形遮罩的半径。 |
<!--DelEnd-->

