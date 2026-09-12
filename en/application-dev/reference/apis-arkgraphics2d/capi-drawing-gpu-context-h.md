# drawing_gpu_context.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=da4ce3899fe5c7dac337992e49d801ccfd653425 translatedAt=2026-08-24T08:28:45.440Z pushedAt=2026-08-31T07:29:22.708Z -->

## Overview

Declares the functions related to the GPU context object in the drawing module, which are used to create, configure, and destroy the GPU context object, providing the context environment required for GPU-accelerated rendering in the drawing module.<br>This module adopts a single-thread model, and the caller is responsible for managing thread safety and context state switching.

**File to include:** \<native_drawing/drawing_gpu_context.h\>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Drawing_GpuContextOptions](capi-drawing-oh-drawing-gpucontextoptions.md) | OH_Drawing_GpuContextOptions | Describes the options about the GPU context.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_GpuContext* OH_Drawing_GpuContextCreateFromGL(OH_Drawing_GpuContextOptions gpuContextOptions)](#oh_drawing_gpucontextcreatefromgl) | Creates a GPU context object that uses OpenGL as the backend interface. After the GPU context object is used, call [OH_Drawing_GpuContextDestroy](#oh_drawing_gpucontextdestroy) to destroy it and reclaim the memory. |
| [OH_Drawing_GpuContext* OH_Drawing_GpuContextCreate(void)](#oh_drawing_gpucontextcreate) | Creates a GPU context object. The backend type used depends on the running device. After the GPU context object is used, call [OH_Drawing_GpuContextDestroy](#oh_drawing_gpucontextdestroy) to destroy it and reclaim the memory. |
| [void OH_Drawing_GpuContextDestroy(OH_Drawing_GpuContext* gpuContext)](#oh_drawing_gpucontextdestroy) | Destroys a GPU context object and reclaims the memory occupied by the object. After this API is called, the pointer to the GPU context object becomes invalid and cannot be used again or called repeatedly. |

## Function Description

### OH_Drawing_GpuContextCreateFromGL()

```c
OH_Drawing_GpuContext* OH_Drawing_GpuContextCreateFromGL(OH_Drawing_GpuContextOptions gpuContextOptions)
```

**Description**

Creates a GPU context object that uses OpenGL as the backend interface. After the created GPU context object is no longer needed, call [OH_Drawing_GpuContextDestroy](#oh_drawing_gpucontextdestroy) to destroy it and reclaim the memory.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Deprecated from**: 18

**Alternative API:** [OH_Drawing_GpuContextCreate](capi-drawing-gpu-context-h.md#oh_drawing_gpucontextcreate)

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_GpuContextOptions](capi-drawing-oh-drawing-gpucontextoptions.md) gpuContextOptions | GPU context options [OH_Drawing_GpuContextOptions](capi-drawing-oh-drawing-gpucontextoptions.md), used to configure the created GPU context object. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md)* | Pointer to the created GPU context object [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md). |

### OH_Drawing_GpuContextCreate()

```c
OH_Drawing_GpuContext* OH_Drawing_GpuContextCreate(void)
```

**Description**

Creates a GPU context object. The backend type used depends on the running device. After the created GPU context object is no longer needed, call [OH_Drawing_GpuContextDestroy](#oh_drawing_gpucontextdestroy) to destroy it and reclaim the memory.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 16

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md)* | Pointer to the created GPU context object [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md). |

### OH_Drawing_GpuContextDestroy()

```c
void OH_Drawing_GpuContextDestroy(OH_Drawing_GpuContext* gpuContext)
```

**Description**

Destroys a GPU context object and reclaims the memory occupied by the object. After this API is called, the pointer to the GPU context object becomes invalid and cannot be used again or passed to this API repeatedly.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md)* gpuContext | Pointer to the GPU context object. After the call, this pointer becomes invalid and cannot be used again; otherwise, undefined behavior or a program crash may occur. |