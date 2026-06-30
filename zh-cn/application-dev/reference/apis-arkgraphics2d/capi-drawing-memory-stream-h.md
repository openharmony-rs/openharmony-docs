# drawing_memory_stream.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## 概述

文件中定义了与内存流相关的功能函数，支持基于内存数据创建和销毁内存流对象。内存流支持数据拷贝或直接引用两种访问方式。<br>本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**引用文件：** \<native_drawing/drawing_memory_stream.h\>

**库：** libnative_drawing.so

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12

**相关模块：** [Drawing](capi-drawing.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_Drawing_MemoryStream* OH_Drawing_MemoryStreamCreate(const void* data, size_t length, bool copyData)](#oh_drawing_memorystreamcreate) | 创建一个内存流对象，用于将内存中的数据封装为流，可作为数据源供图形处理接口（如图像解码）等后续绘制接口使用。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>data为NULL或者length等于0时，错误码被设置为OH_DRAWING_ERROR_INVALID_PARAMETER，请检查传入的data参数是否为有效指针，并确保length大于0。 |
| [void OH_Drawing_MemoryStreamDestroy(OH_Drawing_MemoryStream* memoryStream)](#oh_drawing_memorystreamdestroy) | 销毁由[OH_Drawing_MemoryStreamCreate()](#oh_drawing_memorystreamcreate)创建的内存流对象并回收该对象占用的内存。 |

## 函数说明

### OH_Drawing_MemoryStreamCreate()

```c
OH_Drawing_MemoryStream* OH_Drawing_MemoryStreamCreate(const void* data, size_t length, bool copyData)
```

**描述**

创建一个内存流对象，用于将内存中的数据封装为流，可作为数据源供图形处理接口（如图像解码）等后续绘制接口使用。<br>本接口会产生错误码，可以通过[OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget)查看错误码的取值。<br>data为NULL或者length等于0时，错误码被设置为OH_DRAWING_ERROR_INVALID_PARAMETER，请检查传入的data参数是否为有效指针，并确保length大于0。

**配对调用：** 调用[OH_Drawing_MemoryStreamCreate()](#oh_drawing_memorystreamcreate)创建内存流对象后，必须在使用完毕后调用[OH_Drawing_MemoryStreamDestroy()](#oh_drawing_memorystreamdestroy)销毁该对象并回收内存；若未调用销毁方法会导致内存泄漏。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const void* data | 要创建内存流的数据缓冲区，数据为二进制字节流，长度由length参数指定，单位：字节。data不能为NULL，为NULL时返回OH_DRAWING_ERROR_INVALID_PARAMETER。当copyData为false时，调用者还需确保data指向的数据在内存流对象生命周期内保持有效。 |
| size_t length | 数据段长度，单位：字节，取值必须大于0。为0时返回OH_DRAWING_ERROR_INVALID_PARAMETER。 |
| bool copyData | 是否拷贝数据。true表示内存流对象会拷贝一份数据段数据，false表示内存流对象直接使用数据段数据，不拷贝。当copyData为false时，调用者需确保data指向的数据在内存流对象生命周期内保持有效，否则可能导致读取异常。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Drawing_MemoryStream](capi-drawing-oh-drawing-memorystream.md)* | 指向创建的内存流对象[OH_Drawing_MemoryStream](capi-drawing-oh-drawing-memorystream.md)的指针，可作为数据源传递给后续图形处理接口（如图像解码）使用。 |

### OH_Drawing_MemoryStreamDestroy()

```c
void OH_Drawing_MemoryStreamDestroy(OH_Drawing_MemoryStream* memoryStream)
```

**描述**

销毁由[OH_Drawing_MemoryStreamCreate()](#oh_drawing_memorystreamcreate)创建的内存流对象并回收该对象占用的内存。

**配对调用：** 必须与[OH_Drawing_MemoryStreamCreate()](#oh_drawing_memorystreamcreate)成对使用；在内存流对象使用完毕后调用本接口释放资源，避免内存泄漏；销毁后不应再访问该对象指针。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeDrawing

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_Drawing_MemoryStream](capi-drawing-oh-drawing-memorystream.md)* memoryStream | 指向由[OH_Drawing_MemoryStreamCreate()](#oh_drawing_memorystreamcreate)创建的内存流对象[OH_Drawing_MemoryStream](capi-drawing-oh-drawing-memorystream.md)的指针，该指针不能为NULL，传入NULL可能导致不可预期行为或崩溃。 |



