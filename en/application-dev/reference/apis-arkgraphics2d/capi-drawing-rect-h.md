# drawing_rect.h
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

## Overview

The **drawing_rect.h** file declares the functions related to the rectangle in the drawing module.

<!--RP1-->
**Sample**: [NDKAPIDrawing (API14)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/Drawing/NDKAPIDrawing)<!--RP1End-->

**File to include**: <native_drawing/drawing_rect.h>

**Library**: libnative_drawing.so

**Since**: 11

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect* OH_Drawing_RectCreate(float left, float top, float right, float bottom)](#oh_drawing_rectcreate) | Creates an **OH_Drawing_Rect** object, without sorting the coordinates passed in. This means that the coordinates of the upper left corner of the rectangle can be greater than those of the lower right corner.|
| [bool OH_Drawing_RectIntersect(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other)](#oh_drawing_rectintersect) | Checks whether two rectangles intersect and if yes, sets **rect** to the area of intersection.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **rect** or **other** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [bool OH_Drawing_RectJoin(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other)](#oh_drawing_rectjoin) | Obtains the union of two rectangles.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **rect** or **other** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>|
| [void OH_Drawing_RectSetLeft(OH_Drawing_Rect* rect, float left)](#oh_drawing_rectsetleft) | Sets the horizontal coordinate of the upper left corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_RectSetTop(OH_Drawing_Rect* rect, float top)](#oh_drawing_rectsettop) | Sets the vertical coordinate of the upper left corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_RectSetRight(OH_Drawing_Rect* rect, float right)](#oh_drawing_rectsetright) | Sets the horizontal coordinate of the lower right corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_RectSetBottom(OH_Drawing_Rect* rect, float bottom)](#oh_drawing_rectsetbottom) | Sets the vertical coordinate of the lower right corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [float OH_Drawing_RectGetLeft(OH_Drawing_Rect* rect)](#oh_drawing_rectgetleft) | Obtains the X coordinate of the upper left corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [float OH_Drawing_RectGetTop(OH_Drawing_Rect* rect)](#oh_drawing_rectgettop) | Obtains the Y coordinate of the upper left corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [float OH_Drawing_RectGetRight(OH_Drawing_Rect* rect)](#oh_drawing_rectgetright) | Obtains the X coordinate of the lower right corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [float OH_Drawing_RectGetBottom(OH_Drawing_Rect* rect)](#oh_drawing_rectgetbottom) | Obtains the Y coordinate of the lower right corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [float OH_Drawing_RectGetHeight(OH_Drawing_Rect* rect)](#oh_drawing_rectgetheight) | Obtains the height of a rectangle. The height is calculated by using the Y coordinate of the lower right corner of the rectangle minus the Y coordinate of the upper left corner.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [float OH_Drawing_RectGetWidth(OH_Drawing_Rect* rect)](#oh_drawing_rectgetwidth) | Obtains the width of a rectangle. The width is calculated by using the X coordinate of the lower right corner of the rectangle minus the X coordinate of the upper left corner.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_RectCopy(OH_Drawing_Rect* sRect, OH_Drawing_Rect* dRect)](#oh_drawing_rectcopy) | Copies a source rectangle to create a new one.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **sRect** or **dRect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_RectDestroy(OH_Drawing_Rect* rect)](#oh_drawing_rectdestroy) | Destroys an **OH_Drawing_Rect** object and reclaims the memory occupied by the object.|
| [OH_Drawing_Array* OH_Drawing_RectCreateArray(size_t size)](#oh_drawing_rectcreatearray) | Creates a rectangle array object to store multiple rectangle objects. Release this pointer by calling [OH_Drawing_RectDestroyArray](capi-drawing-rect-h.md#oh_drawing_rectdestroyarray) when this object is no longer needed.|
| [OH_Drawing_ErrorCode OH_Drawing_RectGetArraySize(OH_Drawing_Array* rectArray, size_t* pSize)](#oh_drawing_rectgetarraysize) | Obtains the size of an [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) object.|
| [OH_Drawing_ErrorCode OH_Drawing_RectGetArrayElement(OH_Drawing_Array* rectArray, size_t index,OH_Drawing_Rect** rect)](#oh_drawing_rectgetarrayelement) | Obtains the rectangle with the specified index in a rectangle array.|
| [OH_Drawing_ErrorCode OH_Drawing_RectDestroyArray(OH_Drawing_Array* rectArray)](#oh_drawing_rectdestroyarray) | Destroys an **OH_Drawing_Array** object and reclaims the memory occupied by the object.|

## Function Description

### OH_Drawing_RectCreate()

```
OH_Drawing_Rect* OH_Drawing_RectCreate(float left, float top, float right, float bottom)
```

**Description**

Creates an **OH_Drawing_Rect** object, without sorting the coordinates passed in. This means that the coordinates of the upper left corner of the rectangle can be greater than those of the lower right corner.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| float left | X coordinate of the upper left corner of the rectangle.|
| float top | Y coordinate of the upper left corner of the rectangle.|
| float right | X coordinate of the lower right corner of the rectangle.|
| float bottom | Y coordinate of the lower right corner of the rectangle.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* | Returns the pointer to the **OH_Drawing_Rect** object created.|

### OH_Drawing_RectIntersect()

```
bool OH_Drawing_RectIntersect(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other)
```

**Description**

Checks whether two rectangles intersect and if yes, sets **rect** to the area of intersection.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **rect** or **other** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* other | Pointer to an **OH_Drawing_Rect** object.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if they intersect (**rect** is set to the intersection area); returns **false** otherwise (**rect** remains unchanged).|

### OH_Drawing_RectJoin()

```
bool OH_Drawing_RectJoin(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other)
```

**Description**

Obtains the union of two rectangles.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **rect** or **other** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* other | Pointer to an **OH_Drawing_Rect** object.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the union is obtained; returns **false** otherwise. The possible failure cause is that at least one of the parameters **rect** and **other** is NULL or the size of the rectangle specified by **other** is empty.|

### OH_Drawing_RectSetLeft()

```
void OH_Drawing_RectSetLeft(OH_Drawing_Rect* rect, float left)
```

**Description**

Sets the horizontal coordinate of the upper left corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|
| float left | X coordinate of the upper left corner of the rectangle.|

### OH_Drawing_RectSetTop()

```
void OH_Drawing_RectSetTop(OH_Drawing_Rect* rect, float top)
```

**Description**

Sets the vertical coordinate of the upper left corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|
| float top | Y coordinate of the upper left corner of the rectangle.|

### OH_Drawing_RectSetRight()

```
void OH_Drawing_RectSetRight(OH_Drawing_Rect* rect, float right)
```

**Description**

Sets the horizontal coordinate of the lower right corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|
| float right | X coordinate of the lower right corner of the rectangle.|

### OH_Drawing_RectSetBottom()

```
void OH_Drawing_RectSetBottom(OH_Drawing_Rect* rect, float bottom)
```

**Description**

Sets the vertical coordinate of the lower right corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|
| float bottom | Y coordinate of the lower right corner of the rectangle.|

### OH_Drawing_RectGetLeft()

```
float OH_Drawing_RectGetLeft(OH_Drawing_Rect* rect)
```

**Description**

Obtains the X coordinate of the upper left corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|

**Returns**

| Type| Description|
| -- | -- |
| float | X coordinate of the upper left corner of the rectangle.|

### OH_Drawing_RectGetTop()

```
float OH_Drawing_RectGetTop(OH_Drawing_Rect* rect)
```

**Description**

Obtains the Y coordinate of the upper left corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Y coordinate of the upper left corner of the rectangle.|

### OH_Drawing_RectGetRight()

```
float OH_Drawing_RectGetRight(OH_Drawing_Rect* rect)
```

**Description**

Obtains the X coordinate of the lower right corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|

**Returns**

| Type| Description|
| -- | -- |
| float | X coordinate of the lower right corner of the rectangle.|

### OH_Drawing_RectGetBottom()

```
float OH_Drawing_RectGetBottom(OH_Drawing_Rect* rect)
```

**Description**

Obtains the Y coordinate of the lower right corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Y coordinate of the lower right corner of the rectangle.|

### OH_Drawing_RectGetHeight()

```
float OH_Drawing_RectGetHeight(OH_Drawing_Rect* rect)
```

**Description**

Obtains the height of a rectangle. The height is calculated by using the Y coordinate of the lower right corner of the rectangle minus the Y coordinate of the upper left corner.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Returns the height of the rectangle, in pixels.|

### OH_Drawing_RectGetWidth()

```
float OH_Drawing_RectGetWidth(OH_Drawing_Rect* rect)
```

**Description**

Obtains the width of a rectangle. The width is calculated by using the X coordinate of the lower right corner of the rectangle minus the X coordinate of the upper left corner.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Returns the weight of the rectangle, in pixels.|

### OH_Drawing_RectCopy()

```
void OH_Drawing_RectCopy(OH_Drawing_Rect* sRect, OH_Drawing_Rect* dRect)
```

**Description**

Copies a source rectangle to create a new one.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **sRect** or **dRect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* sRect | Pointer to a source rectangle, which is an **OH_Drawing_Rect** object.|
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* dRect | Pointer to a destination rectangle, which is an **OH_Drawing_Rect** object.|

### OH_Drawing_RectDestroy()

```
void OH_Drawing_RectDestroy(OH_Drawing_Rect* rect)
```

**Description**

Destroys an **OH_Drawing_Rect** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|

### OH_Drawing_RectCreateArray()

```
OH_Drawing_Array* OH_Drawing_RectCreateArray(size_t size)
```

**Description**

Creates a rectangle array object to store multiple rectangle objects. Release this pointer by calling [OH_Drawing_RectDestroyArray](capi-drawing-rect-h.md#oh_drawing_rectdestroyarray) when this object is no longer needed.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| size_t size | Size of the rectangle array. The value cannot exceed 65536, which is the maximum number of glyph indices.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* | Returns the pointer to the [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) object created. If the returned object pointer is null, the creation fails.<br> Possible causes are that no memory is available or an input parameter is incorrect.|

### OH_Drawing_RectGetArraySize()

```
OH_Drawing_ErrorCode OH_Drawing_RectGetArraySize(OH_Drawing_Array* rectArray, size_t* pSize)
```

**Description**

Obtains the size of an [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* rectArray | Pointer to an [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) object.|
| size_t* pSize | Pointer to the size_t type, which is used as an output parameter to store the size of the rectangle array.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if either **rectArray** or **pSize** is NULL.|

### OH_Drawing_RectGetArrayElement()

```
OH_Drawing_ErrorCode OH_Drawing_RectGetArrayElement(OH_Drawing_Array* rectArray, size_t index,OH_Drawing_Rect** rect)
```

**Description**

Obtains the rectangle with the specified index in a rectangle array.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* rectArray | Pointer to an [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) object.|
| size_t index | Index of the rectangle array.|
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)** rect | Double pointer to [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md), which is returned to the caller as an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **rectArray** or **rect** is null or **index** is out of range.|

### OH_Drawing_RectDestroyArray()

```
OH_Drawing_ErrorCode OH_Drawing_RectDestroyArray(OH_Drawing_Array* rectArray)
```

**Description**

Destroys an **OH_Drawing_Array** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18


**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* rectArray | Pointer to an [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **rectArray** is NULL.|
