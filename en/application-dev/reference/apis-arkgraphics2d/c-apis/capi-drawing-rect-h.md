# drawing_rect.h

## Overview

This file declares the functions related to the rectangle in the drawing module.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [OH_Drawing_Rect* OH_Drawing_RectCreate(float left, float top, float right, float bottom)](#oh_drawing_rectcreate) | Creates an **OH_Drawing_Rect** object, without sorting the coordinates passed in. This means that the coordinates of the upper left corner of the rectangle can be greater than those of the lower right corner. |
| [bool OH_Drawing_RectIntersect(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other)](#oh_drawing_rectintersect) | Checks whether two rectangles intersect and if yes, sets **rect** to the area of intersection. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **rect** or **other** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [bool OH_Drawing_RectJoin(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other)](#oh_drawing_rectjoin) | Obtains the union of two rectangles. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **rect** or **other** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_RectSetLeft(OH_Drawing_Rect* rect, float left)](#oh_drawing_rectsetleft) | Sets the horizontal coordinate of the upper left corner of a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_RectSetTop(OH_Drawing_Rect* rect, float top)](#oh_drawing_rectsettop) | Sets the vertical coordinate of the upper left corner of a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_RectSetRight(OH_Drawing_Rect* rect, float right)](#oh_drawing_rectsetright) | Sets the horizontal coordinate of the lower right corner of a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_RectSetBottom(OH_Drawing_Rect* rect, float bottom)](#oh_drawing_rectsetbottom) | Sets the vertical coordinate of the lower right corner of a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [float OH_Drawing_RectGetLeft(OH_Drawing_Rect* rect)](#oh_drawing_rectgetleft) | Obtains the X coordinate of the upper left corner of a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [float OH_Drawing_RectGetTop(OH_Drawing_Rect* rect)](#oh_drawing_rectgettop) | Obtains the Y coordinate of the upper left corner of a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [float OH_Drawing_RectGetRight(OH_Drawing_Rect* rect)](#oh_drawing_rectgetright) | Obtains the X coordinate of the lower right corner of a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [float OH_Drawing_RectGetBottom(OH_Drawing_Rect* rect)](#oh_drawing_rectgetbottom) | Obtains the Y coordinate of the lower right corner of a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [float OH_Drawing_RectGetHeight(OH_Drawing_Rect* rect)](#oh_drawing_rectgetheight) | Obtains the height of a rectangle. The height is calculated by using the Y coordinate of the lower right corner of the rectangle minus the Y coordinate of the upper left corner. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [float OH_Drawing_RectGetWidth(OH_Drawing_Rect* rect)](#oh_drawing_rectgetwidth) | Obtains the width of a rectangle. The width is calculated by using the X coordinate of the lower right corner of the rectangle minus the X coordinate of the upper left corner. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_RectCopy(OH_Drawing_Rect* src, OH_Drawing_Rect* dst)](#oh_drawing_rectcopy) | Copies a source rectangle to create a new one. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **src** or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_RectDestroy(OH_Drawing_Rect* rect)](#oh_drawing_rectdestroy) | Destroys an **OH_Drawing_Rect** object and reclaims the memory occupied by the object. |
| [OH_Drawing_Array* OH_Drawing_RectCreateArray(size_t size)](#oh_drawing_rectcreatearray) | Creates a rectangle array object to store multiple rectangle objects. Release this pointer by calling [OH_Drawing_RectDestroyArray](capi-drawing-rect-h.md#oh_drawing_rectdestroyarray) when this object is no longer needed. |
| [OH_Drawing_ErrorCode OH_Drawing_RectGetArraySize(OH_Drawing_Array* rectArray, size_t* pSize)](#oh_drawing_rectgetarraysize) | Obtains the size of an {@link OH_Drawing_Array} object. |
| [OH_Drawing_ErrorCode OH_Drawing_RectGetArrayElement(OH_Drawing_Array* rectArray, size_t index, OH_Drawing_Rect** rect)](#oh_drawing_rectgetarrayelement) | Obtains the rectangle with the specified index in a rectangle array. |
| [OH_Drawing_ErrorCode OH_Drawing_RectDestroyArray(OH_Drawing_Array* rectArray)](#oh_drawing_rectdestroyarray) | Destroys an **OH_Drawing_Array** object and reclaims the memory occupied by the object. |
| [OH_Drawing_ErrorCode OH_Drawing_RectContains(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other, bool* isContains)](#oh_drawing_rectcontains) | Checks whether a rectangle completely contains another rectangle. |
| [OH_Drawing_ErrorCode OH_Drawing_RectInset(OH_Drawing_Rect* rect, float left, float top, float right, float bottom)](#oh_drawing_rectinset) | Adds a specified value to the bounds of a rectangle. |
| [OH_Drawing_ErrorCode OH_Drawing_RectIsEmpty(const OH_Drawing_Rect* rect, bool* isEmpty)](#oh_drawing_rectisempty) | Checks whether a rectangle is empty. |
| [OH_Drawing_ErrorCode OH_Drawing_RectOffset(OH_Drawing_Rect* rect, float dx, float dy)](#oh_drawing_rectoffset) | Offsets a rectangle along the X axis and Y axis. |
| [OH_Drawing_ErrorCode OH_Drawing_RectOffsetTo(OH_Drawing_Rect* rect, float newLeft, float newTop)](#oh_drawing_rectoffsetto) | Offsets a rectangle to a specific position while keeping the width and height unchanged. |
| [OH_Drawing_ErrorCode OH_Drawing_RectSetEmpty(OH_Drawing_Rect* rect)](#oh_drawing_rectsetempty) | Clears a rectangle (by setting the X and Y coordinates of the upper left corner and lower right corner to **0*<br>*). |
| [OH_Drawing_ErrorCode OH_Drawing_RectSort(OH_Drawing_Rect* rect)](#oh_drawing_rectsort) | Sorts the coordinates of a rectangle based on the actual position. |
| [OH_Drawing_ErrorCode OH_Drawing_RectUnion(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other)](#oh_drawing_rectunion) | Sets the current rectangle to the union of this rectangle and another rectangle. |

## Function description

### OH_Drawing_RectCreate()

```c
OH_Drawing_Rect* OH_Drawing_RectCreate(float left, float top, float right, float bottom)
```

**Description**

Creates an **OH_Drawing_Rect** object, without sorting the coordinates passed in. This means that the coordinates of the upper left corner of the rectangle can be greater than those of the lower right corner.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| float left | X coordinate of the upper left corner of the rectangle. |
| float top | Y coordinate of the upper left corner of the rectangle. |
| float right | X coordinate of the lower right corner of the rectangle. |
| float bottom | Y coordinate of the lower right corner of the rectangle. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Rect* | Returns the pointer to the OH_Drawing_Rect object created. |

### OH_Drawing_RectIntersect()

```c
bool OH_Drawing_RectIntersect(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other)
```

**Description**

Checks whether two rectangles intersect and if yes, sets **rect** to the area of intersection. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **rect** or **other** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to an **OH_Drawing_Rect** object. |
| const OH_Drawing_Rect* other | Pointer to an **OH_Drawing_Rect** object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if they intersect (rect is set to the intersection area); returns false otherwise (  rect remains unchanged). |

### OH_Drawing_RectJoin()

```c
bool OH_Drawing_RectJoin(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other)
```

**Description**

Obtains the union of two rectangles. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **rect** or **other** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to an **OH_Drawing_Rect** object. |
| const OH_Drawing_Rect* other | Pointer to an **OH_Drawing_Rect** object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the union is obtained; returns false otherwise. The possible failure cause is that  at least one of the parameters rect and other is NULL or the size of the rectangle specified by other is  empty. |

### OH_Drawing_RectSetLeft()

```c
void OH_Drawing_RectSetLeft(OH_Drawing_Rect* rect, float left)
```

**Description**

Sets the horizontal coordinate of the upper left corner of a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to an **OH_Drawing_Rect** object. |
| float left | X coordinate of the upper left corner of the rectangle. |

### OH_Drawing_RectSetTop()

```c
void OH_Drawing_RectSetTop(OH_Drawing_Rect* rect, float top)
```

**Description**

Sets the vertical coordinate of the upper left corner of a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to an **OH_Drawing_Rect** object. |
| float top | Y coordinate of the upper left corner of the rectangle. |

### OH_Drawing_RectSetRight()

```c
void OH_Drawing_RectSetRight(OH_Drawing_Rect* rect, float right)
```

**Description**

Sets the horizontal coordinate of the lower right corner of a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to an **OH_Drawing_Rect** object. |
| float right | X coordinate of the lower right corner of the rectangle. |

### OH_Drawing_RectSetBottom()

```c
void OH_Drawing_RectSetBottom(OH_Drawing_Rect* rect, float bottom)
```

**Description**

Sets the vertical coordinate of the lower right corner of a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to an **OH_Drawing_Rect** object. |
| float bottom | Y coordinate of the lower right corner of the rectangle. |

### OH_Drawing_RectGetLeft()

```c
float OH_Drawing_RectGetLeft(OH_Drawing_Rect* rect)
```

**Description**

Obtains the X coordinate of the upper left corner of a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to an **OH_Drawing_Rect** object. |

**Returns**:

| Type | Description |
| -- | -- |
| float | X coordinate of the upper left corner of the rectangle. |

### OH_Drawing_RectGetTop()

```c
float OH_Drawing_RectGetTop(OH_Drawing_Rect* rect)
```

**Description**

Obtains the Y coordinate of the upper left corner of a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to an **OH_Drawing_Rect** object. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Y coordinate of the upper left corner of the rectangle. |

### OH_Drawing_RectGetRight()

```c
float OH_Drawing_RectGetRight(OH_Drawing_Rect* rect)
```

**Description**

Obtains the X coordinate of the lower right corner of a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to an **OH_Drawing_Rect** object. |

**Returns**:

| Type | Description |
| -- | -- |
| float | X coordinate of the lower right corner of the rectangle. |

### OH_Drawing_RectGetBottom()

```c
float OH_Drawing_RectGetBottom(OH_Drawing_Rect* rect)
```

**Description**

Obtains the Y coordinate of the lower right corner of a rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to an **OH_Drawing_Rect** object. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Y coordinate of the lower right corner of the rectangle. |

### OH_Drawing_RectGetHeight()

```c
float OH_Drawing_RectGetHeight(OH_Drawing_Rect* rect)
```

**Description**

Obtains the height of a rectangle. The height is calculated by using the Y coordinate of the lower right corner of the rectangle minus the Y coordinate of the upper left corner. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to an **OH_Drawing_Rect** object. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the height of the rectangle, in pixels. |

### OH_Drawing_RectGetWidth()

```c
float OH_Drawing_RectGetWidth(OH_Drawing_Rect* rect)
```

**Description**

Obtains the width of a rectangle. The width is calculated by using the X coordinate of the lower right corner of the rectangle minus the X coordinate of the upper left corner. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to an **OH_Drawing_Rect** object. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the weight of the rectangle, in pixels. |

### OH_Drawing_RectCopy()

```c
void OH_Drawing_RectCopy(OH_Drawing_Rect* src, OH_Drawing_Rect* dst)
```

**Description**

Copies a source rectangle to create a new one. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **src** or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* src | Pointer to a source rectangle, which is an **OH_Drawing_Rect** object. |
| OH_Drawing_Rect* dst | Pointer to a destination rectangle, which is an **OH_Drawing_Rect** object. |

### OH_Drawing_RectDestroy()

```c
void OH_Drawing_RectDestroy(OH_Drawing_Rect* rect)
```

**Description**

Destroys an **OH_Drawing_Rect** object and reclaims the memory occupied by the object.

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to an **OH_Drawing_Rect** object. |

### OH_Drawing_RectCreateArray()

```c
OH_Drawing_Array* OH_Drawing_RectCreateArray(size_t size)
```

**Description**

Creates a rectangle array object to store multiple rectangle objects. Release this pointer by calling [OH_Drawing_RectDestroyArray](capi-drawing-rect-h.md#oh_drawing_rectdestroyarray) when this object is no longer needed.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| size_t size | Size of the rectangle array. The value cannot exceed 65536, which is the maximum number of glyph indices. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Array* | Returns the pointer to the {@link OH_Drawing_Array} object created. If the returned object pointer is null,  the creation fails.  Possible causes are that no memory is available or an input parameter is incorrect. |

### OH_Drawing_RectGetArraySize()

```c
OH_Drawing_ErrorCode OH_Drawing_RectGetArraySize(OH_Drawing_Array* rectArray, size_t* pSize)
```

**Description**

Obtains the size of an {@link OH_Drawing_Array} object.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Array* rectArray | Pointer to an {@link OH_Drawing_Array} object. |
| size_t* pSize | Pointer to the size_t type, which is used as an output parameter to store the size of the rectangle array. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if either rectArray or pSize is NULL. |

### OH_Drawing_RectGetArrayElement()

```c
OH_Drawing_ErrorCode OH_Drawing_RectGetArrayElement(OH_Drawing_Array* rectArray, size_t index, OH_Drawing_Rect** rect)
```

**Description**

Obtains the rectangle with the specified index in a rectangle array.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Array* rectArray | Pointer to an {@link OH_Drawing_Array} object. |
| size_t index | Index of the rectangle array. |
| OH_Drawing_Rect** rect | Double pointer to {@link OH_Drawing_Rect}, which is returned to the caller as an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if rectArray or rect is null or index is out of range. |

### OH_Drawing_RectDestroyArray()

```c
OH_Drawing_ErrorCode OH_Drawing_RectDestroyArray(OH_Drawing_Array* rectArray)
```

**Description**

Destroys an **OH_Drawing_Array** object and reclaims the memory occupied by the object.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Array* rectArray | Pointer to an {@link OH_Drawing_Array} object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if rectArray is NULL. |

### OH_Drawing_RectContains()

```c
OH_Drawing_ErrorCode OH_Drawing_RectContains(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other, bool* isContains)
```

**Description**

Checks whether a rectangle completely contains another rectangle.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to the {@link OH_Drawing_Rect} object. This rectangle is used to check whether another rectangle (**other**) is contained. |
| const OH_Drawing_Rect* other | Pointer to the {@link OH_Drawing_Rect} object. This rectangle is used to check whether it is contained by another rectangle (**rect**). |
| bool* isContains | Result of whether a rectangle completely contains another rectangle. It is used as an output parameter. **true** indicates that **rect** completely contains **other**. **false** indicates that **rect** does not completely contain **other**. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INCORRECT_PARAMETER if the rect, other, or isContains parameter is empty. |

### OH_Drawing_RectInset()

```c
OH_Drawing_ErrorCode OH_Drawing_RectInset(OH_Drawing_Rect* rect, float left, float top, float right, float bottom)
```

**Description**

Adds a specified value to the bounds of a rectangle.

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to the {@link OH_Drawing_Rect} object. |
| float left | Value to be added to the left bound of the rectangle (X coordinate of the upper left corner of the rectangle). |
| float top | Value to be added to the top bound of the rectangle (Y coordinate of the upper left corner of the rectangle). |
| float right | Value to be added to the right bound of the rectangle (X coordinate of the lower right corner of the rectangle). |
| float bottom | Value to be added to the bottom bound of the rectangle (Y coordinate of the lower right corner of the rectangle). |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INCORRECT_PARAMETER if the rect parameter is empty. |

### OH_Drawing_RectIsEmpty()

```c
OH_Drawing_ErrorCode OH_Drawing_RectIsEmpty(const OH_Drawing_Rect* rect, bool* isEmpty)
```

**Description**

Checks whether a rectangle is empty.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Rect* rect | Pointer to the {@link OH_Drawing_Rect} object. |
| bool* isEmpty | Whether a rectangle is empty. It is used as an output parameter. **true** means yes; **false**<br>otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INCORRECT_PARAMETER if rect or isEmpty is a null pointer. |

### OH_Drawing_RectOffset()

```c
OH_Drawing_ErrorCode OH_Drawing_RectOffset(OH_Drawing_Rect* rect, float dx, float dy)
```

**Description**

Offsets a rectangle along the X axis and Y axis.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to the {@link OH_Drawing_Rect} object. |
| float dx | Offset on the X axis. A positive number indicates an offset towards the positive direction of the X axis, and a negative number indicates an offset towards the negative direction of the X axis. |
| float dy | Offset on the Y axis. A positive number indicates an offset towards the positive direction of the Y axis, and a negative number indicates an offset towards the negative direction of the Y axis. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INCORRECT_PARAMETER if rect is a null pointer. |

### OH_Drawing_RectOffsetTo()

```c
OH_Drawing_ErrorCode OH_Drawing_RectOffsetTo(OH_Drawing_Rect* rect, float newLeft, float newTop)
```

**Description**

Offsets a rectangle to a specific position while keeping the width and height unchanged.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to the {@link OH_Drawing_Rect} object. |
| float newLeft | X coordinate of the upper left corner of the rectangle after the offset. |
| float newTop | Y coordinate of the upper left corner of the rectangle after the offset. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INCORRECT_PARAMETER if rect is a null pointer. |

### OH_Drawing_RectSetEmpty()

```c
OH_Drawing_ErrorCode OH_Drawing_RectSetEmpty(OH_Drawing_Rect* rect)
```

**Description**

Clears a rectangle (by setting the X and Y coordinates of the upper left corner and lower right corner to **0*<br>*).

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to the {@link OH_Drawing_Rect} object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INCORRECT_PARAMETER if rect is a null pointer. |

### OH_Drawing_RectSort()

```c
OH_Drawing_ErrorCode OH_Drawing_RectSort(OH_Drawing_Rect* rect)
```

**Description**

Sorts the coordinates of a rectangle based on the actual position.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to the {@link OH_Drawing_Rect} object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INCORRECT_PARAMETER if rect is a null pointer. |

### OH_Drawing_RectUnion()

```c
OH_Drawing_ErrorCode OH_Drawing_RectUnion(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other)
```

**Description**

Sets the current rectangle to the union of this rectangle and another rectangle.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Rect* rect | Pointer to this {@link OH_Drawing_Rect} object. |
| const OH_Drawing_Rect* other | Pointer to another {@link OH_Drawing_Rect} object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INCORRECT_PARAMETER if rect or other is a null pointer. |


