# drawing_image_filter.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## 概述

声明与绘图模块中的图像滤波器对象相关的函数。支持创建模糊、颜色变换、偏移、基于着色器等多种图像滤波器效果，并支持销毁滤波器对象，适用于图像处理和视觉特效增强的场景。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**引用文件：** <native_drawing/drawing_image_filter.h>

**库：** libnative_drawing.so

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**相关模块：** [Drawing](capi-drawing.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateBlur(float sigmaX, float sigmaY, OH_Drawing_TileMode tileMode, OH_Drawing_ImageFilter* imageFilter)](#oh_drawing_imagefiltercreateblur) | 创建具有模糊效果的图像滤波器。使用本函数创建的图像滤波器对象，在使用完毕后必须调用[OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy)进行销毁，否则会导致内存泄漏。 |
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateBlurWithCrop(float sigmaX, float sigmaY, OH_Drawing_TileMode tileMode, OH_Drawing_ImageFilter* input, const OH_Drawing_Rect* rect)](#oh_drawing_imagefiltercreateblurwithcrop) | 创建具有模糊效果的图像滤波器。支持传入裁剪矩形，用于限制模糊效果仅在图像的指定矩形区域内生效。使用本函数创建的图像滤波器对象，在使用完毕后必须调用[OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy)进行销毁，否则会导致内存泄漏。 |
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateFromColorFilter(OH_Drawing_ColorFilter* colorFilter, OH_Drawing_ImageFilter* imageFilter)](#oh_drawing_imagefiltercreatefromcolorfilter) | 创建具有颜色变换效果的图像滤波器。本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。colorFilter为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER；可用内存不足导致内存分配失败时也会产生错误码。请检查并确保传入的colorFilter为有效的颜色滤波器对象指针。使用本函数创建的图像滤波器对象，在使用完毕后必须调用[OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy)进行销毁，否则会导致内存泄漏。 |
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateOffset(float x, float y, OH_Drawing_ImageFilter* imageFilter)](#oh_drawing_imagefiltercreateoffset) | 创建一个偏移滤波器，将输入的滤波器按照指定向量进行平移。适用于创建阴影偏移效果或位移动画等场景。使用本函数创建的图像滤波器对象，在使用完毕后必须调用[OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy)进行销毁，否则会导致内存泄漏。 |
| [OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateFromShaderEffect(OH_Drawing_ShaderEffect* shaderEffect)](#oh_drawing_imagefiltercreatefromshadereffect) | 基于着色器创建一个图像滤波器。使用本函数创建的图像滤波器对象，在使用完毕后必须调用[OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy)进行销毁，否则会导致内存泄漏。 |
| [void OH_Drawing_ImageFilterDestroy(OH_Drawing_ImageFilter* imageFilter)](#oh_drawing_imagefilterdestroy) | 销毁图像滤波器对象并回收该对象占用的内存。 |

## 函数说明

### OH_Drawing_ImageFilterCreateBlur()

```c
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateBlur(float sigmaX, float sigmaY, OH_Drawing_TileMode tileMode, OH_Drawing_ImageFilter* imageFilter)
```

**描述**

创建具有模糊效果的图像滤波器。使用本函数创建的图像滤波器对象，在使用完毕后必须调用[OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy)进行销毁，否则会导致内存泄漏。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| float sigmaX | 表示沿x轴方向上高斯模糊的标准差，单位为px。传入小于等于0的值时不生效。 |
| float sigmaY | 表示沿y轴方向上高斯模糊的标准差，单位为px。传入小于等于0的值时不生效。 |
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileMode | 用于控制图像滤波器效果在图像边界处的平铺方式。 |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* imageFilter | 表示将要和当前图像滤波器叠加的输入滤波器，如果为NULL，表示直接将当前图像滤波器作用于原始图像。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* | 函数会返回一个指针，指针指向创建的图像滤波器对象[OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)。如果返回NULL，表示创建失败；可能的原因是可用内存不足。 |

### OH_Drawing_ImageFilterCreateBlurWithCrop()

```c
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateBlurWithCrop(float sigmaX, float sigmaY, OH_Drawing_TileMode tileMode, OH_Drawing_ImageFilter* input, const OH_Drawing_Rect* rect)
```

**描述**

创建具有模糊效果的图像滤波器。

支持传入裁剪矩形，用于限制模糊效果仅在图像的指定矩形区域内生效。使用本函数创建的图像滤波器对象，在使用完毕后必须调用[OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy)进行销毁，否则会导致内存泄漏。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| float sigmaX | 表示沿x轴方向上高斯模糊的标准差，单位为px。必须大于0.0，传入小于等于0的值时不生效。 |
| float sigmaY | 表示沿y轴方向上高斯模糊的标准差，单位为px。必须大于0.0，传入小于等于0的值时不生效。 |
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileMode | 用于控制图像滤波器效果在图像边界处的平铺方式。 |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* input | 表示将要和当前图像滤波器叠加的输入滤波器，如果为NULL，表示直接将当前图像滤波器作用于原始图像。 |
| [const OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | 表示裁剪的矩形区域，如果为NULL，表示直接将模糊效果作用于整个图像。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_Drawing_ImageFilter* | 函数会返回一个指针，指针指向创建的图像滤波器对象[OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)。如果返回NULL，表示创建失败；可能的原因是可用内存不足。 |

### OH_Drawing_ImageFilterCreateFromColorFilter()

```c
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateFromColorFilter(OH_Drawing_ColorFilter* colorFilter, OH_Drawing_ImageFilter* imageFilter)
```

**描述**

创建具有颜色变换效果的图像滤波器。本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。colorFilter为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER；可用内存不足导致内存分配失败时也会产生错误码。请检查并确保传入的colorFilter为有效的颜色滤波器对象指针。使用本函数创建的图像滤波器对象，在使用完毕后必须调用[OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy)进行销毁，否则会导致内存泄漏。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* colorFilter | 指向具有颜色变换效果的颜色滤波器对象[OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)。如果为NULL，返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* imageFilter | 表示将要和当前图像滤波器叠加的输入滤波器，如果为NULL，表示直接将当前图像滤波器作用于原始图像。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* | 函数会返回一个指针，指针指向创建的图像滤波器对象[OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)。如果返回NULL，表示创建失败；可能的原因是可用内存不足，或者是colorFilter为NULL。 |

### OH_Drawing_ImageFilterCreateOffset()

```c
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateOffset(float x, float y, OH_Drawing_ImageFilter* imageFilter)
```

**描述**

创建一个偏移滤波器，将输入的滤波器按照指定向量进行平移。适用于创建阴影偏移效果或位移动画等场景。使用本函数创建的图像滤波器对象，在使用完毕后必须调用[OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy)进行销毁，否则会导致内存泄漏。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| float x | 表示沿x轴方向的平移距离。 |
| float y | 表示沿y轴方向的平移距离。 |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* imageFilter | 需要进行平移的滤波器，如果为NULL，则将无滤波效果的绘制结果进行平移。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* | 函数会返回一个指针，指针指向创建的图像滤波器对象[OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)。如果返回NULL，表示创建失败；可能的原因是可用内存不足。 |

### OH_Drawing_ImageFilterCreateFromShaderEffect()

```c
OH_Drawing_ImageFilter* OH_Drawing_ImageFilterCreateFromShaderEffect(OH_Drawing_ShaderEffect* shaderEffect)
```

**描述**

基于着色器创建一个图像滤波器。使用本函数创建的图像滤波器对象，在使用完毕后必须调用[OH_Drawing_ImageFilterDestroy](#oh_drawing_imagefilterdestroy)进行销毁，否则会导致内存泄漏。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* shaderEffect | 表示要应用于图像的着色器效果。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* | 函数会返回一个指针，指针指向创建的图像滤波器对象[OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)。如果返回NULL，表示创建失败；可能的原因是可用内存不足，或者是shaderEffect为NULL。 |

### OH_Drawing_ImageFilterDestroy()

```c
void OH_Drawing_ImageFilterDestroy(OH_Drawing_ImageFilter* imageFilter)
```

**描述**

销毁图像滤波器对象并回收该对象占用的内存。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)* imageFilter | 指向图像滤波器对象[OH_Drawing_ImageFilter](capi-drawing-oh-drawing-imagefilter.md)的指针。 |
