# effect_types.h

## 概述

声明滤镜效果的数据类型，用于定义滤镜效果的矩阵、状态码和平铺模式等，支持创建自定义滤镜效果、处理图像着色器平铺等场景。

**库：** libnative_effect.so

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 12

**相关模块：** [effectKit](capi-effectkit.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_Filter_ColorMatrix](capi-effectkit-oh-filter-colormatrix.md) | - | 定义用于创建滤镜效果的矩阵，矩阵维度为4x5，元素取值范围为浮点数。 |
| [OH_Filter](capi-effectkit-oh-filter.md) | OH_Filter | 滤镜结构体，用于配合effectKit模块相关接口实现滤镜效果处理。 |
| [OH_PixelmapNative](capi-effectkit-oh-pixelmapnative.md) | OH_PixelmapNative | 声明由图像框架定义的像素图对象。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [EffectErrorCode](#effecterrorcode) | EffectErrorCode | 定义滤镜效果的状态码。 |
| [EffectTileMode](#effecttilemode) | EffectTileMode | 定义着色器效果平铺模式的枚举。 |

## 枚举类型说明

### EffectErrorCode

```c
enum EffectErrorCode
```

**描述**

定义滤镜效果的状态码。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| EFFECT_SUCCESS = 0 | 操作成功完成。 |
| EFFECT_BAD_PARAMETER = 401 | 参数错误，请检查参数类型和范围。 |
| EFFECT_UNSUPPORTED_OPERATION = 7600201 | 当前操作不被支持，请检查API使用方式。 |
| EFFECT_UNKNOWN_ERROR = 7600901 | 发生了未被明确识别的错误，可能原因包括系统资源异常、API调用方式不当等。 |

### EffectTileMode

```c
enum EffectTileMode
```

**描述**

定义着色器效果平铺模式的枚举。

**起始版本：** 14

| 枚举项 | 描述 |
| -- | -- |
| CLAMP = 0 | 边缘拉伸模式，如果着色器效果超出其原始边界，剩余区域使用着色器的边缘颜色 |
| REPEAT | 平铺重复模式，在水平和垂直方向上重复着色器效果。适用于需要无缝平铺纹理 |
| MIRROR | 镜像平铺模式，在水平和垂直方向上重复着色器效果，交替镜像图像，以便相邻 |
| DECAL | 贴花模式，仅在其原始边界内渲染着色器效果。适用于需要精确控制着色器边界 |


