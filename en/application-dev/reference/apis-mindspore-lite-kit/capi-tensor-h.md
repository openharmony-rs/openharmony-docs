# tensor.h

<!--Kit: MindSpore Lite Kit-->
<!--Subsystem: AI-->
<!--Owner: @zhuguodong8-->
<!--Designer: @zhuguodong8; @jjfeing-->
<!--Tester: @principal87-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=5d8f328a61b911e9f23d9ab9f1ddc13a0c19f421 translatedAt=2026-11-13T04:10:27.544Z pushedAt=2026-11-13T11:01:20.995Z nl=1 -->

## Overview

Provides tensor-related APIs for creating and modifying tensor information. These APIs are not thread-safe.

**File to include:** <mindspore/tensor.h>

**Library:** libmindspore_lite_ndk.so

**System capability:** SystemCapability.Ai.MindSpore

**Since**: 9

**Related module:** [MindSpore](capi-mindspore.md)

## Summary

### Structs

| Name | typedef Keyword                                                 | Description |
|----|------------------------------------------------------------|----|
| void *   | [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) | Handle to a tensor object.   |
| void *   | [OH_AI_AllocatorHandle](capi-mindspore-oh-ai-allocatorhandle.md)  | Handle to a memory allocator object.   |

### Functions

| Name | Description |
| -- | -- |
| [OH_AI_API OH_AI_TensorHandle OH_AI_TensorCreate(const char *name, OH_AI_DataType type, const int64_t *shape,size_t shape_num, const void *data, size_t data_len)](#oh_ai_tensorcreate) | Creates a tensor object. |
| [OH_AI_API void OH_AI_TensorDestroy(OH_AI_TensorHandle *tensor)](#oh_ai_tensordestroy) | Destroys a tensor object. |
| [OH_AI_API OH_AI_TensorHandle OH_AI_TensorClone(OH_AI_TensorHandle tensor)](#oh_ai_tensorclone) | Deep copies a tensor. |
| [OH_AI_API void OH_AI_TensorSetName(OH_AI_TensorHandle tensor, const char *name)](#oh_ai_tensorsetname) | Sets the tensor name. |
| [OH_AI_API const char *OH_AI_TensorGetName(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetname) | Gets the tensor name. |
| [OH_AI_API void OH_AI_TensorSetDataType(OH_AI_TensorHandle tensor, OH_AI_DataType type)](#oh_ai_tensorsetdatatype) | Sets the tensor data type. |
| [OH_AI_API OH_AI_DataType OH_AI_TensorGetDataType(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetdatatype) | Gets the tensor type. |
| [OH_AI_API void OH_AI_TensorSetShape(OH_AI_TensorHandle tensor, const int64_t *shape, size_t shape_num)](#oh_ai_tensorsetshape) | Sets the tensor shape. |
| [OH_AI_API const int64_t *OH_AI_TensorGetShape(const OH_AI_TensorHandle tensor, size_t *shape_num)](#oh_ai_tensorgetshape) | Gets the tensor shape. |
| [OH_AI_API void OH_AI_TensorSetFormat(OH_AI_TensorHandle tensor, OH_AI_Format format)](#oh_ai_tensorsetformat) | Sets the tensor data layout. |
| [OH_AI_API OH_AI_Format OH_AI_TensorGetFormat(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetformat) | Gets the tensor data layout. |
| [OH_AI_API void OH_AI_TensorSetData(OH_AI_TensorHandle tensor, void *data)](#oh_ai_tensorsetdata) | Sets the data of the tensor. |
| [OH_AI_API const void *OH_AI_TensorGetData(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetdata) | Gets the pointer to the tensor data. |
| [OH_AI_API void *OH_AI_TensorGetMutableData(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetmutabledata) | Gets the mutable tensor data pointer. If the data is empty, memory is allocated. |
| [OH_AI_API int64_t OH_AI_TensorGetElementNum(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetelementnum) | Gets the number of tensor elements. |
| [OH_AI_API size_t OH_AI_TensorGetDataSize(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetdatasize) | Gets the byte count of the tensor data. |
| [OH_AI_API OH_AI_Status OH_AI_TensorSetUserData(OH_AI_TensorHandle tensor, void *data, size_t data_size)](#oh_ai_tensorsetuserdata) | Sets the tensor to user-managed data. This API is often used to reuse user data as model input, which reduces one data copy.<br> Note: This data is external to the tensor and is not released when the tensor is destroyed; the caller is responsible for releasing it. In addition, the caller must ensure that this data remains valid while the tensor is in use. |
| [OH_AI_API OH_AI_AllocatorHandle OH_AI_TensorGetAllocator(OH_AI_TensorHandle tensor)](#oh_ai_tensorgetallocator) | Gets the memory allocator. This API mainly provides a method for obtaining the memory allocator of the tensor. |
| [OH_AI_API OH_AI_Status OH_AI_TensorSetAllocator(OH_AI_TensorHandle tensor, OH_AI_AllocatorHandle allocator)](#oh_ai_tensorsetallocator) | Sets the memory allocator. This API mainly provides a method for setting the memory allocator. The tensor memory is allocated by this allocator. |

## Function Description

### OH_AI_TensorCreate()

```c
OH_AI_API OH_AI_TensorHandle OH_AI_TensorCreate(const char *name, OH_AI_DataType type, const int64_t *shape,size_t shape_num, const void *data, size_t data_len)
```

**Description**

Creates a tensor object. This API must be used together with [OH_AI_TensorDestroy()](#oh_ai_tensordestroy).

**Since**: 9


**Parameters:**

| Name | Description |
| -- | -- |
| const char *name | Tensor name. The string length is subject to the system limit. |
| [OH_AI_DataType](capi-data-type-h.md#oh_ai_datatype) type | Data type of the tensor. |
| const int64_t *shape | Dimension array of the tensor. |
| size_t shape_num | Length of the tensor dimension array. |
| const void *data | Pointer to the data. |
| size_t data_len | Data length. |

**Returns:**

| Type                               | Description |
|----------------------------------| -- |
| OH_AI_API [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) | Handle to a tensor object. |

### OH_AI_TensorDestroy()

```c
OH_AI_API void OH_AI_TensorDestroy(OH_AI_TensorHandle *tensor)
```

**Description**

Destroys a tensor object.

**Since**: 9


**Parameters:**

| Name | Description |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) *tensor | Double pointer to the tensor handle. |

### OH_AI_TensorClone()

```c
OH_AI_API OH_AI_TensorHandle OH_AI_TensorClone(OH_AI_TensorHandle tensor)
```

**Description**

Deep copies a tensor.

**Since**: 9


**Parameters:**

| Name | Description |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | Tensor object handle. |

**Returns:**

| Type | Description |
| -- | -- |
| OH_AI_API [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) | Pointer to the new tensor object handle. |

### OH_AI_TensorSetName()

```c
OH_AI_API void OH_AI_TensorSetName(OH_AI_TensorHandle tensor, const char *name)
```

**Description**

Sets the tensor name.

**Since**: 9


**Parameters:**

| Name | Description |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | Tensor object handle. |
| const char *name | Tensor name. The string length is subject to the system limit. |

### OH_AI_TensorGetName()

```c
OH_AI_API const char *OH_AI_TensorGetName(const OH_AI_TensorHandle tensor)
```

**Description**

Gets the tensor name.

**Since**: 9


**Parameters:**

| Name | Description |
| -- | -- |
| const [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | Tensor object handle. |

**Returns:**

| Type | Description |
| -- | -- |
| OH_AI_API const char * | Name of the tensor. |

### OH_AI_TensorSetDataType()

```c
OH_AI_API void OH_AI_TensorSetDataType(OH_AI_TensorHandle tensor, OH_AI_DataType type)
```

**Description**

Sets the tensor data type.

**Since**: 9


**Parameters:**

| Name | Description |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | Tensor object handle. |
| [OH_AI_DataType](capi-data-type-h.md#oh_ai_datatype) type | Data type. For details, see [OH_AI_DataType](capi-data-type-h.md#oh_ai_datatype). |

### OH_AI_TensorGetDataType()

```c
OH_AI_API OH_AI_DataType OH_AI_TensorGetDataType(const OH_AI_TensorHandle tensor)
```

**Description**

Gets the tensor type.

**Since**: 9


**Parameters:**

| Name | Description |
| -- | -- |
| const [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | Tensor object handle. |

**Returns:**

| Type                                                             | Description |
|----------------------------------------------------------------| -- |
| OH_AI_API [OH_AI_DataType](capi-data-type-h.md#oh_ai_datatype) | Data type of the tensor. |

### OH_AI_TensorSetShape()

```c
OH_AI_API void OH_AI_TensorSetShape(OH_AI_TensorHandle tensor, const int64_t *shape, size_t shape_num)
```

**Description**

Sets the tensor shape.

**Since**: 9


**Parameters:**

| Name | Description |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | Tensor object handle. |
| const int64_t *shape | Shape array. |
| size_t shape_num | Length of the tensor shape array. |

### OH_AI_TensorGetShape()

```c
OH_AI_API const int64_t *OH_AI_TensorGetShape(const OH_AI_TensorHandle tensor, size_t *shape_num)
```

**Description**

Gets the tensor shape.

**Since**: 9


**Parameters:**

| Name | Description |
| -- | -- |
| const [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | Tensor object handle. |
| size_t *shape_num | Output parameter. The length of the shape array is written to this variable. |

**Returns:**

| Type | Description |
| -- | -- |
| OH_AI_API const int64_t * | Shape array. |

### OH_AI_TensorSetFormat()

```c
OH_AI_API void OH_AI_TensorSetFormat(OH_AI_TensorHandle tensor, OH_AI_Format format)
```

**Description**

Sets the tensor data layout.

**Since**: 9


**Parameters:**

| Name | Description |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | Tensor object handle. |
| [OH_AI_Format](capi-format-h.md#oh_ai_format) format | Layout of the tensor data. |

### OH_AI_TensorGetFormat()

```c
OH_AI_API OH_AI_Format OH_AI_TensorGetFormat(const OH_AI_TensorHandle tensor)
```

**Description**

Gets the tensor data layout.

**Since**: 9


**Parameters:**

| Name | Description |
| -- | -- |
| const [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | Tensor object handle. |

**Returns:**

| Type                                                      | Description |
|---------------------------------------------------------| -- |
| OH_AI_API [OH_AI_Format](capi-format-h.md#oh_ai_format) | Data layout of the tensor data. |

### OH_AI_TensorSetData()

```c
OH_AI_API void OH_AI_TensorSetData(OH_AI_TensorHandle tensor, void *data)
```

**Description**

Sets the data of the tensor.

**Since**: 9


**Parameters:**

| Name | Description |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | Tensor object handle. |
| void *data | Pointer to the data. |

### OH_AI_TensorGetData()

```c
OH_AI_API const void *OH_AI_TensorGetData(const OH_AI_TensorHandle tensor)
```

**Description**

Gets the pointer to the tensor data.

**Since**: 9


**Parameters:**

| Name | Description |
| -- | -- |
| const [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | Tensor object handle. |

**Returns:**

| Type | Description |
| -- | -- |
| OH_AI_API const void * | Pointer to the tensor data. |

### OH_AI_TensorGetMutableData()

```c
OH_AI_API void *OH_AI_TensorGetMutableData(const OH_AI_TensorHandle tensor)
```

**Description**

Gets the mutable tensor data pointer. If the data is empty, memory is allocated.

**Since**: 9


**Parameters:**

| Name | Description |
| -- | -- |
| const [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | Tensor object handle. |

**Returns:**

| Type | Description |
| -- | -- |
| OH_AI_API void * | Pointer to the tensor data. |

### OH_AI_TensorGetElementNum()

```c
OH_AI_API int64_t OH_AI_TensorGetElementNum(const OH_AI_TensorHandle tensor)
```

**Description**

Gets the number of tensor elements.

**Since**: 9


**Parameters:**

| Name | Description |
| -- | -- |
| const [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | Tensor object handle. |

**Returns:**

| Type | Description |
| -- | -- |
| OH_AI_API int64_t | Number of elements in the tensor. |

### OH_AI_TensorGetDataSize()

```c
OH_AI_API size_t OH_AI_TensorGetDataSize(const OH_AI_TensorHandle tensor)
```

**Description**

Gets the byte count of the tensor data.

**Since**: 9


**Parameters:**

| Name | Description |
| -- | -- |
| const [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | Tensor object handle. |

**Returns:**

| Type | Description |
| -- | -- |
| OH_AI_API size_t | Byte count of the tensor data. |

### OH_AI_TensorSetUserData()

```c
OH_AI_API OH_AI_Status OH_AI_TensorSetUserData(OH_AI_TensorHandle tensor, void *data, size_t data_size)
```

**Description**

Sets the tensor to user-managed data. This API is commonly used to reuse user data as model input, which reduces one data copy.<br>Note: This data is external to the tensor. It is not released when the tensor is destroyed; the caller is responsible for releasing it. In addition, the caller must ensure that the data remains valid while the tensor is in use.

**Since**: 10


**Parameters:**

| Name | Description |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | Tensor object handle. |
| void *data | Pointer to the start address of the user data. |
| size_t data_size | Length of the user data. |

**Returns:**

| Type                                                      | Description |
|---------------------------------------------------------| -- |
| OH_AI_API [OH_AI_Status](capi-status-h.md#oh_ai_status) | Result code. Returns OH_AI_STATUS_SUCCESS if the operation is successful; returns a specific error code otherwise. |

### OH_AI_TensorGetAllocator()

```c
OH_AI_API OH_AI_AllocatorHandle OH_AI_TensorGetAllocator(OH_AI_TensorHandle tensor)
```

**Description**

Gets the memory allocator. This API mainly provides a method for obtaining the memory allocator of the tensor.

**Since**: 12


**Parameters:**

| Name | Description |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | Tensor object handle. |

**Returns:**

| Type                                  | Description |
|-------------------------------------| -- |
| OH_AI_API [OH_AI_AllocatorHandle](capi-mindspore-oh-ai-allocatorhandle.md) | Handle to the allocator. |

### OH_AI_TensorSetAllocator()

```c
OH_AI_API OH_AI_Status OH_AI_TensorSetAllocator(OH_AI_TensorHandle tensor, OH_AI_AllocatorHandle allocator)
```

**Description**

Sets the memory allocator. This API mainly provides a method for setting the memory allocator. The tensor memory is allocated by this allocator.

**Since**: 12


**Parameters:**

| Name | Description |
| -- | -- |
| [OH_AI_TensorHandle](capi-mindspore-oh-ai-tensorHandle.md) tensor | Tensor object handle. |
| [OH_AI_AllocatorHandle](capi-mindspore-oh-ai-allocatorhandle.md) allocator | Memory allocator object handle. |

**Returns:**

| Type                                                      | Description |
|---------------------------------------------------------| -- |
| OH_AI_API [OH_AI_Status](capi-status-h.md#oh_ai_status) | Result code. Returns OH_AI_STATUS_SUCCESS if the operation is successful; returns a specific error code otherwise. |