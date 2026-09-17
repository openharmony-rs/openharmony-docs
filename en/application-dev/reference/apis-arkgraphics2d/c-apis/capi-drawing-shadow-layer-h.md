# drawing_shadow_layer.h

## Overview

This file declares the functions related to the shadow in the drawing module.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [OH_Drawing_ShadowLayer* OH_Drawing_ShadowLayerCreate(float blurRadius, float x, float y, uint32_t color)](#oh_drawing_shadowlayercreate) | Creates an **OH_Drawing_ShadowLayer** object. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **blurRadius** is less than or equal to 0, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [void OH_Drawing_ShadowLayerDestroy(OH_Drawing_ShadowLayer* shadowLayer)](#oh_drawing_shadowlayerdestroy) | Destroys an **OH_Drawing_ShadowLayer** object and reclaims the memory occupied by the object. |

## Function description

### OH_Drawing_ShadowLayerCreate()

```c
OH_Drawing_ShadowLayer* OH_Drawing_ShadowLayerCreate(float blurRadius, float x, float y, uint32_t color)
```

**Description**

Creates an **OH_Drawing_ShadowLayer** object. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **blurRadius** is less than or equal to 0, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| float blurRadius | Radius of the shadow layer. The value must be greater than 0. |
| float x | Offset on the X axis. |
| float y | Offset on the Y axis. |
| uint32_t color | Color of the shadow. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ShadowLayer* | Returns the pointer to the OH_Drawing_ShadowLayer object created. |

### OH_Drawing_ShadowLayerDestroy()

```c
void OH_Drawing_ShadowLayerDestroy(OH_Drawing_ShadowLayer* shadowLayer)
```

**Description**

Destroys an **OH_Drawing_ShadowLayer** object and reclaims the memory occupied by the object.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_ShadowLayer* shadowLayer | Pointer to the shadow layer. |


