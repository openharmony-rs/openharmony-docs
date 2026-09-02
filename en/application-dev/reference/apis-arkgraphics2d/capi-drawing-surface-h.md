# drawing_surface.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=9d2b351312a4e4fca532309901802ab24e70ce23 translatedAt=2026-08-24T08:59:35.851Z pushedAt=2026-08-31T09:23:01.791Z -->

## Overview

This file declares the functions related to the surface, including creating, destroying, and using the surface. A surface object is used to manage the content drawn on the canvas. It supports creating an offscreen surface through a GPU context and creating a surface bound to a screen window.<br>This module adopts a single-thread model. The caller must manage thread safety and context state switching.

**File to include:** \<native_drawing/drawing_surface.h\>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_Surface* OH_Drawing_SurfaceCreateFromGpuContext(OH_Drawing_GpuContext* gpuContext, bool flag, OH_Drawing_Image_Info imageInfo)](#oh_drawing_surfacecreatefromgpucontext) | Creates an offscreen surface object using a GPU context to manage the canvas drawing content. If the drawing content needs to be displayed on screen (used with [OH_Drawing_SurfaceFlush](#oh_drawing_surfaceflush)), use [OH_Drawing_SurfaceCreateOnScreen](#oh_drawing_surfacecreateonscreen) to create a surface object bound to the screen window instead.<br>This API generates an error code. You can use [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to view the error code value.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if gpuContext is NULL. |
| [OH_Drawing_Surface* OH_Drawing_SurfaceCreateOnScreen(OH_Drawing_GpuContext* gpuContext, OH_Drawing_Image_Info imageInfo, void* window)](#oh_drawing_surfacecreateonscreen) | Creates a surface object bound to the screen window using a GPU context to manage the canvas drawing content. If the drawing content does not need to be displayed on screen, use [OH_Drawing_SurfaceCreateFromGpuContext](#oh_drawing_surfacecreatefromgpucontext) to create an offscreen surface object instead.<br>This API generates an error code. You can use [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to view the error code value.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if gpuContext or window is NULL.<br>The width and height of imageInfo must be consistent with those of window; otherwise, the object fails to be created. |
| [OH_Drawing_Canvas* OH_Drawing_SurfaceGetCanvas(OH_Drawing_Surface* surface)](#oh_drawing_surfacegetcanvas) | Obtains a canvas from an **OH_Drawing_Surface** object.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **surface** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [OH_Drawing_ErrorCode OH_Drawing_SurfaceFlush(OH_Drawing_Surface* surface)](#oh_drawing_surfaceflush) | Submits the canvas drawing content on the surface object to the GPU for processing to display the drawing content on screen. |
| [void OH_Drawing_SurfaceDestroy(OH_Drawing_Surface* surface)](#oh_drawing_surfacedestroy) | Destroys the surface object and reclaims the memory occupied by it. After the surface object is destroyed by calling this API, the canvas object obtained through [OH_Drawing_SurfaceGetCanvas](#oh_drawing_surfacegetcanvas) should no longer be used, and its lifecycle is managed by the surface object. |

## Function Description

### OH_Drawing_SurfaceCreateFromGpuContext()

```c
OH_Drawing_Surface* OH_Drawing_SurfaceCreateFromGpuContext(OH_Drawing_GpuContext* gpuContext, bool flag, OH_Drawing_Image_Info imageInfo)
```

**Description**

Creates an offscreen surface object through a GPU context to manage the content drawn on the canvas. If the drawn content needs to be displayed on the screen (used together with [OH_Drawing_SurfaceFlush](#oh_drawing_surfaceflush)), use [OH_Drawing_SurfaceCreateOnScreen](#oh_drawing_surfacecreateonscreen) instead to create a surface object bound to a screen window.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code.<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if gpuContext is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md)* gpuContext | Pointer to the graphics processor context object [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md). |
| bool flag | Whether the memory allocation is counted toward the cache budget. The value true means the allocation is counted toward the cache budget, and false means it is not. The cache budget is the upper limit of memory available to the graphics processor cache, and allocations counted toward the budget consume cache quota. Set flag to true when the drawing content needs to be included in cache management to improve performance; set flag to false when the drawing content is temporary data that does not require long-term caching. |
| [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md) imageInfo | Image information struct [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md), used to specify the image width, height, color type, and alpha type of the surface to be created. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Surface](capi-drawing-oh-drawing-surface.md)* | Pointer to the created surface object [OH_Drawing_Surface](capi-drawing-oh-drawing-surface.md). |

### OH_Drawing_SurfaceCreateOnScreen()

```c
OH_Drawing_Surface* OH_Drawing_SurfaceCreateOnScreen(OH_Drawing_GpuContext* gpuContext, OH_Drawing_Image_Info imageInfo, void* window)
```

**Description**

Creates a surface object bound to a screen window through a GPU context to manage the content drawn on the canvas. If the content does not need to be displayed on the screen, use [OH_Drawing_SurfaceCreateFromGpuContext](#oh_drawing_surfacecreatefromgpucontext) instead to create an offscreen surface object.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code.<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned if gpuContext or window is NULL.<br>The width and height of imageInfo must be consistent with those of window; otherwise, the object fails to be created.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 16

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md)* gpuContext | Pointer to the graphics processor context object [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md). |
| [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md) imageInfo | Image information [OH_Drawing_Image_Info](capi-drawing-oh-drawing-image-info.md) struct, used to specify the image width, height, color type, and alpha type of the surface to be created. |
| void* window | Pointer to the screen window object (OHNativeWindow). The actual value passed in should be of the OHNativeWindow* type. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Surface](capi-drawing-oh-drawing-surface.md)* | Pointer to the created surface object [OH_Drawing_Surface](capi-drawing-oh-drawing-surface.md). |

### OH_Drawing_SurfaceGetCanvas()

```c
OH_Drawing_Canvas* OH_Drawing_SurfaceGetCanvas(OH_Drawing_Surface* surface)
```

**Description**

Obtains a canvas from an **OH_Drawing_Surface** object.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **surface** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Surface](capi-drawing-oh-drawing-surface.md)* surface | Pointer to the created surface object [OH_Drawing_Surface](capi-drawing-oh-drawing-surface.md), used to obtain the canvas object from it. The surface object can be created by [OH_Drawing_SurfaceCreateFromGpuContext](#oh_drawing_surfacecreatefromgpucontext) or [OH_Drawing_SurfaceCreateOnScreen](#oh_drawing_surfacecreateonscreen). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md)* | Pointer to the obtained canvas object [OH_Drawing_Canvas](capi-drawing-oh-drawing-canvas.md). The returned pointer does not need to be managed by the caller, and its lifecycle is managed by the corresponding surface object. After [OH_Drawing_SurfaceDestroy](#oh_drawing_surfacedestroy) is called to destroy the surface object, the canvas object should no longer be used. |

### OH_Drawing_SurfaceFlush()

```c
OH_Drawing_ErrorCode OH_Drawing_SurfaceFlush(OH_Drawing_Surface* surface)
```

**Description**

Submits the content drawn on the canvas of the surface object to the GPU for processing, so that the drawn content is displayed on the screen.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 16

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Surface](capi-drawing-oh-drawing-surface.md)* surface | Pointer to the created surface object [OH_Drawing_Surface](capi-drawing-oh-drawing-surface.md). The surface object must be created by [OH_Drawing_SurfaceCreateOnScreen](capi-drawing-surface-h.md#oh_drawing_surfacecreateonscreen); otherwise, this API call will not display the drawn content on the screen. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br> Returns **OH_DRAWING_SUCCESS** if the operation is successful.<br> Returns **OH_DRAWING_ERROR_INVALID_PARAMETER** if surface is a null pointer. |

### OH_Drawing_SurfaceDestroy()

```c
void OH_Drawing_SurfaceDestroy(OH_Drawing_Surface* surface)
```

**Description**

Destroys the surface object and reclaims the memory occupied by it. After this API is called to destroy the surface object, the canvas object obtained through [OH_Drawing_SurfaceGetCanvas](#oh_drawing_surfacegetcanvas) must no longer be used, because its lifecycle is managed by the surface object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Surface](capi-drawing-oh-drawing-surface.md)* surface | Pointer to the surface object to be destroyed. The surface object can be created by [OH_Drawing_SurfaceCreateFromGpuContext](#oh_drawing_surfacecreatefromgpucontext) or [OH_Drawing_SurfaceCreateOnScreen](#oh_drawing_surfacecreateonscreen). After destruction, the pointer should no longer be used. |