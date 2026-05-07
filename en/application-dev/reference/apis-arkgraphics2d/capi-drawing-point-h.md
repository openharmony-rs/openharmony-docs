# drawing_point.h
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## Overview

This file declares the functions related to the coordinate point in the drawing module.

**File to include**: <native_drawing/drawing_point.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_Point* OH_Drawing_PointCreate(float x, float y)](#oh_drawing_pointcreate) | Creates an **OH_Drawing_Point** object.|
| [OH_Drawing_ErrorCode OH_Drawing_PointGetX(const OH_Drawing_Point* point, float* x)](#oh_drawing_pointgetx) | Obtains the X coordinate of a point.|
| [OH_Drawing_ErrorCode OH_Drawing_PointGetY(const OH_Drawing_Point* point, float* y)](#oh_drawing_pointgety) | Obtains the Y coordinate of a point.|
| [OH_Drawing_ErrorCode OH_Drawing_PointSet(OH_Drawing_Point* point, float x, float y)](#oh_drawing_pointset) | Sets the X and Y coordinates of a point.|
| [void OH_Drawing_PointDestroy(OH_Drawing_Point* point)](#oh_drawing_pointdestroy) | Destroys an **OH_Drawing_Point** object and reclaims the memory occupied by the object.|

## Function Description

### OH_Drawing_PointCreate()

```c
OH_Drawing_Point* OH_Drawing_PointCreate(float x, float y)
```

**Description**

Creates an **OH_Drawing_Point** object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| float x | X coordinate of the point.|
| float y | Y coordinate of the point.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* | Returns the pointer to the **OH_Drawing_Point** object created.|

### OH_Drawing_PointGetX()

```c
OH_Drawing_ErrorCode OH_Drawing_PointGetX(const OH_Drawing_Point* point, float* x)
```

**Description**

Obtains the X coordinate of a point.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* point | Pointer to an [OH_Drawing_Point](capi-drawing-oh-drawing-point.md) object.|
| float* x | Pointer to the X coordinate.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if either **point** or **x** is NULL.|

### OH_Drawing_PointGetY()

```c
OH_Drawing_ErrorCode OH_Drawing_PointGetY(const OH_Drawing_Point* point, float* y)
```

**Description**

Obtains the Y coordinate of a point.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* point | Pointer to an [OH_Drawing_Point](capi-drawing-oh-drawing-point.md) object.|
| float* y | Pointer to the Y coordinate.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if either **point** or **y** is NULL.|

### OH_Drawing_PointSet()

```c
OH_Drawing_ErrorCode OH_Drawing_PointSet(OH_Drawing_Point* point, float x, float y)
```

**Description**

Sets the X and Y coordinates of a point.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* point | Pointer to an [OH_Drawing_Point](capi-drawing-oh-drawing-point.md) object.|
| float x | Pointer to the X coordinate.|
| float y | Pointer to the Y coordinate.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **point** is NULL.|

### OH_Drawing_PointDestroy()

```c
void OH_Drawing_PointDestroy(OH_Drawing_Point* point)
```

**Description**

Destroys an **OH_Drawing_Point** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Point](capi-drawing-oh-drawing-point.md)* point | Pointer to an **OH_Drawing_Point** object.|
