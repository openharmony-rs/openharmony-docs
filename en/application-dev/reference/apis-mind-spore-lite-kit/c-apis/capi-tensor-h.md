# tensor.h

## Overview

Provides APIs for creating and modifying tensor information.

**Library**: libmindspore_lite_ndk.so

**Since**: 9

**Related module**: [MindSpore](capi-mindspore.md)

## Summary

### Macro

| Name | Description |
| -- | -- |
| MINDSPORE_INCLUDE_C_API_TENSOE_C_H | Provides APIs for creating and modifying tensor information.<br>**Since**: 9 |

### Function

| Name | Description |
| -- | -- |
| [OH_AI_API OH_AI_TensorHandle OH_AI_TensorCreate(const char *name, OH_AI_DataType type, const int64_t *shape, size_t shape_num, const void *data, size_t data_len)](#oh_ai_tensorcreate) | Create a tensor object. |
| [OH_AI_API void OH_AI_TensorDestroy(OH_AI_TensorHandle *tensor)](#oh_ai_tensordestroy) | Destroy the tensor object. |
| [OH_AI_API OH_AI_TensorHandle OH_AI_TensorClone(OH_AI_TensorHandle tensor)](#oh_ai_tensorclone) | Obtain a deep copy of the tensor. |
| [OH_AI_API void OH_AI_TensorSetName(OH_AI_TensorHandle tensor, const char *name)](#oh_ai_tensorsetname) | Set the name for the tensor. |
| [OH_AI_API const char *OH_AI_TensorGetName(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetname) | Obtain the name of the tensor. |
| [OH_AI_API void OH_AI_TensorSetDataType(OH_AI_TensorHandle tensor, OH_AI_DataType type)](#oh_ai_tensorsetdatatype) | Set the data type for the tensor. |
| [OH_AI_API OH_AI_DataType OH_AI_TensorGetDataType(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetdatatype) | Obtain the data type of the tensor. |
| [OH_AI_API void OH_AI_TensorSetShape(OH_AI_TensorHandle tensor, const int64_t *shape, size_t shape_num)](#oh_ai_tensorsetshape) | Set the shape for the tensor. |
| [OH_AI_API const int64_t *OH_AI_TensorGetShape(const OH_AI_TensorHandle tensor, size_t *shape_num)](#oh_ai_tensorgetshape) | Obtain the shape of the tensor. |
| [OH_AI_API void OH_AI_TensorSetFormat(OH_AI_TensorHandle tensor, OH_AI_Format format)](#oh_ai_tensorsetformat) | Set the format for the tensor. |
| [OH_AI_API OH_AI_Format OH_AI_TensorGetFormat(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetformat) | Obtain the format of the tensor. |
| [OH_AI_API void OH_AI_TensorSetData(OH_AI_TensorHandle tensor, void *data)](#oh_ai_tensorsetdata) | Obtain the data for the tensor. |
| [OH_AI_API const void *OH_AI_TensorGetData(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetdata) | Obtain the data pointer of the tensor. |
| [OH_AI_API void *OH_AI_TensorGetMutableData(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetmutabledata) | Obtain the mutable data pointer of the tensor. If the internal data is empty, it will allocate memory. |
| [OH_AI_API int64_t OH_AI_TensorGetElementNum(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetelementnum) | Obtain the element number of the tensor. |
| [OH_AI_API size_t OH_AI_TensorGetDataSize(const OH_AI_TensorHandle tensor)](#oh_ai_tensorgetdatasize) | Obtain the data size fo the tensor. |
| [OH_AI_API OH_AI_Status OH_AI_TensorSetUserData(OH_AI_TensorHandle tensor, void *data, size_t data_size)](#oh_ai_tensorsetuserdata) | Set the data for the tensor with user-allocated data buffer.<br> The main purpose of this interface is providing a way of using memory already allocated by user as the Model's input, but not which allocated inside the Model object. It can reduce one copy. Note: The tensor won't free the data provided by invoker. Invoker has the responsibility to free it. And this free action should not be preformed before destruction of the tensor. |
| [OH_AI_API OH_AI_AllocatorHandle OH_AI_TensorGetAllocator(OH_AI_TensorHandle tensor)](#oh_ai_tensorgetallocator) | Get allocator for the tensor.<br> The main purpose of this interface is providing a way of getting memory allocator of the tensor. |
| [OH_AI_API OH_AI_Status OH_AI_TensorSetAllocator(OH_AI_TensorHandle tensor, OH_AI_AllocatorHandle allocator)](#oh_ai_tensorsetallocator) | Set allocator to the tensor.<br> The main purpose of this interface is providing a way of setting memory allocator, so tensor's memory will be allocated by this allocator. |

### Variable

| Name | Description |
| -- | -- |
| void *OH_AI_TensorHandle | Tensor object handle.<br>**Since**: 12 |
| void *OH_AI_AllocatorHandle | Tensor allocator handle.<br>**Since**: 12 |

## Function description

### OH_AI_TensorCreate()

```c
OH_AI_API OH_AI_TensorHandle OH_AI_TensorCreate(const char *name, OH_AI_DataType type, const int64_t *shape, size_t shape_num, const void *data, size_t data_len)
```

**Description**

Create a tensor object.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char *name | The name of the tensor. |
| OH_AI_DataType type | The data type of the tensor. |
| const int64_t *shape | The shape of the tensor. |
| size_t shape_num | The num of the shape. |
| const void *data | The data pointer that points to allocated memory. |
| size_t data_len | The length of the memory, in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_TensorHandle | Tensor object handle. |

### OH_AI_TensorDestroy()

```c
OH_AI_API void OH_AI_TensorDestroy(OH_AI_TensorHandle *tensor)
```

**Description**

Destroy the tensor object.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_TensorHandle *tensor | Tensor object handle address. |

### OH_AI_TensorClone()

```c
OH_AI_API OH_AI_TensorHandle OH_AI_TensorClone(OH_AI_TensorHandle tensor)
```

**Description**

Obtain a deep copy of the tensor.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_TensorHandle tensor | Tensor object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_TensorHandle | Tensor object handle. |

### OH_AI_TensorSetName()

```c
OH_AI_API void OH_AI_TensorSetName(OH_AI_TensorHandle tensor, const char *name)
```

**Description**

Set the name for the tensor.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_TensorHandle tensor | Tensor object handle. |
| const char *name | The name of the tensor. |

### OH_AI_TensorGetName()

```c
OH_AI_API const char *OH_AI_TensorGetName(const OH_AI_TensorHandle tensor)
```

**Description**

Obtain the name of the tensor.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_TensorHandle tensor | Tensor object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API const char * | The name of the tensor. |

### OH_AI_TensorSetDataType()

```c
OH_AI_API void OH_AI_TensorSetDataType(OH_AI_TensorHandle tensor, OH_AI_DataType type)
```

**Description**

Set the data type for the tensor.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_TensorHandle tensor | Tensor object handle. |
| OH_AI_DataType type | The data type of the tensor. |

### OH_AI_TensorGetDataType()

```c
OH_AI_API OH_AI_DataType OH_AI_TensorGetDataType(const OH_AI_TensorHandle tensor)
```

**Description**

Obtain the data type of the tensor.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_TensorHandle tensor | Tensor object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_DataType | The date type of the tensor. |

### OH_AI_TensorSetShape()

```c
OH_AI_API void OH_AI_TensorSetShape(OH_AI_TensorHandle tensor, const int64_t *shape, size_t shape_num)
```

**Description**

Set the shape for the tensor.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_TensorHandle tensor | Tensor object handle. |
| const int64_t *shape | The shape array. |
| size_t shape_num | Dimension of shape. |

### OH_AI_TensorGetShape()

```c
OH_AI_API const int64_t *OH_AI_TensorGetShape(const OH_AI_TensorHandle tensor, size_t *shape_num)
```

**Description**

Obtain the shape of the tensor.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_TensorHandle tensor | Tensor object handle. |
| size_t *shape_num | Dimension of shape. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API const int64_t * | The shape array of the tensor. |

### OH_AI_TensorSetFormat()

```c
OH_AI_API void OH_AI_TensorSetFormat(OH_AI_TensorHandle tensor, OH_AI_Format format)
```

**Description**

Set the format for the tensor.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_TensorHandle tensor | Tensor object handle. |
| OH_AI_Format format | The format of the tensor. |

### OH_AI_TensorGetFormat()

```c
OH_AI_API OH_AI_Format OH_AI_TensorGetFormat(const OH_AI_TensorHandle tensor)
```

**Description**

Obtain the format of the tensor.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_TensorHandle tensor | Tensor object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Format | The format of the tensor. |

### OH_AI_TensorSetData()

```c
OH_AI_API void OH_AI_TensorSetData(OH_AI_TensorHandle tensor, void *data)
```

**Description**

Obtain the data for the tensor.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_TensorHandle tensor | Tensor object handle. |
| void *data | A pointer to the data of the tensor. |

### OH_AI_TensorGetData()

```c
OH_AI_API const void *OH_AI_TensorGetData(const OH_AI_TensorHandle tensor)
```

**Description**

Obtain the data pointer of the tensor.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_TensorHandle tensor | Tensor object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API const void * | The data pointer of the tensor. |

### OH_AI_TensorGetMutableData()

```c
OH_AI_API void *OH_AI_TensorGetMutableData(const OH_AI_TensorHandle tensor)
```

**Description**

Obtain the mutable data pointer of the tensor. If the internal data is empty, it will allocate memory.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_TensorHandle tensor | Tensor object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API void * | The data pointer of the tensor. |

### OH_AI_TensorGetElementNum()

```c
OH_AI_API int64_t OH_AI_TensorGetElementNum(const OH_AI_TensorHandle tensor)
```

**Description**

Obtain the element number of the tensor.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_TensorHandle tensor | Tensor object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API int64_t | The element number of the tensor. |

### OH_AI_TensorGetDataSize()

```c
OH_AI_API size_t OH_AI_TensorGetDataSize(const OH_AI_TensorHandle tensor)
```

**Description**

Obtain the data size fo the tensor.

**Since**: 9

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_AI_TensorHandle tensor | Tensor object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API size_t | The data size of the tensor. |

### OH_AI_TensorSetUserData()

```c
OH_AI_API OH_AI_Status OH_AI_TensorSetUserData(OH_AI_TensorHandle tensor, void *data, size_t data_size)
```

**Description**

Set the data for the tensor with user-allocated data buffer.<br> The main purpose of this interface is providing a way of using memory already allocated by user as the Model's input, but not which allocated inside the Model object. It can reduce one copy. Note: The tensor won't free the data provided by invoker. Invoker has the responsibility to free it. And this free action should not be preformed before destruction of the tensor.

**Since**: 10

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_TensorHandle tensor | Tensor object handle. |
| void *data | A pointer to the user data buffer. |
| void *data | the byte size of the user data buffer. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_STATUS_SUCCESS if success, or detail error code if failed. |

### OH_AI_TensorGetAllocator()

```c
OH_AI_API OH_AI_AllocatorHandle OH_AI_TensorGetAllocator(OH_AI_TensorHandle tensor)
```

**Description**

Get allocator for the tensor.<br> The main purpose of this interface is providing a way of getting memory allocator of the tensor.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_TensorHandle tensor | Tensor object handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_AllocatorHandle | handle of the tensor's allocator. |

### OH_AI_TensorSetAllocator()

```c
OH_AI_API OH_AI_Status OH_AI_TensorSetAllocator(OH_AI_TensorHandle tensor, OH_AI_AllocatorHandle allocator)
```

**Description**

Set allocator to the tensor.<br> The main purpose of this interface is providing a way of setting memory allocator, so tensor's memory will be allocated by this allocator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AI_TensorHandle tensor | Tensor object handle. |
| OH_AI_AllocatorHandle allocator | A allocator handle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AI_API OH_AI_Status | OH_AI_STATUS_SUCCESS if success, or detail error code if failed. |


