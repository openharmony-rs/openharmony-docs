# effect_filter.h

## 概述

声明滤镜效果的接口。

**库：** libnative_effect.so

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 12

**相关模块：** [effectKit](capi-effectkit.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [EffectErrorCode OH_Filter_CreateEffect(OH_PixelmapNative* pixelmap, OH_Filter** filter)](#oh_filter_createeffect) | 创建一个OH_Filter对象。 |
| [EffectErrorCode OH_Filter_Release(OH_Filter* filter)](#oh_filter_release) | 释放OH_Filter对象。 |
| [EffectErrorCode OH_Filter_Blur(OH_Filter* filter, float radius)](#oh_filter_blur) | 创建一个毛玻璃滤镜效果，然后添加到滤镜里面。 |
| [EffectErrorCode OH_Filter_BlurWithTileMode(OH_Filter* filter, float radius, EffectTileMode tileMode)](#oh_filter_blurwithtilemode) | 创建一个毛玻璃滤镜效果，然后添加到滤镜里面，支持着色器效果平铺模式选择。 |
| [EffectErrorCode OH_Filter_Brighten(OH_Filter* filter, float brightness)](#oh_filter_brighten) | 创建一个提亮效果并且添加到滤镜中。 |
| [EffectErrorCode OH_Filter_GrayScale(OH_Filter* filter)](#oh_filter_grayscale) | 创建一个灰度效果并且添加到滤镜中。 |
| [EffectErrorCode OH_Filter_Invert(OH_Filter* filter)](#oh_filter_invert) | 创建一个反色效果并且添加到滤镜中。 |
| [EffectErrorCode OH_Filter_SetColorMatrix(OH_Filter* filter, OH_Filter_ColorMatrix* matrix)](#oh_filter_setcolormatrix) | 通过矩阵创建一个自定义的效果并且添加到滤镜中。 |
| [EffectErrorCode OH_Filter_GetEffectPixelMap(OH_Filter* filter, OH_PixelmapNative** pixelmap)](#oh_filter_geteffectpixelmap) | 获取滤镜生成的位图。 |

## 函数说明

### OH_Filter_CreateEffect()

```c
EffectErrorCode OH_Filter_CreateEffect(OH_PixelmapNative* pixelmap, OH_Filter** filter)
```

**描述**

创建一个OH_Filter对象。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_PixelmapNative](capi-effectkit-oh-pixelmapnative.md)* pixelmap | [in] 创建滤镜的位图。不能为NULL。 |
| [OH_Filter](capi-effectkit-oh-filter.md)** filter | [out] 用来接收滤镜的二级指针。不能为NULL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [EffectErrorCode](capi-effect-types-h.md#effecterrorcode) | <ul><br>         <li>{@link EffectErrorCode#EFFECT_SUCCESS} 操作成功。</li><br>         <li>{@link EffectErrorCode#EFFECT_BAD_PARAMETER} pixelmap或filter为NULL。</li><br>         </ul> |

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
| [OH_Filter](capi-effectkit-oh-filter.md)* filter | [in] 被释放的对象指针。不能为NULL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [EffectErrorCode](capi-effect-types-h.md#effecterrorcode) | <ul><br>         <li>{@link EffectErrorCode#EFFECT_SUCCESS} 操作成功。</li><br>         <li>{@link EffectErrorCode#EFFECT_BAD_PARAMETER} filter为NULL。</li><br>         </ul> |

### OH_Filter_Blur()

```c
EffectErrorCode OH_Filter_Blur(OH_Filter* filter, float radius)
```

**描述**

创建一个毛玻璃滤镜效果，然后添加到滤镜里面。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Filter](capi-effectkit-oh-filter.md)* filter | [in] 滤镜指针。不能为NULL。 |
| float radius | [in] 毛玻璃效果的模糊半径，单位为像素。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [EffectErrorCode](capi-effect-types-h.md#effecterrorcode) | <ul><br>         <li>{@link EffectErrorCode#EFFECT_SUCCESS} 操作成功。</li><br>         <li>{@link EffectErrorCode#EFFECT_BAD_PARAMETER} filter为NULL。</li><br>         </ul> |

### OH_Filter_BlurWithTileMode()

```c
EffectErrorCode OH_Filter_BlurWithTileMode(OH_Filter* filter, float radius, EffectTileMode tileMode)
```

**描述**

创建一个毛玻璃滤镜效果，然后添加到滤镜里面，支持着色器效果平铺模式选择。

**起始版本：** 14

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Filter](capi-effectkit-oh-filter.md)* filter | [in] 滤镜指针。不能为NULL。 |
| float radius | [in] 毛玻璃效果的模糊半径，单位为像素。 |
| [EffectTileMode](capi-effect-types-h.md#effecttilemode) tileMode | [in] 着色器效果平铺模式，支持可选的具体模式可见[EffectTileMode](capi-effect-types-h.md#effecttilemode)枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [EffectErrorCode](capi-effect-types-h.md#effecterrorcode) | <ul><br>         <li>{@link EffectErrorCode#EFFECT_SUCCESS} 操作成功。</li><br>         <li>{@link EffectErrorCode#EFFECT_BAD_PARAMETER} filter为NULL。</li><br>         </ul> |

### OH_Filter_Brighten()

```c
EffectErrorCode OH_Filter_Brighten(OH_Filter* filter, float brightness)
```

**描述**

创建一个提亮效果并且添加到滤镜中。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Filter](capi-effectkit-oh-filter.md)* filter | [in] 滤镜指针。不能为NULL。 |
| float brightness | [in] 提亮效果的亮度值，取值范围在0-1之间，取值为0时图像保持不变，取值为1时图像全白。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [EffectErrorCode](capi-effect-types-h.md#effecterrorcode) | <ul><br>         <li>{@link EffectErrorCode#EFFECT_SUCCESS} 操作成功。</li><br>         <li>{@link EffectErrorCode#EFFECT_BAD_PARAMETER} filter为NULL。</li><br>         </ul> |

### OH_Filter_GrayScale()

```c
EffectErrorCode OH_Filter_GrayScale(OH_Filter* filter)
```

**描述**

创建一个灰度效果并且添加到滤镜中。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Filter](capi-effectkit-oh-filter.md)* filter | [in] 滤镜指针。不能为NULL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [EffectErrorCode](capi-effect-types-h.md#effecterrorcode) | <ul><br>         <li>{@link EffectErrorCode#EFFECT_SUCCESS} 操作成功。</li><br>         <li>{@link EffectErrorCode#EFFECT_BAD_PARAMETER} filter为NULL。</li><br>         </ul> |

### OH_Filter_Invert()

```c
EffectErrorCode OH_Filter_Invert(OH_Filter* filter)
```

**描述**

创建一个反色效果并且添加到滤镜中。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Filter](capi-effectkit-oh-filter.md)* filter | [in] 滤镜指针。不能为NULL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [EffectErrorCode](capi-effect-types-h.md#effecterrorcode) | <ul><br>         <li>{@link EffectErrorCode#EFFECT_SUCCESS} 操作成功。</li><br>         <li>{@link EffectErrorCode#EFFECT_BAD_PARAMETER} filter为NULL。</li><br>         </ul> |

### OH_Filter_SetColorMatrix()

```c
EffectErrorCode OH_Filter_SetColorMatrix(OH_Filter* filter, OH_Filter_ColorMatrix* matrix)
```

**描述**

通过矩阵创建一个自定义的效果并且添加到滤镜中。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Filter](capi-effectkit-oh-filter.md)* filter | [in] 滤镜指针。不能为NULL。 |
| [OH_Filter_ColorMatrix](capi-effectkit-oh-filter-colormatrix.md)* matrix | [in] 用来创建滤镜的自定义矩阵[OH_Filter_ColorMatrix](capi-effectkit-oh-filter-colormatrix.md)。不能为NULL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [EffectErrorCode](capi-effect-types-h.md#effecterrorcode) | <ul><br>         <li>{@link EffectErrorCode#EFFECT_SUCCESS} 操作成功。</li><br>         <li>{@link EffectErrorCode#EFFECT_BAD_PARAMETER} filter或matrix为NULL。</li><br>         </ul> |

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
| [OH_Filter](capi-effectkit-oh-filter.md)* filter | [in] 用来创建位图的滤镜指针。不能为NULL。 |
| [OH_PixelmapNative](capi-effectkit-oh-pixelmapnative.md)** pixelmap | [out] 用来接收位图的二级指针。不能为NULL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [EffectErrorCode](capi-effect-types-h.md#effecterrorcode) | <ul><br>         <li>{@link EffectErrorCode#EFFECT_SUCCESS} 操作成功。</li><br>         <li>{@link EffectErrorCode#EFFECT_BAD_PARAMETER} filter或pixelmap为NULL。</li><br>         </ul> |


