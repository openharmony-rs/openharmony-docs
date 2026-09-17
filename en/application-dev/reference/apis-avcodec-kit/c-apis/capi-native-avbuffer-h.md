# native_avbuffer.h

## Overview

The file declares the functions of the media struct AVBuffer.

**Library**: libnative_media_core.so

**System capability**: SystemCapability.Multimedia.Media.Core

**Since**: 9

**Related module**: [Core](capi-core.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AVBuffer](capi-core-oh-avbuffer.md) | OH_AVBuffer | Describes a native object for the media memory interface. |
| [OH_NativeBuffer](capi-core-oh-nativebuffer.md) | OH_NativeBuffer | Describes a native object for the graphics memory interface. |

### Function

| Name | Description |
| -- | -- |
| [OH_AVBuffer *OH_AVBuffer_Create(int32_t capacity)](#oh_avbuffer_create) | Creates an OH_AVBuffer instance. You must call [OH_AVBuffer_Destroy](capi-native-avbuffer-h.md#oh_avbuffer_destroy) to manually release the OH_AVBuffer instance returned. |
| [OH_AVErrCode OH_AVBuffer_Destroy(OH_AVBuffer *buffer)](#oh_avbuffer_destroy) | Releases an OH_AVBuffer instance. A buffer cannot be destroyed repeatedly. |
| [OH_AVErrCode OH_AVBuffer_GetBufferAttr(OH_AVBuffer *buffer, OH_AVCodecBufferAttr *attr)](#oh_avbuffer_getbufferattr) | Obtains the basic attributes, including **pts**, **size**, **offset**, and **flags**, of a buffer. |
| [OH_AVErrCode OH_AVBuffer_SetBufferAttr(OH_AVBuffer *buffer, const OH_AVCodecBufferAttr *attr)](#oh_avbuffer_setbufferattr) | Sets the basic attributes, including **pts**, **size**, **offset**, and **flags**, of a buffer. |
| [OH_AVFormat *OH_AVBuffer_GetParameter(OH_AVBuffer *buffer)](#oh_avbuffer_getparameter) | Obtains parameters except basic attributes of a buffer. The information is carried in an OH_AVFormat instance. You must call {@link OH_AVFormat_Destroy} to manually release the OH_AVFormat instance returned. |
| [OH_AVErrCode OH_AVBuffer_SetParameter(OH_AVBuffer *buffer, const OH_AVFormat *format)](#oh_avbuffer_setparameter) | Sets parameters except basic attributes of a buffer. The information is carried in an OH_AVFormat instance. |
| [uint8_t *OH_AVBuffer_GetAddr(OH_AVBuffer *buffer)](#oh_avbuffer_getaddr) | Obtains the virtual address of a data buffer. |
| [int32_t OH_AVBuffer_GetCapacity(OH_AVBuffer *buffer)](#oh_avbuffer_getcapacity) | Obtains the capacity (in bytes) of a buffer. |
| [OH_NativeBuffer *OH_AVBuffer_GetNativeBuffer(OH_AVBuffer *buffer)](#oh_avbuffer_getnativebuffer) | Obtains the pointer to an OH_NativeBuffer instance. You must call {@link OH_NativeBuffer_Unreference} to manually release the OH_NativeBuffer instance returned. |

## Function description

### OH_AVBuffer_Create()

```c
OH_AVBuffer *OH_AVBuffer_Create(int32_t capacity)
```

**Description**

Creates an OH_AVBuffer instance. You must call [OH_AVBuffer_Destroy](capi-native-avbuffer-h.md#oh_avbuffer_destroy) to manually release the OH_AVBuffer instance returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t capacity | Size of the created memory, in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_AVBuffer *](capi-core-oh-avbuffer.md) | Pointer to the OH_AVBuffer instance created. If the operation fails, NULL is returned.      <br>The possible causes of an operation failure are as follows:      <br>1. The value of capacity is less than or equal to 0.      <br>2. An internal error occurs, or the system does not have resources. |

### OH_AVBuffer_Destroy()

```c
OH_AVErrCode OH_AVBuffer_Destroy(OH_AVBuffer *buffer)
```

**Description**

Releases an OH_AVBuffer instance. A buffer cannot be destroyed repeatedly.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVBuffer](capi-core-oh-avbuffer.md) *buffer | Pointer to an OH_AVBuffer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    <br>{@link AV_ERR_INVALID_VAL}: The value of buffer is nullptr or fails format verification.<br>    <br>{@link AV_ERR_OPERATE_NOT_PERMIT}: The input buffer is not created by the user. |

### OH_AVBuffer_GetBufferAttr()

```c
OH_AVErrCode OH_AVBuffer_GetBufferAttr(OH_AVBuffer *buffer, OH_AVCodecBufferAttr *attr)
```

**Description**

Obtains the basic attributes, including **pts**, **size**, **offset**, and **flags**, of a buffer.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVBuffer](capi-core-oh-avbuffer.md) *buffer | Pointer to an OH_AVBuffer instance. |
| OH_AVCodecBufferAttr *attr | Pointer to an OH_AVCodecBufferAttr instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    <br>{@link AV_ERR_INVALID_VAL}: The possible causes are as follows:      <br>1. The value of buffer or attr is nullptr.      <br>2. The value of buffer fails parameter structure verification. |

### OH_AVBuffer_SetBufferAttr()

```c
OH_AVErrCode OH_AVBuffer_SetBufferAttr(OH_AVBuffer *buffer, const OH_AVCodecBufferAttr *attr)
```

**Description**

Sets the basic attributes, including **pts**, **size**, **offset**, and **flags**, of a buffer.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVBuffer](capi-core-oh-avbuffer.md) *buffer | Pointer to an OH_AVBuffer instance. |
| const OH_AVCodecBufferAttr *attr | Pointer to an OH_AVCodecBufferAttr instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    <br>{@link AV_ERR_INVALID_VAL}: The possible causes are as follows:      <br>1. The value of buffer or attr is nullptr.      <br>2. The value of buffer fails parameter structure verification.      <br>3. The memory size or offset of the buffer is invalid. |

### OH_AVBuffer_GetParameter()

```c
OH_AVFormat *OH_AVBuffer_GetParameter(OH_AVBuffer *buffer)
```

**Description**

Obtains parameters except basic attributes of a buffer. The information is carried in an OH_AVFormat instance. You must call {@link OH_AVFormat_Destroy} to manually release the OH_AVFormat instance returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVBuffer](capi-core-oh-avbuffer.md) *buffer | Pointer to an OH_AVBuffer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVFormat * | {@link AV_ERR_OK}: The operation is successful.<br>    {@link AV_ERR_INVALID_VAL}: The possible causes are as follows:      <br>1. The value of buffer is nullptr.      <br>2. The meta of the buffer is nullptr.      <br>3. The value of buffer fails parameter structure verification. |

### OH_AVBuffer_SetParameter()

```c
OH_AVErrCode OH_AVBuffer_SetParameter(OH_AVBuffer *buffer, const OH_AVFormat *format)
```

**Description**

Sets parameters except basic attributes of a buffer. The information is carried in an OH_AVFormat instance.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVBuffer](capi-core-oh-avbuffer.md) *buffer | Pointer to an OH_AVBuffer instance. |
| const OH_AVFormat *format | Pointer to an OH_AVFormat instance. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_AVErrCode | {@link AV_ERR_OK}: The operation is successful.<br>    {@link AV_ERR_INVALID_VAL}: The possible causes are as follows:      <br>1. The value of buffer or format is nullptr.      <br>2. The meta of the buffer is nullptr.      <br>3. The value of buffer fails parameter structure verification. |

### OH_AVBuffer_GetAddr()

```c
uint8_t *OH_AVBuffer_GetAddr(OH_AVBuffer *buffer)
```

**Description**

Obtains the virtual address of a data buffer.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVBuffer](capi-core-oh-avbuffer.md) *buffer | Pointer to an OH_AVBuffer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| uint8_t * | Virtual address. If the operation fails, NULL is returned.      <br>The possible causes of an operation failure are as follows:      <br>1. The value of buffer is a null pointer.      <br>2. The value of OH_AVBuffer fails parameter structure verification.      <br>3. An internal error occurs. |

### OH_AVBuffer_GetCapacity()

```c
int32_t OH_AVBuffer_GetCapacity(OH_AVBuffer *buffer)
```

**Description**

Obtains the capacity (in bytes) of a buffer.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVBuffer](capi-core-oh-avbuffer.md) *buffer | Pointer to an OH_AVBuffer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Capacity. If the operation fails, -1 is returned.      <br>The possible causes of an operation failure are as follows:      <br>1. The value of buffer is a null pointer.      <br>2. The value of OH_AVBuffer fails parameter structure verification.      <br>3. An internal error occurs. |

### OH_AVBuffer_GetNativeBuffer()

```c
OH_NativeBuffer *OH_AVBuffer_GetNativeBuffer(OH_AVBuffer *buffer)
```

**Description**

Obtains the pointer to an OH_NativeBuffer instance. You must call {@link OH_NativeBuffer_Unreference} to manually release the OH_NativeBuffer instance returned.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AVBuffer](capi-core-oh-avbuffer.md) *buffer | Pointer to an OH_AVBuffer instance. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_NativeBuffer *](capi-core-oh-nativebuffer.md) | Pointer to the OH_NativeBuffer instance created. If the operation fails, NULL is returned.      <br>The possible causes of an operation failure are as follows:      <br>1. The value of buffer is a null pointer.      <br>2. The value of OH_AVBuffer fails parameter structure verification.      <br>3. An internal error occurs. |


