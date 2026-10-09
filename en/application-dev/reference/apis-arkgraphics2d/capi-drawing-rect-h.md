# drawing_rect.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=8ed03ffe90bb2522b0df0e44ac852e6dea1907ea translatedAt=2026-08-24T08:53:58.856Z pushedAt=2026-08-31T09:17:56.807Z -->

## Overview

Defines functions related to rectangles.<br>This module adopts a single-thread model policy, and the caller must manage thread safety and context state switching.

<!--RP1-->

**Sample**: [NDKAPIDrawing (API Version 20)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkGraphics2D/Drawing/NDKAPIDrawing)<!--RP1End-->

**File to include**: <native_drawing/drawing_rect.h>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect* OH_Drawing_RectCreate(float left, float top, float right, float bottom)](#oh_drawing_rectcreate) | Creates an **OH_Drawing_Rect** object, without sorting the coordinates passed in. This means that the coordinates of the upper left corner of the rectangle can be greater than those of the lower right corner.|
| [bool OH_Drawing_RectIntersect(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other)](#oh_drawing_rectintersect) | Checks whether two rectangles intersect and if yes, sets **rect** to the area of intersection.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **rect** or **other** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [bool OH_Drawing_RectJoin(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other)](#oh_drawing_rectjoin) | Sets rect to the union of two rectangles.<br>This API will generate an error code, which can be obtained via [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to view the error code value.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if any one of rect and other is NULL. |
| [void OH_Drawing_RectSetLeft(OH_Drawing_Rect* rect, float left)](#oh_drawing_rectsetleft) | Sets the horizontal coordinate of the upper left corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_RectSetTop(OH_Drawing_Rect* rect, float top)](#oh_drawing_rectsettop) | Sets the vertical coordinate of the upper left corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_RectSetRight(OH_Drawing_Rect* rect, float right)](#oh_drawing_rectsetright) | Sets the horizontal coordinate of the lower right corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_RectSetBottom(OH_Drawing_Rect* rect, float bottom)](#oh_drawing_rectsetbottom) | Sets the vertical coordinate of the lower right corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [float OH_Drawing_RectGetLeft(OH_Drawing_Rect* rect)](#oh_drawing_rectgetleft) | Obtains the X coordinate of the upper left corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [float OH_Drawing_RectGetTop(OH_Drawing_Rect* rect)](#oh_drawing_rectgettop) | Obtains the Y coordinate of the upper left corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [float OH_Drawing_RectGetRight(OH_Drawing_Rect* rect)](#oh_drawing_rectgetright) | Obtains the X coordinate of the lower right corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [float OH_Drawing_RectGetBottom(OH_Drawing_Rect* rect)](#oh_drawing_rectgetbottom) | Obtains the Y coordinate of the lower right corner of a rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [float OH_Drawing_RectGetHeight(OH_Drawing_Rect* rect)](#oh_drawing_rectgetheight) | Used to obtain the height of the rectangle object. The calculation method is the y-coordinate of the lower-right corner minus the y-coordinate of the upper-left corner as set.<br>This API will generate an error code, which can be obtained via [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to view the error code value.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if rect is NULL. |
| [float OH_Drawing_RectGetWidth(OH_Drawing_Rect* rect)](#oh_drawing_rectgetwidth) | Obtains the width of a rectangle. The width is calculated by using the X coordinate of the lower right corner of the rectangle minus the X coordinate of the upper left corner.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_RectCopy(OH_Drawing_Rect* src, OH_Drawing_Rect* dst)](#oh_drawing_rectcopy) | Copies a source rectangle to create a new one.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **src** or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_RectDestroy(OH_Drawing_Rect* rect)](#oh_drawing_rectdestroy) | Used to destroy the rectangle object and reclaim the memory occupied by it. |
| [OH_Drawing_Array* OH_Drawing_RectCreateArray(size_t size)](#oh_drawing_rectcreatearray) | Used to create a rectangle array object to store multiple rectangle objects. When the [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) is no longer needed, use [OH_Drawing_RectDestroyArray](capi-drawing-rect-h.md#oh_drawing_rectdestroyarray) to release the pointer to the object. |
| [OH_Drawing_ErrorCode OH_Drawing_RectGetArraySize(OH_Drawing_Array* rectArray, size_t* pSize)](#oh_drawing_rectgetarraysize) | Obtains the size of an [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) object.|
| [OH_Drawing_ErrorCode OH_Drawing_RectGetArrayElement(OH_Drawing_Array* rectArray, size_t index,OH_Drawing_Rect** rect)](#oh_drawing_rectgetarrayelement) | Obtains the rectangle with the specified index in a rectangle array.|
| [OH_Drawing_ErrorCode OH_Drawing_RectDestroyArray(OH_Drawing_Array* rectArray)](#oh_drawing_rectdestroyarray) | Used to destroy the rectangle array object and reclaim the memory occupied by it. |
| [OH_Drawing_ErrorCode OH_Drawing_RectContains(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other, bool* isContains)](#oh_drawing_rectcontains) | Used to determine whether a rectangle completely contains another rectangle. |
| [OH_Drawing_ErrorCode OH_Drawing_RectInset(OH_Drawing_Rect* rect, float left, float top, float right, float bottom)](#oh_drawing_rectinset) | Adds the specified values to the left, top, right, and bottom boundary coordinates of the rectangle respectively, adjusting the size and position of the rectangle. |
| [OH_Drawing_ErrorCode OH_Drawing_RectIsEmpty(const OH_Drawing_Rect* rect, bool* isEmpty)](#oh_drawing_rectisempty) | Used to determine whether the rectangle is empty, that is, whether the width or height of the rectangle is less than or equal to 0. |
| [OH_Drawing_ErrorCode OH_Drawing_RectOffset(OH_Drawing_Rect* rect, float dx, float dy)](#oh_drawing_rectoffset) | Offsets the rectangle along the x-axis and y-axis by the distances specified by the parameters dx and dy respectively. |
| [OH_Drawing_ErrorCode OH_Drawing_RectOffsetTo(OH_Drawing_Rect* rect, float newLeft, float newTop)](#oh_drawing_rectoffsetto) | Offsets the upper-left corner of the rectangle to the coordinates specified by the parameters newLeft and newTop, keeping the width and height unchanged. |
| [OH_Drawing_ErrorCode OH_Drawing_RectSetEmpty(OH_Drawing_Rect* rect)](#oh_drawing_rectsetempty) | Clears a rectangle (by setting the X and Y coordinates of the upper left corner and lower right corner to **0**).|
| [OH_Drawing_ErrorCode OH_Drawing_RectSort(OH_Drawing_Rect* rect)](#oh_drawing_rectsort) | Sorts the coordinates of the rectangle to ensure that the upper-left corner coordinates are not greater than the lower-right corner coordinates.<br><br>If the x-axis coordinate of the upper-left corner is greater than the x-axis coordinate of the lower-right corner, then swap the two; if the y-axis coordinate of the upper-left corner is greater than the y-axis coordinate of the lower-right corner, then swap the two. If the coordinates are already ordered, no operation is performed. |
| [OH_Drawing_ErrorCode OH_Drawing_RectUnion(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other)](#oh_drawing_rectunion) | Sets the current rectangle to the union of this rectangle and another rectangle.|

## Function Description

### OH_Drawing_RectCreate()

```c
OH_Drawing_Rect* OH_Drawing_RectCreate(float left, float top, float right, float bottom)
```

**Description**

Creates an **OH_Drawing_Rect** object, without sorting the coordinates passed in. This means that the coordinates of the upper left corner of the rectangle can be greater than those of the lower right corner.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| float left | x-coordinate of the upper-left corner of the rectangle, in physical pixels (px). |
| float top | y-coordinate of the upper-left corner of the rectangle, in physical pixels (px). |
| float right | x-coordinate of the lower-right corner of the rectangle, in physical pixels (px). |
| float bottom | y-coordinate of the lower-right corner of the rectangle, in physical pixels (px). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* | Pointer to the created rectangle object. |

### OH_Drawing_RectIntersect()

```c
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
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* other | Pointer to another rectangle object. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if they intersect (**rect** is set to the intersection area); returns **false** otherwise (**rect** remains unchanged).|

### OH_Drawing_RectJoin()

```c
bool OH_Drawing_RectJoin(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other)
```

**Description**

Sets rect to the union of two rectangles.<br>This API will generate an error code, which can be obtained via [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to view the error code value.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if any one of rect and other is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the rectangle object. After the union is obtained, this rectangle is set to the union of the two rectangles. |
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* other | Pointer to another rectangle object. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns the execution result of the operation. true indicates success, and false indicates failure. The failure may be caused by at least one of the two rectangles being NULL, or the width or height of the other rectangle being 0. |

### OH_Drawing_RectSetLeft()

```c
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
| float left | x-coordinate of the upper-left corner of the rectangle, in physical pixels (px). |

### OH_Drawing_RectSetTop()

```c
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
| float top | y-coordinate of the upper-left corner of the rectangle, in physical pixels (px). |

### OH_Drawing_RectSetRight()

```c
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
| float right | X-coordinate of the lower-right corner of the rectangle, in physical pixels (px). |

### OH_Drawing_RectSetBottom()

```c
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
| float bottom | y-coordinate of the lower-right corner of the rectangle, in physical pixels (px). |

### OH_Drawing_RectGetLeft()

```c
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
| float | Returns the x-coordinate of the upper-left corner of the rectangle, in physical pixels (px). |

### OH_Drawing_RectGetTop()

```c
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
| float | Returns the y-coordinate of the upper-left corner of the rectangle, in physical pixels (px). |

### OH_Drawing_RectGetRight()

```c
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
| float | x-coordinate of the lower-right corner of the rectangle, in physical pixels (px). |

### OH_Drawing_RectGetBottom()

```c
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
| float | return the y-coordinate of the lower-right corner of the rectangle, in physical pixels (px). |

### OH_Drawing_RectGetHeight()

```c
float OH_Drawing_RectGetHeight(OH_Drawing_Rect* rect)
```

**Description**

Used to obtain the height of the rectangle object. The calculation method is the y-coordinate of the lower-right corner of the rectangle as set minus the y-coordinate of the upper-left corner.<br>This API will generate an error code, which can be obtained via [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to view the error code value.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if rect is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Height of the rectangle object, in physical pixels (px). |

### OH_Drawing_RectGetWidth()

```c
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
| float | Returns the width of the rectangle object, in physical pixels (px). |

### OH_Drawing_RectCopy()

```c
void OH_Drawing_RectCopy(OH_Drawing_Rect* src, OH_Drawing_Rect* dst)
```

**Description**

Copies a source rectangle to create a new one.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **src** or **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* src | Pointer to a source rectangle, which is an **OH_Drawing_Rect** object.|
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* dst | Pointer to a destination rectangle, which is an **OH_Drawing_Rect** object.|

### OH_Drawing_RectDestroy()

```c
void OH_Drawing_RectDestroy(OH_Drawing_Rect* rect)
```

**Description**

Used to destroy the rectangle object and reclaim the memory occupied by it.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to an **OH_Drawing_Rect** object.|

### OH_Drawing_RectCreateArray()

```c
OH_Drawing_Array* OH_Drawing_RectCreateArray(size_t size)
```

**Description**

Used to create a rectangle array object to store multiple rectangle objects. When the [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) is no longer needed, use the [OH_Drawing_RectDestroyArray](capi-drawing-rect-h.md#oh_drawing_rectdestroyarray) API to release the pointer to the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| size_t size | Size of the rectangle array. The value ranges from 0 to 65536. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* | Pointer to the created OH_Drawing_Array object. If the returned object pointer is null, the creation fails.<br> The failure may be caused by insufficient memory or invalid parameters. |

### OH_Drawing_RectGetArraySize()

```c
OH_Drawing_ErrorCode OH_Drawing_RectGetArraySize(OH_Drawing_Array* rectArray, size_t* pSize)
```

**Description**

Obtains the size of an [OH_Drawing_Array](capi-drawing-oh-drawing-array.md) object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* rectArray | Pointer to the rectangle array object OH_Drawing_Array. |
| size_t* pSize | Pointer to the size_t type, which is used as an output parameter to store the size of the rectangle array.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if rectArray or pSize is NULL. |

### OH_Drawing_RectGetArrayElement()

```c
OH_Drawing_ErrorCode OH_Drawing_RectGetArrayElement(OH_Drawing_Array* rectArray, size_t index, OH_Drawing_Rect** rect)
```

**Description**

Obtains the rectangle with the specified index in a rectangle array.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* rectArray | Pointer to the rectangle array object OH_Drawing_Array. |
| size_t index | Index of the rectangle array.|
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)** rect | Double pointer to OH_Drawing_Rect, used as an output parameter to return the result to the caller. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **rectArray** or **rect** is null or **index** is out of range.|

### OH_Drawing_RectDestroyArray()

```c
OH_Drawing_ErrorCode OH_Drawing_RectDestroyArray(OH_Drawing_Array* rectArray)
```

**Description**

Used to destroy the rectangle array object and reclaim the memory occupied by it.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Array](capi-drawing-oh-drawing-array.md)* rectArray | Pointer to the rectangle array object OH_Drawing_Array. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **rectArray** is NULL.|

### OH_Drawing_RectContains()

```c
OH_Drawing_ErrorCode OH_Drawing_RectContains(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other, bool* isContains)
```

**Description**

Used to determine whether a rectangle completely contains another rectangle.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the rectangle object OH_Drawing_Rect. |
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* other | Pointer to the rectangle object OH_Drawing_Rect. |
| bool* isContains | Pointer to the parameter indicating whether a rectangle completely contains another rectangle, used as an output parameter. true indicates that rect completely contains other, and false indicates that rect does not completely contain other. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if the **rect**, **other**, or **isContains** parameter is empty.|

### OH_Drawing_RectInset()

```c
OH_Drawing_ErrorCode OH_Drawing_RectInset(OH_Drawing_Rect* rect, float left, float top, float right, float bottom)
```

**Description**

Adds the specified values to the left, top, right, and bottom boundary coordinates of the rectangle respectively to adjust the size and position of the rectangle.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the rectangle object OH_Drawing_Rect. |
| float left | Value added to the x-coordinate of the left boundary of the rectangle (the x-coordinate of the upper-left corner of the rectangle), in physical pixels (px). A positive value moves the left boundary rightward (the rectangle shrinks from the left side), a negative value moves the left boundary leftward (the rectangle expands toward the left side), and 0 means no change. |
| float top | Value added to the y-coordinate of the top boundary of the rectangle (the y-coordinate of the upper-left corner of the rectangle), in physical pixels (px). A positive value moves the top boundary downward (the rectangle shrinks from the top), a negative value moves the top boundary upward (the rectangle expands toward the top), and 0 means no change. |
| float right | Value added to the x-coordinate of the right boundary of the rectangle (the x-coordinate of the lower-right corner of the rectangle), in physical pixels (px). A positive value moves the right boundary rightward (the rectangle expands toward the right side), a negative value moves the right boundary leftward (the rectangle shrinks from the right side), and 0 means no change. |
| float bottom | Value added to the y-coordinate of the bottom boundary of the rectangle (the y-coordinate of the lower-right corner of the rectangle), in physical pixels (px). A positive value moves the bottom boundary downward (the rectangle expands toward the bottom), a negative value moves the bottom boundary upward (the rectangle shrinks from the bottom), and 0 means no change. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if the **rect** parameter is empty.|

### OH_Drawing_RectIsEmpty()

```c
OH_Drawing_ErrorCode OH_Drawing_RectIsEmpty(const OH_Drawing_Rect* rect, bool* isEmpty)
```

**Description**

Used to determine whether the rectangle is empty, that is, whether the width or height of the rectangle is less than or equal to 0.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the rectangle object OH_Drawing_Rect. |
| bool* isEmpty | Whether a rectangle is empty. It is used as an output parameter. **true** means yes; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **rect** or **isEmpty** is a null pointer.|

### OH_Drawing_RectOffset()

```c
OH_Drawing_ErrorCode OH_Drawing_RectOffset(OH_Drawing_Rect* rect, float dx, float dy)
```

**Description**

Offsets the rectangle along the x-axis and y-axis by the distances specified by the parameters dx and dy respectively.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the rectangle object OH_Drawing_Rect. |
| float dx | Offset distance along the x-axis. The unit is physical pixel px. A positive value indicates an offset along the positive direction of the x-axis, a negative value indicates an offset along the negative direction of the x-axis, and 0 indicates no offset. |
| float dy | Offset distance along the y-axis. The unit is physical pixel px. A positive value indicates an offset along the positive direction of the y-axis, a negative value indicates an offset along the negative direction of the y-axis, and 0 indicates no offset. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **rect** is a null pointer.|

### OH_Drawing_RectOffsetTo()

```c
OH_Drawing_ErrorCode OH_Drawing_RectOffsetTo(OH_Drawing_Rect* rect, float newLeft, float newTop)
```

**Description**

Offsets the upper-left corner of the rectangle to the coordinate position specified by the parameters newLeft and newTop, while keeping the width and height unchanged.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the rectangle object OH_Drawing_Rect. |
| float newLeft | x-coordinate of the upper-left corner of the rectangle after the offset, in physical pixels (px). |
| float newTop | y-coordinate of the upper-left corner of the rectangle after the offset, in physical pixels (px). |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **rect** is a null pointer.|

### OH_Drawing_RectSetEmpty()

```c
OH_Drawing_ErrorCode OH_Drawing_RectSetEmpty(OH_Drawing_Rect* rect)
```

**Description**

Clears a rectangle (by setting the X and Y coordinates of the upper left corner and lower right corner to **0**).

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the rectangle object OH_Drawing_Rect. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **rect** is a null pointer.|

### OH_Drawing_RectSort()

```c
OH_Drawing_ErrorCode OH_Drawing_RectSort(OH_Drawing_Rect* rect)
```

**Description**

Sorts the rectangle coordinates to ensure that the upper-left corner coordinates are not greater than the lower-right corner coordinates.

If the X coordinate of the upper left corner is greater than that of the lower right corner, the two coordinates are exchanged. If the Y coordinate of the upper left corner is greater than that of the lower right corner, the two coordinates are exchanged. If the coordinates are already in order, no operation is performed.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the rectangle object OH_Drawing_Rect. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **rect** is a null pointer.|

### OH_Drawing_RectUnion()

```c
OH_Drawing_ErrorCode OH_Drawing_RectUnion(OH_Drawing_Rect* rect, const OH_Drawing_Rect* other)
```

**Description**

Sets the current rectangle to the union of this rectangle and another rectangle.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the current rectangle object OH_Drawing_Rect. |
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* other | Pointer to another rectangle object OH_Drawing_Rect. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **rect** or **other** is a null pointer.|