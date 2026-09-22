# drawing_gpu_context.h

## Overview

This file declares the functions related to the GPU context in the drawing module.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Drawing_GpuContextOptions](capi-drawing-oh-drawing-gpucontextoptions.md) | OH_Drawing_GpuContextOptions | This struct describes the options about the GPU context. |

### Function

| Name | Description |
| -- | -- |
| [OH_Drawing_GpuContext* OH_Drawing_GpuContextCreateFromGL(OH_Drawing_GpuContextOptions gpuContextOptions)](#oh_drawing_gpucontextcreatefromgl) | Creates an **OH_Drawing_GpuContext** object that uses OpenGL as the backend interface.(Deprecated in API18) |
| [OH_Drawing_GpuContext* OH_Drawing_GpuContextCreate(void)](#oh_drawing_gpucontextcreate) | Creates an **OH_Drawing_GpuContext** object, for which the backend type depends on the device. |
| [void OH_Drawing_GpuContextDestroy(OH_Drawing_GpuContext* gpuContext)](#oh_drawing_gpucontextdestroy) | Destroys an **OH_Drawing_GpuContext** object and reclaims the memory occupied by the object. |

## Function description

### OH_Drawing_GpuContextCreateFromGL()

```c
OH_Drawing_GpuContext* OH_Drawing_GpuContextCreateFromGL(OH_Drawing_GpuContextOptions gpuContextOptions)
```

**Description**

Creates an **OH_Drawing_GpuContext** object that uses OpenGL as the backend interface.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Deprecated**: 18

**Replaced by**: OH_Drawing_GpuContextCreate

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_Drawing_GpuContextOptions](capi-drawing-oh-drawing-gpucontextoptions.md) gpuContextOptions | GPU context options, which is [OH_Drawing_GpuContextOptions](capi-drawing-oh-drawing-gpucontextoptions.md). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_GpuContext* | Returns the pointer to the [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md) object created. |

### OH_Drawing_GpuContextCreate()

```c
OH_Drawing_GpuContext* OH_Drawing_GpuContextCreate(void)
```

**Description**

Creates an **OH_Drawing_GpuContext** object, for which the backend type depends on the device.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 16

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_GpuContext* | Returns the pointer to the [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md) object created. |

### OH_Drawing_GpuContextDestroy()

```c
void OH_Drawing_GpuContextDestroy(OH_Drawing_GpuContext* gpuContext)
```

**Description**

Destroys an **OH_Drawing_GpuContext** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_GpuContext* gpuContext | Pointer to an [OH_Drawing_GpuContext](capi-drawing-oh-drawing-gpucontext.md) object. |


