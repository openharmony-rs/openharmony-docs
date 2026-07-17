# @ohos.effectKit

图像效果模块提供了处理图像的基础能力，包括亮度调节、模糊化、灰度调节和智能取色等。effectKit用于离线处理图像（如pixelmap、png、jpeg）以获得视觉效果，而uiEffect则实时接入渲染服务，针对屏幕帧缓存进行处理以获得动态视觉效果。

该模块提供以下图像效果相关的常用功能：

- [Filter](arkts-arkgraphics2d-effectkit-filter-i.md)：效果类，用于添加指定效果到图像源。  
- [Color](arkts-arkgraphics2d-effectkit-color-i.md)：颜色类，用于保存取色的结果。  
- [ColorPicker](arkts-arkgraphics2d-effectkit-colorpicker-i.md)：智能取色器。

**起始版本：** 9

<!--Device-unnamed-declare namespace effectKit--><!--Device-unnamed-declare namespace effectKit-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { effectKit } from '@kit.ArkGraphics2D';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createColorPicker](arkts-arkgraphics2d-effectkit-createcolorpicker-f.md#createcolorpicker-1) | 通过传入的PixelMap创建ColorPicker实例，使用Promise异步回调。 |
| [createColorPicker](arkts-arkgraphics2d-effectkit-createcolorpicker-f.md#createcolorpicker-2) | 通过传入的PixelMap创建选定取色区域的ColorPicker实例，使用Promise异步回调。 |
| [createColorPicker](arkts-arkgraphics2d-effectkit-createcolorpicker-f.md#createcolorpicker-3) | 通过传入的PixelMap创建ColorPicker实例，使用callback异步回调。 |
| [createColorPicker](arkts-arkgraphics2d-effectkit-createcolorpicker-f.md#createcolorpicker-4) | 通过传入的PixelMap创建选定取色区域的ColorPicker实例，使用callback异步回调。 |
| [createEffect](arkts-arkgraphics2d-effectkit-createeffect-f.md#createeffect-1) | 通过传入的PixelMap创建Filter实例。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Color](arkts-arkgraphics2d-effectkit-color-i.md) | 颜色类，用于保存取色的结果。 |
| [ColorPicker](arkts-arkgraphics2d-effectkit-colorpicker-i.md) | 取色类，用于从一张图像数据中获取它的主要颜色。在调用ColorPicker的方法前，需要先通过[createColorPicker](arkts-arkgraphics2d-effectkit-createcolorpicker-f.md#createcolorpicker-1)创建一个ColorPicker实例。 |
| [Filter](arkts-arkgraphics2d-effectkit-filter-i.md) | 图像效果类，用于将指定的效果添加到输入图像中。在调用Filter的方法前，需要先通过[createEffect](arkts-arkgraphics2d-effectkit-createeffect-f.md#createeffect-1)创建一个Filter实例。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ColorPicker](arkts-arkgraphics2d-effectkit-colorpicker-i-sys.md) | 取色类，用于从一张图像数据中获取它的主要颜色。在调用ColorPicker的方法前，需要先通过[createColorPicker](arkts-arkgraphics2d-effectkit-createcolorpicker-f.md#createcolorpicker-1)创建一个ColorPicker实例。 |
| [Filter](arkts-arkgraphics2d-effectkit-filter-i-sys.md) | 图像效果类，用于将指定的效果添加到输入图像中。在调用Filter的方法前，需要先通过[createEffect](arkts-arkgraphics2d-effectkit-createeffect-f.md#createeffect-1)创建一个Filter实例。 |
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

