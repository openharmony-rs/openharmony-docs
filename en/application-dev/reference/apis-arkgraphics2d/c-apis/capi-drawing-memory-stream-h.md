# drawing_memory_stream.h

## Overview

This file declares the functions related to the memory stream in the drawing module.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [OH_Drawing_MemoryStream* OH_Drawing_MemoryStreamCreate(const void* data, size_t length, bool copyData)](#oh_drawing_memorystreamcreate) | Creates an **OH_Drawing_MemoryStream** object. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **data** is NULL or **length** is **0**, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_MemoryStreamDestroy(OH_Drawing_MemoryStream* memoryStream)](#oh_drawing_memorystreamdestroy) | Destroys an **OH_Drawing_MemoryStream** object and reclaims the memory occupied by the object. |

## Function description

### OH_Drawing_MemoryStreamCreate()

```c
OH_Drawing_MemoryStream* OH_Drawing_MemoryStreamCreate(const void* data, size_t length, bool copyData)
```

**Description**

Creates an **OH_Drawing_MemoryStream** object. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **data** is NULL or **length** is **0**, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const void* data | Pointer to the data. |
| size_t length | Length of the data. |
| bool copyData | Whether to copy data. The value **true** means that the **OH_Drawing_MemoryStream** object copies the data, and **false** means that the **OH_Drawing_MemoryStream** object directly uses the data without copying. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_MemoryStream* | Returns the pointer to the {@link OH_Drawing_MemoryStream} object created. |

### OH_Drawing_MemoryStreamDestroy()

```c
void OH_Drawing_MemoryStreamDestroy(OH_Drawing_MemoryStream* memoryStream)
```

**Description**

Destroys an **OH_Drawing_MemoryStream** object and reclaims the memory occupied by the object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_MemoryStream* memoryStream | Pointer to an {@link OH_Drawing_MemoryStream} object. |


