# drawing_path.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=19992cfe2df5744678be8760e29a40e1754bec58 translatedAt=2026-08-24T08:49:03.673Z pushedAt=2026-08-31T08:55:14.436Z -->

## Overview

This file declares the functions related to custom paths. It can efficiently build complex geometric paths, supports SVG data exchange for cross-platform compatibility, and ensures memory safety through paired creation and destruction mechanisms. The following capabilities are mainly supported:

- Creating, copying, and destroying a path.

- Adding geometric shapes such as line segments, arcs, Bézier curves, conic curves, rectangles, ellipses, circles, and polygons.

- Performing operations such as matrix transformation, offsetting, merging, and closing on a path.

- Querying and measuring capabilities such as path length, bounds, and containment relationships.

<br>This module follows a single-thread model. The caller must manage thread safety and context state switching.

<!--RP1-->

**Sample**: [NDKAPIDrawing (API Version 20)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkGraphics2D/Drawing/NDKAPIDrawing)<!--RP1End-->

**File to include:** \<native_drawing/drawing_path.h\>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Drawing_PathDirection](#oh_drawing_pathdirection) | OH_Drawing_PathDirection | Enumerates the directions for adding a closed path. |
| [OH_Drawing_PathFillType](#oh_drawing_pathfilltype) | OH_Drawing_PathFillType | Defines an enum for the fill types of a path.|
| [OH_Drawing_PathAddMode](#oh_drawing_pathaddmode) | OH_Drawing_PathAddMode | Defines an enum for the path adding modes.|
| [OH_Drawing_PathOpMode](#oh_drawing_pathopmode) | OH_Drawing_PathOpMode | Defines an enum for the operation modes available for a path.|
| [OH_Drawing_PathMeasureMatrixFlags](#oh_drawing_pathmeasurematrixflags) | OH_Drawing_PathMeasureMatrixFlags | Defines an enum for the types of matrix information obtained during path measurement.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_Path* OH_Drawing_PathCreate(void)](#oh_drawing_pathcreate) | Creates an **OH_Drawing_Path** object.|
| [OH_Drawing_Path* OH_Drawing_PathCopy(OH_Drawing_Path* path)](#oh_drawing_pathcopy) | Copies an existing path object and returns a copy of the path object [OH_Drawing_Path](capi-drawing-oh-drawing-path.md).<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if path is NULL. |
| [void OH_Drawing_PathDestroy(OH_Drawing_Path* path)](#oh_drawing_pathdestroy) | Destroys a path object and reclaims the memory occupied by the object. |
| [OH_Drawing_ErrorCode OH_Drawing_PathSetPath(OH_Drawing_Path* path, OH_Drawing_Path* other)](#oh_drawing_pathsetpath) | Sets the content of another path object to the current path object. |
| [OH_Drawing_ErrorCode OH_Drawing_PathIsEmpty(OH_Drawing_Path* path, bool* isEmpty)](#oh_drawing_pathisempty) | Checks whether a path object is empty.|
| [OH_Drawing_ErrorCode OH_Drawing_PathIsRect(OH_Drawing_Path* path, OH_Drawing_Rect* rect, bool* isRect)](#oh_drawing_pathisrect) | Checks whether a path object forms a rectangle.|
| [OH_Drawing_ErrorCode OH_Drawing_PathGetLastPoint(OH_Drawing_Path* path, OH_Drawing_Point2D* point)](#oh_drawing_pathgetlastpoint) | Obtains the coordinates of the last point of a path. |
| [OH_Drawing_ErrorCode OH_Drawing_PathIsEqual(OH_Drawing_Path* path, OH_Drawing_Path* other, bool* equal)](#oh_drawing_pathisequal) | Checks whether two paths are equal, that is, whether the two paths are consistent in their constituent data. |
| [void OH_Drawing_PathMoveTo(OH_Drawing_Path* path, float x, float y)](#oh_drawing_pathmoveto) | Sets the start point of a path.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if path is NULL. |
| [void OH_Drawing_PathLineTo(OH_Drawing_Path* path, float x, float y)](#oh_drawing_pathlineto) | Draws a line segment from the last point of this path to the target point. If the path is empty, the start point (0, 0) is used.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PathArcTo(OH_Drawing_Path* path, float x1, float y1, float x2, float y2, float startDeg, float sweepDeg)](#oh_drawing_patharcto) | Adds an arc to a path. The arc is drawn as an angular arc: a rectangular bounding box is specified, and its inscribed ellipse is used to intercept the arc; the start angle and sweep degrees are then specified, and the portion of the ellipse circumference swept from the start angle is the arc. If the path already has content, a line segment from the last point of the path to the start point of the arc is added by default.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if path is NULL. |
| [void OH_Drawing_PathQuadTo(OH_Drawing_Path* path, float ctrlX, float ctrlY, float endX, float endY)](#oh_drawing_pathquadto) | Draws a quadratic Bezier curve from the last point of a path to the target point. If the path is empty, the start point (0, 0) is used.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PathConicTo(OH_Drawing_Path* path, float ctrlX, float ctrlY, float endX, float endY, float weight)](#oh_drawing_pathconicto) | Adds a conic curve segment from the last point of the current path (or (0, 0) if the path has no content) to the target point, with the control point at (ctrlX, ctrlY) and the end point at (endX, endY).<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if path is NULL. |
| [void OH_Drawing_PathCubicTo(OH_Drawing_Path* path, float ctrlX1, float ctrlY1, float ctrlX2, float ctrlY2, float endX, float endY)](#oh_drawing_pathcubicto) | Adds a cubic Bézier curve from the last point of the path to the target point.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if path is NULL. |
| [void OH_Drawing_PathRMoveTo(OH_Drawing_Path* path, float x, float y)](#oh_drawing_pathrmoveto) | Sets the start position relative to the last point of a path. If the path is empty, the start point (0, 0) is used.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PathRLineTo(OH_Drawing_Path* path, float x, float y)](#oh_drawing_pathrlineto) | Draws a line segment from the last point of this path to a point relative to the last point. If the path is empty, the start point (0, 0) is used.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PathRQuadTo(OH_Drawing_Path* path, float ctrlX, float ctrlY, float endX, float endY)](#oh_drawing_pathrquadto) | Draws a quadratic Bezier curve from the last point of this path to a point relative to the last point. If the path is empty, the start point (0, 0) is used.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PathRConicTo(OH_Drawing_Path* path, float ctrlX, float ctrlY, float endX, float endY, float weight)](#oh_drawing_pathrconicto) | Adds a conic curve segment from the last point of the current path (or (0, 0) if the path has no content) to the target point using relative positions.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if path is NULL. |
| [void OH_Drawing_PathRCubicTo(OH_Drawing_Path* path, float ctrlX1, float ctrlY1, float ctrlX2, float ctrlY2, float endX, float endY)](#oh_drawing_pathrcubicto) | Adds a cubic Bézier curve from the end point of the current path (or (0, 0) if the path has no content) to the target point using relative positions.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if path is NULL. |
| [void OH_Drawing_PathAddRect(OH_Drawing_Path* path, float left, float top, float right, float bottom, OH_Drawing_PathDirection pathDirection)](#oh_drawing_pathaddrect) | Adds a rectangle to a path in the specified direction. The start point of the rectangle outline is the upper-left corner of the rectangle.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if path is NULL;<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if pathDirection is outside the enum range. |
| [void OH_Drawing_PathAddRectWithInitialCorner(OH_Drawing_Path* path, const OH_Drawing_Rect* rect, OH_Drawing_PathDirection pathDirection, uint32_t start)](#oh_drawing_pathaddrectwithinitialcorner) | Adds a rectangle outline to a path in the specified direction.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either path or rect is NULL;<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if pathDirection is outside the enum range. |
| [void OH_Drawing_PathAddRoundRect(OH_Drawing_Path* path, const OH_Drawing_RoundRect* roundRect, OH_Drawing_PathDirection pathDirection)](#oh_drawing_pathaddroundrect) | Adds a rounded rectangle outline to a path in the specified direction. When the path is added clockwise, the start point is at the intersection of the lower-left rounded corner and the left boundary of the rounded rectangle; when the path is added counterclockwise, the start point is at the intersection of the upper-left rounded corner and the left boundary of the rounded rectangle.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either path or roundRect is NULL;<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if pathDirection is outside the enum range. |
| [void OH_Drawing_PathAddOvalWithInitialPoint(OH_Drawing_Path* path, const OH_Drawing_Rect* rect, uint32_t start, OH_Drawing_PathDirection pathDirection)](#oh_drawing_pathaddovalwithinitialpoint) | Adds an oval to a path, where the rectangle object serves as the bounding rectangle of the oval, and the drawing direction specifies whether to draw clockwise or counterclockwise.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either path or rect is NULL;<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if pathDirection is outside the enum range. |
| [void OH_Drawing_PathAddOval(OH_Drawing_Path* path, const OH_Drawing_Rect* rect, OH_Drawing_PathDirection pathDirection)](#oh_drawing_pathaddoval) | Adds an oval to a path in the specified direction, where the rectangle object serves as the bounding rectangle of the oval.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either path or rect is NULL;<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if pathDirection is outside the enum range. |
| [void OH_Drawing_PathAddArc(OH_Drawing_Path* path, const OH_Drawing_Rect* rect, float startAngle, float sweepAngle)](#oh_drawing_pathaddarc) | Adds an arc to a path as the start point of a new contour. Starting from the start angle, the arc is added by the sweep degrees, and the added arc is part of the ellipse inscribed in the rectangle.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either path or rect is NULL. |
| [void OH_Drawing_PathAddPath(OH_Drawing_Path* path, const OH_Drawing_Path* src, const OH_Drawing_Matrix* matrix)](#oh_drawing_pathaddpath) | Transforms the points in a **src** path by a matrix and adds the new one to the current path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **path** or **src** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PathAddPathWithMatrixAndMode(OH_Drawing_Path* path, const OH_Drawing_Path* src, const OH_Drawing_Matrix* matrix, OH_Drawing_PathAddMode pathAddMode)](#oh_drawing_pathaddpathwithmatrixandmode) | Transforms the source path by a matrix and adds it to the current path in the specified mode.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either path or src is NULL;<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if pathAddMode is outside the enum range. |
| [void OH_Drawing_PathAddPathWithMode(OH_Drawing_Path* path, const OH_Drawing_Path* src, OH_Drawing_PathAddMode pathAddMode)](#oh_drawing_pathaddpathwithmode) | Adds the source path to the current path in the specified mode.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either path or src is NULL;<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if pathAddMode is outside the enum range. |
| [void OH_Drawing_PathAddPathWithOffsetAndMode(OH_Drawing_Path* path, const OH_Drawing_Path* src, float dx, float dy, OH_Drawing_PathAddMode pathAddMode)](#oh_drawing_pathaddpathwithoffsetandmode) | Offsets the source path and adds it to the current path in the specified mode.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either path or src is NULL;<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if pathAddMode is outside the enum range. |
| [void OH_Drawing_PathAddPolygon(OH_Drawing_Path* path, const OH_Drawing_Point2D* points, uint32_t count, bool isClosed)](#oh_drawing_pathaddpolygon) | Adds a polygon to a path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **path** or **points** is NULL or **count** is **0**, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PathAddCircle(OH_Drawing_Path* path, float x, float y, float radius, OH_Drawing_PathDirection pathDirection)](#oh_drawing_pathaddcircle) | Adds a circle to a path in the specified direction.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if path is NULL;<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if radius is less than or equal to 0;<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if pathDirection is outside the enum range. |
| [bool OH_Drawing_PathBuildFromSvgString(OH_Drawing_Path* path, const char* str)](#oh_drawing_pathbuildfromsvgstring) | Parses the path represented by an SVG string.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **path** or **str** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [OH_Drawing_ErrorCode OH_Drawing_PathConvertToSvgString(const OH_Drawing_Path* path, char* str, size_t* strSize)](#oh_drawing_pathconverttosvgstring) | Converts a path to an SVG path data string. |
| [bool OH_Drawing_PathContains(OH_Drawing_Path* path, float x, float y)](#oh_drawing_pathcontains) | Checks whether a specified coordinate point is contained in a path. The determination rule follows [OH_Drawing_PathFillType](#oh_drawing_pathfilltype).<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if path is NULL. |
| [void OH_Drawing_PathTransform(OH_Drawing_Path* path, const OH_Drawing_Matrix* matrix)](#oh_drawing_pathtransform) | Applies a matrix transformation to a path. The transformation result directly modifies the current path object.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either path or matrix is NULL. |
| [void OH_Drawing_PathTransformWithPerspectiveClip(OH_Drawing_Path* src, const OH_Drawing_Matrix* matrix, OH_Drawing_Path* dst, bool applyPerspectiveClip)](#oh_drawing_pathtransformwithperspectiveclip) | Applies a matrix transformation to a path. The transformed path replaces the destination path; if the destination path is NULL, the source path is replaced.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either src or matrix is NULL. |
| [void OH_Drawing_PathSetFillType(OH_Drawing_Path* path, OH_Drawing_PathFillType pathFillType)](#oh_drawing_pathsetfilltype) | Sets the fill type of a path, which determines how the interior region of the path is defined.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if path is NULL;<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if pathFillType is outside the enum range. |
| [OH_Drawing_ErrorCode OH_Drawing_PathGetFillType(OH_Drawing_Path* path, OH_Drawing_PathFillType* pathFillType)](#oh_drawing_pathgetfilltype) | Obtains the fill type of a path.|
| [float OH_Drawing_PathGetLength(OH_Drawing_Path* path, bool forceClosed)](#oh_drawing_pathgetlength) | Obtains the length of a path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PathGetBounds(OH_Drawing_Path* path, OH_Drawing_Rect* rect)](#oh_drawing_pathgetbounds) | Obtains the minimum bounds that enclose a path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **path** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PathClose(OH_Drawing_Path* path)](#oh_drawing_pathclose) | Draws a line segment from the start point to the last point to close this path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PathOffset(OH_Drawing_Path* path, OH_Drawing_Path* dst, float dx, float dy)](#oh_drawing_pathoffset) | Translates a path by an offset along the X axis and Y axis and adds the new one to the **dst** path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_PathReset(OH_Drawing_Path* path)](#oh_drawing_pathreset) | Resets the path data.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [bool OH_Drawing_PathIsClosed(OH_Drawing_Path* path, bool forceClosed)](#oh_drawing_pathisclosed) | Checks whether a path is closed.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [bool OH_Drawing_PathGetPositionTangent(OH_Drawing_Path* path, bool forceClosed, float distance, OH_Drawing_Point2D* position, OH_Drawing_Point2D* tangent)](#oh_drawing_pathgetpositiontangent) | Obtains the coordinate point and tangent value at a specified distance from the start point of a path.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if any of path, position, or tangent is NULL. |
| [OH_Drawing_ErrorCode OH_Drawing_PathGetSegment(OH_Drawing_Path* path, bool forceClosed, float start, float stop, bool startWithMoveTo, OH_Drawing_Path* dst, bool* result)](#oh_drawing_pathgetsegment) | Extracts a segment of a path and appends it to the destination path. |
| [bool OH_Drawing_PathOp(OH_Drawing_Path* path, const OH_Drawing_Path* other, OH_Drawing_PathOpMode op)](#oh_drawing_pathop) | Combines two paths according to the specified path operation type.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either path or other is NULL;<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if op is outside the enum range. |
| [bool OH_Drawing_PathGetMatrix(OH_Drawing_Path* path, bool forceClosed, float distance, OH_Drawing_Matrix* matrix, OH_Drawing_PathMeasureMatrixFlags flag)](#oh_drawing_pathgetmatrix) | Obtains the corresponding transformation matrix at a specified distance from the start point of a path.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either path or matrix is NULL;<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if flag is outside the enum range. |
| [OH_Drawing_ErrorCode OH_Drawing_PathApproximate(OH_Drawing_Path* path, float acceptableError, float* vals, uint32_t* count)](#oh_drawing_pathapproximate) | Converts the current path into an approximate path composed of consecutive line segments. |
| [OH_Drawing_ErrorCode OH_Drawing_PathGetVerbData(const OH_Drawing_Path* path, OH_Drawing_PathIteratorVerb* verbs, uint32_t* count)](#oh_drawing_pathgetverbdata) | Obtains the verb data of a path. In a path primitive, the verb data describes the basic drawing actions during path construction. |
| [OH_Drawing_ErrorCode OH_Drawing_PathGetPointData(const OH_Drawing_Path* path, OH_Drawing_Point2D* points, uint32_t* count)](#oh_drawing_pathgetpointdata) | Obtains the point data of a path.<br>In a path primitive, the point data exists as a sequence of numeric values, corresponding one-to-one with the verb instructions, and is used to precisely specify the geometric coordinate positions of drawing actions. |
| [OH_Drawing_ErrorCode OH_Drawing_PathGetConicWeightData(const OH_Drawing_Path* path, float* conicWeights, uint32_t* count)](#oh_drawing_pathgetconicweightdata) | Obtains the conic curve weight data of a path.<br>The conic curve weight data of a path is used to describe the weight information of the conic curves in the path.<br>In a path primitive, the conic curve data is represented in the form of a rational Bézier curve, in which each control point carries a weight value. |
| [OH_Drawing_ErrorCode OH_Drawing_PathInterpolate(OH_Drawing_Path* path, OH_Drawing_Path* other, float weight, bool* success, OH_Drawing_Path* interpolatedPath)](#oh_drawing_pathinterpolate) | Interpolates between the current path and another path according to a given weight, and stores the result in the destination path object.<br>Interpolation succeeds as long as the two paths have the same number of points, and the destination path is created according to the structure of the current path. |
| [OH_Drawing_ErrorCode OH_Drawing_PathIsInterpolate(OH_Drawing_Path* path, OH_Drawing_Path* other, bool* result)](#oh_drawing_pathisinterpolate) | Checks whether the current path and another path (other) are completely consistent in structure and operation order, to determine whether the two paths are compatible for interpolation. This API is used for pre-checking before calling [OH_Drawing_PathInterpolate](#oh_drawing_pathinterpolate).<br> If the path contains conic curve operations, the weight values of the corresponding operations must also be consistent for the paths to be considered compatible for interpolation. |
| [OH_Drawing_ErrorCode OH_Drawing_PathIsInverseFillType(const OH_Drawing_Path* path, bool* isInverse)](#oh_drawing_pathisinversefilltype) | Checks whether the fill type of a path is an inverse type.<br>The inverse types are PATH_FILL_TYPE_INVERSE_WINDING and PATH_FILL_TYPE_INVERSE_EVEN_ODD in [OH_Drawing_PathFillType](#oh_drawing_pathfilltype). |
| [OH_Drawing_ErrorCode OH_Drawing_PathToggleInverseFillType(OH_Drawing_Path* path)](#oh_drawing_pathtoggleinversefilltype) | Toggles the inverse state of the fill type of a path, that is, flips between the inverse type and the non-inverse type.<br>The inverse types are PATH_FILL_TYPE_INVERSE_WINDING and PATH_FILL_TYPE_INVERSE_EVEN_ODD in [OH_Drawing_PathFillType](#oh_drawing_pathfilltype). |

## Enum Description

### OH_Drawing_PathDirection

```c
enum OH_Drawing_PathDirection
```

**Description**

Enumerates the directions for adding a closed path.

**Since**: 12

| Value| Description|
| -- | -- |
| PATH_DIRECTION_CW | Adds a closed contour clockwise.|
| PATH_DIRECTION_CCW | Adds a closed contour counterclockwise.|

### OH_Drawing_PathFillType

```c
enum OH_Drawing_PathFillType
```

**Description**

Enumerates the fill types of a path.

**Since**: 12

| Value| Description|
| -- | -- |
| PATH_FILL_TYPE_WINDING | For any point within the drawing area, a ray is cast in an arbitrary direction. The count starts at 0 for all intersections between this ray and the path.<br>Each clockwise intersection—where the path crosses the ray from left to right—results in the count being incremented by 1, while each counterclockwise intersection—where the path crosses the ray from right to left—causes the count to be decremented by 1. A point is deemed inside the path and needs to be colored if the final count is non-zero; if the count is 0, the point remains uncolored.|
| PATH_FILL_TYPE_EVEN_ODD | For any point in the drawing area, a ray is cast in an arbitrary direction. If the number of intersections between this ray and the path is odd, the point is deemed inside the path and needs to be colored; if the number is even, it remains uncolored.|
| PATH_FILL_TYPE_INVERSE_WINDING | Same as **PATH_FILL_TYPE_WINDING**, but draws outside of the path, rather than inside.|
| PATH_FILL_TYPE_INVERSE_EVEN_ODD | Same as **PATH_FILL_TYPE_EVEN_ODD**, but draws outside of the path, rather than inside.|

### OH_Drawing_PathAddMode

```c
enum OH_Drawing_PathAddMode
```

**Description**

Enumerates the path adding modes.

**Since**: 12

| Value| Description|
| -- | -- |
| PATH_ADD_MODE_APPEND | Adds a path in append mode.|
| PATH_ADD_MODE_EXTEND | If the current path is not closed, adds a straight line to close it. |

### OH_Drawing_PathOpMode

```c
enum OH_Drawing_PathOpMode
```

**Description**

Enumerates the operation modes available for a path.

**Since**: 12

| Value| Description|
| -- | -- |
| PATH_OP_MODE_DIFFERENCE | Difference operation.|
| PATH_OP_MODE_INTERSECT | Intersection operation.|
| PATH_OP_MODE_UNION | Union operation.|
| PATH_OP_MODE_XOR | XOR operation.|
| PATH_OP_MODE_REVERSE_DIFFERENCE | Reverse difference operation.|

### OH_Drawing_PathMeasureMatrixFlags

```c
enum OH_Drawing_PathMeasureMatrixFlags
```

**Description**

Enumerates the types of matrix information obtained during path measurement.

**Since**: 12

| Value| Description|
| -- | -- |
| GET_POSITION_MATRIX | Matrix corresponding to the position information.|
| GET_TANGENT_MATRIX | Matrix corresponding to the tangent information.|
| GET_POSITION_AND_TANGENT_MATRIX | Matrix corresponding to the position and tangent information.|

## Function Description

### OH_Drawing_PathCreate()

```c
OH_Drawing_Path* OH_Drawing_PathCreate(void)
```

**Description**

Creates an **OH_Drawing_Path** object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* | Returns the pointer to the **OH_Drawing_Path** object created.|

### OH_Drawing_PathCopy()

```c
OH_Drawing_Path* OH_Drawing_PathCopy(OH_Drawing_Path* path)
```

**Description**

Copies an existing path object and returns a copy of the path object [OH_Drawing_Path](capi-drawing-oh-drawing-path.md).<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if path is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the source path object [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) to be copied. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* | Pointer to the copy of the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|

### OH_Drawing_PathDestroy()

```c
void OH_Drawing_PathDestroy(OH_Drawing_Path* path)
```

**Description**

Destroys a path object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to an **OH_Drawing_Path** object.|

### OH_Drawing_PathSetPath()

```c
OH_Drawing_ErrorCode OH_Drawing_PathSetPath(OH_Drawing_Path* path, OH_Drawing_Path* other)
```

**Description**

Sets the content of another path object to the current path object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* other | Pointer to the source path object [OH_Drawing_Path](capi-drawing-oh-drawing-path.md), whose content will be set to the current path object. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br> Returns **OH_DRAWING_SUCCESS** if the operation is successful.<br> Returns **OH_DRAWING_ERROR_INVALID_PARAMETER** if path or other is a null pointer. |

### OH_Drawing_PathIsEmpty()

```c
OH_Drawing_ErrorCode OH_Drawing_PathIsEmpty(OH_Drawing_Path* path, bool* isEmpty)
```

**Description**

Checks whether a path object is empty.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| bool* isEmpty | Whether the path object is empty. **true** means empty; **false** otherwise. It as an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **path** or **isEmpty** is NULL.|

### OH_Drawing_PathIsRect()

```c
OH_Drawing_ErrorCode OH_Drawing_PathIsRect(OH_Drawing_Path* path, OH_Drawing_Rect* rect, bool* isRect)
```

**Description**

Checks whether a path object forms a rectangle.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) object, which is used as an output parameter and can be null.|
| bool* isRect | Whether a path forms a rectangle. **true** means yes; **false** otherwise. It as an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **path** or **isRect** is NULL.|

### OH_Drawing_PathGetLastPoint()

```c
OH_Drawing_ErrorCode OH_Drawing_PathGetLastPoint(OH_Drawing_Path* path, OH_Drawing_Point2D* point)
```

**Description**

Obtains the coordinates of the last point of the path.

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to an [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object. |
| [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* point | Pointer to an [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md) object, which is used as an output parameter to store the last point. |

**Return value**

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER if **path** or **point** is a null pointer, or **path** is an empty path. |

### OH_Drawing_PathIsEqual()

```c
OH_Drawing_ErrorCode OH_Drawing_PathIsEqual(OH_Drawing_Path* path, OH_Drawing_Path* other, bool* equal)
```

**Description**

Checks whether two paths are equal, that is, whether the two paths are consistent in their constituent data.

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to an [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object. |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* other | Pointer to another [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object. |
| bool* equal | Whether the two paths are equal. The value **true** indicates that the two paths are equal, and **false** indicates that they are not equal. This is an output parameter. |

**Return value**

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER if **path** or **other** is a null pointer, or **equal** is a null pointer. |

### OH_Drawing_PathMoveTo()

```c
void OH_Drawing_PathMoveTo(OH_Drawing_Path* path, float x, float y)
```

**Description**

Sets the start point of a path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if **path** is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to an **OH_Drawing_Path** object.|
| float x | X-coordinate of the start point, in physical pixels (px). |
| float y | Y-coordinate of the start point, in physical pixels (px). |

### OH_Drawing_PathLineTo()

```c
void OH_Drawing_PathLineTo(OH_Drawing_Path* path, float x, float y)
```

**Description**

Draws a line segment from the last point of this path to the target point. If the path is empty, the start point (0, 0) is used.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to an **OH_Drawing_Path** object.|
| float x | X-coordinate of the target point, in physical pixels (px). |
| float y | Y-coordinate of the target point, in physical pixels (px). |

### OH_Drawing_PathArcTo()

```c
void OH_Drawing_PathArcTo(OH_Drawing_Path* path, float x1, float y1, float x2, float y2, float startDeg, float sweepDeg)
```

**Description**

Adds an arc to a path. The arc is drawn in angle arc mode: a rectangle is specified first, and its inscribed ellipse is used to intercept the arc; then a start angle and a scanning degree are specified, and the portion of the ellipse circumference scanned from the start angle is the arc. If the path already has content, a line segment from the last point of the path to the start point of the arc is added by default.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if **path** is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to an **OH_Drawing_Path** object.|
| float x1 | Horizontal coordinate of the upper-left corner of the rectangle that bounds the ellipse, in physical pixels (px). |
| float y1 | Vertical coordinate of the upper-left corner of the rectangle that bounds the ellipse, in physical pixels (px). |
| float x2 | Horizontal coordinate of the lower-right corner of the rectangle that bounds the ellipse, in physical pixels (px). |
| float y2 | Vertical coordinate of the lower-right corner of the rectangle that bounds the ellipse, in physical pixels (px). |
| float startDeg | Start angle, in degrees. The start direction of the angle (0°) is the positive direction of the x-axis. |
| float sweepDeg | Sweep angle, in degrees. A positive value sweeps clockwise, and a negative value sweeps counterclockwise. The actual sweep angle is the result of this input parameter modulo 360°. |

### OH_Drawing_PathQuadTo()

```c
void OH_Drawing_PathQuadTo(OH_Drawing_Path* path, float ctrlX, float ctrlY, float endX, float endY)
```

**Description**

Draws a quadratic Bezier curve from the last point of a path to the target point. If the path is empty, the start point (0, 0) is used.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to an **OH_Drawing_Path** object.|
| float ctrlX | X-coordinate of the control point position, in physical pixels (px). |
| float ctrlY | Y-coordinate of the control point position, in physical pixels (px). |
| float endX | X-coordinate of the target point position, in physical pixels (px). |
| float endY | Y-coordinate of the target point position, in physical pixels (px). |

### OH_Drawing_PathConicTo()

```c
void OH_Drawing_PathConicTo(OH_Drawing_Path* path, float ctrlX, float ctrlY, float endX, float endY, float weight)
```

**Description**

Adds a conic curve segment from the last point of the current path (or (0, 0) if the path is empty) to the target point, with the control point at (ctrlX, ctrlY) and the end point at (endX, endY).<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if **path** is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| float ctrlX | X-coordinate of the control point, in physical pixels (px). |
| float ctrlY | Y-coordinate of the control point, in physical pixels (px). |
| float endX | X-coordinate of the end point, in physical pixels (px). |
| float endY | Y-coordinate of the end point, in physical pixels (px). |
| float weight | Weight of the curve, which determines the shape of the curve. A larger value brings the curve closer to the control point.<br>If the value is less than or equal to 0, it is equivalent to using [OH_Drawing_PathLineTo](#oh_drawing_pathlineto) to add a line segment to the end point.<br>If the value is 1, it is equivalent to [OH_Drawing_PathQuadTo](#oh_drawing_pathquadto). |

### OH_Drawing_PathCubicTo()

```c
void OH_Drawing_PathCubicTo(OH_Drawing_Path* path, float ctrlX1, float ctrlY1, float ctrlX2, float ctrlY2, float endX, float endY)
```

**Description**

Adds a cubic Bezier curve from the last point of the path to the target point.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if **path** is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to an **OH_Drawing_Path** object.|
| float ctrlX1 | X coordinate of the first control point, in physical pixels (px). |
| float ctrlY1 | Y coordinate of the first control point, in physical pixels (px). |
| float ctrlX2 | X coordinate of the second control point, in physical pixels (px). |
| float ctrlY2 | Y coordinate of the second control point, in physical pixels (px). |
| float endX | X coordinate of the target point, in physical pixels (px). |
| float endY | Y coordinate of the target point, in physical pixels (px). |

### OH_Drawing_PathRMoveTo()

```c
void OH_Drawing_PathRMoveTo(OH_Drawing_Path* path, float x, float y)
```

**Description**

Sets the start position relative to the last point of a path. If the path is empty, the start point (0, 0) is used.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| float x | Offset along the x-axis relative to the end point of the current path, in physical pixels (px). A positive value offsets toward the positive direction of the x-axis, and a negative value offsets toward the negative direction of the x-axis. |
| float y | Offset along the y-axis relative to the end point of the current path, in physical pixels (px). A positive value offsets toward the positive direction of the y-axis, and a negative value offsets toward the negative direction of the y-axis. |

### OH_Drawing_PathRLineTo()

```c
void OH_Drawing_PathRLineTo(OH_Drawing_Path* path, float x, float y)
```

**Description**

Draws a line segment from the last point of this path to a point relative to the last point. If the path is empty, the start point (0, 0) is used.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| float x | Offset of the target point relative to the end point of the current path along the x-axis, in physical pixels (px), used to specify the horizontal coordinate of the target point. |
| float y | Offset of the target point relative to the end point of the current path along the y-axis, in physical pixels (px), used to specify the vertical coordinate of the target point. |

### OH_Drawing_PathRQuadTo()

```c
void OH_Drawing_PathRQuadTo(OH_Drawing_Path* path, float ctrlX, float ctrlY, float endX, float endY)
```

**Description**

Draws a quadratic Bezier curve from the last point of this path to a point relative to the last point. If the path is empty, the start point (0, 0) is used.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| float ctrlX | Offset of the x-axis relative to the end point of the path, in physical pixels (px), used to specify the x-coordinate of the control point. |
| float ctrlY | Offset of the y-axis relative to the end point of the path, in physical pixels (px), used to specify the y-coordinate of the control point. |
| float endX | Offset of the x-axis relative to the end point of the path, in physical pixels (px), used to specify the x-coordinate of the target point. |
| float endY | Offset of the y-axis relative to the end point of the path, in physical pixels (px), used to specify the y-coordinate of the target point. |

### OH_Drawing_PathRConicTo()

```c
void OH_Drawing_PathRConicTo(OH_Drawing_Path* path, float ctrlX, float ctrlY, float endX, float endY, float weight)
```

**Description**

Adds a conic curve segment from the last point of the current path (or (0, 0) if the path is empty) to the target point using relative positions.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if **path** is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| float ctrlX | X-axis offset relative to the end point of the path, in physical pixels (px), used to specify the horizontal coordinate of the control point. |
| float ctrlY | Y-axis offset relative to the end point of the path, in physical pixels (px), used to specify the vertical coordinate of the control point. |
| float endX | X-axis offset relative to the end point of the path, in physical pixels (px), used to specify the horizontal coordinate of the target point. |
| float endY | Y-axis offset relative to the end point of the path, in physical pixels (px), used to specify the vertical coordinate of the target point. |
| float weight | Weight of the curve, which determines the shape of the curve. A larger value brings the curve closer to the control point.<br>If the value is less than or equal to 0, it is equivalent to using [OH_Drawing_PathRLineTo](#oh_drawing_pathrlineto) to add a line segment to the end point.<br>If the value is 1, it is equivalent to [OH_Drawing_PathRQuadTo](#oh_drawing_pathrquadto). |

### OH_Drawing_PathRCubicTo()

```c
void OH_Drawing_PathRCubicTo(OH_Drawing_Path* path, float ctrlX1, float ctrlY1, float ctrlX2, float ctrlY2, float endX, float endY)
```

**Description**

Adds a cubic Bezier curve from the end point of the current path (or (0, 0) if the path is empty) to the target point using relative positions.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if **path** is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| float ctrlX1 | Offset of the x-axis relative to the end point of the path, in physical pixels (px), used to specify the x-coordinate of the first control point. |
| float ctrlY1 | Offset of the y-axis relative to the end point of the path, in physical pixels (px), used to specify the y-coordinate of the first control point. |
| float ctrlX2 | Offset of the x-axis relative to the end point of the path, in physical pixels (px), used to specify the x-coordinate of the second control point. |
| float ctrlY2 | Offset of the y-axis relative to the end point of the path, in physical pixels (px), used to specify the y-coordinate of the second control point. |
| float endX | Offset of the x-axis relative to the end point of the path, in physical pixels (px), used to specify the x-coordinate of the target point. |
| float endY | Offset of the y-axis relative to the end point of the path, in physical pixels (px), used to specify the y-coordinate of the target point. |

### OH_Drawing_PathAddRect()

```c
void OH_Drawing_PathAddRect(OH_Drawing_Path* path, float left, float top, float right, float bottom, OH_Drawing_PathDirection pathDirection)
```

**Description**

Adds a rectangle to a path in the specified direction. The starting point of the rectangle outline is the upper-left corner of the rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if path is NULL.<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if pathDirection is outside the enum range.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| float left | X coordinate of the upper left corner of the rectangle, in physical pixels (px). |
| float top | Y coordinate of the upper left corner of the rectangle, in physical pixels (px). |
| float right | X coordinate of the lower right corner of the rectangle, in physical pixels (px). |
| float bottom | Y coordinate of the lower right corner of the rectangle, in physical pixels (px). |
| [OH_Drawing_PathDirection](#oh_drawing_pathdirection) pathDirection | Path adding direction [OH_Drawing_PathDirection](#oh_drawing_pathdirection), used to specify the drawing direction of the rectangle outline. |

### OH_Drawing_PathAddRectWithInitialCorner()

```c
void OH_Drawing_PathAddRectWithInitialCorner(OH_Drawing_Path* path, const OH_Drawing_Rect* rect, OH_Drawing_PathDirection pathDirection, uint32_t start)
```

**Description**

Adds a rectangle contour to a path in the specified direction.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **path** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **pathDirection** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) object.|
| [OH_Drawing_PathDirection](#oh_drawing_pathdirection) pathDirection | Path adding direction [OH_Drawing_PathDirection](#oh_drawing_pathdirection), used to specify the drawing direction of the rectangle outline. |
| uint32_t start | Position of the starting point, indicating from which corner of the rectangle the path starts to be drawn. The value ranges from 0 to 3, where 0: top-left corner, 1: top-right corner, 2: bottom-right corner, 3: bottom-left corner. |

### OH_Drawing_PathAddRoundRect()

```c
void OH_Drawing_PathAddRoundRect(OH_Drawing_Path* path, const OH_Drawing_RoundRect* roundRect, OH_Drawing_PathDirection pathDirection)
```

**Description**

Adds a rounded rectangle to a path in the specified direction. When the path direction is clockwise, the start point is at the intersection of the rounded rectangle's left boundary and its lower left corner. When the path direction is counterclockwise, the start point is at the intersection point between the left boundary and the upper left corner.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **path** or **roundRect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **pathDirection** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| const [OH_Drawing_RoundRect](capi-drawing-oh-drawing-roundrect.md)* roundRect | Pointer to the [OH_Drawing_RoundRect](capi-drawing-oh-drawing-roundrect.md) object.|
| [OH_Drawing_PathDirection](#oh_drawing_pathdirection) pathDirection | Direction in which the path is added, used to specify the drawing direction of the rounded rectangle outline. |

### OH_Drawing_PathAddOvalWithInitialPoint()

```c
void OH_Drawing_PathAddOvalWithInitialPoint(OH_Drawing_Path* path, const OH_Drawing_Rect* rect, uint32_t start, OH_Drawing_PathDirection pathDirection)
```

**Description**

Adds an oval to a path. **OH_Drawing_Rect** specifies the outer tangent rectangle of the oval, and **OH_Drawing_PathDirection** specifies whether the drawing is clockwise or counterclockwise.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **path** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **pathDirection** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) object, which serves as the bounding rectangle of the ellipse and defines its shape and size. |
| uint32_t start | Start point of the oval.|
| [OH_Drawing_PathDirection](#oh_drawing_pathdirection) pathDirection | Path adding direction [OH_Drawing_PathDirection](#oh_drawing_pathdirection), which specifies the drawing direction of the ellipse. |

### OH_Drawing_PathAddOval()

```c
void OH_Drawing_PathAddOval(OH_Drawing_Path* path, const OH_Drawing_Rect* rect, OH_Drawing_PathDirection pathDirection)
```

**Description**

Adds an oval to a path in the specified direction, where the rectangle object serves as the outer tangent rectangle of the oval.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either path or rect is NULL.<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if pathDirection is outside the enum range.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the rectangle object [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md), which serves as the bounding rectangle of the ellipse and defines its shape and size. |
| [OH_Drawing_PathDirection](#oh_drawing_pathdirection) pathDirection | Path adding direction [OH_Drawing_PathDirection](#oh_drawing_pathdirection), which specifies the drawing direction of the ellipse. |

### OH_Drawing_PathAddArc()

```c
void OH_Drawing_PathAddArc(OH_Drawing_Path* path, const OH_Drawing_Rect* rect, float startAngle, float sweepAngle)
```

**Description**

Adds an arc to a path as the start of a new contour. Starting from the start angle, the arc is added by the sweep angle. The added arc is part of the oval inscribed in the rectangle.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code.<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either path or rect is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) object, which serves as the bounding rectangle of the arc. Its inscribed ellipse is used to clip the arc. |
| float startAngle | Start angle of the arc, in degrees.|
| float sweepAngle | Sweep angle in degrees. A positive value sweeps clockwise, and a negative value sweeps counterclockwise. The actual sweep angle is the result of this input parameter modulo 360°. |

### OH_Drawing_PathAddPath()

```c
void OH_Drawing_PathAddPath(OH_Drawing_Path* path, const OH_Drawing_Path* src, const OH_Drawing_Matrix* matrix)
```

**Description**

Transforms the points in a **src** path by a matrix and adds the new one to the current path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **path** or **src** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the existing [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| const [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* src | Pointer to the source [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| const [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. A null pointer means an identity matrix.|

### OH_Drawing_PathAddPathWithMatrixAndMode()

```c
void OH_Drawing_PathAddPathWithMatrixAndMode(OH_Drawing_Path* path, const OH_Drawing_Path* src, const OH_Drawing_Matrix* matrix, OH_Drawing_PathAddMode pathAddMode)
```

**Description**

Transforms the points in a **src** path by a matrix and adds the new one to the current path with the specified adding mode.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **path** or **src** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **pathAddMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the existing [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| const [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* src | Pointer to the source [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| const [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. A null pointer means an identity matrix.|
| [OH_Drawing_PathAddMode](#oh_drawing_pathaddmode) pathAddMode | Path add mode. |

### OH_Drawing_PathAddPathWithMode()

```c
void OH_Drawing_PathAddPathWithMode(OH_Drawing_Path* path, const OH_Drawing_Path* src, OH_Drawing_PathAddMode pathAddMode)
```

**Description**

Adds a **src** path to the current path with the specified adding mode.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **path** or **src** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **pathAddMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the existing [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| const [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* src | Pointer to the source [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| [OH_Drawing_PathAddMode](#oh_drawing_pathaddmode) pathAddMode | Enumerates the path add modes. |

### OH_Drawing_PathAddPathWithOffsetAndMode()

```c
void OH_Drawing_PathAddPathWithOffsetAndMode(OH_Drawing_Path* path, const OH_Drawing_Path* src, float dx, float dy, OH_Drawing_PathAddMode pathAddMode)
```

**Description**

Translates a **src** path by an offset and adds the new one to the current path with the specified adding mode.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **path** or **src** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **pathAddMode** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the existing [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| const [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* src | Pointer to the source [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| float dx | Horizontal offset of the source path, in physical pixels (px). |
| float dy | Vertical offset of the source path, in physical pixels (px). |
| [OH_Drawing_PathAddMode](#oh_drawing_pathaddmode) pathAddMode | Path add mode. |

### OH_Drawing_PathAddPolygon()

```c
void OH_Drawing_PathAddPolygon(OH_Drawing_Path* path, const OH_Drawing_Point2D* points, uint32_t count, bool isClosed)
```

**Description**

Adds a polygon to a path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **path** or **points** is NULL or **count** is **0**, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the existing [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| const [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* points | Pointer to an array that holds the vertex coordinates of the polygon.|
| uint32_t count | Size of the polygon vertex coordinate array. The value must be greater than 0. |
| bool isClosed | Whether the path is closed. The value **true** means that the path is closed, and **false** means the opposite.|

### OH_Drawing_PathAddCircle()

```c
void OH_Drawing_PathAddCircle(OH_Drawing_Path* path, float x, float y, float radius, OH_Drawing_PathDirection pathDirection)
```

**Description**

Adds a circle to a path in the specified direction.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **radius** is less than or equal to 0, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.<br>If **pathDirection** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| float x | X-coordinate of the center of the circle, in physical pixels (px). |
| float y | Y-coordinate of the center of the circle, in physical pixels (px). |
| float radius | Radius of the circle, in physical pixels (px). |
| [OH_Drawing_PathDirection](#oh_drawing_pathdirection) pathDirection | Path direction [OH_Drawing_PathDirection](#oh_drawing_pathdirection), which specifies the drawing direction of the circle outline. |

### OH_Drawing_PathBuildFromSvgString()

```c
bool OH_Drawing_PathBuildFromSvgString(OH_Drawing_Path* path, const char* str)
```

**Description**

Parses the path represented by an SVG string.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **path** or **str** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| const char* str | Pointer to the SVG path data string, which must comply with the format requirements of the SVG path syntax. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns whether the SVG string is successfully parsed. **true** means successful; **false** otherwise.|

### OH_Drawing_PathConvertToSvgString()

```c
OH_Drawing_ErrorCode OH_Drawing_PathConvertToSvgString(const OH_Drawing_Path* path, char* str, size_t* strSize)
```

**Description**

Converts the path to an SVG path data string.

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| const [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object. |
| char* str | SVG string. The developer needs to allocate and release the corresponding memory. You can pass a null pointer to obtain the memory size of the SVG string. When used as an output parameter, it indicates the SVG string result after path conversion. |
| size_t* strSize | Memory size of the SVG string, in bytes. When used as an output parameter, it is used to obtain the actual memory size of the string. When used as an input parameter, it indicates the memory size allocated for str. |

**Return value**

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER if path or strSize is nullptr, or if strSize is too small. |

### OH_Drawing_PathContains()

```c
bool OH_Drawing_PathContains(OH_Drawing_Path* path, float x, float y)
```

**Description**

Checks whether the specified coordinate point is contained in the path. The determination rule refers to [OH_Drawing_PathFillType](#oh_drawing_pathfilltype).<br>This API generates an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if path is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| float x | X-axis coordinate of the point to be determined, in physical pixels (px). |
| float y | Y-axis coordinate of the point to be determined, in physical pixels (px). |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the coordinate point is included in the path; returns **false** otherwise.|

### OH_Drawing_PathTransform()

```c
void OH_Drawing_PathTransform(OH_Drawing_Path* path, const OH_Drawing_Matrix* matrix)
```

**Description**

Applies a matrix transformation to the path. The transformation result directly modifies the current path object.<br>This API generates an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either path or matrix is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| const [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the matrix object [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md), which specifies the matrix used to transform the path. If it is NULL, the identity matrix is used (the path is not transformed). |

### OH_Drawing_PathTransformWithPerspectiveClip()

```c
void OH_Drawing_PathTransformWithPerspectiveClip(OH_Drawing_Path* src, const OH_Drawing_Matrix* matrix, OH_Drawing_Path* dst, bool applyPerspectiveClip)
```

**Description**

Transforms the points in a path by matrix, and uses the new one to replace the **dst** path. If **dst** is NULL, the **src** path is replaced.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **src** or **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* src | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| const [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the matrix object [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md), which specifies the transformation matrix for applying a matrix transformation to the path. |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* dst | Pointer to the target [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| bool applyPerspectiveClip | Whether to apply perspective clipping to the transformed path. The value **true** means to apply perspective clipping to the matrix-transformed path and retain the clipped portion of the path; the value **false** means not to apply perspective clipping and retain the complete transformed path. |

### OH_Drawing_PathSetFillType()

```c
void OH_Drawing_PathSetFillType(OH_Drawing_Path* path, OH_Drawing_PathFillType pathFillType)
```

**Description**

Sets the fill type of the path, which determines how the interior region of the path is defined.<br>This API generates an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if path is NULL;<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if pathFillType is outside the enum range.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| [OH_Drawing_PathFillType](#oh_drawing_pathfilltype) pathFillType | Path fill type [OH_Drawing_PathFillType](#oh_drawing_pathfilltype), which determines how the interior of the path is defined, that is, the fill rule of the path. |

### OH_Drawing_PathGetFillType()

```c
OH_Drawing_ErrorCode OH_Drawing_PathGetFillType(OH_Drawing_Path* path, OH_Drawing_PathFillType* pathFillType)
```

**Description**

Obtains the fill type of a path.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| [OH_Drawing_PathFillType](#oh_drawing_pathfilltype)* pathFillType | Path fill type, which is used as an output parameter. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **path** or **pathFillType** is NULL.|

### OH_Drawing_PathGetLength()

```c
float OH_Drawing_PathGetLength(OH_Drawing_Path* path, bool forceClosed)
```

**Description**

Obtains the length of a path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| bool forceClosed | Whether the path is measured as a closed path. **true** means that the path is forcibly considered as a closed path; **false** means that the path is measured depending on whether it is a closed path.|

**Returns**

| Type| Description|
| -- | -- |
| float | Length of the current path, in physical pixels (px). |

### OH_Drawing_PathGetBounds()

```c
void OH_Drawing_PathGetBounds(OH_Drawing_Path* path, OH_Drawing_Rect* rect)
```

**Description**

Obtains the minimum bounds that enclose a path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **path** or **rect** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* rect | Pointer to the [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) object, which stores the path bounding box result and is used as an output parameter. |

### OH_Drawing_PathClose()

```c
void OH_Drawing_PathClose(OH_Drawing_Path* path)
```

**Description**

Draws a line segment from the current point to the start point of this path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|

### OH_Drawing_PathOffset()

```c
void OH_Drawing_PathOffset(OH_Drawing_Path* path, OH_Drawing_Path* dst, float dx, float dy)
```

**Description**

Translates a path by an offset along the X axis and Y axis and adds the new one to the **dst** path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the existing [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* dst | Pointer to a destination path, which is an [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object. If NULL is passed in, the result is stored in the current path.|
| float dx | Offset in the x-axis direction, in physical pixels (px). |
| float dy | Offset in the y-axis direction, in physical pixels (px). |

### OH_Drawing_PathReset()

```c
void OH_Drawing_PathReset(OH_Drawing_Path* path)
```

**Description**

Resets the path data.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to an **OH_Drawing_Path** object.|

### OH_Drawing_PathIsClosed()

```c
bool OH_Drawing_PathIsClosed(OH_Drawing_Path* path, bool forceClosed)
```

**Description**

Checks whether a path is closed.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **path** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| bool forceClosed | Whether the path is measured as a closed path. The value **true** means that the path is considered closed during measurement, and **false** means that the path is measured based on the actual closed status.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the path is closed; returns **false** otherwise.|

### OH_Drawing_PathGetPositionTangent()

```c
bool OH_Drawing_PathGetPositionTangent(OH_Drawing_Path* path, bool forceClosed, float distance, OH_Drawing_Point2D* position, OH_Drawing_Point2D* tangent)
```

**Description**

Obtains the coordinates and tangent at a distance from the start point of this path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If any of **path**, **position**, or **tangent** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| bool forceClosed | Whether the path is measured as a closed path. The value **true** means that the path is considered closed during measurement, and **false** means that the path is measured based on the actual closed status.|
| float distance | Distance from the start point, in physical pixels (px). A value less than 0 is treated as 0, and a value greater than the path length is treated as the path length. |
| [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* position | Pointer to the coordinate point at the specified distance from the start point of the path. It is used as an output parameter to store the calculated coordinate point result. |
| [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* tangent | Pointer to the tangent value at the specified distance from the start point of the path. It is used as an output parameter. tangent.x indicates the cosine value of the tangent at the point, and tangent.y indicates the sine value of the tangent at the point. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns whether the measurement is successful. **true** means successful; **false** otherwise.|

### OH_Drawing_PathGetSegment()

```c
OH_Drawing_ErrorCode OH_Drawing_PathGetSegment(OH_Drawing_Path* path, bool forceClosed, float start, float stop, bool startWithMoveTo, OH_Drawing_Path* dst, bool* result)
```

**Description**

Extracts a segment of a path and appends it to a destination path.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 18

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| bool forceClosed | Whether the path is measured as a closed path. The value **true** means that the path is considered closed during measurement, and **false** means that the path is measured based on the actual closed status.|
| float start | Distance from the start point of the path, in physical pixels (px). The position at the distance of start from the path start point is the start point of the extracted path segment. A value less than 0 is treated as 0, and a value greater than or equal to stop causes the extraction to fail. |
| float stop | Distance from the start point of the path, in physical pixels (px). The position at the distance of stop from the path start point is the end point of the extracted path segment. A value less than or equal to start causes the extraction to fail, and a value greater than the path length is treated as the path length. |
| bool startWithMoveTo | Whether to call [OH_Drawing_PathMoveTo](#oh_drawing_pathmoveto) on the target path to move to the start point of the extracted path segment. The value true means to call it, and false means not to call it. |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* dst | Pointer to a destination path, which is an [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object. If the extraction succeeds, the segment is appended to the path. If the extraction fails, nothing changes.|
| bool* result | Pointer to the extraction result. The value **true** means that the extraction is successful, and **false** means the opposite. It as an output parameter.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns one of the following result codes:<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if at least one of the **path**, **dst**, and **result** parameters is a null pointer.|

### OH_Drawing_PathOp()

```c
bool OH_Drawing_PathOp(OH_Drawing_Path* path, const OH_Drawing_Path* other, OH_Drawing_PathOpMode op)
```

**Description**

Merges two paths according to the specified path operation type.<br>This API generates an error code, which can be viewed through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either path or other is NULL;<br>Returns OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE if op is outside the enum range.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to an [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object, in which the resulting path is saved.|
| const [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* other | Pointer to the path object [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) that participates in the path operation and is combined with the current path according to the specified operation type. |
| [OH_Drawing_PathOpMode](#oh_drawing_pathopmode) op | Path operation enum type. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the resulting path is not empty; returns **false** otherwise.|

### OH_Drawing_PathGetMatrix()

```c
bool OH_Drawing_PathGetMatrix(OH_Drawing_Path* path, bool forceClosed, float distance, OH_Drawing_Matrix* matrix, OH_Drawing_PathMeasureMatrixFlags flag)
```

**Description**

Obtains a transformation matrix at a distance from the start point of this path.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If either **path** or **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **flag** is not set to one of the enumerated values, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| bool forceClosed | Whether the path is measured as a closed path. The value **true** means that the path is considered closed during measurement, and **false** means that the path is measured based on the actual closed status.|
| float distance | Distance from the start point, in physical pixels (px). A value less than 0 is treated as 0, and a value greater than the path length is treated as the path length. |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the transformation matrix to obtain. It is used as an output parameter to store the transformation matrix at the specified distance from the start point of the path. |
| [OH_Drawing_PathMeasureMatrixFlags](#oh_drawing_pathmeasurematrixflags) flag | Enum for the matrix information dimension. |

**Returns**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the transformation matrix is obtained successfully; returns **false** otherwise. The possible failure cause is that **path** is NULL or the path length is 0.|

### OH_Drawing_PathApproximate()

```c
OH_Drawing_ErrorCode OH_Drawing_PathApproximate(OH_Drawing_Path* path, float acceptableError, float* vals, uint32_t* count)
```

**Description**

Converts the existing path into an approximate path consisting of consecutive line segments.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| float acceptableError | Acceptable error of each line segment on the path, in physical pixels (px). The value cannot be less than 0.<br> 1. When acceptableError is 0, the curve path is subdivided extremely finely, which significantly increases performance and memory consumption. Setting the error value to 0 is not recommended.<br> 2. When acceptableError is far greater than the path size (that is, the error tolerance far exceeds the geometric range of the path), the path is simplified extremely, retaining only the key endpoints of the path, which may lose the original shape.<br> 3. For curves such as an ellipse, when acceptableError is far greater than the ellipse radius (that is, the error tolerance far exceeds the geometric range of the ellipse), the fitting result usually contains only the start and end points of the segmented Bézier curves of the ellipse, and the ellipse is simplified extremely into a polygon. |
| float* vals | An array of approximate points of the path.<br> Each point consists of three values, indicating:<br> 1. Length ratio of the point to the start point of the path.<br> 2. X coordinate of the point.<br> 3. Y coordinate of the point.|
| uint32_t* count | Pointer to the size of the returned array. The array size is at least 6. When vals is a null pointer, the size of the fitted point data array is returned. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **path** or **count** is a null pointer.<br> **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** if **acceptableError** is less than 0.|

### OH_Drawing_PathGetVerbData()

```c
OH_Drawing_ErrorCode OH_Drawing_PathGetVerbData(const OH_Drawing_Path* path, OH_Drawing_PathIteratorVerb* verbs, uint32_t* count)
```

**Description**

Obtains the verb data of a path. In a path primitive, the verb data describes the basic drawing actions during path construction.

The verb data exists in the form of an enum, where each value corresponds to a geometric operation type, for example:

- [OH_Drawing_PathMoveTo](#oh_drawing_pathmoveto): Moves the current drawing point to the specified coordinates without generating a line segment.

- [OH_Drawing_PathLineTo](#oh_drawing_pathlineto): Draws a straight line segment from the current point to the specified point.

- [OH_Drawing_PathQuadTo](#oh_drawing_pathquadto): Draws a quadratic Bézier curve from the current point to the specified point.

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| const [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object. |
| [OH_Drawing_PathIteratorVerb](capi-drawing-path-iterator-h.md#oh_drawing_pathiteratorverb)* verbs | Output parameter, which indicates the array of verb data of the path. The developer needs to allocate and release the corresponding memory. You can pass a null pointer to obtain the size of the verb data array, allocate memory based on the size, and then call this API again to obtain the complete data. |
| uint32_t* count | When used as an output parameter, indicates the size of the verb data array. When used as an input parameter, indicates the size of the memory allocated for **verbs**. |

**Return value**

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns **OH_DRAWING_SUCCESS** if the operation is successful.<br>Returns **OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **path** or **count** is null. |

### OH_Drawing_PathGetPointData()

```c
OH_Drawing_ErrorCode OH_Drawing_PathGetPointData(const OH_Drawing_Path* path, OH_Drawing_Point2D* points, uint32_t* count)
```

**Description**

Obtains the point data of a path.

In a path primitive, point data exists as a sequence of numeric values that correspond one-to-one with verb commands, and is used to precisely specify the geometric coordinate positions of drawing operations.

The main types of point data are as follows:

- Endpoint coordinates: used together with commands such as [OH_Drawing_PathMoveTo](#oh_drawing_pathmoveto) and [OH_Drawing_PathLineTo](#oh_drawing_pathlineto) to define the target position of a line segment or a move.

- Control point coordinates: used together with curve commands to define the shape of a Bézier curve (for example, a cubic Bézier curve requires two control points and one endpoint).

- Closing point: usually no coordinates are provided separately; the path start point is implicitly used by the [OH_Drawing_PathClose](#oh_drawing_pathclose) command.

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| const [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to an [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object. |
| [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* points | Used as an output parameter, indicating the array of point data of the path. The developer needs to allocate and release the corresponding memory. You can pass a null pointer to obtain the size of the point data array, allocate memory based on the size, and then call this API again to obtain the complete data. |
| uint32_t* count | When used as an output parameter, indicates the size of the point data array. When used as an input parameter, indicates the size of the memory allocated for points. |

**Return value**

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER if path or count is null. |

### OH_Drawing_PathGetConicWeightData()

```c
OH_Drawing_ErrorCode OH_Drawing_PathGetConicWeightData(const OH_Drawing_Path* path, float* conicWeights, uint32_t* count)
```

**Description**

Obtains the conic curve weight data of a path.

The conic curve weight data of a path is used to describe the weight information of conic curves in the path.

In a path primitive, conic curve data is represented in the form of a rational Bézier curve, where each control point carries a weight value. The weight is a geometric parameter of the curve definition and serves the following purposes:

- Shape control: A larger weight value brings the curve closer to the corresponding control point. A weight of 1 degenerates the curve into a standard Bézier curve. A weight of 0 makes the control point ineffective.

- Precise representation of conic curves: By combining weights with a quadratic Bézier curve, conic curve segments such as arcs, elliptical arcs, and parabolas can be represented precisely, without the need for piecewise approximation or dedicated elliptical arc commands.

- Data organization: Weights are usually stored in an array alongside the point data, corresponding to each control point in order, and are used together with the corresponding verb, such as [OH_Drawing_PathConicTo](#oh_drawing_pathconicto).

**Since**: 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| const [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to an [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object. |
| float* conicWeights | Output parameter, which indicates the array of conic curve weight data of the path. The developer needs to allocate and release the corresponding memory. You can pass a null pointer to obtain the size of the weight data array, allocate memory based on the size, and then call this API again to obtain the complete data. |
| uint32_t* count | When used as an output parameter, indicates the size of the conic curve weight data array. When used as an input parameter, indicates the size of the memory allocated for conicWeights. |

**Return value**

| Type | Description |
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER if path or count is null. |

### OH_Drawing_PathInterpolate()

```c
OH_Drawing_ErrorCode OH_Drawing_PathInterpolate(OH_Drawing_Path* path, OH_Drawing_Path* other, float weight, bool* success, OH_Drawing_Path* interpolatedPath)
```

**Description**

Interpolates between the current path and another path based on the given weights, and stores the result in the target path object.<br>The interpolation succeeds as long as the two paths have the same number of points. The target path is created based on the structure of the current path.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* other | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object of the other path used for interpolation.|
| float weight | Interpolation weight. The value range is [0, 1].|
| bool* success | Whether the interpolation is successful. **true** means yes; **false** otherwise. It as an output parameter.|
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* interpolatedPath | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object used to store the interpolation result, which is used as an output parameter. |

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **path**, **other**, **success**, or **interpolatedPath** is a null pointer.<br> **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** if **weight** is not in the range of [0, 1].|

### OH_Drawing_PathIsInterpolate()

```c
OH_Drawing_ErrorCode OH_Drawing_PathIsInterpolate(OH_Drawing_Path* path, OH_Drawing_Path* other, bool* result)
```

**Description**

Checks whether the current path is completely identical to another path (other) in structure and operation order, to determine whether the two paths are compatible for interpolation. This API is used for pre-checking before calling [OH_Drawing_PathInterpolate](#oh_drawing_pathinterpolate).<br> If a path contains conic curve operations, the weight values of the corresponding operations must also be identical for the paths to be considered compatible for interpolation.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* other | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|
| bool* result | Checks whether a path is compatible with another path. It is used as an output parameter.<br> **true** if the paths are compatible, **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br> **OH_DRAWING_SUCCESS** if the operation is successful.<br> **OH_DRAWING_ERROR_INVALID_PARAMETER** if **path**, **other**, or **result** is a null pointer.|

### OH_Drawing_PathIsInverseFillType()

```c
OH_Drawing_ErrorCode OH_Drawing_PathIsInverseFillType(const OH_Drawing_Path* path, bool* isInverse)
```

**Description**

Checks whether the fill type of the path is the inverse type.

The inverse types are PATH_FILL_TYPE_INVERSE_WINDING and PATH_FILL_TYPE_INVERSE_EVEN_ODD in [OH_Drawing_PathFillType](#oh_drawing_pathfilltype).

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the path object [OH_Drawing_Path](capi-drawing-oh-drawing-path.md). |
| bool* isInverse | Whether the fill type is the inverse type. It is used as an output parameter. **true** if the fill type is the inverse type; **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **path** or **isInverse** is a null pointer.|

### OH_Drawing_PathToggleInverseFillType()

```c
OH_Drawing_ErrorCode OH_Drawing_PathToggleInverseFillType(OH_Drawing_Path* path)
```

**Description**

Toggles the inverse state of the path fill type, that is, flips between the inverse type and the non-inverse type.

The inverse types are PATH_FILL_TYPE_INVERSE_WINDING and PATH_FILL_TYPE_INVERSE_EVEN_ODD in [OH_Drawing_PathFillType](#oh_drawing_pathfilltype).

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Path](capi-drawing-oh-drawing-path.md)* path | Pointer to the [OH_Drawing_Path](capi-drawing-oh-drawing-path.md) object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Execution result.<br>**OH_DRAWING_SUCCESS** if the operation is successful.<br>**OH_DRAWING_ERROR_INCORRECT_PARAMETER** if **path** is a null pointer.|