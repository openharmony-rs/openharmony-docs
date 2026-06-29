# drawing_color_filter.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## 概述

声明与绘图模块中的颜色滤波器对象相关的函数。支持创建混合模式、组合、矩阵、伽马转换、亮度和光照等多种颜色滤波器效果，适用于图像渲染中的色彩调整与特效处理场景。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**引用文件：** <native_drawing/drawing_color_filter.h>

**库：** libnative_drawing.so

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11

**相关模块：** [Drawing](capi-drawing.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateBlendMode(uint32_t color, OH_Drawing_BlendMode blendMode)](#oh_drawing_colorfiltercreateblendmode) | 创建具有混合模式的颜色滤波器。 |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateCompose(OH_Drawing_ColorFilter* outerColorFilter,OH_Drawing_ColorFilter* innerColorFilter)](#oh_drawing_colorfiltercreatecompose) | 将两个颜色滤波器合成一个新的颜色滤波器。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>outerColorFilter、innerColorFilter任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateMatrix(const float matrix[20])](#oh_drawing_colorfiltercreatematrix) | 创建具有4x5颜色矩阵的颜色滤波器。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>matrix为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateLinearToSrgbGamma(void)](#oh_drawing_colorfiltercreatelineartosrgbgamma) | 创建一个从线性颜色空间转换到SRGB颜色空间的颜色滤波器。 |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateSrgbGammaToLinear(void)](#oh_drawing_colorfiltercreatesrgbgammatolinear) | 创建一个从SRGB颜色空间转换到线性颜色空间的颜色滤波器。 |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateLuma(void)](#oh_drawing_colorfiltercreateluma) | 创建一个颜色滤波器，将其输入的亮度值乘以透明度通道的值，并将红色、绿色和蓝色通道设置为零。 |
| [OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateLighting(uint32_t mulColor, uint32_t addColor)](#oh_drawing_colorfiltercreatelighting) | 创建一个光照颜色滤波器，此滤波器会将RGB通道的颜色值乘以一种颜色值并加上另一种颜色值，计算结果会被限制在0到255范围内。 |
| [void OH_Drawing_ColorFilterDestroy(OH_Drawing_ColorFilter* colorFilter)](#oh_drawing_colorfilterdestroy) | 销毁颜色滤波器对象，并回收该对象占用的内存。 |

## 函数说明

### OH_Drawing_ColorFilterCreateBlendMode()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateBlendMode(uint32_t color, OH_Drawing_BlendMode blendMode)
```

**描述**

创建具有混合模式的颜色滤波器，适用于需要按指定混合模式将源色与目标色合成的场景。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t color | 表示颜色，是一个32位（ARGB）变量。 |
| [OH_Drawing_BlendMode](capi-drawing-types-h.md#oh_drawing_blendmode) blendMode | 表示混合模式。支持的混合模式详见[OH_Drawing_BlendMode](capi-drawing-types-h.md#oh_drawing_blendmode)枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* | 返回创建的颜色滤波器对象的指针。 |

### OH_Drawing_ColorFilterCreateCompose()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateCompose(OH_Drawing_ColorFilter* outerColorFilter, OH_Drawing_ColorFilter* innerColorFilter)
```

**描述**

将两个颜色滤波器合成一个新的颜色滤波器。合成时先应用innerColorFilter进行滤波，再应用outerColorFilter进行滤波。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>outerColorFilter、innerColorFilter任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。请检查并确保传入的outerColorFilter和innerColorFilter为有效的颜色滤波器对象指针。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* outerColorFilter | 指向颜色滤波器中外部颜色滤波器对象的指针。 |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* innerColorFilter | 指向颜色滤波器中内部颜色滤波器对象的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* | 返回创建的颜色滤波器对象的指针。 |

### OH_Drawing_ColorFilterCreateMatrix()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateMatrix(const float matrix[20])
```

**描述**

创建具有4x5颜色矩阵的颜色滤波器，适用于需要自定义颜色变换的场景。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>matrix为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。请检查并确保传入的matrix为有效的浮点数组指针。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const float matrix[20] | 表示4x5颜色矩阵，用于对图像的颜色通道进行线性变换。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* | 返回创建的颜色滤波器对象的指针。 |

### OH_Drawing_ColorFilterCreateLinearToSrgbGamma()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateLinearToSrgbGamma(void)
```

**描述**

创建一个从线性颜色空间转换到SRGB颜色空间的颜色滤波器。该接口与OH_Drawing_ColorFilterCreateSrgbGammaToLinear互为逆操作。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* | 返回创建的颜色滤波器对象的指针。 |

### OH_Drawing_ColorFilterCreateSrgbGammaToLinear()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateSrgbGammaToLinear(void)
```

**描述**

创建一个从SRGB颜色空间转换到线性颜色空间的颜色滤波器。该接口与OH_Drawing_ColorFilterCreateLinearToSrgbGamma互为逆操作。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* | 返回创建的颜色滤波器对象的指针。 |

### OH_Drawing_ColorFilterCreateLuma()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateLuma(void)
```

**描述**

创建一个颜色滤波器，将其输入的亮度值乘以透明度通道的值，并将红色、绿色和蓝色通道设置为零。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* | 返回创建的颜色滤波器对象的指针。 |

### OH_Drawing_ColorFilterCreateLighting()

```c
OH_Drawing_ColorFilter* OH_Drawing_ColorFilterCreateLighting(uint32_t mulColor, uint32_t addColor)
```

**描述**

创建一个光照颜色滤波器，此滤波器会将RGB通道的颜色值乘以一种颜色值并加上另一种颜色值，计算结果会被限制在0到255范围内。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t mulColor | 用于乘法运算的颜色值，是一个32位（ARGB）变量。 |
| uint32_t addColor | 用于加法运算的颜色值，是一个32位（ARGB）变量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* | 返回创建的颜色滤波器对象的指针。 |

### OH_Drawing_ColorFilterDestroy()

```c
void OH_Drawing_ColorFilterDestroy(OH_Drawing_ColorFilter* colorFilter)
```

**描述**

销毁颜色滤波器对象，并回收该对象占用的内存。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_ColorFilter](capi-drawing-oh-drawing-colorfilter.md)* colorFilter | 表示指向颜色滤波器对象的指针。 |

