# drawing_sampling_options.h
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## 概述

文件中定义了与采样选项相关的功能函数，用于创建、拷贝和销毁采样选项对象，以及指定图像采样时的过滤模式和纹理采样时的多级渐远纹理模式。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**引用文件：** <native_drawing/drawing_sampling_options.h>

**库：** libnative_drawing.so

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**相关模块：** [Drawing](capi-drawing.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_Drawing_FilterMode](#oh_drawing_filtermode) | OH_Drawing_FilterMode | 过滤模式枚举。 |
| [OH_Drawing_MipmapMode](#oh_drawing_mipmapmode) | OH_Drawing_MipmapMode | 多级渐远纹理模式枚举。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_Drawing_SamplingOptions* OH_Drawing_SamplingOptionsCreate(OH_Drawing_FilterMode filterMode,OH_Drawing_MipmapMode mipmapMode)](#oh_drawing_samplingoptionscreate) | 创建一个采样选项对象。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>mipmapMode不在枚举范围内时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。<br>使用完毕后，必须调用[OH_Drawing_SamplingOptionsDestroy](#oh_drawing_samplingoptionsdestroy)销毁采样选项对象并释放内存，避免内存泄漏。 |
| [OH_Drawing_SamplingOptions* OH_Drawing_SamplingOptionsCopy(OH_Drawing_SamplingOptions* samplingOptions)](#oh_drawing_samplingoptionscopy) | 拷贝一个已有采样选项对象。<br> 本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br> samplingOptions为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。副本为独立的新对象，使用完毕后，必须调用[OH_Drawing_SamplingOptionsDestroy](#oh_drawing_samplingoptionsdestroy)销毁副本对象并释放内存，避免内存泄漏。 |
| [void OH_Drawing_SamplingOptionsDestroy(OH_Drawing_SamplingOptions* samplingOptions)](#oh_drawing_samplingoptionsdestroy) | 销毁采样选项对象，并回收该对象占有的内存。 |

## 枚举类型说明

### OH_Drawing_FilterMode

```c
enum OH_Drawing_FilterMode
```

**描述**

过滤模式枚举。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| FILTER_MODE_NEAREST | 邻近过滤模式，采用最近邻采样，使用距离采样点最近的像素值。 |
| FILTER_MODE_LINEAR | 线性过滤模式，采用线性插值采样，在相邻像素之间进行插值计算。 |

### OH_Drawing_MipmapMode

```c
enum OH_Drawing_MipmapMode
```

**描述**

多级渐远纹理模式枚举。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| MIPMAP_MODE_NONE | 忽略多级渐远纹理级别。 |
| MIPMAP_MODE_NEAREST | 邻近多级渐远纹理级别采样。 |
| MIPMAP_MODE_LINEAR | 两个邻近多级渐远纹理级别之间，线性插值采样。 |


## 函数说明

### OH_Drawing_SamplingOptionsCreate()

```c
OH_Drawing_SamplingOptions* OH_Drawing_SamplingOptionsCreate(OH_Drawing_FilterMode filterMode, OH_Drawing_MipmapMode mipmapMode)
```

**描述**

创建一个采样选项对象。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>mipmapMode不在枚举范围内时返回OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE。<br>使用完毕后，必须调用[OH_Drawing_SamplingOptionsDestroy](#oh_drawing_samplingoptionsdestroy)销毁采样选项对象并释放内存，避免内存泄漏。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_FilterMode](#oh_drawing_filtermode) filterMode | 过滤采样模式，用于指定图像采样时的过滤方式。FILTER_MODE_NEAREST为邻近过滤，采用最近邻采样，适合对性能要求高、对画面平滑度要求不高的场景；FILTER_MODE_LINEAR为线性过滤，采用线性插值采样，适合对画面平滑度和质量要求较高的场景。 |
| [OH_Drawing_MipmapMode](#oh_drawing_mipmapmode) mipmapMode | 多级渐远纹理采样模式，用于指定多级渐远纹理的采样方式。MIPMAP_MODE_NONE为忽略多级渐远纹理级别，适合不使用多级渐远纹理的场景；MIPMAP_MODE_NEAREST为邻近多级渐远纹理级别采样，适合性能优先的场景；MIPMAP_MODE_LINEAR为两个邻近多级渐远纹理级别之间线性插值采样，适合对画质要求较高的场景。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md)* | 函数会返回一个指针，指针指向创建的采样选项对象[OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md)。如果返回NULL，表示创建失败；可能的原因是可用内存不足，或者是mipmapMode不在枚举范围内。 |

### OH_Drawing_SamplingOptionsCopy()

```c
OH_Drawing_SamplingOptions* OH_Drawing_SamplingOptionsCopy(OH_Drawing_SamplingOptions* samplingOptions)
```

**描述**

创建一个采样选项对象副本[OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md)，用于拷贝一个已有采样选项对象。

本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。

samplingOptions为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。

拷贝对象为独立的新对象，使用完毕后，必须调用[OH_Drawing_SamplingOptionsDestroy](#oh_drawing_samplingoptionsdestroy)销毁副本对象并释放内存，避免内存泄漏。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md)* samplingOptions | 指向采样选项对象OH_Drawing_SamplingOptions的指针。为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md)* | 函数会返回一个指针，指针指向创建的采样选项拷贝对象[OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md)。如果返回NULL，表示创建失败；可能的原因是可用内存不足，或者是samplingOptions为NULL。 |

### OH_Drawing_SamplingOptionsDestroy()

```c
void OH_Drawing_SamplingOptionsDestroy(OH_Drawing_SamplingOptions* samplingOptions)
```

**描述**

销毁采样选项对象，并回收该对象占有的内存。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_SamplingOptions](capi-drawing-oh-drawing-samplingoptions.md)* samplingOptions | 指向采样选项对象OH_Drawing_SamplingOptions的指针。若为NULL，则不执行销毁操作。 |
