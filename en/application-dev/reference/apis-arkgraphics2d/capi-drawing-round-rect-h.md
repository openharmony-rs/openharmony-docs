# drawing_round_rect.h
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## Overview

This file declares the functions related to the rounded rectangle in the drawing module.

**File to include**: <native_drawing/drawing_round_rect.h>

**Library**: libnative_drawing.so

**Since**: 11

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Enumerated value

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Drawing_CornerPos](#oh_drawing_cornerpos) | OH_Drawing_CornerPos | Defines an enum for the corner positions of a rounded rectangle.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_RoundRect* OH_Drawing_RoundRectCreate(const OH_Drawing_Rect* rect, float xRad, float yRad)](#oh_drawing_roundrectcreate) | Creates an **OH_Drawing_RoundRect** object. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [OH_Drawing_RoundRect* OH_Drawing_RoundRectCopy(const OH_Drawing_RoundRect* roundRect)](#oh_drawing_roundrectcopy) | Creates a copy of a rounded rectangle.|
| [void OH_Drawing_RoundRectSetCorner(OH_Drawing_RoundRect* roundRect,OH_Drawing_CornerPos pos, OH_Drawing_Corner_Radii radii)](#oh_drawing_roundrectsetcorner) | Sets the radii of the specified rounded corner in this rounded rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **roundRect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [OH_Drawing_Corner_Radii OH_Drawing_RoundRectGetCorner(OH_Drawing_RoundRect* roundRect, OH_Drawing_CornerPos pos)](#oh_drawing_roundrectgetcorner) | Obtains the radii of the specified rounded corner in a rounded rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **roundRect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_RoundRectDestroy(OH_Drawing_RoundRect* roundRect)](#oh_drawing_roundrectdestroy) | Destroys an **OH_Drawing_RoundRect** object and reclaims the memory occupied by the object.|
| [OH_Drawing_ErrorCode OH_Drawing_RoundRectOffset(OH_Drawing_RoundRect* roundRect, float dx, float dy)](#oh_drawing_roundrectoffset) | Translates a rounded rectangle by an offset along the X axis and Y axis.|

## Enum Description

### OH_Drawing_CornerPos

```
enum OH_Drawing_CornerPos
```

**Description**

Defines an enum for the corner positions of a rounded rectangle.

**Since**: 12

| Value| Description|
| -- | -- |
| CORNER_POS_TOP_LEFT | Top left corner of the rounded rectangle.|
| CORNER_POS_TOP_RIGHT | Top right corner of the rounded rectangle.|
| CORNER_POS_BOTTOM_RIGHT | Bottom right corner of the rounded rectangle.|
| CORNER_POS_BOTTOM_LEFT | Bottom left corner of the rounded rectangle.|


## Function Description

### OH_Drawing_RoundRectCreate()

```
OH_Drawing_RoundRect* OH_Drawing_RoundRectCreate(const OH_Drawing_Rect* rect, float xRad, float yRad)
```

**Description**

Creates an **OH_Drawing_RoundRect** object. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|
| float xRad | Radius of the rounded corner on the X axis. A negative number is invalid.|
| float yRad | Radius of the rounded corner on the Y axis. A negative number is invalid.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_RoundRect](capi-drawing-oh-drawing-roundrect.md)* | Returns the pointer to the **OH_Drawing_RoundRect** object created.|

### OH_Drawing_RoundRectCopy()

```
OH_Drawing_RoundRect* OH_Drawing_RoundRectCopy(const OH_Drawing_RoundRect* roundRect)
```

**Description**

Creates a copy of a rounded rectangle.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20


**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_RoundRect](capi-drawing-oh-drawing-roundrect.md)* roundRect | Pointer to an [OH_Drawing_RoundRect](capi-drawing-oh-drawing-roundrect.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_RoundRect](capi-drawing-oh-drawing-roundrect.md)* | Returns the pointer to the new **OH_Drawing_RoundRect** object created.|

### OH_Drawing_RoundRectSetCorner()

```
void OH_Drawing_RoundRectSetCorner(OH_Drawing_RoundRect* roundRect,OH_Drawing_CornerPos pos, OH_Drawing_Corner_Radii radii)
```

**Description**

Sets the radii of the specified rounded corner in this rounded rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **roundRect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_RoundRect](capi-drawing-oh-drawing-roundrect.md)* roundRect | Pointer to an **OH_Drawing_RoundRect** object.|
| [OH_Drawing_CornerPos](#oh_drawing_cornerpos) pos | Position of the rounded corner. For details about the available options, see [OH_Drawing_CornerPos](capi-drawing-round-rect-h.md#oh_drawing_cornerpos).|
| OH_Drawing_Corner_Radii radii | OH_Drawing_Corner_Radii struct, including the radii on the X axis and Y axis. A radius less than or equal to 0 is invalid.|

### OH_Drawing_RoundRectGetCorner()

```
OH_Drawing_Corner_Radii OH_Drawing_RoundRectGetCorner(OH_Drawing_RoundRect* roundRect, OH_Drawing_CornerPos pos)
```

**Description**

Obtains the radii of the specified rounded corner in a rounded rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **roundRect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_RoundRect](capi-drawing-oh-drawing-roundrect.md)* roundRect | Pointer to an **OH_Drawing_RoundRect** object.|
| [OH_Drawing_CornerPos](#oh_drawing_cornerpos) pos | Position of the rounded corner. For details about the available options, see [OH_Drawing_CornerPos](capi-drawing-round-rect-h.md#oh_drawing_cornerpos).|

**Returns**

| Type| Description|
| -- | -- |
| OH_Drawing_Corner_Radii | Returns an OH_Drawing_Corner_Radii struct, including the radii on the X axis and Y axis.|

### OH_Drawing_RoundRectDestroy()

```
void OH_Drawing_RoundRectDestroy(OH_Drawing_RoundRect* roundRect)
```

**Description**

Destroys an **OH_Drawing_RoundRect** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_RoundRect](capi-drawing-oh-drawing-roundrect.md)* roundRect | Pointer to an **OH_Drawing_RoundRect** object.|

### OH_Drawing_RoundRectOffset()

```
OH_Drawing_ErrorCode OH_Drawing_RoundRectOffset(OH_Drawing_RoundRect* roundRect, float dx, float dy)
```

**Description**

Translates a rounded rectangle by an offset along the X axis and Y axis.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_RoundRect](capi-drawing-oh-drawing-roundrect.md)* roundRect | Pointer to the [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md) object.|
| float dx | X offset.|
| float dy | Y offset.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **roundRect** is NULL.|
