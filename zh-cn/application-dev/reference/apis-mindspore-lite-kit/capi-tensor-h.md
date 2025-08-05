# tensor.h

<!--Kit: MindSpore Lite Kit-->
<!--Subsystem: AI-->
<!--Owner: @zhuguodong8-->
<!--SE: @zhuguodong8; @jjfeing-->
<!--TSE: @principal87-->

## 概述

提供了张量相关的接口，可用于创建和修改张量信息，该接口是非线程安全的。

**引用文件：** <mindspore/tensor.h>

**库：** libmindspore_lite_ndk.so

**系统能力：** SystemCapability.Ai.MindSpore

**起始版本：** 9

**相关模块：** [MindSpore](capi-mindspore.md)

## 汇总

### 结构体

| 名称 | typedef关键字                                                 | 描述 |
|----|------------------------------------------------------------|----|
| void *   | [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) | 指向张量对象句柄。   |
| void *   | [OH_AI_AllocatorHandle](capi-mindspore-oh-ai-allocatorhandle.md)  | 指向内存分配器对象句柄。   |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_AI_API OH_AI_TensorHandle OH_AI_TensorCreate(const char *name, OH_AI_DataType type, const int64_t *shape,size_t shape_num, const void *data, size_t data_len)](#oh_ai_tensorcreate) | 创建一个张量对象。 |
| [OH_AI_API void OH_AI_TensorDestroy(OH_AI_TensorHandle *tensor)](#oh_ai_tensordestroy) | 释放张量对象。 |
| [OH_AI_API OH_AI_TensorHandle OH_AI_TensorClone(OH_AI_TensorHandle tensor)](#oh_ai_tensorclone) | 深拷贝一个张量。 |
| [OH_AI_API void OH_AI_TensorSetName(OH_AI_TensorHandle tensor, const char *name)](#oh_ai_tensorsetname) | 设置张量的名称。 |
| [OH_AI_API const char *OH_AI_TensorGetName(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetname) | 获取张量的名称。 |
| [OH_AI_API void OH_AI_TensorSetDataType(OH_AI_TensorHandle tensor, OH_AI_DataType type)](#oh_ai_tensorsetdatatype) | 设置张量的数据类型。 |
| [OH_AI_API OH_AI_DataType OH_AI_TensorGetDataType(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetdatatype) | 获取张量类型。 |
| [OH_AI_API void OH_AI_TensorSetShape(OH_AI_TensorHandle tensor, const int64_t *shape, size_t shape_num)](#oh_ai_tensorsetshape) | 设置张量的形状。 |
| [OH_AI_API const int64_t *OH_AI_TensorGetShape(const OH_AI_TensorHandle tensor, size_t *shape_num)](#oh_ai_tensorgetshape) | 获取张量的形状。 |
| [OH_AI_API void OH_AI_TensorSetFormat(OH_AI_TensorHandle tensor, OH_AI_Format format)](#oh_ai_tensorsetformat) | 设置张量数据的排列方式。 |
| [OH_AI_API OH_AI_Format OH_AI_TensorGetFormat(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetformat) | 获取张量数据的排列方式。 |
| [OH_AI_API void OH_AI_TensorSetData(OH_AI_TensorHandle tensor, void *data)](#oh_ai_tensorsetdata) | 设置张量的数据。 |
| [OH_AI_API const void *OH_AI_TensorGetData(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetdata) | 获取张量数据的指针。 |
| [OH_AI_API void *OH_AI_TensorGetMutableData(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetmutabledata) | 获取可变的张量数据指针。如果数据为空则会开辟内存。 |
| [OH_AI_API int64_t OH_AI_TensorGetElementNum(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetelementnum) | 获取张量元素数量。 |
| [OH_AI_API size_t OH_AI_TensorGetDataSize(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetdatasize) | 获取张量中的数据的字节数大小。 |
| [OH_AI_API OH_AI_Status OH_AI_TensorSetUserData(OH_AI_TensorHandle tensor, void *data, size_t data_size)](#oh_ai_tensorsetuserdata) | 设置张量为用户自行管理的数据。此接口常用于复用用户数据作为模型输入，可减少一次数据拷贝。<br> 注意：此数据对于张量来说是外部数据，张量销毁时不会主动释放，由调用者负责释放。另外，在此张量使用过程中，调用者须确保此数据有效。 |
| [OH_AI_API OH_AI_AllocatorHandle OH_AI_TensorGetAllocator(OH_AI_TensorHandle tensor)](#oh_ai_tensorgetallocator) | 获取内存分配器。此接口主要是提供一种获取张量的内存分配器的方法。 |
| [OH_AI_API OH_AI_Status OH_AI_TensorSetAllocator(OH_AI_TensorHandle tensor, OH_AI_AllocatorHandle allocator)](#oh_ai_tensorsetallocator) | 设置内存分配器。此接口主要是提供一种设置内存分配器的方法，tensor的内存将由这个分配器分配。 |

## 函数说明

### OH_AI_TensorCreate()

```
OH_AI_API OH_AI_TensorHandle OH_AI_TensorCreate(const char *name, OH_AI_DataType type, const int64_t *shape,size_t shape_num, const void *data, size_t data_len)
```

**描述**

创建一个张量对象。

**起始版本：** 9


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *name | 张量名称。 |
| [OH_AI_DataType](capi-data-type-h.md#oh_ai_datatype) type | 张量的数据类型。 |
| const int64_t *shape | 张量的维度数组。 |
| size_t shape_num | 张量维度数组长度。 |
| const void *data | 指向数据的指针。 |
| size_t data_len | 数据的长度。 |

**返回：**

| 类型                               | 说明 |
|----------------------------------| -- |
| OH_AI_API [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) | 指向张量对象句柄。 |

### OH_AI_TensorDestroy()

```
OH_AI_API void OH_AI_TensorDestroy(OH_AI_TensorHandle *tensor)
```

**描述**

释放张量对象。

**起始版本：** 9


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) *tensor | 指向张量句柄的二级指针。 |

### OH_AI_TensorClone()

```
OH_AI_API OH_AI_TensorHandle OH_AI_TensorClone(OH_AI_TensorHandle tensor)
```

**描述**

深拷贝一个张量。

**起始版本：** 9


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | 待拷贝张量的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AI_API [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) | 指向新张量对象句柄。 |

### OH_AI_TensorSetName()

```
OH_AI_API void OH_AI_TensorSetName(OH_AI_TensorHandle tensor, const char *name)
```

**描述**

设置张量的名称。

**起始版本：** 9


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | 张量对象句柄。 |
| const char *name | 张量名称。 |

### OH_AI_TensorGetName()

```
OH_AI_API const char *OH_AI_TensorGetName(const OH_AI_TensorHandle tensor)
```

**描述**

获取张量的名称。

**起始版本：** 9


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | 张量对象句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AI_API const char * | 张量的名称。 |

### OH_AI_TensorSetDataType()

```
OH_AI_API void OH_AI_TensorSetDataType(OH_AI_TensorHandle tensor, OH_AI_DataType type)
```

**描述**

设置张量的数据类型。

**起始版本：** 9


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | 张量对象句柄。 |
| [OH_AI_DataType](capi-data-type-h.md#oh_ai_datatype) type | 数据类型，具体见[OH_AI_DataType](capi-data-type-h.md#oh_ai_datatype)。 |

### OH_AI_TensorGetDataType()

```
OH_AI_API OH_AI_DataType OH_AI_TensorGetDataType(const OH_AI_TensorHandle tensor)
```

**描述**

获取张量类型。

**起始版本：** 9


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | 张量对象句柄。 |

**返回：**

| 类型                                                             | 说明 |
|----------------------------------------------------------------| -- |
| OH_AI_API [OH_AI_DataType](capi-data-type-h.md#oh_ai_datatype) | 张量的数据类型。 |

### OH_AI_TensorSetShape()

```
OH_AI_API void OH_AI_TensorSetShape(OH_AI_TensorHandle tensor, const int64_t *shape, size_t shape_num)
```

**描述**

设置张量的形状。

**起始版本：** 9


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | 张量对象句柄。 |
| const int64_t *shape | 形状数组。 |
| size_t shape_num | 张量形状数组长度。 |

### OH_AI_TensorGetShape()

```
OH_AI_API const int64_t *OH_AI_TensorGetShape(const OH_AI_TensorHandle tensor, size_t *shape_num)
```

**描述**

获取张量的形状。

**起始版本：** 9


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | 张量对象句柄。 |
| size_t *shape_num | 该参数是输出参数，形状数组的长度会写入该变量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AI_API const int64_t * | 形状数组。 |

### OH_AI_TensorSetFormat()

```
OH_AI_API void OH_AI_TensorSetFormat(OH_AI_TensorHandle tensor, OH_AI_Format format)
```

**描述**

设置张量数据的排列方式。

**起始版本：** 9


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | 张量对象句柄。 |
| [OH_AI_Format](capi-format-h.md#oh_ai_format) format | 张量数据排列方式。 |

### OH_AI_TensorGetFormat()

```
OH_AI_API OH_AI_Format OH_AI_TensorGetFormat(const OH_AI_TensorHandle tensor)
```

**描述**

获取张量数据的排列方式。

**起始版本：** 9


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | 张量对象句柄。 |

**返回：**

| 类型                                                      | 说明 |
|---------------------------------------------------------| -- |
| OH_AI_API [OH_AI_Format](capi-format-h.md#oh_ai_format) | 张量数据的排列方式。 |

### OH_AI_TensorSetData()

```
OH_AI_API void OH_AI_TensorSetData(OH_AI_TensorHandle tensor, void *data)
```

**描述**

设置张量的数据。

**起始版本：** 9


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | 张量对象句柄。 |
| void *data | 指向数据的指针。 |

### OH_AI_TensorGetData()

```
OH_AI_API const void *OH_AI_TensorGetData(const OH_AI_TensorHandle tensor)
```

**描述**

获取张量数据的指针。

**起始版本：** 9


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | 张量对象句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AI_API const void * | 张量数据的指针。 |

### OH_AI_TensorGetMutableData()

```
OH_AI_API void *OH_AI_TensorGetMutableData(const OH_AI_TensorHandle tensor)
```

**描述**

获取可变的张量数据指针。如果数据为空则会开辟内存。

**起始版本：** 9


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | 张量对象句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AI_API void * | 张量数据的指针。 |

### OH_AI_TensorGetElementNum()

```
OH_AI_API int64_t OH_AI_TensorGetElementNum(const OH_AI_TensorHandle tensor)
```

**描述**

获取张量元素数量。

**起始版本：** 9


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | 张量对象句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AI_API int64_t | 张量的元素数量。 |

### OH_AI_TensorGetDataSize()

```
OH_AI_API size_t OH_AI_TensorGetDataSize(const OH_AI_TensorHandle tensor)
```

**描述**

获取张量中的数据的字节数大小。

**起始版本：** 9


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | 张量对象句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AI_API size_t | 张量数据的字节数大小。 |

### OH_AI_TensorSetUserData()

```
OH_AI_API OH_AI_Status OH_AI_TensorSetUserData(OH_AI_TensorHandle tensor, void *data, size_t data_size)
```

**描述**

设置张量为用户自行管理的数据。此接口常用于复用用户数据作为模型输入，可减少一次数据拷贝。<br>注意：此数据对于张量来说是外部数据，张量销毁时不会主动释放，由调用者负责释放。另外，在此张量使用过程中，调用者须确保此数据有效。

**起始版本：** 10


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | 张量对象句柄。 |
| void *data | 用户数据首地址。 |
| size_t data_size | 用户数据长度。 |

**返回：**

| 类型                                                      | 说明 |
|---------------------------------------------------------| -- |
| OH_AI_API [OH_AI_Status](capi-status-h.md#oh_ai_status) | 执行状态码。若成功返回OH_AI_STATUS_SUCCESS，否则返回具体错误码。 |

### OH_AI_TensorGetAllocator()

```
OH_AI_API OH_AI_AllocatorHandle OH_AI_TensorGetAllocator(OH_AI_TensorHandle tensor)
```

**描述**

获取内存分配器。此接口主要是提供一种获取张量的内存分配器的方法。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | 张量对象句柄。 |

**返回：**

| 类型                                  | 说明 |
|-------------------------------------| -- |
| OH_AI_API [OH_AI_AllocatorHandle](capi-mindspore-oh-ai-allocatorhandle.md) | 内存分配器的句柄。 |

### OH_AI_TensorSetAllocator()

```
OH_AI_API OH_AI_Status OH_AI_TensorSetAllocator(OH_AI_TensorHandle tensor, OH_AI_AllocatorHandle allocator)
```

**描述**

设置内存分配器。此接口主要是提供一种设置内存分配器的方法，tensor的内存将由这个分配器分配。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | 张量对象句柄。 |
| [OH_AI_AllocatorHandle](capi-mindspore-oh-ai-allocatorhandle.md) allocator | 内存分配器对象句柄。 |

**返回：**

| 类型                                                      | 说明 |
|---------------------------------------------------------| -- |
| OH_AI_API [OH_AI_Status](capi-status-h.md#oh_ai_status) | 执行状态码。若成功返回OH_AI_STATUS_SUCCESS，否则返回具体错误码。 |