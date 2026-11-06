# drawing_point.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=cfa59f2ade5e74278a5dbd3dbd7bab536925f809 translatedAt=2026-08-24T08:48:47.302Z pushedAt=2026-08-31T09:12:22.828Z -->

## Overview

This file declares the functions related to coordinate points, supporting operations such as creating, obtaining, setting, negating, offsetting, and destroying coordinate point objects, to facilitate the management and transformation of coordinate points in 2D graphics drawing.<br>This module adopts a single-thread model, and the caller is responsible for managing thread safety and context state switching.

**File to include**: \<native_drawing/drawing_point.h\>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_Point* OH_Drawing_PointCreate(float x, float y)](#oh_drawing_pointcreate) | Creates a coordinate point object. When the coordinate point object is no longer needed, you must call [OH_Drawing_PointDestroy](#oh_drawing_pointdestroy) to destroy it and reclaim the memory. |
| [OH_Drawing_ErrorCode OH_Drawing_PointGetX(const OH_Drawing_Point* point, float* x)](#oh_drawing_pointgetx) | Obtains the x-axis coordinate value of the coordinate point. |
| [OH_Drawing_ErrorCode OH_Drawing_PointGetY(const OH_Drawing_Point* point, float* y)](#oh_drawing_pointgety) | Obtains the y-axis coordinate value of the coordinate point. |
| [OH_Drawing_ErrorCode OH_Drawing_PointSet(OH_Drawing_Point* point, float x, float y)](#oh_drawing_pointset) | Sets the x-axis and y-axis coordinates of the coordinate point. |
| [OH_Drawing_ErrorCode OH_Drawing_PointNegate(OH_Drawing_Point* point)](#oh_drawing_pointnegate) | Negates the x-axis and y-axis coordinates of the coordinate point. |
| [OH_Drawing_ErrorCode OH_Drawing_PointOffset(OH_Drawing_Point* point, float dx, float dy)](#oh_drawing_pointoffset) | Offsets the coordinate point by a specified distance along the x-axis and y-axis. |
| [void OH_Drawing_PointDestroy(OH_Drawing_Point* point)](#oh_drawing_pointdestroy) | Destroys the coordinate point object and reclaims the memory occupied by it. Call this function after the object is created by [OH_Drawing_PointCreate](#oh_drawing_pointcreate) and is no longer used. |

## Function Description

### OH_Drawing_PointCreate()

```c
OH_Drawing_Point* OH_Drawing_PointCreate(float x, float y)
```

**Description**

Creates a coordinate point object. When this coordinate point object is no longer needed, you must call [OH_Drawing_PointDestroy](#oh_drawing_pointdestroy) to destroy it and reclaim the memory.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| float x | Indicates the x-axis coordinate of the point, in physical pixels (px). |
| float y | Indicates the y-axis coordinate of the point, in physical pixels (px). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* | Function returns a pointer to the created point object. |

### OH_Drawing_PointGetX()

```c
OH_Drawing_ErrorCode OH_Drawing_PointGetX(const OH_Drawing_Point* point, float* x)
```

**Description**

Obtains the x-axis coordinate value of the coordinate point.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* point | Pointer to an [OH_Drawing_Point](capi-drawing-oh-drawing-point.md) object.|
| float* x | Output parameter used to receive the x-axis coordinate value of the point, in physical pixels (px). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if either **point** or **x** is NULL.|

### OH_Drawing_PointGetY()

```c
OH_Drawing_ErrorCode OH_Drawing_PointGetY(const OH_Drawing_Point* point, float* y)
```

**Description**

Obtains the y-axis coordinate value of the coordinate point.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* point | Pointer to an [OH_Drawing_Point](capi-drawing-oh-drawing-point.md) object.|
| float* y | Output parameter, used to receive the y-axis coordinate value of the point object, in physical pixels (px). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if either **point** or **y** is NULL.|

### OH_Drawing_PointSet()

```c
OH_Drawing_ErrorCode OH_Drawing_PointSet(OH_Drawing_Point* point, float x, float y)
```

**Description**

Sets the x-axis and y-axis coordinates of the coordinate point.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* point | Pointer to an [OH_Drawing_Point](capi-drawing-oh-drawing-point.md) object.|
| float x | Indicates the x-axis coordinate of the point, in physical pixels (px). |
| float y | Indicates the y-axis coordinate of the point, in physical pixels (px). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **point** is NULL.|

### OH_Drawing_PointNegate()

```c
OH_Drawing_ErrorCode OH_Drawing_PointNegate(OH_Drawing_Point* point)
```

**Description**

Negates the x-axis and y-axis coordinates of the point object.

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* point | Pointer to an **OH_Drawing_Point** object. |

**Return value**

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER if the point parameter is null. |

### OH_Drawing_PointOffset()

```c
OH_Drawing_ErrorCode OH_Drawing_PointOffset(OH_Drawing_Point* point, float dx, float dy)
```

**Description**

Offsets the coordinate point by a specified distance along the x-axis and y-axis.

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* point | Pointer to the coordinate point object [OH_Drawing_Point](capi-drawing-oh-drawing-point.md). |
| float dx | Offset on the x-axis, in physical pixels (px). A positive value translates the point in the positive direction of the x-axis, and a negative value translates it in the negative direction of the x-axis. |
| float dy | Offset on the y-axis, in physical pixels (px). A positive value translates the point in the positive direction of the y-axis, and a negative value translates it in the negative direction of the y-axis. |

**Return value**

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Function returns the execution error code.<br>Returns OH_DRAWING_SUCCESS, indicating execution success.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER, indicating that the parameter point is null. |

### OH_Drawing_PointDestroy()

```c
void OH_Drawing_PointDestroy(OH_Drawing_Point* point)
```

**Description**

Destroys the coordinate point object and reclaims the memory occupied by it. Call this function after the object is created by [OH_Drawing_PointCreate](#oh_drawing_pointcreate) and is no longer used.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* point | Pointer to an **OH_Drawing_Point** object.|