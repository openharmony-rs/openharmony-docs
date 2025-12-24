# drawing_gpu_context.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## Overview

This file declares the functions related to the GPU context in the drawing module.

**File to include**: <native_drawing/drawing_gpu_context.h>

**Library**: libnative_drawing.so

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
| [OH_Drawing_GpuContext* OH_Drawing_GpuContextCreateFromGL(OH_Drawing_GpuContextOptions gpuContextOptions)](#oh_drawing_gpucontextcreatefromgl) | Creates an **OH_Drawing_GpuContext** object that uses OpenGL as the backend interface.|
| [OH_Drawing_GpuContext* OH_Drawing_GpuContextCreate(void)](#oh_drawing_gpucontextcreate) | Creates an **OH_Drawing_GpuContext** object, for which the backend type depends on the device.|
| [void OH_Drawing_GpuContextDestroy(OH_Drawing_GpuContext* gpuContext)](#oh_drawing_gpucontextdestroy) | Destroys an **OH_Drawing_GpuContext** object and reclaims the memory occupied by the object.|

## Function Description

### OH_Drawing_GpuContextCreateFromGL()

```c
OH_Drawing_GpuContext* OH_Drawing_GpuContextCreateFromGL(OH_Drawing_GpuContextOptions gpuContextOptions)
```

**Description**

Creates an **OH_Drawing_GpuContext** object that uses OpenGL as the backend interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Deprecated from**: 18

**Substitute**: OH_Drawing_GpuContextCreate


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_GpuContextOptions](capi-drawing-oh-drawing-gpucontextoptions.md) gpuContextOptions | GPU context options, which is [OH_Drawing_GpuContextOptions](capi-drawing-oh-drawing-gpucontextoptions.md).|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md)* | Returns the pointer to the [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md) object created.|

### OH_Drawing_GpuContextCreate()

```c
OH_Drawing_GpuContext* OH_Drawing_GpuContextCreate(void)
```

**Description**

Creates an **OH_Drawing_GpuContext** object, for which the backend type depends on the device.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 16

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md)* | Returns the pointer to the [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md) object created.|

### OH_Drawing_GpuContextDestroy()

```c
void OH_Drawing_GpuContextDestroy(OH_Drawing_GpuContext* gpuContext)
```

**Description**

Destroys an **OH_Drawing_GpuContext** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md)* gpuContext | Pointer to an [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md) object.|
