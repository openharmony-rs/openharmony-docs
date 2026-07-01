# effect_types.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanamaru-->
<!--Designer: @chensiyi_CE-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

## 概述

声明滤镜效果的数据类型，用于定义滤镜效果的矩阵、状态码和平铺模式等，支持创建自定义滤镜效果、处理图像着色器平铺等场景，适用于需要在应用内实现图像滤镜处理的场景。

本文档定义的错误码类型用于相关接口的错误状态返回，具体接口的错误码使用说明请参见对应接口文档。

**引用文件：** <native_effect/effect_types.h>

**库：** libnative_effect.so

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 12

**相关模块：** [effectKit](capi-effectkit.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_Filter_ColorMatrix](capi-effectkit-oh-filter-colormatrix.md) | OH_Filter_ColorMatrix | 定义用于创建滤镜效果的矩阵，矩阵维度为4x5，元素取值范围为浮点数。 |
| [OH_Filter](capi-effectkit-oh-filter.md) | OH_Filter | 滤镜结构体，用于配合effectKit模块相关接口实现滤镜效果处理。 |
| [OH_PixelmapNative](capi-drawing-oh-pixelmapnative.md) | OH_PixelmapNative | 定义一个位图，用于配合滤镜效果相关接口进行图像数据输入输出处理。 |

### 枚举

| 名称 | 描述 |
| -- | -- |
| [EffectErrorCode](#effecterrorcode) | 定义滤镜效果的状态码。这些错误码在使用滤镜效果相关接口时返回，开发者应根据返回的错误码判断操作结果并进行相应处理。 |
| [EffectTileMode](#effecttilemode) | 定义着色器效果平铺模式的枚举。 |

## 枚举类型说明

### EffectErrorCode

```c
enum EffectErrorCode
```

**描述**

定义滤镜效果的状态码。这些错误码在使用滤镜效果相关接口时返回，开发者应根据返回的错误码判断操作结果并进行相应处理。具体接口的错误码使用说明请参见对应接口文档。

**起始版本：** 12

| 枚举项 | 描述 | 说明 |
| -- | -- | -- |
| EFFECT_SUCCESS = 0 | 成功。 | 操作成功完成。 |
| EFFECT_BAD_PARAMETER = 401 | 无效的参数。 | 参数错误，请检查参数类型和范围。 |
| EFFECT_UNSUPPORTED_OPERATION = 7600201 | 不支持的操作。 | 当前操作不被支持，请检查API使用方式。 |
| EFFECT_UNKNOWN_ERROR = 7600901 | 未知错误。 | 发生了未被明确识别的错误，可能原因包括系统资源异常、API调用方式不当等。建议先检查API调用参数和系统资源状态。 |

### EffectTileMode

```c
enum EffectTileMode
```

**描述**

定义着色器效果平铺模式的枚举。

**起始版本：** 14

| 枚举项 | 描述 | 说明 |
| -- | -- | -- |
| CLAMP = 0 | 边缘拉伸模式，如果着色器效果超出其原始边界，剩余区域使用着色器的边缘颜色填充。 | 适用于需要平滑过渡到纯色背景的场景。 |
| REPEAT = 1 | 平铺重复模式，在水平和垂直方向上重复着色器效果。 | 适用于需要无缝平铺纹理的场景，如背景图案填充。 |
| MIRROR = 2 | 镜像平铺模式，在水平和垂直方向上重复着色器效果，交替镜像图像，以便相邻图像始终接合。 | 适用于需要连续但避免生硬重复边缘的场景，如渐变背景。 |
| DECAL = 3 | 贴花模式，仅在其原始边界内渲染着色器效果。 | 适用于需要精确控制着色器边界的场景，边界外保持透明或原有内容。 |


