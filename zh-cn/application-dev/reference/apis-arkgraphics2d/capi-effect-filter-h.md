# effect_filter.h
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanamaru-->
<!--Designer: @chensiyi_CE-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

## 概述

声明滤镜效果的接口。支持创建和管理多种滤镜效果，包括毛玻璃模糊、亮度调节、灰度转换、颜色反转等，支持通过自定义矩阵实现丰富的图像处理效果，适用于图像编辑、照片美化、视觉特效等场景。

> **说明：**
>
> 必须成对调用[OH_Filter_CreateEffect](#oh_filter_createeffect)和[OH_Filter_Release](#oh_filter_release)，确保资源正确释放。
>
> 本文件接口均不支持多线程调用。

**引用文件：** <native_effect/effect_filter.h>

**库：** libnative_effect.so

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 12

**相关模块：** [effectKit](capi-effectkit.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [EffectErrorCode OH_Filter_CreateEffect(OH_PixelmapNative* pixelmap, OH_Filter** filter)](#oh_filter_createeffect) | 创建一个OH_Filter对象，对图像应用各种滤镜效果（如模糊、提亮或灰度等），适用于图像编辑、相册应用和视频处理等场景。 |
| [EffectErrorCode OH_Filter_Release(OH_Filter* filter)](#oh_filter_release) | 释放OH_Filter对象。 |
| [EffectErrorCode OH_Filter_Blur(OH_Filter* filter, float radius)](#oh_filter_blur) | 创建一个毛玻璃滤镜效果，并添加到滤镜效果链中。 |
| [EffectErrorCode OH_Filter_BlurWithTileMode(OH_Filter* filter, float radius, EffectTileMode tileMode)](#oh_filter_blurwithtilemode) | 创建一个毛玻璃滤镜效果，并添加到滤镜效果链中，支持选择着色器效果平铺模式。 |
| [EffectErrorCode OH_Filter_Brighten(OH_Filter* filter, float brightness)](#oh_filter_brighten) | 创建一个提亮效果，并添加到滤镜效果链中。 |
| [EffectErrorCode OH_Filter_GrayScale(OH_Filter* filter)](#oh_filter_grayscale) | 创建一个灰度效果，并添加到滤镜效果链中。 |
| [EffectErrorCode OH_Filter_Invert(OH_Filter* filter)](#oh_filter_invert) | 创建一个反色效果，并添加到滤镜效果链中。 |
| [EffectErrorCode OH_Filter_SetColorMatrix(OH_Filter* filter, OH_Filter_ColorMatrix* matrix)](#oh_filter_setcolormatrix) | 通过矩阵创建一个自定义的效果，并添加到滤镜效果链中，适用于需要实现特定的颜色变换效果（如色彩校正、色调调整或色温调节等）的场景。 |
| [EffectErrorCode OH_Filter_GetEffectPixelMap(OH_Filter* filter, OH_PixelmapNative** pixelmap)](#oh_filter_geteffectpixelmap) | 获取滤镜生成的位图。 |

## 函数说明

### OH_Filter_CreateEffect()

```c
EffectErrorCode OH_Filter_CreateEffect(OH_PixelmapNative* pixelmap, OH_Filter** filter)
```

**描述**

创建一个OH_Filter对象，对图像应用各种滤镜效果（如模糊、提亮或灰度等），适用于图像编辑、相册应用和视频处理等场景。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PixelmapNative](capi-drawing-oh-pixelmapnative.md)* pixelmap | 作为滤镜效果处理源图像的位图对象。 |
| [OH_Filter](capi-effectkit-oh-filter.md)** filter | 用来接收滤镜的二级指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [EffectErrorCode](capi-effect-types-h.md#effecterrorcode) | 操作成功则返回EFFECT_SUCCESS。<br> 当pixelmap或filter为空指针时，返回EFFECT_BAD_PARAMETER。 |

### OH_Filter_Release()

```c
EffectErrorCode OH_Filter_Release(OH_Filter* filter)
```

**描述**

释放OH_Filter对象。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Filter](capi-effectkit-oh-filter.md)* filter | 被释放的对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [EffectErrorCode](capi-effect-types-h.md#effecterrorcode) | 操作成功则返回EFFECT_SUCCESS。<br> 当filter为空指针时，返回EFFECT_BAD_PARAMETER。 |

### OH_Filter_Blur()

```c
EffectErrorCode OH_Filter_Blur(OH_Filter* filter, float radius)
```

**描述**

创建一个毛玻璃滤镜效果，并添加到滤镜效果链中。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Filter](capi-effectkit-oh-filter.md)* filter | 滤镜指针，需要通过[OH_Filter_CreateEffect](#oh_filter_createeffect)创建并添加滤镜效果。 |
| float radius | 毛玻璃效果的模糊半径，取值范围为[0, +∞)，单位为像素。值为0时不产生模糊效果；值越大，模糊效果越强；值越小，模糊效果越弱。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [EffectErrorCode](capi-effect-types-h.md#effecterrorcode) | 操作成功则返回EFFECT_SUCCESS。<br> 当filter为空指针或radius小于0时，返回EFFECT_BAD_PARAMETER。 |

### OH_Filter_BlurWithTileMode()

```c
EffectErrorCode OH_Filter_BlurWithTileMode(OH_Filter* filter, float radius, EffectTileMode tileMode)
```

**描述**

创建一个毛玻璃滤镜效果，并添加到滤镜效果链中，支持选择着色器效果平铺模式。

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Filter](capi-effectkit-oh-filter.md)* filter | 滤镜指针，需要通过[OH_Filter_CreateEffect](#oh_filter_createeffect)创建并添加滤镜效果。 |
| float radius | 毛玻璃效果的模糊半径，取值范围为[0, +∞)，单位为像素。参数值为0时不产生模糊效果。值越大模糊效果越强。 |
| [EffectTileMode](capi-effect-types-h.md#effecttilemode) tileMode | 着色器效果平铺模式，不同模式决定图像边缘区域的不同处理方式。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [EffectErrorCode](capi-effect-types-h.md#effecterrorcode) | 操作成功则返回EFFECT_SUCCESS。<br> 当filter为空指针或radius小于0时，返回EFFECT_BAD_PARAMETER。 |

### OH_Filter_Brighten()

```c
EffectErrorCode OH_Filter_Brighten(OH_Filter* filter, float brightness)
```

**描述**

创建一个提亮效果，并添加到滤镜效果链中。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Filter](capi-effectkit-oh-filter.md)* filter | 滤镜指针，需要通过[OH_Filter_CreateEffect](#oh_filter_createeffect)创建并添加滤镜效果。 |
| float brightness | 提亮效果的亮度值，取值范围为[0, 1]。取值为0时图像保持不变，取值为1时图像全白。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [EffectErrorCode](capi-effect-types-h.md#effecterrorcode) | 操作成功则返回EFFECT_SUCCESS。<br> 当filter为空指针或brightness超出取值范围[0, 1]时，返回EFFECT_BAD_PARAMETER。 |

### OH_Filter_GrayScale()

```c
EffectErrorCode OH_Filter_GrayScale(OH_Filter* filter)
```

**描述**

创建一个灰度效果，并添加到滤镜效果链中。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Filter](capi-effectkit-oh-filter.md)* filter | 滤镜指针，需要通过[OH_Filter_CreateEffect](#oh_filter_createeffect)创建并添加滤镜效果。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [EffectErrorCode](capi-effect-types-h.md#effecterrorcode) | 操作成功则返回EFFECT_SUCCESS。<br> 当filter为空指针时，返回EFFECT_BAD_PARAMETER。 |

### OH_Filter_Invert()

```c
EffectErrorCode OH_Filter_Invert(OH_Filter* filter)
```

**描述**

创建一个反色效果，并添加到滤镜效果链中。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Filter](capi-effectkit-oh-filter.md)* filter | 滤镜指针，需要通过[OH_Filter_CreateEffect](#oh_filter_createeffect)创建并添加滤镜效果。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [EffectErrorCode](capi-effect-types-h.md#effecterrorcode) | 操作成功则返回EFFECT_SUCCESS。<br> 当filter为空指针时，返回EFFECT_BAD_PARAMETER。 |

### OH_Filter_SetColorMatrix()

```c
EffectErrorCode OH_Filter_SetColorMatrix(OH_Filter* filter, OH_Filter_ColorMatrix* matrix)
```

**描述**

通过矩阵创建一个自定义的效果，并添加到滤镜效果链中，适用于需要实现特定的颜色变换效果（如色彩校正、色调调整或色温调节等）的场景。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Filter](capi-effectkit-oh-filter.md)* filter | 滤镜指针，需要通过[OH_Filter_CreateEffect](#oh_filter_createeffect)创建并添加滤镜效果。 |
| [OH_Filter_ColorMatrix](capi-effectkit-oh-filter-colormatrix.md)* matrix | 用来创建滤镜的自定义矩阵。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [EffectErrorCode](capi-effect-types-h.md#effecterrorcode) | 操作成功则返回EFFECT_SUCCESS。<br> 当filter或matrix为空指针时，返回EFFECT_BAD_PARAMETER。 |

### OH_Filter_GetEffectPixelMap()

```c
EffectErrorCode OH_Filter_GetEffectPixelMap(OH_Filter* filter, OH_PixelmapNative** pixelmap)
```

**描述**

获取滤镜生成的位图。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Filter](capi-effectkit-oh-filter.md)* filter | 用来创建位图的滤镜指针，需要通过[OH_Filter_CreateEffect](#oh_filter_createeffect)创建并添加滤镜效果。 |
| [OH_PixelmapNative](capi-drawing-oh-pixelmapnative.md)** pixelmap | 用来接收位图的二级指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [EffectErrorCode](capi-effect-types-h.md#effecterrorcode) | 操作成功则返回EFFECT_SUCCESS。<br> 当filter或pixelmap为空指针时，返回EFFECT_BAD_PARAMETER。 |