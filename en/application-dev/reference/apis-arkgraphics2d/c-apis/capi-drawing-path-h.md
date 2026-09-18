# drawing_path.h

## Overview

This file declares the functions related to the path in the drawing module.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Drawing_PathDirection](#oh_drawing_pathdirection) | OH_Drawing_PathDirection | Enumerates the directions of a closed contour. |
| [OH_Drawing_PathFillType](#oh_drawing_pathfilltype) | OH_Drawing_PathFillType | Enumerates the fill types of a path. |
| [OH_Drawing_PathAddMode](#oh_drawing_pathaddmode) | OH_Drawing_PathAddMode | Enumerates the path adding modes. |
| [OH_Drawing_PathOpMode](#oh_drawing_pathopmode) | OH_Drawing_PathOpMode | Enumerates the operation modes available for a path. |
| [OH_Drawing_PathMeasureMatrixFlags](#oh_drawing_pathmeasurematrixflags) | OH_Drawing_PathMeasureMatrixFlags | Enumerates the types of matrix information obtained during path measurement. |

### Function

| Name | Description |
| -- | -- |
| [OH_Drawing_Path* OH_Drawing_PathCreate(void)](#oh_drawing_pathcreate) | Creates an **OH_Drawing_Path** object. |
| [OH_Drawing_Path* OH_Drawing_PathCopy(OH_Drawing_Path* path)](#oh_drawing_pathcopy) | Creates a copy of the {@link OH_Drawing_Path} object.<br>This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathDestroy(OH_Drawing_Path* path)](#oh_drawing_pathdestroy) | Destroys an **OH_Drawing_Path** object and reclaims the memory occupied by the object. |
| [OH_Drawing_ErrorCode OH_Drawing_PathSetPath(OH_Drawing_Path* path, OH_Drawing_Path* other)](#oh_drawing_pathsetpath) | Sets a path object as the current path object. |
| [OH_Drawing_ErrorCode OH_Drawing_PathIsEmpty(OH_Drawing_Path* path, bool* isEmpty)](#oh_drawing_pathisempty) | Checks whether a path object is empty. |
| [OH_Drawing_ErrorCode OH_Drawing_PathIsRect(OH_Drawing_Path* path, OH_Drawing_Rect* rect, bool* isRect)](#oh_drawing_pathisrect) | Checks whether a path object forms a rectangle. |
| [void OH_Drawing_PathMoveTo(OH_Drawing_Path* path, float x, float y)](#oh_drawing_pathmoveto) | Sets the start point of this path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathLineTo(OH_Drawing_Path* path, float x, float y)](#oh_drawing_pathlineto) | Draws a line segment from the last point of this path to the target point. If the path is empty, the start point (0, 0) is used. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathArcTo(OH_Drawing_Path* path, float x1, float y1, float x2, float y2, float startDeg, float sweepDeg)](#oh_drawing_patharcto) | Draws an arc to a path. This is done by using angle arc mode. In this mode, a rectangle is specified first, and then a start angle and scanning degree are specified. The inscribed ellipse of the rectangle will be used to intercept the arc. The arc is a portion of the ellipse defined by the start angle and the sweep angle. If the path is empty, a line segment from the last point of the path to the start point of the arc is also added. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathQuadTo(OH_Drawing_Path* path, float ctrlX, float ctrlY, float endX, float endY)](#oh_drawing_pathquadto) | Draws a quadratic Bezier curve from the last point of a path to the target point. If the path is empty, the start point (0, 0) is used. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathConicTo(OH_Drawing_Path* path, float ctrlX, float ctrlY, float endX, float endY, float weight)](#oh_drawing_pathconicto) | Draws a conic curve from the last point of a path to the target point. If the path is empty, the start point ( 0, 0) is used. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathCubicTo(OH_Drawing_Path* path, float ctrlX1, float ctrlY1, float ctrlX2, float ctrlY2, float endX, float endY)](#oh_drawing_pathcubicto) | Draws a cubic Bezier curve from the last point of this path to the target point. If the path is empty, the start point (0, 0) is used. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathRMoveTo(OH_Drawing_Path* path, float x, float y)](#oh_drawing_pathrmoveto) | Sets the start position relative to the last point of a path. If the path is empty, the start point (0, 0) is used. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathRLineTo(OH_Drawing_Path* path, float x, float y)](#oh_drawing_pathrlineto) | Draws a line segment from the last point of this path to a point relative to the last point. If the path is empty, the start point (0, 0) is used. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathRQuadTo(OH_Drawing_Path* path, float ctrlX, float ctrlY, float endX, float endY)](#oh_drawing_pathrquadto) | Draws a quadratic Bezier curve from the last point of this path to a point relative to the last point. If the path is empty, the start point (0, 0) is used. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathRConicTo(OH_Drawing_Path* path, float ctrlX, float ctrlY, float endX, float endY, float weight)](#oh_drawing_pathrconicto) | Draws a conic curve from the last point of a path to a point relative to the last point. If the path is empty, the start point (0, 0) is used. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathRCubicTo(OH_Drawing_Path* path, float ctrlX1, float ctrlY1, float ctrlX2, float ctrlY2, float endX, float endY)](#oh_drawing_pathrcubicto) | Draws a cubic Bezier curve from the last point of a path to a point relative to the last point. If the path is empty, the start point (0, 0) is used. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathAddRect(OH_Drawing_Path* path, float left, float top, float right, float bottom, OH_Drawing_PathDirection pathDirection)](#oh_drawing_pathaddrect) | Adds a rectangle to a path in the specified direction. The start point is the upper left corner of the rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **pathDirection** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [void OH_Drawing_PathAddRectWithInitialCorner(OH_Drawing_Path* path, const OH_Drawing_Rect* rect, OH_Drawing_PathDirection pathDirection, uint32_t start)](#oh_drawing_pathaddrectwithinitialcorner) | Adds a rectangle contour to a path in the specified direction. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **pathDirection** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [void OH_Drawing_PathAddRoundRect(OH_Drawing_Path* path, const OH_Drawing_RoundRect* roundRect, OH_Drawing_PathDirection pathDirection)](#oh_drawing_pathaddroundrect) | Adds a rounded rectangle to a path in the specified direction. When the path direction is clockwise, the start point is at the intersection of the rounded rectangle's left boundary and its lower left corner. When the path direction is counterclockwise, the start point is at the intersection point between the left boundary and the upper left corner. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **roundRect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **pathDirection** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [void OH_Drawing_PathAddOvalWithInitialPoint(OH_Drawing_Path* path, const OH_Drawing_Rect* rect, uint32_t start, OH_Drawing_PathDirection pathDirection)](#oh_drawing_pathaddovalwithinitialpoint) | Adds an oval to a path. **OH_Drawing_Rect** specifies the outer tangent rectangle of the oval, and **<br>OH_Drawing_PathDirection** specifies whether the drawing is clockwise or counterclockwise. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **pathDirection** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [void OH_Drawing_PathAddOval(OH_Drawing_Path* path, const OH_Drawing_Rect* rect, OH_Drawing_PathDirection pathDirection)](#oh_drawing_pathaddoval) | Adds an oval to a path in the specified direction. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **pathDirection** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [void OH_Drawing_PathAddArc(OH_Drawing_Path* path, const OH_Drawing_Rect* rect, float startAngle, float sweepAngle)](#oh_drawing_pathaddarc) | Adds an arc to a path as the start of a new contour. The arc added is part of the inscribed ellipse of the rectangle, from the start angle through the sweep angle. If the sweep angle is less than or equal to -360°, or if the sweep angle is greater than or equal to 360°, and start angle modulo 90 is nearly zero, an oval instead of an ellipse is added. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathAddPath(OH_Drawing_Path* path, const OH_Drawing_Path* src, const OH_Drawing_Matrix* matrix)](#oh_drawing_pathaddpath) | Transforms the points in a **src** path by a matrix and adds the new one to the current path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **src** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathAddPathWithMatrixAndMode(OH_Drawing_Path* path, const OH_Drawing_Path* src, const OH_Drawing_Matrix* matrix, OH_Drawing_PathAddMode pathAddMode)](#oh_drawing_pathaddpathwithmatrixandmode) | Transforms the points in a **src** path by a matrix and adds the new one to the current path with the specified adding mode. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **src** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **pathAddMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [void OH_Drawing_PathAddPathWithMode(OH_Drawing_Path* path, const OH_Drawing_Path* src, OH_Drawing_PathAddMode pathAddMode)](#oh_drawing_pathaddpathwithmode) | Adds a **src** path to the current path with the specified adding mode. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **src** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **pathAddMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [void OH_Drawing_PathAddPathWithOffsetAndMode(OH_Drawing_Path* path, const OH_Drawing_Path* src, float dx, float dy, OH_Drawing_PathAddMode pathAddMode)](#oh_drawing_pathaddpathwithoffsetandmode) | Translates a **src** path by an offset and adds the new one to the current path with the specified adding mode. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **src** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **pathAddMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [void OH_Drawing_PathAddPolygon(OH_Drawing_Path* path, const OH_Drawing_Point2D* points, uint32_t count, bool isClosed)](#oh_drawing_pathaddpolygon) | Adds a polygon to a path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **points** is NULL or **count** is **0**, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathAddCircle(OH_Drawing_Path* path, float x, float y, float radius, OH_Drawing_PathDirection pathDirection)](#oh_drawing_pathaddcircle) | Adds a circle to a path in the specified direction. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **radius** is less than or equal to 0, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. If **pathDirection** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [bool OH_Drawing_PathBuildFromSvgString(OH_Drawing_Path* path, const char* str)](#oh_drawing_pathbuildfromsvgstring) | Parses the path represented by an SVG string. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **str** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_PathConvertToSvgString(const OH_Drawing_Path* path, char* str, size_t* strSize)](#oh_drawing_pathconverttosvgstring) | Convert path to an SVG string. |
| [OH_Drawing_ErrorCode OH_Drawing_PathGetPointData(const OH_Drawing_Path* path, OH_Drawing_Point2D* points, uint32_t* count)](#oh_drawing_pathgetpointdata) | Get path point data. |
| [OH_Drawing_ErrorCode OH_Drawing_PathGetVerbData(const OH_Drawing_Path* path, OH_Drawing_PathIteratorVerb* verbs, uint32_t* count)](#oh_drawing_pathgetverbdata) | Get path verb data. |
| [OH_Drawing_ErrorCode OH_Drawing_PathGetConicWeightData(const OH_Drawing_Path* path, float* conicWeights, uint32_t* count)](#oh_drawing_pathgetconicweightdata) | Get path conic weight data. |
| [bool OH_Drawing_PathContains(OH_Drawing_Path* path, float x, float y)](#oh_drawing_pathcontains) | Checks whether a coordinate point is included in this path. For details, see [OH_Drawing_PathFillType](capi-drawing-path-h.md#oh_drawing_pathfilltype). This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathTransform(OH_Drawing_Path* path, const OH_Drawing_Matrix* matrix)](#oh_drawing_pathtransform) | Transforms the points in a path by matrix. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathTransformWithPerspectiveClip(OH_Drawing_Path* src, const OH_Drawing_Matrix* matrix, OH_Drawing_Path* dst, bool applyPerspectiveClip)](#oh_drawing_pathtransformwithperspectiveclip) | Transforms the points in a path by matrix, and uses the new one to replace the **dst** path. If **dst** is NULL, the **src** path is replaced. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **src** or **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathSetFillType(OH_Drawing_Path* path, OH_Drawing_PathFillType pathFillType)](#oh_drawing_pathsetfilltype) | Sets the fill type of a path. The fill type determines how "inside" of the path is drawn. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **pathFillType** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_PathGetFillType(OH_Drawing_Path* path, OH_Drawing_PathFillType* pathFillType)](#oh_drawing_pathgetfilltype) | Obtains the fill type of a path. |
| [float OH_Drawing_PathGetLength(OH_Drawing_Path* path, bool forceClosed)](#oh_drawing_pathgetlength) | Obtains the length of a path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathGetBounds(OH_Drawing_Path* path, OH_Drawing_Rect* rect)](#oh_drawing_pathgetbounds) | Obtains the minimum bounds that enclose a path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathClose(OH_Drawing_Path* path)](#oh_drawing_pathclose) | Draws a line segment from the current point to the start point of this path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathOffset(OH_Drawing_Path* path, OH_Drawing_Path* dst, float dx, float dy)](#oh_drawing_pathoffset) | Translates a path by an offset along the X axis and Y axis and adds the new one to the **dst** path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_PathReset(OH_Drawing_Path* path)](#oh_drawing_pathreset) | Resets the path data. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [bool OH_Drawing_PathIsClosed(OH_Drawing_Path* path, bool forceClosed)](#oh_drawing_pathisclosed) | Checks whether a path is closed. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [bool OH_Drawing_PathGetPositionTangent(OH_Drawing_Path* path, bool forceClosed, float distance, OH_Drawing_Point2D* position, OH_Drawing_Point2D* tangent)](#oh_drawing_pathgetpositiontangent) | Obtains the coordinates and tangent at a distance from the start point of this path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If any of **path**, **position**, or **tangent** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_PathGetSegment(OH_Drawing_Path* path, bool forceClosed, float start, float stop, bool startWithMoveTo, OH_Drawing_Path* dst, bool* result)](#oh_drawing_pathgetsegment) | Extracts a segment of a path and appends it to a destination path. |
| [bool OH_Drawing_PathOp(OH_Drawing_Path* path, const OH_Drawing_Path* other, OH_Drawing_PathOpMode op)](#oh_drawing_pathop) | Combines two paths based on the specified operation mode. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **srcPath** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **op** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [bool OH_Drawing_PathGetMatrix(OH_Drawing_Path* path, bool forceClosed, float distance, OH_Drawing_Matrix* matrix, OH_Drawing_PathMeasureMatrixFlags flag)](#oh_drawing_pathgetmatrix) | Obtains a transformation matrix at a distance from the start point of this path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **flag** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_PathApproximate(OH_Drawing_Path* path, float acceptableError, float* vals, uint32_t* count)](#oh_drawing_pathapproximate) | Converts the existing path into an approximate path consisting of consecutive line segments. |
| [OH_Drawing_ErrorCode OH_Drawing_PathInterpolate(OH_Drawing_Path* path, OH_Drawing_Path* other, float weight, bool* success, OH_Drawing_Path* interpolatedPath)](#oh_drawing_pathinterpolate) | Interpolates between the existing path and another path based on the given weight and stores the result in the target path object. Interpolation is achievable if the two paths have the same number of points. The target path is created based on the structure of the existing path. |
| [OH_Drawing_ErrorCode OH_Drawing_PathIsInterpolate(OH_Drawing_Path* path, OH_Drawing_Path* other, bool* result)](#oh_drawing_pathisinterpolate) | Checks whether the existing path and another path (**other**) are compatible for interpolation in terms of structure and operation sequence. If the paths contain conic operations, the weight values of the operations must be the same. |
| [OH_Drawing_ErrorCode OH_Drawing_PathGetLastPoint(OH_Drawing_Path* path, OH_Drawing_Point2D* point)](#oh_drawing_pathgetlastpoint) | Gets the last point of the path. |
| [OH_Drawing_ErrorCode OH_Drawing_PathIsInverseFillType(const OH_Drawing_Path* path, bool* isInverse)](#oh_drawing_pathisinversefilltype) | Checks whether the fill type of the path is the inverse type. |
| [OH_Drawing_ErrorCode OH_Drawing_PathToggleInverseFillType(OH_Drawing_Path* path)](#oh_drawing_pathtoggleinversefilltype) | Toggles the fill type of the path to the inverse type. |
| [OH_Drawing_ErrorCode OH_Drawing_PathIsEqual(OH_Drawing_Path* path, OH_Drawing_Path* other, bool* equal)](#oh_drawing_pathisequal) | Checks if two paths are equal. |

## Enum type description

### OH_Drawing_PathDirection

```c
enum OH_Drawing_PathDirection
```

**Description**

Enumerates the directions of a closed contour.

**Since**: 12

| Enum item | Description |
| -- | -- |
| PATH_DIRECTION_CW | Adds a closed contour clockwise. |
| PATH_DIRECTION_CCW | Adds a closed contour counterclockwise. |

### OH_Drawing_PathFillType

```c
enum OH_Drawing_PathFillType
```

**Description**

Enumerates the fill types of a path.

**Since**: 12

| Enum item | Description |
| -- | -- |
| PATH_FILL_TYPE_WINDING | For any point within the drawing area, a ray is cast in an arbitrary direction. The count starts at 0 for all intersections between this ray and the path.<br>Each clockwise intersection—where the path crosses the ray from left to right—results in the count being incremented by 1, while each counterclockwise intersection—where the path crosses the ray from right to left—causes the count to be decremented by 1. A point is deemed inside the path and needs to be colored if the final count is non-zero; if the count is 0, the point remains uncolored. |
| PATH_FILL_TYPE_EVEN_ODD | For any point in the drawing area, a ray is cast in an arbitrary direction. If the number of intersections between this ray and the path is odd, the point is deemed inside the path and needs to be colored; if the number is even, it remains uncolored. |
| PATH_FILL_TYPE_INVERSE_WINDING | Same as **PATH_FILL_TYPE_WINDING**, but draws outside of the path, rather than inside. |
| PATH_FILL_TYPE_INVERSE_EVEN_ODD | Same as **PATH_FILL_TYPE_EVEN_ODD**, but draws outside of the path, rather than inside. |

### OH_Drawing_PathAddMode

```c
enum OH_Drawing_PathAddMode
```

**Description**

Enumerates the path adding modes.

**Since**: 12

| Enum item | Description |
| -- | -- |
| PATH_ADD_MODE_APPEND | Adds a path in append mode. |
| PATH_ADD_MODE_EXTEND | Adds a line segment to close the path if the previous path is not closed. |

### OH_Drawing_PathOpMode

```c
enum OH_Drawing_PathOpMode
```

**Description**

Enumerates the operation modes available for a path.

**Since**: 12

| Enum item | Description |
| -- | -- |
| PATH_OP_MODE_DIFFERENCE | Difference operation. |
| PATH_OP_MODE_INTERSECT | Intersection operation. |
| PATH_OP_MODE_UNION | Union operation. |
| PATH_OP_MODE_XOR | XOR operation. |
| PATH_OP_MODE_REVERSE_DIFFERENCE | Reverse difference operation. |

### OH_Drawing_PathMeasureMatrixFlags

```c
enum OH_Drawing_PathMeasureMatrixFlags
```

**Description**

Enumerates the types of matrix information obtained during path measurement.

**Since**: 12

| Enum item | Description |
| -- | -- |
| GET_POSITION_MATRIX | Matrix corresponding to the position information. |
| GET_TANGENT_MATRIX | Matrix corresponding to the tangent information. |
| GET_POSITION_AND_TANGENT_MATRIX | Matrix corresponding to the position and tangent information. |


## Function description

### OH_Drawing_PathCreate()

```c
OH_Drawing_Path* OH_Drawing_PathCreate(void)
```

**Description**

Creates an **OH_Drawing_Path** object.

**Since**: 8

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Path* | Returns the pointer to the OH_Drawing_Path object created. |

### OH_Drawing_PathCopy()

```c
OH_Drawing_Path* OH_Drawing_PathCopy(OH_Drawing_Path* path)
```

**Description**

Creates a copy of the {@link OH_Drawing_Path} object.<br>This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Path* | Pointer to the copy of the {@link OH_Drawing_Path} object. |

### OH_Drawing_PathDestroy()

```c
void OH_Drawing_PathDestroy(OH_Drawing_Path* path)
```

**Description**

Destroys an **OH_Drawing_Path** object and reclaims the memory occupied by the object.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to an **OH_Drawing_Path** object. |

### OH_Drawing_PathSetPath()

```c
OH_Drawing_ErrorCode OH_Drawing_PathSetPath(OH_Drawing_Path* path, OH_Drawing_Path* other)
```

**Description**

Sets a path object as the current path object.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| OH_Drawing_Path* other | Pointer to the {@link OH_Drawing_Path} object to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if path or other is NULL. |

### OH_Drawing_PathIsEmpty()

```c
OH_Drawing_ErrorCode OH_Drawing_PathIsEmpty(OH_Drawing_Path* path, bool* isEmpty)
```

**Description**

Checks whether a path object is empty.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| bool* isEmpty | Whether the path object is empty. **true** means empty; **false** otherwise. It as an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if path or isEmpty is NULL. |

### OH_Drawing_PathIsRect()

```c
OH_Drawing_ErrorCode OH_Drawing_PathIsRect(OH_Drawing_Path* path, OH_Drawing_Rect* rect, bool* isRect)
```

**Description**

Checks whether a path object forms a rectangle.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| OH_Drawing_Rect* rect | Pointer to the {@link OH_Drawing_Rect} object, which is used as an output parameter and can be null. |
| bool* isRect | Whether a path forms a rectangle. **true** means yes; **false** otherwise. It as an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if path or isRect is NULL. |

### OH_Drawing_PathMoveTo()

```c
void OH_Drawing_PathMoveTo(OH_Drawing_Path* path, float x, float y)
```

**Description**

Sets the start point of this path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to an **OH_Drawing_Path** object. |
| float x | X coordinate of the start point. |
| float y | Y coordinate of the start point. |

### OH_Drawing_PathLineTo()

```c
void OH_Drawing_PathLineTo(OH_Drawing_Path* path, float x, float y)
```

**Description**

Draws a line segment from the last point of this path to the target point. If the path is empty, the start point (0, 0) is used. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to an **OH_Drawing_Path** object. |
| float x | X coordinate of the target point. |
| float y | Y coordinate of the target point. |

### OH_Drawing_PathArcTo()

```c
void OH_Drawing_PathArcTo(OH_Drawing_Path* path, float x1, float y1, float x2, float y2, float startDeg, float sweepDeg)
```

**Description**

Draws an arc to a path. This is done by using angle arc mode. In this mode, a rectangle is specified first, and then a start angle and scanning degree are specified. The inscribed ellipse of the rectangle will be used to intercept the arc. The arc is a portion of the ellipse defined by the start angle and the sweep angle. If the path is empty, a line segment from the last point of the path to the start point of the arc is also added. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to an **OH_Drawing_Path** object. |
| float x1 | X coordinate of the upper left corner of the rectangle. |
| float y1 | Y coordinate of the upper left corner of the rectangle. |
| float x2 | X coordinate of the lower right corner of the rectangle. |
| float y2 | Y coordinate of the lower right corner of the rectangle. |
| float startDeg | Start angle. The start direction (0°) of the angle is the positive direction of the X axis. |
| float sweepDeg | Angle to sweep, in degrees. A positive number indicates a clockwise sweep, and a negative value indicates a counterclockwise swipe. The actual swipe degree is the modulo operation result of the input parameter by 360. |

### OH_Drawing_PathQuadTo()

```c
void OH_Drawing_PathQuadTo(OH_Drawing_Path* path, float ctrlX, float ctrlY, float endX, float endY)
```

**Description**

Draws a quadratic Bezier curve from the last point of a path to the target point. If the path is empty, the start point (0, 0) is used. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to an **OH_Drawing_Path** object. |
| float ctrlX | X coordinate of the control point. |
| float ctrlY | Y coordinate of the control point. |
| float endX | X coordinate of the target point. |
| float endY | Y coordinate of the target point. |

### OH_Drawing_PathConicTo()

```c
void OH_Drawing_PathConicTo(OH_Drawing_Path* path, float ctrlX, float ctrlY, float endX, float endY, float weight)
```

**Description**

Draws a conic curve from the last point of a path to the target point. If the path is empty, the start point ( 0, 0) is used. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| float ctrlX | X coordinate of the control point. |
| float ctrlY | Y coordinate of the control point. |
| float endX | X coordinate of the target point. |
| float endY | Y coordinate of the target point. |
| float weight | Weight of the curve, which determines its shape. The larger the value, the closer of the curve to the control point. If the value is less than or equal to **0**, the result is equivalent to a line segment from the start point to the end point, which is added by calling [OH_Drawing_PathLineTo](capi-drawing-path-h.md#oh_drawing_pathlineto). If the value is **1**, the result is equivalent to [OH_Drawing_PathQuadTo](capi-drawing-path-h.md#oh_drawing_pathquadto). |

### OH_Drawing_PathCubicTo()

```c
void OH_Drawing_PathCubicTo(OH_Drawing_Path* path, float ctrlX1, float ctrlY1, float ctrlX2, float ctrlY2, float endX, float endY)
```

**Description**

Draws a cubic Bezier curve from the last point of this path to the target point. If the path is empty, the start point (0, 0) is used. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to an **OH_Drawing_Path** object. |
| float ctrlX1 | X coordinate of the first control point. |
| float ctrlY1 | Y coordinate of the first control point. |
| float ctrlX2 | X coordinate of the second control point. |
| float ctrlY2 | Y coordinate of the second control point. |
| float endX | X coordinate of the target point. |
| float endY | Y coordinate of the target point. |

### OH_Drawing_PathRMoveTo()

```c
void OH_Drawing_PathRMoveTo(OH_Drawing_Path* path, float x, float y)
```

**Description**

Sets the start position relative to the last point of a path. If the path is empty, the start point (0, 0) is used. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| float x | X-axis offset relative to the end point of a path. A positive number indicates an offset in the positive direction of the X axis, and a negative number indicates an offset in the negative direction of the X axis. |
| float y | Y-axis offset relative to the end point of a path. A positive number indicates an offset in the positive direction of the Y axis, and a negative number indicates an offset in the negative direction of the Y axis. |

### OH_Drawing_PathRLineTo()

```c
void OH_Drawing_PathRLineTo(OH_Drawing_Path* path, float x, float y)
```

**Description**

Draws a line segment from the last point of this path to a point relative to the last point. If the path is empty, the start point (0, 0) is used. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| float x | X offset relative to the last point, which is used to specify the X coordinate of the target point. |
| float y | Y offset relative to the last point, which is used to specify the X coordinate of the target point. |

### OH_Drawing_PathRQuadTo()

```c
void OH_Drawing_PathRQuadTo(OH_Drawing_Path* path, float ctrlX, float ctrlY, float endX, float endY)
```

**Description**

Draws a quadratic Bezier curve from the last point of this path to a point relative to the last point. If the path is empty, the start point (0, 0) is used. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| float ctrlX | X offset relative to the last point, which is used to specify the X coordinate of the control point. |
| float ctrlY | Y offset relative to the last point, which is used to specify the Y coordinate of the control point. |
| float endX | X offset relative to the last point, which is used to specify the X coordinate of the target point. |
| float endY | Y offset relative to the last point, which is used to specify the Y coordinate of the target point. |

### OH_Drawing_PathRConicTo()

```c
void OH_Drawing_PathRConicTo(OH_Drawing_Path* path, float ctrlX, float ctrlY, float endX, float endY, float weight)
```

**Description**

Draws a conic curve from the last point of a path to a point relative to the last point. If the path is empty, the start point (0, 0) is used. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| float ctrlX | X offset relative to the last point, which is used to specify the X coordinate of the control point. |
| float ctrlY | Y offset relative to the last point, which is used to specify the Y coordinate of the control point. |
| float endX | X offset relative to the last point, which is used to specify the X coordinate of the target point. |
| float endY | Y offset relative to the last point, which is used to specify the Y coordinate of the target point. |
| float weight | Weight of the curve, which determines its shape. The larger the value, the closer of the curve to the control point. If the value is less than or equal to **0**, the result is equivalent to a line segment from the start point to the end point, which is added by calling [OH_Drawing_PathRLineTo](capi-drawing-path-h.md#oh_drawing_pathrlineto). If the value is **1**, the result is equivalent to [OH_Drawing_PathRQuadTo](capi-drawing-path-h.md#oh_drawing_pathrquadto). |

### OH_Drawing_PathRCubicTo()

```c
void OH_Drawing_PathRCubicTo(OH_Drawing_Path* path, float ctrlX1, float ctrlY1, float ctrlX2, float ctrlY2, float endX, float endY)
```

**Description**

Draws a cubic Bezier curve from the last point of a path to a point relative to the last point. If the path is empty, the start point (0, 0) is used. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| float ctrlX1 | X offset relative to the last point, which is used to specify the X coordinate of the first control point. |
| float ctrlY1 | Y offset relative to the last point, which is used to specify the Y coordinate of the first control point. |
| float ctrlX2 | X offset relative to the last point, which is used to specify the X coordinate of the second control point. |
| float ctrlY2 | Y offset relative to the last point, which is used to specify the Y coordinate of the second control point. |
| float endX | X offset relative to the last point, which is used to specify the X coordinate of the target point. |
| float endY | Y offset relative to the last point, which is used to specify the Y coordinate of the target point. |

### OH_Drawing_PathAddRect()

```c
void OH_Drawing_PathAddRect(OH_Drawing_Path* path, float left, float top, float right, float bottom, OH_Drawing_PathDirection pathDirection)
```

**Description**

Adds a rectangle to a path in the specified direction. The start point is the upper left corner of the rectangle. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **pathDirection** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| float left | X coordinate of the upper left corner of the rectangle. |
| float top | Y coordinate of the upper left corner of the rectangle. |
| float right | X coordinate of the lower right corner of the rectangle. |
| float bottom | Y coordinate of the lower right corner of the rectangle. |
| [OH_Drawing_PathDirection](capi-drawing-path-h.md#oh_drawing_pathdirection) pathDirection | [OH_Drawing_PathDirection](capi-drawing-path-h.md#oh_drawing_pathdirection) object. |

### OH_Drawing_PathAddRectWithInitialCorner()

```c
void OH_Drawing_PathAddRectWithInitialCorner(OH_Drawing_Path* path, const OH_Drawing_Rect* rect, OH_Drawing_PathDirection pathDirection, uint32_t start)
```

**Description**

Adds a rectangle contour to a path in the specified direction. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **pathDirection** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| const OH_Drawing_Rect* rect | Pointer to the {@link OH_Drawing_Rect} object. |
| [OH_Drawing_PathDirection](capi-drawing-path-h.md#oh_drawing_pathdirection) pathDirection | Indicates the path direction. |
| uint32_t start | Start point, indicating the corner of the rectangle from which the path is drawn. The value **0** means the upper left corner, **1** means the upper right corner, **2** means the lower right corner, and **3** means the lower left corner. |

### OH_Drawing_PathAddRoundRect()

```c
void OH_Drawing_PathAddRoundRect(OH_Drawing_Path* path, const OH_Drawing_RoundRect* roundRect, OH_Drawing_PathDirection pathDirection)
```

**Description**

Adds a rounded rectangle to a path in the specified direction. When the path direction is clockwise, the start point is at the intersection of the rounded rectangle's left boundary and its lower left corner. When the path direction is counterclockwise, the start point is at the intersection point between the left boundary and the upper left corner. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **roundRect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **pathDirection** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| const OH_Drawing_RoundRect* roundRect | Pointer to the {@link OH_Drawing_RoundRect} object. |
| [OH_Drawing_PathDirection](capi-drawing-path-h.md#oh_drawing_pathdirection) pathDirection | [OH_Drawing_PathDirection](capi-drawing-path-h.md#oh_drawing_pathdirection) object. |

### OH_Drawing_PathAddOvalWithInitialPoint()

```c
void OH_Drawing_PathAddOvalWithInitialPoint(OH_Drawing_Path* path, const OH_Drawing_Rect* rect, uint32_t start, OH_Drawing_PathDirection pathDirection)
```

**Description**

Adds an oval to a path. **OH_Drawing_Rect** specifies the outer tangent rectangle of the oval, and **<br>OH_Drawing_PathDirection** specifies whether the drawing is clockwise or counterclockwise. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **pathDirection** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| const OH_Drawing_Rect* rect | Pointer to the {@link OH_Drawing_Rect} object. |
| uint32_t start | Start point of the oval. |
| [OH_Drawing_PathDirection](capi-drawing-path-h.md#oh_drawing_pathdirection) pathDirection | [OH_Drawing_PathDirection](capi-drawing-path-h.md#oh_drawing_pathdirection) object. |

### OH_Drawing_PathAddOval()

```c
void OH_Drawing_PathAddOval(OH_Drawing_Path* path, const OH_Drawing_Rect* rect, OH_Drawing_PathDirection pathDirection)
```

**Description**

Adds an oval to a path in the specified direction. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **pathDirection** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| const OH_Drawing_Rect* rect | Pointer to the {@link OH_Drawing_Rect} object. |
| [OH_Drawing_PathDirection](capi-drawing-path-h.md#oh_drawing_pathdirection) pathDirection | [OH_Drawing_PathDirection](capi-drawing-path-h.md#oh_drawing_pathdirection) object. |

### OH_Drawing_PathAddArc()

```c
void OH_Drawing_PathAddArc(OH_Drawing_Path* path, const OH_Drawing_Rect* rect, float startAngle, float sweepAngle)
```

**Description**

Adds an arc to a path as the start of a new contour. The arc added is part of the inscribed ellipse of the rectangle, from the start angle through the sweep angle. If the sweep angle is less than or equal to -360°, or if the sweep angle is greater than or equal to 360°, and start angle modulo 90 is nearly zero, an oval instead of an ellipse is added. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| const OH_Drawing_Rect* rect | Pointer to the {@link OH_Drawing_Rect} object. |
| float startAngle | Start angle of the arc, in degrees. |
| float sweepAngle | Angle to sweep, in degrees. A positive number indicates a clockwise sweep, and a negative value indicates a counterclockwise swipe. The actual swipe degree is the modulo operation result of the input parameter by 360. |

### OH_Drawing_PathAddPath()

```c
void OH_Drawing_PathAddPath(OH_Drawing_Path* path, const OH_Drawing_Path* src, const OH_Drawing_Matrix* matrix)
```

**Description**

Transforms the points in a **src** path by a matrix and adds the new one to the current path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **src** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the existing {@link OH_Drawing_Path} object. |
| const OH_Drawing_Path* src | Pointer to the source {@link OH_Drawing_Path} object. |
| const OH_Drawing_Matrix* matrix | Pointer to the {@link OH_Drawing_Matrix} object. A null pointer means an identity matrix. |

### OH_Drawing_PathAddPathWithMatrixAndMode()

```c
void OH_Drawing_PathAddPathWithMatrixAndMode(OH_Drawing_Path* path, const OH_Drawing_Path* src, const OH_Drawing_Matrix* matrix, OH_Drawing_PathAddMode pathAddMode)
```

**Description**

Transforms the points in a **src** path by a matrix and adds the new one to the current path with the specified adding mode. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **src** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **pathAddMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the existing {@link OH_Drawing_Path} object. |
| const OH_Drawing_Path* src | Pointer to the source {@link OH_Drawing_Path} object. |
| const OH_Drawing_Matrix* matrix | Pointer to the {@link OH_Drawing_Matrix} object. A null pointer means an identity matrix. |
| [OH_Drawing_PathAddMode](capi-drawing-path-h.md#oh_drawing_pathaddmode) pathAddMode | [OH_Drawing_PathAddMode](capi-drawing-path-h.md#oh_drawing_pathaddmode) object. |

### OH_Drawing_PathAddPathWithMode()

```c
void OH_Drawing_PathAddPathWithMode(OH_Drawing_Path* path, const OH_Drawing_Path* src, OH_Drawing_PathAddMode pathAddMode)
```

**Description**

Adds a **src** path to the current path with the specified adding mode. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **src** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **pathAddMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the existing {@link OH_Drawing_Path} object. |
| const OH_Drawing_Path* src | Pointer to the source {@link OH_Drawing_Path} object. |
| [OH_Drawing_PathAddMode](capi-drawing-path-h.md#oh_drawing_pathaddmode) pathAddMode | [OH_Drawing_PathAddMode](capi-drawing-path-h.md#oh_drawing_pathaddmode) object. |

### OH_Drawing_PathAddPathWithOffsetAndMode()

```c
void OH_Drawing_PathAddPathWithOffsetAndMode(OH_Drawing_Path* path, const OH_Drawing_Path* src, float dx, float dy, OH_Drawing_PathAddMode pathAddMode)
```

**Description**

Translates a **src** path by an offset and adds the new one to the current path with the specified adding mode. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **src** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **pathAddMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the existing {@link OH_Drawing_Path} object. |
| const OH_Drawing_Path* src | Pointer to the source {@link OH_Drawing_Path} object. |
| float dx | X offset. |
| float dy | Y offset. |
| [OH_Drawing_PathAddMode](capi-drawing-path-h.md#oh_drawing_pathaddmode) pathAddMode | [OH_Drawing_PathAddMode](capi-drawing-path-h.md#oh_drawing_pathaddmode) object. |

### OH_Drawing_PathAddPolygon()

```c
void OH_Drawing_PathAddPolygon(OH_Drawing_Path* path, const OH_Drawing_Point2D* points, uint32_t count, bool isClosed)
```

**Description**

Adds a polygon to a path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **points** is NULL or **count** is **0**, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the existing {@link OH_Drawing_Path} object. |
| const OH_Drawing_Point2D* points | Pointer to an array that holds the vertex coordinates of the polygon. |
| uint32_t count | Size of the array. |
| bool isClosed | Whether the path is closed. The value **true** means that the path is closed, and **false** means the opposite. |

### OH_Drawing_PathAddCircle()

```c
void OH_Drawing_PathAddCircle(OH_Drawing_Path* path, float x, float y, float radius, OH_Drawing_PathDirection pathDirection)
```

**Description**

Adds a circle to a path in the specified direction. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **radius** is less than or equal to 0, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. If **pathDirection** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| float x | X coordinate of the circle center. |
| float y | Y coordinate of the circle center. |
| float radius | Radius of the circle. |
| [OH_Drawing_PathDirection](capi-drawing-path-h.md#oh_drawing_pathdirection) pathDirection | [OH_Drawing_PathDirection](capi-drawing-path-h.md#oh_drawing_pathdirection) object. |

### OH_Drawing_PathBuildFromSvgString()

```c
bool OH_Drawing_PathBuildFromSvgString(OH_Drawing_Path* path, const char* str)
```

**Description**

Parses the path represented by an SVG string. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **str** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| const char* str | Pointer to the SVG string. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns whether the SVG string is successfully parsed. true means successful; false otherwise. |

### OH_Drawing_PathConvertToSvgString()

```c
OH_Drawing_ErrorCode OH_Drawing_PathConvertToSvgString(const OH_Drawing_Path* path, char* str, size_t* strSize)
```

**Description**

Convert path to an SVG string.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Path* path | Indicates the pointer to an <b>OH_Drawing_Path</b> object. |
| char* str | Indicates the SVG string. API users are responsible for allocating and freeing memory. |
| size_t* strSize | Indicates the SVG string memory size in bytes. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the error code.          Returns {@link OH_DRAWING_SUCCESS} if the operation is successful.<br>        Returns {@link OH_DRAWING_ERROR_INCORRECT_PARAMETER} if path or strSize is nullptr. |

### OH_Drawing_PathGetPointData()

```c
OH_Drawing_ErrorCode OH_Drawing_PathGetPointData(const OH_Drawing_Path* path, OH_Drawing_Point2D* points, uint32_t* count)
```

**Description**

Get path point data.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Path* path | Indicates the pointer to an <b>OH_Drawing_Path</b> object. |
| OH_Drawing_Point2D* points | Indicates the path point array. |
| uint32_t* count | Indicates the size of point array. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the error code.          Returns {@link OH_DRAWING_SUCCESS} if the operation is successful.<br>        Returns {@link OH_DRAWING_ERROR_INCORRECT_PARAMETER} if path or count is nullptr. |

### OH_Drawing_PathGetVerbData()

```c
OH_Drawing_ErrorCode OH_Drawing_PathGetVerbData(const OH_Drawing_Path* path, OH_Drawing_PathIteratorVerb* verbs, uint32_t* count)
```

**Description**

Get path verb data.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Path* path | Indicates the pointer to an <b>OH_Drawing_Path</b> object. |
| OH_Drawing_PathIteratorVerb* verbs | Indicates the path verb array. |
| uint32_t* count | Indicates the size of verb array. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the error code.          Returns {@link OH_DRAWING_SUCCESS} if the operation is successful.<br>        Returns {@link OH_DRAWING_ERROR_INCORRECT_PARAMETER} if path or count is nullptr. |

### OH_Drawing_PathGetConicWeightData()

```c
OH_Drawing_ErrorCode OH_Drawing_PathGetConicWeightData(const OH_Drawing_Path* path, float* conicWeights, uint32_t* count)
```

**Description**

Get path conic weight data.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Path* path | Indicates the pointer to an <b>OH_Drawing_Path</b> object. |
| float* conicWeights | Indicates the path conic weight array. |
| uint32_t* count | Indicates the size of conic weight array. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the error code.          Returns {@link OH_DRAWING_SUCCESS} if the operation is successful.<br>        Returns {@link OH_DRAWING_ERROR_INCORRECT_PARAMETER} if path or count is nullptr. |

### OH_Drawing_PathContains()

```c
bool OH_Drawing_PathContains(OH_Drawing_Path* path, float x, float y)
```

**Description**

Checks whether a coordinate point is included in this path. For details, see [OH_Drawing_PathFillType](capi-drawing-path-h.md#oh_drawing_pathfilltype). This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| float x | Coordinate point on the X axis. |
| float y | Coordinate point on the Y axis. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the coordinate point is included in the path; returns false otherwise. |

### OH_Drawing_PathTransform()

```c
void OH_Drawing_PathTransform(OH_Drawing_Path* path, const OH_Drawing_Matrix* matrix)
```

**Description**

Transforms the points in a path by matrix. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| const OH_Drawing_Matrix* matrix | Pointer to the {@link OH_Drawing_Matrix} object. |

### OH_Drawing_PathTransformWithPerspectiveClip()

```c
void OH_Drawing_PathTransformWithPerspectiveClip(OH_Drawing_Path* src, const OH_Drawing_Matrix* matrix, OH_Drawing_Path* dst, bool applyPerspectiveClip)
```

**Description**

Transforms the points in a path by matrix, and uses the new one to replace the **dst** path. If **dst** is NULL, the **src** path is replaced. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **src** or **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* src | Pointer to the {@link OH_Drawing_Path} object. |
| const OH_Drawing_Matrix* matrix | Pointer to the {@link OH_Drawing_Matrix} object. |
| OH_Drawing_Path* dst | Pointer to the target {@link OH_Drawing_Path} object. |
| bool applyPerspectiveClip | Whether to apply perspective cropping to the new path. The value **true** means to apply perspective cropping, and **false** means the opposite. |

### OH_Drawing_PathSetFillType()

```c
void OH_Drawing_PathSetFillType(OH_Drawing_Path* path, OH_Drawing_PathFillType pathFillType)
```

**Description**

Sets the fill type of a path. The fill type determines how "inside" of the path is drawn. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **pathFillType** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| [OH_Drawing_PathFillType](capi-drawing-path-h.md#oh_drawing_pathfilltype) pathFillType | [OH_Drawing_PathFillType](capi-drawing-path-h.md#oh_drawing_pathfilltype) object. |

### OH_Drawing_PathGetFillType()

```c
OH_Drawing_ErrorCode OH_Drawing_PathGetFillType(OH_Drawing_Path* path, OH_Drawing_PathFillType* pathFillType)
```

**Description**

Obtains the fill type of a path.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| [OH_Drawing_PathFillType](capi-drawing-path-h.md#oh_drawing_pathfilltype)* pathFillType | Pointer to the [OH_Drawing_PathFillType](capi-drawing-path-h.md#oh_drawing_pathfilltype) object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if path or pathFillType is NULL. |

### OH_Drawing_PathGetLength()

```c
float OH_Drawing_PathGetLength(OH_Drawing_Path* path, bool forceClosed)
```

**Description**

Obtains the length of a path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| bool forceClosed | Whether the path is measured as a closed path. **true** means that the path is forcibly considered as a closed path; **false** means that the path is measured depending on whether it is a closed path. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the length of the path. |

### OH_Drawing_PathGetBounds()

```c
void OH_Drawing_PathGetBounds(OH_Drawing_Path* path, OH_Drawing_Rect* rect)
```

**Description**

Obtains the minimum bounds that enclose a path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| OH_Drawing_Rect* rect | Pointer to the {@link OH_Drawing_Rect} object. |

### OH_Drawing_PathClose()

```c
void OH_Drawing_PathClose(OH_Drawing_Path* path)
```

**Description**

Draws a line segment from the current point to the start point of this path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |

### OH_Drawing_PathOffset()

```c
void OH_Drawing_PathOffset(OH_Drawing_Path* path, OH_Drawing_Path* dst, float dx, float dy)
```

**Description**

Translates a path by an offset along the X axis and Y axis and adds the new one to the **dst** path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the existing {@link OH_Drawing_Path} object. |
| OH_Drawing_Path* dst | Pointer to a destination path, which is an {@link OH_Drawing_Path} object. If NULL is passed in, the result is stored in the current path. |
| float dx | X offset. |
| float dy | Y offset. |

### OH_Drawing_PathReset()

```c
void OH_Drawing_PathReset(OH_Drawing_Path* path)
```

**Description**

Resets the path data. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 8

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to an **OH_Drawing_Path** object. |

### OH_Drawing_PathIsClosed()

```c
bool OH_Drawing_PathIsClosed(OH_Drawing_Path* path, bool forceClosed)
```

**Description**

Checks whether a path is closed. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| bool forceClosed | Whether the path is measured as a closed path. The value **true** means that the path is considered closed during measurement, and **false** means that the path is measured based on the actual closed status. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the path is closed; returns false otherwise. |

### OH_Drawing_PathGetPositionTangent()

```c
bool OH_Drawing_PathGetPositionTangent(OH_Drawing_Path* path, bool forceClosed, float distance, OH_Drawing_Point2D* position, OH_Drawing_Point2D* tangent)
```

**Description**

Obtains the coordinates and tangent at a distance from the start point of this path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If any of **path**, **position**, or **tangent** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| bool forceClosed | Whether the path is measured as a closed path. The value **true** means that the path is considered closed during measurement, and **false** means that the path is measured based on the actual closed status. |
| float distance | Distance from the start point. If the distance is less than 0, it is considered as 0. If the distance is greater than the path length, it is considered as the path length. |
| OH_Drawing_Point2D* position | Pointer to the coordinates. |
| OH_Drawing_Point2D* tangent | Pointer to the tangent, where **tangent.x** and **tangent.y** represent the cosine and sine of the tangent of the point, respectively. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns whether the measurement is successful. true means successful; false otherwise. |

### OH_Drawing_PathGetSegment()

```c
OH_Drawing_ErrorCode OH_Drawing_PathGetSegment(OH_Drawing_Path* path, bool forceClosed, float start, float stop, bool startWithMoveTo, OH_Drawing_Path* dst, bool* result)
```

**Description**

Extracts a segment of a path and appends it to a destination path.

**Since**: 18

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| bool forceClosed | Whether the path is measured as a closed path. The value **true** means that the path is considered closed during measurement, and **false** means that the path is measured based on the actual closed status. |
| float start | Distance from the start point of the path to the start point of the segment. If it is less than 0, it defaults to 0. If it is greater than or equal to **stop**, the extraction fails. |
| float stop | Distance from the start point of the path to the end point of the segment. If it is less than or equal to **start**, the extraction fails. If it is greater than the path length, it defaults to the path length. |
| bool startWithMoveTo | Whether to execute [OH_Drawing_PathMoveTo](capi-drawing-path-h.md#oh_drawing_pathmoveto) in the destination path to move to its start point. The value **true** means to move to the start point, and **false** means the opposite. |
| OH_Drawing_Path* dst | Pointer to a destination path, which is an {@link OH_Drawing_Path} object. If the extraction succeeds, the segment is appended to the path. If the extraction fails, nothing changes. |
| bool* result | Pointer to the extraction result. The value **true** means that the extraction is successful, and **<br>false** means the opposite. It as an output parameter. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns one of the following result codes:  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if at least one of the path, dst, and result parameters is a null  pointer. |

### OH_Drawing_PathOp()

```c
bool OH_Drawing_PathOp(OH_Drawing_Path* path, const OH_Drawing_Path* other, OH_Drawing_PathOpMode op)
```

**Description**

Combines two paths based on the specified operation mode. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **srcPath** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **op** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to an {@link OH_Drawing_Path} object, in which the resulting path is saved. |
| const OH_Drawing_Path* other | Pointer to the {@link OH_Drawing_Path} object. |
| [OH_Drawing_PathOpMode](capi-drawing-path-h.md#oh_drawing_pathopmode) op | Operation mode of the path. For details about the available options, see [OH_Drawing_PathOpMode](capi-drawing-path-h.md#oh_drawing_pathopmode). |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the resulting path is not empty; returns false otherwise. |

### OH_Drawing_PathGetMatrix()

```c
bool OH_Drawing_PathGetMatrix(OH_Drawing_Path* path, bool forceClosed, float distance, OH_Drawing_Matrix* matrix, OH_Drawing_PathMeasureMatrixFlags flag)
```

**Description**

Obtains a transformation matrix at a distance from the start point of this path. This API may return an error code. For details, call {@link OH_Drawing_ErrorCodeGet}. If either **path** or **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **flag** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| bool forceClosed | Whether the path is measured as a closed path. The value **true** means that the path is considered closed during measurement, and **false** means that the path is measured based on the actual closed status. |
| float distance | Distance from the start point. If the distance is less than 0, it is considered as 0. If the distance is greater than the path length, it is considered as the path length. |
| OH_Drawing_Matrix* matrix | Pointer to the transformation matrix. |
| [OH_Drawing_PathMeasureMatrixFlags](capi-drawing-path-h.md#oh_drawing_pathmeasurematrixflags) flag | Type of the matrix information. For details about the available options, see [OH_Drawing_PathMeasureMatrixFlags](capi-drawing-path-h.md#oh_drawing_pathmeasurematrixflags) . |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the transformation matrix is obtained successfully; returns false otherwise. The  possible failure cause is that path is NULL or the path length is 0. |

### OH_Drawing_PathApproximate()

```c
OH_Drawing_ErrorCode OH_Drawing_PathApproximate(OH_Drawing_Path* path, float acceptableError, float* vals, uint32_t* count)
```

**Description**

Converts the existing path into an approximate path consisting of consecutive line segments.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| float acceptableError | Acceptable error of each line segment on the path. The value cannot be less than 0. 1. Avoid setting **acceptableError** to **0** as it heavily divides the curve path, significantly impacting performance and memory usage. 2. Setting a high **acceptableError** simplifies the path greatly by keeping only essential points, potentially distorting the original shape. 3. When you set a high **acceptableError** for curves such as ellipses, the fitting process often simplifies them to polygons by keeping just the start and end points of their Bezier curve segments. |
| float* vals | An array of approximate points of the path. Each point consists of three values, indicating: 1. Length ratio of the point to the start point of the path. 2. X coordinate of the point. 3. Y coordinate of the point. |
| uint32_t* count | Size of the returned array, which is at least 6. The size of the point array after fitting is returned if **vals** is a null pointer. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if path or count is a null pointer.  OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if acceptableError is less than 0. |

### OH_Drawing_PathInterpolate()

```c
OH_Drawing_ErrorCode OH_Drawing_PathInterpolate(OH_Drawing_Path* path, OH_Drawing_Path* other, float weight, bool* success, OH_Drawing_Path* interpolatedPath)
```

**Description**

Interpolates between the existing path and another path based on the given weight and stores the result in the target path object. Interpolation is achievable if the two paths have the same number of points. The target path is created based on the structure of the existing path.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| OH_Drawing_Path* other | Pointer to the {@link OH_Drawing_Path} object of the other path used for interpolation. |
| float weight | Interpolation weight. The value range is [0, 1]. |
| bool* success | Whether the interpolation is successful. **true** means yes; **false** otherwise. It as an output parameter. |
| OH_Drawing_Path* interpolatedPath | Pointer to the {@link OH_Drawing_Path} object used to store the interpolation result. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if path, other, success, or interpolatedPath is a null  pointer.  OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if weight is not in the range of [0, 1]. |

### OH_Drawing_PathIsInterpolate()

```c
OH_Drawing_ErrorCode OH_Drawing_PathIsInterpolate(OH_Drawing_Path* path, OH_Drawing_Path* other, bool* result)
```

**Description**

Checks whether the existing path and another path (**other**) are compatible for interpolation in terms of structure and operation sequence. If the paths contain conic operations, the weight values of the operations must be the same.

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| OH_Drawing_Path* other | Pointer to the {@link OH_Drawing_Path} object. |
| bool* result | Checks whether a path is compatible with another path. It is used as an output parameter. **true** if the paths are compatible, **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INVALID_PARAMETER if path, other, or result is a null pointer. |

### OH_Drawing_PathGetLastPoint()

```c
OH_Drawing_ErrorCode OH_Drawing_PathGetLastPoint(OH_Drawing_Path* path, OH_Drawing_Point2D* point)
```

**Description**

Gets the last point of the path.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Indicates the pointer to an <b>OH_Drawing_Path</b> object. |
| OH_Drawing_Point2D* point | Indicates the pointer to an <b>OH_Drawing_Point2D</b> object to store the last point. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the error code.          Returns {@link OH_DRAWING_SUCCESS} if the operation is successful.<br>        Returns {@link OH_DRAWING_ERROR_INCORRECT_PARAMETER} if path or point is nullptr, or the path is empty. |

### OH_Drawing_PathIsInverseFillType()

```c
OH_Drawing_ErrorCode OH_Drawing_PathIsInverseFillType(const OH_Drawing_Path* path, bool* isInverse)
```

**Description**

Checks whether the fill type of the path is the inverse type.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |
| bool* isInverse | Whether the fill type is the inverse type. It is used as an output parameter. **true** if the fill type is the inverse type; **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INCORRECT_PARAMETER if path or isInverse is a null pointer. |

### OH_Drawing_PathToggleInverseFillType()

```c
OH_Drawing_ErrorCode OH_Drawing_PathToggleInverseFillType(OH_Drawing_Path* path)
```

**Description**

Toggles the fill type of the path to the inverse type.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Pointer to the {@link OH_Drawing_Path} object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Execution result.  OH_DRAWING_SUCCESS if the operation is successful.  OH_DRAWING_ERROR_INCORRECT_PARAMETER if path is a null pointer. |

### OH_Drawing_PathIsEqual()

```c
OH_Drawing_ErrorCode OH_Drawing_PathIsEqual(OH_Drawing_Path* path, OH_Drawing_Path* other, bool* equal)
```

**Description**

Checks if two paths are equal.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Path* path | Indicates the pointer to an <b>OH_Drawing_Path</b> object. |
| OH_Drawing_Path* other | Indicates the pointer to another <b>OH_Drawing_Path</b> object to compare. |
| bool* equal | Indicates whether the two paths are equal. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the error code.          Returns {@link OH_DRAWING_SUCCESS} if the operation is successful.<br>        Returns {@link OH_DRAWING_ERROR_INCORRECT_PARAMETER} if path or other is nullptr, or equal is nullptr. |


