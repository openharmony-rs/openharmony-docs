# drawing_surface.h
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## Overview

This file declares the functions related to the surface in the drawing module, including creating, destroying, and using the surface.

**File to include**: <native_drawing/drawing_surface.h>

**Library**: libnative_drawing.so

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_Surface* OH_Drawing_SurfaceCreateFromGpuContext(OH_Drawing_GpuContext* gpuContext, bool flag, OH_Drawing_Image_Info imageInfo)](#oh_drawing_surfacecreatefromgpucontext) | Creates an **OH_Drawing_Surface** object using the GPU context to manage the content drawn on the canvas.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **gpuContext** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [OH_Drawing_Surface* OH_Drawing_SurfaceCreateOnScreen(OH_Drawing_GpuContext* gpuContext, OH_Drawing_Image_Info imageInfo, void* window)](#oh_drawing_surfacecreateonscreen) | Creates an **OH_Drawing_Surface** object bound to the window using the GPU context to manage the content drawn on the canvas.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>**OH_DRAWING_ERROR_INVALID_PARAMETER** if **gpuContext** or **window** is NULL.|
| [OH_Drawing_Canvas* OH_Drawing_SurfaceGetCanvas(OH_Drawing_Surface* surface)](#oh_drawing_surfacegetcanvas) | Obtains a canvas from an **OH_Drawing_Surface** object.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **surface** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [OH_Drawing_ErrorCode OH_Drawing_SurfaceFlush(OH_Drawing_Surface* surface)](#oh_drawing_surfaceflush) | Pushes the drawing content from an **OH_Drawing_Surface** object to the GPU for rendering.|
| [void OH_Drawing_SurfaceDestroy(OH_Drawing_Surface* surface)](#oh_drawing_surfacedestroy) | Destroys an **OH_Drawing_Surface** object and reclaims the memory occupied.|

## Function Description

### OH_Drawing_SurfaceCreateFromGpuContext()

```
OH_Drawing_Surface* OH_Drawing_SurfaceCreateFromGpuContext(OH_Drawing_GpuContext* gpuContext, bool flag, OH_Drawing_Image_Info imageInfo)
```

**Description**

Creates an **OH_Drawing_Surface** object using the GPU context to manage the content drawn on the canvas.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **gpuContext** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md)* gpuContext | Pointer to an [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md) object.|
| bool flag | Whether the memory allocation is counted in the cache budget. **true** means yes; **false** otherwise.|
| [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md) imageInfo | Image information struct.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Surface](capi-drawing-oh-drawing-surface.md)* | Returns a pointer to the created [OH_Drawing_Surface](capi-drawing-oh-drawing-surface.md) object.|

### OH_Drawing_SurfaceCreateOnScreen()

```
OH_Drawing_Surface* OH_Drawing_SurfaceCreateOnScreen(OH_Drawing_GpuContext* gpuContext, OH_Drawing_Image_Info imageInfo, void* window)
```

**Description**

Creates an **OH_Drawing_Surface** object bound to the window using the GPU context to manage the content drawn on the canvas.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>**OH_DRAWING_ERROR_INVALID_PARAMETER** if **gpuContext** or **window** is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 16


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md)* gpuContext | Pointer to an [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md) object.<br>This object must be created by [OH_Drawing_GpuContextCreate](capi-drawing-gpu-context-h.md#oh_drawing_gpucontextcreate). Otherwise, the **OH_Drawing_Surface** object fails to be created.|
| [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md) imageInfo | Image information struct.|
| void* window | Pointer to the window object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Surface](capi-drawing-oh-drawing-surface.md)* | Returns a pointer to the created [OH_Drawing_Surface](capi-drawing-oh-drawing-surface.md) object.|

### OH_Drawing_SurfaceGetCanvas()

```
OH_Drawing_Canvas* OH_Drawing_SurfaceGetCanvas(OH_Drawing_Surface* surface)
```

**Description**

Obtains a canvas from an **OH_Drawing_Surface** object.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **surface** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Surface](capi-drawing-oh-drawing-surface.md)* surface | Pointer to an **OH_Drawing_Surface** object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* | Returns a pointer to the created [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md) object. The pointer returned does not need to be managed by the caller.|

### OH_Drawing_SurfaceFlush()

```
OH_Drawing_ErrorCode OH_Drawing_SurfaceFlush(OH_Drawing_Surface* surface)
```

**Description**

Pushes the drawing content from an **OH_Drawing_Surface** object to the GPU for rendering.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 16


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Surface](capi-drawing-oh-drawing-surface.md)* surface | Pointer to the created [OH_Drawing_Surface](capi-drawing-oh-drawing-surface.md) object. This object must be created by calling [OH_Drawing_SurfaceCreateOnScreen](capi-drawing-surface-h.md#oh_drawing_surfacecreateonscreen). Otherwise, calling the current API has no effect.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **surface** is NULL.|

### OH_Drawing_SurfaceDestroy()

```
void OH_Drawing_SurfaceDestroy(OH_Drawing_Surface* surface)
```

**Description**

Destroys an **OH_Drawing_Surface** object and reclaims the memory occupied.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Surface](capi-drawing-oh-drawing-surface.md)* surface | Pointer to an **OH_Drawing_Surface** object.|
