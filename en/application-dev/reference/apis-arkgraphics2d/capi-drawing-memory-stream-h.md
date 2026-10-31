# drawing_memory_stream.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=da4ce3899fe5c7dac337992e49d801ccfd653425 translatedAt=2026-08-24T08:35:09.339Z pushedAt=2026-08-31T08:43:41.352Z -->

## Overview

This file declares the functions related to the memory stream, which support creating and destroying memory stream objects based on in-memory data. A memory stream supports two access modes: copying data or directly referencing data.<br>This module uses a single-thread model. The caller must manage thread safety and context state switching.

**File to include:** \<native_drawing/drawing_memory_stream.h\>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_MemoryStream* OH_Drawing_MemoryStreamCreate(const void* data, size_t length, bool copyData)](#oh_drawing_memorystreamcreate) | Creates a memory stream object to encapsulate data in memory as a stream, which can be used as a data source for graphics processing APIs (such as image decoding) and subsequent drawing APIs. After the created memory stream object is used, call [OH_Drawing_MemoryStreamDestroy()](#oh_drawing_memorystreamdestroy) to destroy it and reclaim the memory.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if data is NULL or length is 0. |
| [void OH_Drawing_MemoryStreamDestroy(OH_Drawing_MemoryStream* memoryStream)](#oh_drawing_memorystreamdestroy) | Destroys the memory stream object created by [OH_Drawing_MemoryStreamCreate()](#oh_drawing_memorystreamcreate) and reclaims the memory occupied by the object. |

## Function Description

### OH_Drawing_MemoryStreamCreate()

```c
OH_Drawing_MemoryStream* OH_Drawing_MemoryStreamCreate(const void* data, size_t length, bool copyData)
```

**Description**

Creates a memory stream object to encapsulate in-memory data as a stream, which can be used as a data source for subsequent drawing APIs such as graphics processing APIs (for example, image decoding). After the created memory stream object is used, call [OH_Drawing_MemoryStreamDestroy()](#oh_drawing_memorystreamdestroy) to destroy it and reclaim the memory.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code value.<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if data is NULL or length is 0.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const void* data | Pointer to the data buffer for creating the memory stream. The data is a binary byte stream, and its length is specified by the length parameter, in bytes. data cannot be NULL. If it is NULL, OH_DRAWING_ERROR_INVALID_PARAMETER is returned. When copyData is false, the caller must also ensure that the data pointed to by data remains valid throughout the lifetime of the memory stream object. |
| size_t length | Length of the data segment, in bytes. The value must be greater than 0. If it is 0, OH_DRAWING_ERROR_INVALID_PARAMETER is returned. |
| bool copyData | Whether to copy data. The value **true** means that the **OH_Drawing_MemoryStream** object copies the data, and **false** means that the **OH_Drawing_MemoryStream** object directly uses the data without copying.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_MemoryStream](capi-drawing-oh-drawing-memorystream.md)* | Pointer to the created memory stream object [OH_Drawing_MemoryStream](capi-drawing-oh-drawing-memorystream.md), which can be used as a data source for subsequent graphics processing APIs (such as image decoding). |

### OH_Drawing_MemoryStreamDestroy()

```c
void OH_Drawing_MemoryStreamDestroy(OH_Drawing_MemoryStream* memoryStream)
```

**Description**

Destroys the memory stream object created by [OH_Drawing_MemoryStreamCreate()](#oh_drawing_memorystreamcreate) and reclaims the memory occupied by the object. After destruction, the memory stream object must not be accessed again.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_MemoryStream](capi-drawing-oh-drawing-memorystream.md)* memoryStream | Pointer to an [OH_Drawing_MemoryStream](capi-drawing-oh-drawing-memorystream.md) object.|