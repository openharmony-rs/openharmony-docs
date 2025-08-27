# drawing_brush.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## 概述

文件中定义了与画刷相关的功能函数。

<!--RP1-->
**相关示例：** [NDKAPIDrawing (API14)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Drawing/NDKAPIDrawing)<!--RP1End-->

**引用文件：** <native_drawing/drawing_brush.h>

**库：** libnative_drawing.so

**起始版本：** 8

**相关模块：** [Drawing](capi-drawing.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_NativeColorSpaceManager](capi-nativecolorspacemanager-oh-nativecolorspacemanager.md) | OH_NativeColorSpaceManager | 声明色域管理对象，提供获取色域基础属性的能力。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_Drawing_Brush* OH_Drawing_BrushCreate(void)](#oh_drawing_brushcreate) | 用于创建一个画刷对象。 |
| [OH_Drawing_Brush* OH_Drawing_BrushCopy(OH_Drawing_Brush* brush)](#oh_drawing_brushcopy) | 创建一个画刷对象副本[OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)，用于拷贝一个已有画刷对象。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [void OH_Drawing_BrushDestroy(OH_Drawing_Brush* brush)](#oh_drawing_brushdestroy) | 用于销毁画刷对象并回收该对象占有的内存。 |
| [bool OH_Drawing_BrushIsAntiAlias(const OH_Drawing_Brush* brush)](#oh_drawing_brushisantialias) | 用于获取画刷是否设置抗锯齿属性，如果为真则说明画刷会启用抗锯齿功能，在绘制图形时会对图形的边缘像素进行半透明的模糊处理。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [void OH_Drawing_BrushSetAntiAlias(OH_Drawing_Brush* brush, bool antiAlias)](#oh_drawing_brushsetantialias) | 用于设置画刷的抗锯齿属性，设置为真则画刷在绘制图形时会对图形的边缘像素进行半透明的模糊处理。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [uint32_t OH_Drawing_BrushGetColor(const OH_Drawing_Brush* brush)](#oh_drawing_brushgetcolor) | 用于获取画刷的颜色属性，颜色属性描述了画刷填充图形时使用的颜色，用一个32位（ARGB）的变量表示。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [void OH_Drawing_BrushSetColor(OH_Drawing_Brush* brush, uint32_t color)](#oh_drawing_brushsetcolor) | 用于设置画刷的颜色属性，颜色属性描述了画刷填充图形时使用的颜色，用一个32位（ARGB）的变量表示。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [uint8_t OH_Drawing_BrushGetAlpha(const OH_Drawing_Brush* brush)](#oh_drawing_brushgetalpha) | 获取画刷的透明度值。画刷在填充形状时透明通道会使用该值。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [void OH_Drawing_BrushSetAlpha(OH_Drawing_Brush* brush, uint8_t alpha)](#oh_drawing_brushsetalpha) | 为画刷设置透明度值。画刷在填充形状时透明通道会使用该值。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [void OH_Drawing_BrushSetShaderEffect(OH_Drawing_Brush* brush, OH_Drawing_ShaderEffect* shaderEffect)](#oh_drawing_brushsetshadereffect) | 为画刷设置着色器效果。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [void OH_Drawing_BrushSetShadowLayer(OH_Drawing_Brush* brush, OH_Drawing_ShadowLayer* shadowLayer)](#oh_drawing_brushsetshadowlayer) | 为画刷设置阴影层，设置的阴影层效果当前仅在绘制文字时生效。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [void OH_Drawing_BrushSetFilter(OH_Drawing_Brush* brush, OH_Drawing_Filter* filter)](#oh_drawing_brushsetfilter) | 为画刷设置滤波器[OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md)。滤波器是一个容器，可以承载蒙版滤波器和颜色滤波器。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [void OH_Drawing_BrushGetFilter(OH_Drawing_Brush* brush, OH_Drawing_Filter* filter)](#oh_drawing_brushgetfilter) | 从画刷获取滤波器[OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md)。滤波器是一个容器，可以承载蒙版滤波器和颜色滤波器。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush、filter任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [void OH_Drawing_BrushSetBlendMode(OH_Drawing_Brush* brush, OH_Drawing_BlendMode blendMode)](#oh_drawing_brushsetblendmode) | 为画刷设置一个混合器，该混合器实现了指定的混合模式枚举。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER；<br>blendMode不在枚举范围内时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。 |
| [void OH_Drawing_BrushReset(OH_Drawing_Brush* brush)](#oh_drawing_brushreset) | 将画刷重置至初始状态，清空所有已设置的属性。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [OH_Drawing_ErrorCode OH_Drawing_BrushSetColor4f(OH_Drawing_Brush* brush, float a, float r, float g, float b,OH_NativeColorSpaceManager* colorSpaceManager)](#oh_drawing_brushsetcolor4f) | 设置画刷的颜色。颜色将被画刷用来填充形状。<br> 颜色采用浮点数表示的ARGB格式，色彩空间由[OH_NativeColorSpaceManager](capi-nativecolorspacemanager-oh-nativecolorspacemanager.md)指定。<br> 如果colorSpaceManager为nullptr，使用SRGB（基于IEC 61966-2.1：1999的标准红绿蓝色彩空间）色彩空间作为默认值。 |
| [OH_Drawing_ErrorCode OH_Drawing_BrushGetAlphaFloat(const OH_Drawing_Brush* brush, float* a)](#oh_drawing_brushgetalphafloat) | 获取画刷颜色的透明度值。 |
| [OH_Drawing_ErrorCode OH_Drawing_BrushGetRedFloat(const OH_Drawing_Brush* brush, float* r)](#oh_drawing_brushgetredfloat) | 获取画刷颜色的红色分量。 |
| [OH_Drawing_ErrorCode OH_Drawing_BrushGetGreenFloat(const OH_Drawing_Brush* brush, float* g)](#oh_drawing_brushgetgreenfloat) | 获取画刷颜色的绿色分量。 |
| [OH_Drawing_ErrorCode OH_Drawing_BrushGetBlueFloat(const OH_Drawing_Brush* brush, float* b)](#oh_drawing_brushgetbluefloat) | 获取画刷颜色的蓝色分量。 |

## 函数说明

### OH_Drawing_BrushCreate()

```
OH_Drawing_Brush* OH_Drawing_BrushCreate(void)
```

**描述**

用于创建一个画刷对象。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 8

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* | 函数会返回一个指针，指针指向创建的画刷对象。 |

### OH_Drawing_BrushCopy()

```
OH_Drawing_Brush* OH_Drawing_BrushCopy(OH_Drawing_Brush* brush)
```

**描述**

创建一个画刷对象副本[OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)，用于拷贝一个已有画刷对象。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | 指向画刷对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* | 函数会返回一个指针，指针指向创建的画刷对象副本[OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)。如果对象返回NULL，表示创建失败；可能的原因是可用内存为空，或者是brush为NULL。 |

### OH_Drawing_BrushDestroy()

```
void OH_Drawing_BrushDestroy(OH_Drawing_Brush* brush)
```

**描述**

用于销毁画刷对象并回收该对象占有的内存。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | 指向画刷对象的指针。 |

### OH_Drawing_BrushIsAntiAlias()

```
bool OH_Drawing_BrushIsAntiAlias(const OH_Drawing_Brush* brush)
```

**描述**

用于获取画刷是否设置抗锯齿属性，如果为真则说明画刷会启用抗锯齿功能，在绘制图形时会对图形的边缘像素进行半透明的模糊处理。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | 指向画刷对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 函数返回画刷对象是否设置抗锯齿属性，返回真则设置了抗锯齿，返回假则没有设置抗锯齿。 |

### OH_Drawing_BrushSetAntiAlias()

```
void OH_Drawing_BrushSetAntiAlias(OH_Drawing_Brush* brush, bool antiAlias)
```

**描述**

用于设置画刷的抗锯齿属性，设置为真则画刷在绘制图形时会对图形的边缘像素进行半透明的模糊处理。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | 指向画刷对象的指针。 |
| bool antiAlias | 真为抗锯齿，假则不做抗锯齿处理。 |

### OH_Drawing_BrushGetColor()

```
uint32_t OH_Drawing_BrushGetColor(const OH_Drawing_Brush* brush)
```

**描述**

用于获取画刷的颜色属性，颜色属性描述了画刷填充图形时使用的颜色，用一个32位（ARGB）的变量表示。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | 指向画刷对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | 函数返回一个描述颜色的32位（ARGB）变量。 |

### OH_Drawing_BrushSetColor()

```
void OH_Drawing_BrushSetColor(OH_Drawing_Brush* brush, uint32_t color)
```

**描述**

用于设置画刷的颜色属性，颜色属性描述了画刷填充图形时使用的颜色，用一个32位（ARGB）的变量表示。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 8


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | 指向画刷对象的指针。 |
| uint32_t color | 描述颜色的32位（ARGB）变量。 |

### OH_Drawing_BrushGetAlpha()

```
uint8_t OH_Drawing_BrushGetAlpha(const OH_Drawing_Brush* brush)
```

**描述**

获取画刷的透明度值。画刷在填充形状时透明通道会使用该值。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | 表示指向画刷对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint8_t | 返回一个8位变量，用于表示透明度值。 |

### OH_Drawing_BrushSetAlpha()

```
void OH_Drawing_BrushSetAlpha(OH_Drawing_Brush* brush, uint8_t alpha)
```

**描述**

为画刷设置透明度值。画刷在填充形状时透明通道会使用该值。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | 指向画刷对象的指针。 |
| uint8_t alpha | 表示要设置的透明度值，是一个8位变量。 |

### OH_Drawing_BrushSetShaderEffect()

```
void OH_Drawing_BrushSetShaderEffect(OH_Drawing_Brush* brush, OH_Drawing_ShaderEffect* shaderEffect)
```

**描述**

为画刷设置着色器效果。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | 指向画刷对象的指针。 |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* shaderEffect | 表示指向着色器对象的指针，为NULL表示清空画刷的着色器效果。 |

### OH_Drawing_BrushSetShadowLayer()

```
void OH_Drawing_BrushSetShadowLayer(OH_Drawing_Brush* brush, OH_Drawing_ShadowLayer* shadowLayer)
```

**描述**

为画刷设置阴影层，设置的阴影层效果当前仅在绘制文字时生效。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | 指向画刷对象的指针。 |
| [OH_Drawing_ShadowLayer](capi-drawing-oh-drawing-shadowlayer.md)* shadowLayer | 表示指向阴影层的指针，为NULL表示清空画刷的阴影层效果。 |

### OH_Drawing_BrushSetFilter()

```
void OH_Drawing_BrushSetFilter(OH_Drawing_Brush* brush, OH_Drawing_Filter* filter)
```

**描述**

为画刷设置滤波器[OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md)。滤波器是一个容器，可以承载蒙版滤波器和颜色滤波器。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | 指向画刷对象的指针。 |
| [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md)* filter | 表示指向滤波器对象的指针，为NULL表示清空画刷滤波器。 |

### OH_Drawing_BrushGetFilter()

```
void OH_Drawing_BrushGetFilter(OH_Drawing_Brush* brush, OH_Drawing_Filter* filter)
```

**描述**

从画刷获取滤波器[OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md)。滤波器是一个容器，可以承载蒙版滤波器和颜色滤波器。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush、filter任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | 指向画刷对象[OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)的指针。 |
| [OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md)* filter | 表示指向滤波器对象[OH_Drawing_Filter](capi-drawing-oh-drawing-filter.md)的指针。 |

### OH_Drawing_BrushSetBlendMode()

```
void OH_Drawing_BrushSetBlendMode(OH_Drawing_Brush* brush, OH_Drawing_BlendMode blendMode)
```

**描述**

为画刷设置一个混合器，该混合器实现了指定的混合模式枚举。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER；<br>blendMode不在枚举范围内时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | 指向画刷对象[OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)的指针。 |
| [OH_Drawing_BlendMode](capi-drawing-types-h.md#oh_drawing_blendmode) blendMode | 混合模式枚举类型[OH_Drawing_BlendMode](capi-drawing-types-h.md#oh_drawing_blendmode)。 |

### OH_Drawing_BrushReset()

```
void OH_Drawing_BrushReset(OH_Drawing_Brush* brush)
```

**描述**

将画刷重置至初始状态，清空所有已设置的属性。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>brush为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | 指向画刷对象[OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)的指针。 |


### OH_Drawing_BrushSetColor4f()

```
OH_Drawing_ErrorCode OH_Drawing_BrushSetColor4f(OH_Drawing_Brush* brush, float a, float r, float g, float b,OH_NativeColorSpaceManager* colorSpaceManager)
```

**描述**

设置画刷的颜色。颜色将被画刷用来填充形状。<br> 颜色采用浮点数表示的ARGB格式，色彩空间由[OH_NativeColorSpaceManager](capi-nativecolorspacemanager-oh-nativecolorspacemanager.md)指定。<br> 如果colorSpaceManager为nullptr，使用SRGB（基于IEC 61966-2.1：1999的标准红绿蓝色彩空间）色彩空间作为默认值。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_Drawing_Brush* brush | 表示指向[OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)对象的指针。 |
| float a | 表示颜色中的透明度值，用0.0 ~ 1.0之间的浮点数表示，大于1.0时，取1.0，小于0.0时，取0.0。 |
| float r | 表示颜色中的红色分量，用0.0 ~ 1.0之间的浮点数表示，大于1.0时，取1.0，小于0.0时，取0.0。 |
| float g | 表示颜色中的绿色分量，用0.0 ~ 1.0之间的浮点数表示，大于1.0时，取1.0，小于0.0时，取0.0。 |
| float b | 表示颜色中的蓝色分量，用0.0 ~ 1.0之间的浮点数表示，大于1.0时，取1.0，小于0.0时，取0.0。 |
| [OH_NativeColorSpaceManager](capi-nativecolorspacemanager-oh-nativecolorspacemanager.md)* colorSpaceManager | 表示指向[OH_NativeColorSpaceManager](capi-nativecolorspacemanager-oh-nativecolorspacemanager.md)对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | 函数返回执行结果。<br> 返回OH_DRAWING_SUCCESS，表示执行成功。<br> 返回OH_DRAWING_ERROR_INVALID_PARAMETER，表示参数brush为NULL。 |

### OH_Drawing_BrushGetAlphaFloat()

```
OH_Drawing_ErrorCode OH_Drawing_BrushGetAlphaFloat(const OH_Drawing_Brush* brush, float* a)
```

**描述**

获取画刷颜色的透明度值。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | 表示指向[OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)对象的指针。 |
| float* a | 表示颜色的透明度，范围为0.0 ~ 1.0的浮点数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | 函数返回执行结果。<br> 返回OH_DRAWING_SUCCESS，表示执行成功。<br> 返回OH_DRAWING_ERROR_INVALID_PARAMETER，表示参数brush或a为NULL。 |

### OH_Drawing_BrushGetRedFloat()

```
OH_Drawing_ErrorCode OH_Drawing_BrushGetRedFloat(const OH_Drawing_Brush* brush, float* r)
```

**描述**

获取画刷颜色的红色分量。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | 表示指向[OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)对象的指针。 |
| float* r | 表示颜色中的红色分量，范围为0.0 ~ 1.0的浮点数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | 函数返回执行结果。<br> 返回OH_DRAWING_SUCCESS，表示执行成功。<br> 返回OH_DRAWING_ERROR_INVALID_PARAMETER，表示参数brush或r为NULL。 |

### OH_Drawing_BrushGetGreenFloat()

```
OH_Drawing_ErrorCode OH_Drawing_BrushGetGreenFloat(const OH_Drawing_Brush* brush, float* g)
```

**描述**

获取画刷颜色的绿色分量。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | 表示指向[OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)对象的指针。 |
| float* g | 表示颜色中的绿色分量，范围为0.0 ~ 1.0的浮点数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | 函数返回执行结果。<br> 返回OH_DRAWING_SUCCESS，表示执行成功。<br> 返回OH_DRAWING_ERROR_INVALID_PARAMETER，表示参数brush或g为NULL。 |

### OH_Drawing_BrushGetBlueFloat()

```
OH_Drawing_ErrorCode OH_Drawing_BrushGetBlueFloat(const OH_Drawing_Brush* brush, float* b)
```

**描述**

获取画刷颜色的蓝色分量。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)* brush | 表示指向[OH_Drawing_Brush](capi-drawing-oh-drawing-brush.md)对象的指针。 |
| float* b | 表示颜色中的蓝色分量，范围为0.0 ~ 1.0的浮点数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | 函数返回执行结果。<br> 返回OH_DRAWING_SUCCESS，表示执行成功。<br> 返回OH_DRAWING_ERROR_INVALID_PARAMETER，表示参数brush或b为NULL。 |