# drawing_shader_effect.h

## 概述

声明与绘图模块中的着色器对象相关的函数。

**引用文件：** <native_drawing/drawing_shader_effect.h>

**库：** libnative_drawing.so

**起始版本：** 11

**相关模块：** [Drawing](capi-drawing.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_Drawing_TileMode](#oh_drawing_tilemode) | OH_Drawing_TileMode | 着色器效果平铺模式的枚举。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateColorShader(const uint32_t color)](#oh_drawing_shadereffectcreatecolorshader) | 创建具有单一颜色的着色器。 |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateLinearGradient(const OH_Drawing_Point* startPt,const OH_Drawing_Point* endPt, const uint32_t* colors,const float* pos, uint32_t size, OH_Drawing_TileMode tileMode)](#oh_drawing_shadereffectcreatelineargradient) | 创建着色器，在两个指定点之间生成线性渐变。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>startPt、endPt、colors任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER；<br>tileMode不在枚举范围内时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。 |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateLinearGradientWithLocalMatrix(const OH_Drawing_Point2D* startPt, const OH_Drawing_Point2D* endPt, const uint32_t* colors, const float* pos,uint32_t size, OH_Drawing_TileMode tileMode, const OH_Drawing_Matrix* matrix)](#oh_drawing_shadereffectcreatelineargradientwithlocalmatrix) | 创建着色器，在两个指定点之间生成线性渐变。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>startPt、endPt、colors任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER；<br>tileMode不在枚举范围内时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。 |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateRadialGradient(const OH_Drawing_Point* centerPt, float radius,const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode)](#oh_drawing_shadereffectcreateradialgradient) | 创建着色器，在给定圆心和半径的情况下生成径向渐变。<br>从起点到终点颜色从内到外进行圆形渐变（从中间向外拉）被称为径向渐变。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>centerPt、colors任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER；<br>tileMode不在枚举范围内时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。 |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateRadialGradientWithLocalMatrix(const OH_Drawing_Point2D* centerPt, float radius, const uint32_t* colors, const float* pos, uint32_t size,OH_Drawing_TileMode tileMode, const OH_Drawing_Matrix* matrix)](#oh_drawing_shadereffectcreateradialgradientwithlocalmatrix) | 创建着色器，在给定圆心和半径的情况下生成径向渐变。<br>从起点到终点颜色从内到外进行圆形渐变（从中间向外拉）被称为径向渐变。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>centerPt、colors任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER；<br>tileMode不在枚举范围内时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。 |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateSweepGradientWithLocalMatrix(const OH_Drawing_Point* centerPt,const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode, const OH_Drawing_Matrix* matrix)](#oh_drawing_shadereffectcreatesweepgradientwithlocalmatrix) | 创建着色器，在给定中心的情况下结合矩阵变换生成扇形渐变。<br>颜色从0°到360°渐变被称为扇形渐变。 |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateSweepGradient(const OH_Drawing_Point* centerPt,const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode)](#oh_drawing_shadereffectcreatesweepgradient) | 创建着色器，在给定中心的情况下生成扇形渐变。<br>颜色从0°到360°渐变被称为扇形渐变。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>centerPt、colors任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER；<br>tileMode不在枚举范围内时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。 |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateImageShader(OH_Drawing_Image* image,OH_Drawing_TileMode tileX, OH_Drawing_TileMode tileY, const OH_Drawing_SamplingOptions* samplingOptions,const OH_Drawing_Matrix* matrix)](#oh_drawing_shadereffectcreateimageshader) | 创建图像着色器。此接口不建议用于录制类型的画布，会影响性能。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>image、samplingOptions任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER；<br>tileX、tileY任意一个不在枚举范围内时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。 |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateTwoPointConicalGradient(const OH_Drawing_Point2D* startPt,float startRadius, const OH_Drawing_Point2D* endPt, float endRadius, const uint32_t* colors, const float* pos,uint32_t size, OH_Drawing_TileMode tileMode, const OH_Drawing_Matrix* matrix)](#oh_drawing_shadereffectcreatetwopointconicalgradient) | 创建着色器，在给定两个圆之间生成渐变。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>startPt、endPt、colors任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER；<br>tileMode不在枚举范围内时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。 |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateCompose(OH_Drawing_ShaderEffect* dst,OH_Drawing_ShaderEffect* src, OH_Drawing_BlendMode mode)](#oh_drawing_shadereffectcreatecompose) | 按照指定的混合模式对两个着色器进行叠加，生成一个新的着色器。 |
| [void OH_Drawing_ShaderEffectDestroy(OH_Drawing_ShaderEffect* shaderEffect)](#oh_drawing_shadereffectdestroy) | 销毁着色器对象，并收回该对象占用的内存。 |
| [OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreatePixelMapShader(OH_Drawing_PixelMap* pixelMap,OH_Drawing_TileMode tileX, OH_Drawing_TileMode tileY, const OH_Drawing_SamplingOptions* samplingOptions,const OH_Drawing_Matrix* matrix)](#oh_drawing_shadereffectcreatepixelmapshader) | 创建像素图着色器。 |

## 枚举类型说明

### OH_Drawing_TileMode

```
enum OH_Drawing_TileMode
```

**描述**

着色器效果平铺模式的枚举。

**起始版本：** 11

| 枚举项 | 描述 |
| -- | -- |
| CLAMP | 如果着色器效果超出其原始边界，则复制边缘颜色。 |
| REPEAT | 在水平和垂直方向上重复着色器效果图像。 |
| MIRROR | 水平和垂直重复着色器效果图像，交替镜像。 |
| DECAL | 只在原始区域内绘制，其他地方返回透明黑色。 |


## 函数说明

### OH_Drawing_ShaderEffectCreatePixelMapShader()

```
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreatePixelMapShader(OH_Drawing_PixelMap* pixelMap,OH_Drawing_TileMode tileX, OH_Drawing_TileMode tileY, const OH_Drawing_SamplingOptions* samplingOptions,const OH_Drawing_Matrix* matrix)
```

**描述**

创建像素图着色器。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md)* pixelMap | 指向像素图[OH_Drawing_PixelMap](capi-drawing-oh-drawing-pixelmap.md)的指针。 |
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileX | 水平方向着色器效果平铺模式类型，支持可选的具体模式可见[OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode)枚举。 |
| [OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode) tileY | 垂直方向着色器效果平铺模式类型，支持可选的具体模式可见[OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode)枚举。 |
| [const OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md)* samplingOptions | 指向采样选项对象[OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md)的指针。 |
| [const OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | 指向矩阵对象[OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)的指针。如果矩阵指针为空，默认传入单位矩阵。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_Drawing_ShaderEffect* | 返回创建的着色器对象的指针。 |

### OH_Drawing_ShaderEffectCreateColorShader()

```
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateColorShader(const uint32_t color)
```

**描述**

创建具有单一颜色的着色器。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const uint32_t color | 表示着色器的ARGB格式颜色，该参数为32位无符号整数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* | 函数会返回一个指针，指针指向创建的着色器对象[OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)。如果对象返回NULL，表示创建失败；可能的原因是可用内存为空。 |

### OH_Drawing_ShaderEffectCreateLinearGradient()

```
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateLinearGradient(const OH_Drawing_Point* startPt,const OH_Drawing_Point* endPt, const uint32_t* colors,const float* pos, uint32_t size, OH_Drawing_TileMode tileMode)
```

**描述**

创建着色器，在两个指定点之间生成线性渐变。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>startPt、endPt、colors任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER；<br>tileMode不在枚举范围内时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* startPt | 表示渐变的起点。 |
| const [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* endPt | 表示渐变的终点。 |
| const uint32_t* colors | 表示在两个点之间分布的颜色。 |
| const float* pos | 表示colors中每个对应颜色的相对位置，数组长度需和colors保持一致。如果pos为NULL，颜色均匀分布在起点和终点之间。 |
| uint32_t size | 表示颜色和位置的数量（如果pos不为NULL）。 |
| [OH_Drawing_TileMode](#oh_drawing_tilemode) tileMode | 着色器效果平铺模式类型，支持可选的具体模式可见[OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode)枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* | 返回创建的着色器对象的指针。 |

### OH_Drawing_ShaderEffectCreateLinearGradientWithLocalMatrix()

```
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateLinearGradientWithLocalMatrix(const OH_Drawing_Point2D* startPt, const OH_Drawing_Point2D* endPt, const uint32_t* colors, const float* pos,uint32_t size, OH_Drawing_TileMode tileMode, const OH_Drawing_Matrix* matrix)
```

**描述**

创建着色器，在两个指定点之间生成线性渐变。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>startPt、endPt、colors任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER；<br>tileMode不在枚举范围内时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* startPt | 表示渐变的起点。 |
| const [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* endPt | 表示渐变的终点。 |
| const uint32_t* colors | 表示在两个点之间分布的颜色。 |
| const float* pos | 表示colors中每个对应颜色的相对位置，数组长度需和colors保持一致。如果pos为NULL，颜色均匀分布在起点和终点之间。 |
| uint32_t size | 表示颜色和位置的数量（如果pos不为NULL）。 |
| [OH_Drawing_TileMode](#oh_drawing_tilemode) tileMode | 着色器效果平铺模式类型，支持可选的具体模式可见[OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode)枚举。 |
| const [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | 表示作用于着色器上的矩阵变换，如果matrix是NULL, 默认是一个单位矩阵。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* | 函数会返回一个指针，指针指向创建的着色器对象[OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)。如果对象返回NULL，表示创建失败；可能的原因是可用内存为空，或者是startPt、endPt、colors至少一个为NULL。 |

### OH_Drawing_ShaderEffectCreateRadialGradient()

```
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateRadialGradient(const OH_Drawing_Point* centerPt, float radius,const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode)
```

**描述**

创建着色器，在给定圆心和半径的情况下生成径向渐变。<br>从起点到终点颜色从内到外进行圆形渐变（从中间向外拉）被称为径向渐变。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>centerPt、colors任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER；<br>tileMode不在枚举范围内时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* centerPt | 表示渐变的圆心。 |
| float radius | 表示渐变的半径，需为非负数。 |
| const uint32_t* colors | 表示在径向上分布的颜色。 |
| const float* pos | 表示colors中每个对应颜色的相对位置，数组长度需和colors保持一致。如果pos为NULL，颜色均匀分布在径向上。 |
| uint32_t size | 表示颜色和位置的数量（如果pos不为NULL）。 |
| [OH_Drawing_TileMode](#oh_drawing_tilemode) tileMode | 着色器效果平铺模式类型，支持可选的具体模式可见[OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode)枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* | 返回创建的着色器对象的指针。 |

### OH_Drawing_ShaderEffectCreateRadialGradientWithLocalMatrix()

```
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateRadialGradientWithLocalMatrix(const OH_Drawing_Point2D* centerPt, float radius, const uint32_t* colors, const float* pos, uint32_t size,OH_Drawing_TileMode tileMode, const OH_Drawing_Matrix* matrix)
```

**描述**

创建着色器，在给定圆心和半径的情况下生成径向渐变。<br>从起点到终点颜色从内到外进行圆形渐变（从中间向外拉）被称为径向渐变。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>centerPt、colors任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER；<br>tileMode不在枚举范围内时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* centerPt | 表示渐变的圆心。 |
| float radius | 表示渐变的半径。 |
| const uint32_t* colors | 表示在径向上分布的颜色。 |
| const float* pos | 表示colors中每个对应颜色的相对位置，数组长度需和colors保持一致。如果pos为NULL，颜色均匀分布在径向上。 |
| uint32_t size | 表示颜色和位置的数量（如果pos不为NULL）。 |
| [OH_Drawing_TileMode](#oh_drawing_tilemode) tileMode | 着色器效果平铺模式类型，支持可选的具体模式可见[OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode)枚举。 |
| const [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | 表示作用于着色器上的矩阵变换，如果matrix是NULL, 默认是一个单位矩阵。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* | 函数会返回一个指针，指针指向创建的着色器对象[OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)。如果对象返回NULL，表示创建失败；可能的原因是可用内存为空，或者是centerPt、colors至少一个为NULL。 |

### OH_Drawing_ShaderEffectCreateSweepGradientWithLocalMatrix()

```
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateSweepGradientWithLocalMatrix(const OH_Drawing_Point* centerPt,const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode, const OH_Drawing_Matrix* matrix)
```

**描述**

创建着色器，在给定中心的情况下结合矩阵变换生成扇形渐变。<br>颜色从0°到360°渐变被称为扇形渐变。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* centerPt | 表示渐变的圆心。 |
| const uint32_t* colors | 表示在两个点之间分布的颜色。 |
| const float* pos | 表示colors中每个对应颜色的相对位置，数组长度需和colors保持一致。如果pos为NULL，颜色均匀分布在0°和360°之间。 |
| uint32_t size | 表示颜色和位置的数量（如果pos不为NULL）。 |
| [OH_Drawing_TileMode](#oh_drawing_tilemode) tileMode | 着色器效果平铺模式类型，支持可选的具体模式可见[OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode)枚举。 |
| const [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | 表示作用于着色器上的矩阵变换，如果matrix是NULL, 默认是一个单位矩阵。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* | 函数会返回一个指针，指针指向创建的着色器对象[OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)。<br>存在以下任意一种情况时，会返回空指针：1.可用内存为空；2.centerPt、colors任意为空；3.tileMode超出枚举范围。 |

### OH_Drawing_ShaderEffectCreateSweepGradient()

```
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateSweepGradient(const OH_Drawing_Point* centerPt,const uint32_t* colors, const float* pos, uint32_t size, OH_Drawing_TileMode tileMode)
```

**描述**

创建着色器，在给定中心的情况下生成扇形渐变。<br>颜色从0°到360°渐变被称为扇形渐变。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>centerPt、colors任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER；<br>tileMode不在枚举范围内时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* centerPt | 表示渐变的圆心。 |
| const uint32_t* colors | 表示在两个点之间分布的颜色。 |
| const float* pos | 表示colors中每个对应颜色的相对位置，数组长度需和colors保持一致。如果pos为NULL，颜色均匀分布在0°和360°之间。 |
| uint32_t size | 表示颜色和位置的数量（如果pos不为NULL）。 |
| [OH_Drawing_TileMode](#oh_drawing_tilemode) tileMode | 着色器效果平铺模式类型，支持可选的具体模式可见[OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode)枚举。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* |  函数会返回一个指针，指针指向创建的着色器对象[OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)。<br>存在以下任意一种情况时，会返回空指针：1.可用内存为空；2.centerPt、colors任意为空；3.tileMode超出枚举范围。

### OH_Drawing_ShaderEffectCreateImageShader()

```
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateImageShader(OH_Drawing_Image* image,OH_Drawing_TileMode tileX, OH_Drawing_TileMode tileY, const OH_Drawing_SamplingOptions* samplingOptions,const OH_Drawing_Matrix* matrix)
```

**描述**

创建图像着色器。此接口不建议用于录制类型的画布，会影响性能。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>image、samplingOptions任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER；<br>tileX、tileY任意一个不在枚举范围内时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_Image](capi-drawing-oh-drawing-image.md)* image | 指向图片对象[OH_Drawing_Image](capi-drawing-oh-drawing-image.md)的指针。 |
| [OH_Drawing_TileMode](#oh_drawing_tilemode) tileX | 水平方向着色器效果平铺模式类型，支持可选的具体模式可见[OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode)枚举。 |
| [OH_Drawing_TileMode](#oh_drawing_tilemode) tileY | 垂直方向着色器效果平铺模式类型，支持可选的具体模式可见[OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode)枚举。 |
| const [OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md)* samplingOptions | 指向采样选项对象[OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md)的指针。 |
| const [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | 指向矩阵对象[OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)的指针。如果矩阵指针为空，默认传入单位矩阵。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* | 函数会返回一个指针，指针指向创建的着色器对象[OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)。<br>存在以下任意一种情况时，会返回空指针：1.可用内存为空；2.image、samplingOptions任意为空；3.tileX、tileY超出枚举范围。 |

### OH_Drawing_ShaderEffectCreateTwoPointConicalGradient()

```
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateTwoPointConicalGradient(const OH_Drawing_Point2D* startPt,float startRadius, const OH_Drawing_Point2D* endPt, float endRadius, const uint32_t* colors, const float* pos,uint32_t size, OH_Drawing_TileMode tileMode, const OH_Drawing_Matrix* matrix)
```

**描述**

创建着色器，在给定两个圆之间生成渐变。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>startPt、endPt、colors任意一个为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER；<br>tileMode不在枚举范围内时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* startPt | 表示渐变的起点圆心。 |
| float startRadius | 表示渐变的起点半径，需为非负数。 |
| const [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* endPt | 表示渐变的终点圆心。 |
| float endRadius | 表示渐变的终点半径，需为非负数。 |
| const uint32_t* colors | 表示在两个圆之间分布的颜色。 |
| const float* pos | 表示colors中每个对应颜色的相对位置，数组长度需和colors保持一致。如果pos为NULL，颜色均匀分布在两个圆之间。 |
| uint32_t size | 表示颜色和位置的数量(如果pos不为NULL)。 |
| [OH_Drawing_TileMode](#oh_drawing_tilemode) tileMode | 着色器效果平铺模式类型，支持可选的具体模式可见[OH_Drawing_TileMode](capi-drawing-shader-effect-h.md#oh_drawing_tilemode)枚举。 |
| const [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | 表示作用于着色器上的矩阵变换，如果matrix是NULL, 默认是一个单位矩阵。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* | 函数会返回一个指针，指针指向创建的着色器对象[OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)。如果对象返回NULL，表示创建失败；可能的原因是：1.可用内存为空；2.startPt、endPt、colors任意为空；3.tileMode超出枚举范围。 |

### OH_Drawing_ShaderEffectCreateCompose()

```
OH_Drawing_ShaderEffect* OH_Drawing_ShaderEffectCreateCompose(OH_Drawing_ShaderEffect* dst,OH_Drawing_ShaderEffect* src, OH_Drawing_BlendMode mode)
```

**描述**

按照指定的混合模式对两个着色器进行叠加，生成一个新的着色器。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* dst | 在混合模式中作为目标色的着色器。 |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* src | 在混合模式中作为源色的着色器。 |
| [OH_Drawing_BlendMode](capi-drawing-types-h.md#oh_drawing_blendmode) mode | 混合模式[OH_Drawing_BlendMode](capi-drawing-types-h.md#oh_drawing_blendmode)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* | 函数会返回一个指针，指针指向创建的着色器对象[OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)。<br>当可用内存为空，或者是dst、src任意一个为空，或mode超出枚举范围时，结果返回NULL，表示创建失败。 |

### OH_Drawing_ShaderEffectDestroy()

```
void OH_Drawing_ShaderEffectDestroy(OH_Drawing_ShaderEffect* shaderEffect)
```

**描述**

销毁着色器对象，并收回该对象占用的内存。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 11


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_ShaderEffect](capi-drawing-oh-drawing-shadereffect.md)* shaderEffect | 表示指向着色器对象的指针。 |


