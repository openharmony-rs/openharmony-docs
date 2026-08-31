# drawing_matrix.h

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphic-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=4fbb151d5d06197ab5bea36827f51c1d37a38ef1 translatedAt=2026-08-24T08:39:44.120Z pushedAt=2026-08-31T08:43:28.699Z -->

## Overview

The file defines functions for creating, copying, transforming (rotating, scaling, translating, and skewing), querying (determining equality, determining whether it is an identity matrix, and obtaining element values), and mapping matrices.<br>This module uses a single-thread model, and the caller must manage thread safety and context state switching.

<!--RP1-->

**Sample**: [NDKAPIDrawing (API Version 20)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkGraphics2D/Drawing/NDKAPIDrawing)<!--RP1End-->

**File to include:** \<native_drawing/drawing_matrix.h\>

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_Drawing_ScaleToFit](#oh_drawing_scaletofit) | OH_Drawing_ScaleToFit | Defines an enum for the matrix scaling modes.|

### Functions

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix* OH_Drawing_MatrixCreate(void)](#oh_drawing_matrixcreate) | Creates a matrix object. After the matrix object created by this function is used, you must call [OH_Drawing_MatrixDestroy](capi-drawing-matrix-h.md#oh_drawing_matrixdestroy) to release the memory occupied by the object. Otherwise, a memory leak occurs. |
| [OH_Drawing_Matrix* OH_Drawing_MatrixCopy(const OH_Drawing_Matrix* matrix)](#oh_drawing_matrixcopy) | Creates a copy of a matrix object. The object returned by this function is a new independent matrix object. After it is used, you must call [OH_Drawing_MatrixDestroy](capi-drawing-matrix-h.md#oh_drawing_matrixdestroy) to release the memory occupied by the copy separately. Otherwise, a memory leak occurs. |
| [OH_Drawing_Matrix* OH_Drawing_MatrixCreateRotation(float deg, float x, float y)](#oh_drawing_matrixcreaterotation) | Creates a matrix object with a rotation attribute.<br>The matrix object is the matrix obtained by rotating the identity matrix by degrees around the rotation center (x, y). After the matrix object created by this function is used, you must call [OH_Drawing_MatrixDestroy](capi-drawing-matrix-h.md#oh_drawing_matrixdestroy) to release the memory occupied by the object. Otherwise, a memory leak occurs. |
| [OH_Drawing_Matrix* OH_Drawing_MatrixCreateScale(float sx, float sy, float px, float py)](#oh_drawing_matrixcreatescale) | Creates a matrix object with a scale attribute.<br>The matrix object is the matrix obtained by scaling the identity matrix with sx and sy as the scale factors around the scale center (px, py). After the matrix object created by this function is used, you must call [OH_Drawing_MatrixDestroy](#oh_drawing_matrixdestroy) to release the memory occupied by the object. |
| [OH_Drawing_Matrix* OH_Drawing_MatrixCreateTranslation(float dx, float dy)](#oh_drawing_matrixcreatetranslation) | Creates a matrix object with a translation attribute.<br>The matrix object is the matrix obtained by translating the identity matrix by (dx, dy). After the matrix object created by this function is used, you must call [OH_Drawing_MatrixDestroy](capi-drawing-matrix-h.md#oh_drawing_matrixdestroy) to release the memory occupied by the object. Otherwise, a memory leak occurs. |
| [void OH_Drawing_MatrixSetMatrix(OH_Drawing_Matrix* matrix, float scaleX, float skewX, float transX, float skewY, float scaleY, float transY, float persp0, float persp1, float persp2)](#oh_drawing_matrixsetmatrix) | Sets the transformation parameters for a matrix object, including scale, skew, translation, and perspective coefficients.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when OH_Drawing_Matrix is NULL. |
| [bool OH_Drawing_MatrixSetRectToRect(OH_Drawing_Matrix* matrix, const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, OH_Drawing_ScaleToFit stf)](#oh_drawing_matrixsetrecttorect) | Fits the matrix to the target rectangle in a scale mode.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when any of matrix, src, or dst is NULL. |
| [void OH_Drawing_MatrixPreRotate(OH_Drawing_Matrix* matrix, float degree, float px, float py)](#oh_drawing_matrixprerotate) | Sets the matrix to the matrix obtained by left multiplying the matrix by the identity matrix rotated by degree around the rotation center.<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when matrix is NULL. |
| [void OH_Drawing_MatrixPreScale(OH_Drawing_Matrix* matrix, float sx, float sy, float px, float py)](#oh_drawing_matrixprescale) | Sets the matrix to the matrix obtained by left multiplying the matrix by the identity matrix scaled with sx and sy as the scale factors around the scale center.<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when matrix is NULL. |
| [void OH_Drawing_MatrixPreTranslate(OH_Drawing_Matrix* matrix, float dx, float dy)](#oh_drawing_matrixpretranslate) | Sets the matrix to the matrix obtained by left multiplying the matrix by the identity matrix translated by dx and dy.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when matrix is NULL. |
| [void OH_Drawing_MatrixPostRotate(OH_Drawing_Matrix* matrix, float degree, float px, float py)](#oh_drawing_matrixpostrotate) | Sets the matrix to the matrix obtained by right multiplying the matrix by the identity matrix rotated by degree around the rotation center.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when matrix is NULL. |
| [void OH_Drawing_MatrixPostScale(OH_Drawing_Matrix* matrix, float sx, float sy, float px, float py)](#oh_drawing_matrixpostscale) | Sets the matrix to the matrix obtained by right multiplying the matrix by the identity matrix scaled with sx and sy as the scale factors around the scale center.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when matrix is NULL. |
| [void OH_Drawing_MatrixPostTranslate(OH_Drawing_Matrix* matrix, float dx, float dy)](#oh_drawing_matrixposttranslate) | Sets the matrix to the matrix obtained by right multiplying the matrix by the identity matrix translated by dx and dy.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when matrix is NULL. |
| [void OH_Drawing_MatrixReset(OH_Drawing_Matrix* matrix)](#oh_drawing_matrixreset) | Resets the current matrix to the identity matrix.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when matrix is NULL. |
| [void OH_Drawing_MatrixConcat(OH_Drawing_Matrix* total, const OH_Drawing_Matrix* a, const OH_Drawing_Matrix* b)](#oh_drawing_matrixconcat) | Sets the matrix total to the product of matrix a and matrix b.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when any of total, a, or b is NULL. |
| [OH_Drawing_ErrorCode OH_Drawing_MatrixGetAll(OH_Drawing_Matrix* matrix, float value[9])](#oh_drawing_matrixgetall) | Obtains all element values of the matrix. The nine elements are stored in row-major order, corresponding to a 3x3 matrix structure. For the specific arrangement, see [OH_Drawing_MatrixSetMatrix](#oh_drawing_matrixsetmatrix). |
| [float OH_Drawing_MatrixGetValue(OH_Drawing_Matrix* matrix, int index)](#oh_drawing_matrixgetvalue) | Obtains a matrix value of a given index, which ranges from 0 to 8.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **index** is less than 0 or greater than 8, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.|
| [void OH_Drawing_MatrixRotate(OH_Drawing_Matrix* matrix, float degree, float px, float py)](#oh_drawing_matrixrotate) | Sets the matrix to the identity matrix and rotates it around the rotation center at (px, py).<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when matrix is NULL. |
| [void OH_Drawing_MatrixTranslate(OH_Drawing_Matrix* matrix, float dx, float dy)](#oh_drawing_matrixtranslate) | Sets a matrix as an identity matrix and translates it by a given distance (dx, dy).<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.|
| [void OH_Drawing_MatrixScale(OH_Drawing_Matrix* matrix, float sx, float sy, float px, float py)](#oh_drawing_matrixscale) | Sets the matrix to the identity matrix and scales it with sx and sy around the scale center at (px, py).<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when matrix is NULL. |
| [bool OH_Drawing_MatrixInvert(OH_Drawing_Matrix* matrix, OH_Drawing_Matrix* inverse)](#oh_drawing_matrixinvert) | Sets the matrix inverse to the inverse matrix of the matrix and returns the result.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when either matrix or inverse is NULL. |
| [bool OH_Drawing_MatrixSetPolyToPoly(OH_Drawing_Matrix* matrix, const OH_Drawing_Point2D* src, const OH_Drawing_Point2D* dst, uint32_t count)](#oh_drawing_matrixsetpolytopoly) | Generates the corresponding transformation matrix by setting the source points and target points.<br>The number of source points and target points must be greater than or equal to 0 and less than or equal to 4. This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when matrix is NULL;<br>OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE is returned when count is less than 0 or greater than 4. |
| [void OH_Drawing_MatrixMapPoints(const OH_Drawing_Matrix* matrix, const OH_Drawing_Point2D* src, OH_Drawing_Point2D* dst, int count)](#oh_drawing_matrixmappoints) | Maps the source point array to the target point array through matrix transformation.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when any of matrix, src, or dst is NULL, or when count is less than or equal to 0. |
| [bool OH_Drawing_MatrixMapRect(const OH_Drawing_Matrix* matrix, const OH_Drawing_Rect* src, OH_Drawing_Rect* dst)](#oh_drawing_matrixmaprect) | Sets the target rectangle to a new rectangle, which is the smallest rectangle that can enclose the new vertices formed by mapping the four vertices of the source rectangle through matrix transformation.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when any of matrix, src, or dst is NULL. |
| [bool OH_Drawing_MatrixIsEqual(OH_Drawing_Matrix* matrix, OH_Drawing_Matrix* other)](#oh_drawing_matrixisequal) | Checks whether two matrices are equal.<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when either matrix or other is NULL. |
| [bool OH_Drawing_MatrixIsIdentity(OH_Drawing_Matrix* matrix)](#oh_drawing_matrixisidentity) | Checks whether the matrix is an identity matrix. The identity matrix is `[1 0 0; 0 1 0; 0 0 1]`.<br>To check whether two matrices are equal, use [OH_Drawing_MatrixIsEqual](#oh_drawing_matrixisequal).<br>This API generates an error code, which can be obtained through [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when matrix is NULL. |
| [void OH_Drawing_MatrixDestroy(OH_Drawing_Matrix* matrix)](#oh_drawing_matrixdestroy) | Destroys a matrix object and reclaims the memory occupied by the object. |
| [OH_Drawing_ErrorCode OH_Drawing_MatrixPreConcat(OH_Drawing_Matrix* a, OH_Drawing_Matrix* b)](#oh_drawing_matrixpreconcat) | Left multiplies matrix a by matrix b. This is similar to [OH_Drawing_MatrixConcat](#oh_drawing_matrixconcat), except that OH_Drawing_MatrixConcat stores the result in a separate total matrix, while this method directly modifies matrix a. |
| [OH_Drawing_ErrorCode OH_Drawing_MatrixIsAffine(const OH_Drawing_Matrix* matrix, bool* isAffine)](#oh_drawing_matrixisaffine) | Checks whether the existing matrix is an affine matrix, which includes transformations such as translation, rotation, and scaling.|
| [OH_Drawing_ErrorCode OH_Drawing_MatrixPreSkew(OH_Drawing_Matrix* matrix, float kx, float ky, float px, float py)](#oh_drawing_matrixpreskew) | Left multiplies the current matrix by a matrix constructed by skewing with (kx, ky) around the center (px, py). This belongs to the same Pre series of methods as [OH_Drawing_MatrixPreRotate](#oh_drawing_matrixprerotate), [OH_Drawing_MatrixPreScale](#oh_drawing_matrixprescale), and [OH_Drawing_MatrixPreTranslate](#oh_drawing_matrixpretranslate). |
| [OH_Drawing_ErrorCode OH_Drawing_MatrixRectStaysRect(const OH_Drawing_Matrix* matrix, bool* isRectStaysRect)](#oh_drawing_matrixrectstaysrect) | Checks whether a rectangle remains a rectangle after being mapped by the current matrix. This condition is satisfied when the matrix is an identity matrix or contains only affine transformations such as translation, scaling, and rotation by multiples of 90 degrees. |
| [OH_Drawing_ErrorCode OH_Drawing_MatrixSetSinCos(OH_Drawing_Matrix* matrix, float sinValue, float cosValue, float px, float py)](#oh_drawing_matrixsetsincos) | Sets the matrix to rotate around the rotation center (px, py) with the specified sine and cosine values. This is similar to [OH_Drawing_MatrixRotate](#oh_drawing_matrixrotate), except that OH_Drawing_MatrixRotate directly passes an angle value, while this method passes sine and cosine values. |

## Enum Description

### OH_Drawing_ScaleToFit

```c
enum OH_Drawing_ScaleToFit
```

**Description**

Defines an enum for the matrix scaling modes.

**Since**: 12

| Enum| Description|
| -- | -- |
| SCALE_TO_FIT_FILL | Scales along the horizontal and vertical axes to fill the target rectangle without preserving the aspect ratio of the source rectangle. |
| SCALE_TO_FIT_START | Scales the source rectangle and aligns it to the left and top edges of the destination rectangle.|
| SCALE_TO_FIT_CENTER | Scales the source rectangle and aligns it to the center of the destination rectangle.|
| SCALE_TO_FIT_END | Scales the source rectangle and aligns it to the right and bottom edges of the destination rectangle.|

## Function Description

### OH_Drawing_MatrixCreate()

```c
OH_Drawing_Matrix* OH_Drawing_MatrixCreate(void)
```

**Description**

Creates a matrix object. After using the matrix object created by this function, you must call [OH_Drawing_MatrixDestroy](capi-drawing-matrix-h.md#oh_drawing_matrixdestroy) to release the memory occupied by the object. Otherwise, a memory leak occurs.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* | Pointer to the created matrix object [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md). |

### OH_Drawing_MatrixCopy()

```c
OH_Drawing_Matrix* OH_Drawing_MatrixCopy(const OH_Drawing_Matrix* matrix)
```

**Description**

Creates a copy of a matrix object. The object returned by this function is a new independent matrix object. After using it, you must call [OH_Drawing_MatrixDestroy](capi-drawing-matrix-h.md#oh_drawing_matrixdestroy) to release the memory occupied by the copy separately. Otherwise, a memory leak occurs.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| const [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object to be copied.|

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* | The function returns a pointer that points to the newly created matrix object [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md). |

### OH_Drawing_MatrixCreateRotation()

```c
OH_Drawing_Matrix* OH_Drawing_MatrixCreateRotation(float deg, float x, float y)
```

**Description**

Creates a matrix object with rotation attributes.<br>The matrix object is obtained by rotating the identity matrix around the rotation center (x, y) by a specified number of degrees. After using the matrix object created by this function, you must call [OH_Drawing_MatrixDestroy](capi-drawing-matrix-h.md#oh_drawing_matrixdestroy) to release the memory occupied by the object. Otherwise, a memory leak occurs.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| float deg | Rotation angle, in degrees. A positive value indicates clockwise rotation, and a negative value indicates counterclockwise rotation. |
| float x | X-coordinate of the rotation center, in physical pixels (px). |
| float y | Y-coordinate of the rotation center, in physical pixels (px). |

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* | Returns a pointer to the created [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|

### OH_Drawing_MatrixCreateScale()

```c
OH_Drawing_Matrix* OH_Drawing_MatrixCreateScale(float sx, float sy, float px, float py)
```

**Description**

Creates a matrix object with scale attributes.<br>The matrix object is obtained by scaling the identity matrix around the scale center (px, py) with sx and sy as the scale factors. After using the matrix object created by this function, you must call [OH_Drawing_MatrixDestroy](#oh_drawing_matrixdestroy) to release the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| float sx | Horizontal scale factor. A negative value indicates that the object is mirrored about x = px before scaling. |
| float sy | Vertical scale factor. A negative value indicates that the object is mirrored about y = py before scaling. |
| float px | X-coordinate of the scale center, in physical pixels (px). |
| float py | Y-coordinate of the scale center, in physical pixels (px). |

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* | Returns a pointer to the created [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|

### OH_Drawing_MatrixCreateTranslation()

```c
OH_Drawing_Matrix* OH_Drawing_MatrixCreateTranslation(float dx, float dy)
```

**Description**

Creates a matrix object with translation attributes.<br>The matrix object is obtained by translating the identity matrix by (dx, dy). After using the matrix object created by this function, you must call [OH_Drawing_MatrixDestroy](capi-drawing-matrix-h.md#oh_drawing_matrixdestroy) to release the memory occupied by the object. Otherwise, a memory leak occurs.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| float dx | Horizontal translation distance, in physical pixels (px). A positive value translates in the positive direction of the x-axis, and a negative value translates in the negative direction of the x-axis. |
| float dy | Vertical translation distance, in physical pixels (px). A positive value translates in the positive direction of the y-axis, and a negative value translates in the negative direction of the y-axis. |

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* | Returns a pointer to the created [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|

### OH_Drawing_MatrixSetMatrix()

```c
void OH_Drawing_MatrixSetMatrix(OH_Drawing_Matrix* matrix, float scaleX, float skewX, float transX, float skewY, float scaleY, float transY, float persp0, float persp1, float persp2)
```

**Description**

Sets transformation parameters for a matrix object, including scale, skew, translation, and perspective coefficients.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code.<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when OH_Drawing_Matrix is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

The nine parameters are arranged in rows to correspond to a 3x3 matrix structure:

```text
scaleX  skewX   transX
skewY   scaleY  transY
persp0  persp1  persp2
```

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to an **OH_Drawing_Matrix** object.|
| float scaleX | Horizontal scale factor. |
| float skewX | Skew factor on the X axis.|
| float transX | Translation coefficient on the X axis.|
| float skewY | Skew factor on the Y axis.|
| float scaleY | Vertical scale factor. |
| float transY | Translation coefficient on the Y axis.|
| float persp0 | Perspective coefficient of the x-axis. |
| float persp1 | Perspective coefficient of the y-axis. |
| float persp2 | Perspective scale coefficient.|

### OH_Drawing_MatrixSetRectToRect()

```c
bool OH_Drawing_MatrixSetRectToRect(OH_Drawing_Matrix* matrix, const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, OH_Drawing_ScaleToFit stf)
```

**Description**

Adapts the matrix to the target rectangle in scale mode.<br>This API generates an error code. You can call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) to obtain the error code.<br>OH_DRAWING_ERROR_INVALID_PARAMETER is returned when any of matrix, src, or dst is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* src | Pointer to the source rectangle object, which is an [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) object. |
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* dst | Pointer to the destination rectangle object, which is an [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) object. |
| [OH_Drawing_ScaleToFit](capi-drawing-matrix-h.md#oh_drawing_scaletofit) stf | Scale mode. For details, see [OH_Drawing_ScaleToFit](#oh_drawing_scaletofit). |

**Return value**

| Type| Description|
| -- | -- |
| bool | true if set successfully; false otherwise. Special cases:<br> If either the width or height of the source rectangle src is less than or equal to 0, false is returned and the matrix is set to the identity matrix;<br> If either the width or height of the target rectangle dst is less than or equal to 0, true is returned and the matrix is set to a matrix in which all values are 0 except the perspective scale coefficient, which is 1. |

### OH_Drawing_MatrixPreRotate()

```c
void OH_Drawing_MatrixPreRotate(OH_Drawing_Matrix* matrix, float degree, float px, float py)
```

**Description**

Premultiplies this matrix by a matrix that is derived from an identity matrix after it has been rotated by a given degree around the rotation point (px, py).<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| float degree | Angle to rotate, in degrees. A positive value indicates a clockwise rotation, and a negative value indicates a counterclockwise rotation.|
| float px | X-axis coordinate of the rotation center, in physical pixels (px). |
| float py | Y-axis coordinate of the rotation center, in physical pixels (px). |

### OH_Drawing_MatrixPreScale()

```c
void OH_Drawing_MatrixPreScale(OH_Drawing_Matrix* matrix, float sx, float sy, float px, float py)
```

**Description**

Premultiplies this matrix by a matrix that is derived from an identity matrix after it has been scaled by the factors (sx, sy) around the scale point (px, py).<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| float sx | Horizontal scale factor. A negative value indicates that the image is mirrored about x = px before scaling. |
| float sy | Vertical scale factor. A negative value indicates that the image is mirrored about y = py before scaling. |
| float px | X-coordinate of the scale center, in physical pixels (px). |
| float py | Y-coordinate of the scale center, in physical pixels (px). |

### OH_Drawing_MatrixPreTranslate()

```c
void OH_Drawing_MatrixPreTranslate(OH_Drawing_Matrix* matrix, float dx, float dy)
```

**Description**

Premultiplies this matrix by a matrix that is derived from an identity matrix after it has been translated by a given distance (dx, dy).<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| float dx | Horizontal translation distance, in physical pixels (px). A positive value translates in the positive direction of the x-axis, and a negative value translates in the negative direction of the x-axis. |
| float dy | Vertical translation distance, in physical pixels (px). A positive value translates in the positive direction of the y-axis, and a negative value translates in the negative direction of the y-axis. |

### OH_Drawing_MatrixPostRotate()

```c
void OH_Drawing_MatrixPostRotate(OH_Drawing_Matrix* matrix, float degree, float px, float py)
```

**Description**

Post multiplies this matrix by a matrix that is derived from an identity matrix after it has been rotated by a given degree around the rotation point (px, py).<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| float degree | Angle to rotate, in degrees. A positive value indicates a clockwise rotation, and a negative value indicates a counterclockwise rotation.|
| float px | X-coordinate of the rotation center, in physical pixels (px). |
| float py | Y-coordinate of the rotation center, in physical pixels (px). |

### OH_Drawing_MatrixPostScale()

```c
void OH_Drawing_MatrixPostScale(OH_Drawing_Matrix* matrix, float sx, float sy, float px, float py)
```

**Description**

Post multiplies this matrix by a matrix that is derived from an identity matrix after it has been scaled by the factors (sx, sy) around the scale point (px, py).<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| float sx | Horizontal scale factor. If the value is negative, the matrix is first mirrored about x = px and then scaled. |
| float sy | Vertical scale factor. If the value is negative, the matrix is first mirrored about y = py and then scaled. |
| float px | X-coordinate of the scale center, in physical pixels (px). |
| float py | Y-coordinate of the scale center, in physical pixels (px). |

### OH_Drawing_MatrixPostTranslate()

```c
void OH_Drawing_MatrixPostTranslate(OH_Drawing_Matrix* matrix, float dx, float dy)
```

**Description**

Post multiplies this matrix by a matrix that is derived from an identity matrix after it has been translated by a given distance (dx, dy).<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| float dx | Horizontal translation distance, in physical pixels (px). A positive value indicates translation in the positive direction of the x-axis, and a negative value indicates translation in the negative direction of the x-axis. |
| float dy | Vertical translation distance, in physical pixels (px). A positive value indicates translation in the positive direction of the y-axis, and a negative value indicates translation in the negative direction of the y-axis. |

### OH_Drawing_MatrixReset()

```c
void OH_Drawing_MatrixReset(OH_Drawing_Matrix* matrix)
```

**Description**

Resets a matrix to an identity matrix.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|

### OH_Drawing_MatrixConcat()

```c
void OH_Drawing_MatrixConcat(OH_Drawing_Matrix* total, const OH_Drawing_Matrix* a, const OH_Drawing_Matrix* b)
```

**Description**

Sets the matrix **total** to the product of matrix **a** and matrix **b**.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If any of **total**, **a**, or **b** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* total | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| const [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* a | Pointer to [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object a.|
| const [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* b | Pointer to [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object b.|

### OH_Drawing_MatrixGetAll()

```c
OH_Drawing_ErrorCode OH_Drawing_MatrixGetAll(OH_Drawing_Matrix* matrix, float value[9])
```

**Description**

Obtains all element values of a matrix. The nine elements are stored in row-major order, corresponding to a 3x3 matrix structure. For details about the arrangement, see [OH_Drawing_MatrixSetMatrix](#oh_drawing_matrixsetmatrix).

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| float value[9] | Array used to store the obtained matrix element values. The array length must be at least 9. The 9 elements are arranged in row order and correspond to scaleX, skewX, transX, skewY, scaleY, transY, persp0, persp1, and persp2 of the 3x3 matrix in sequence. |

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br> Returns OH_DRAWING_SUCCESS if all matrix element values are obtained successfully.<br> Returns OH_DRAWING_ERROR_INVALID_PARAMETER if matrix or value is NULL. |

### OH_Drawing_MatrixGetValue()

```c
float OH_Drawing_MatrixGetValue(OH_Drawing_Matrix* matrix, int index)
```

**Description**

Obtains a matrix value of a given index, which ranges from 0 to 8.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **index** is less than 0 or greater than 8, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| int index | Index, which ranges from 0 to 8.|

**Return value**

| Type| Description|
| -- | -- |
| float | Returns the matrix value.|

### OH_Drawing_MatrixRotate()

```c
void OH_Drawing_MatrixRotate(OH_Drawing_Matrix* matrix, float degree, float px, float py)
```

**Description**

Sets this matrix as an identity matrix and rotates it by a given degree around the rotation point (px, py).<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| float degree | Angle to rotate, in degrees. A positive value indicates a clockwise rotation, and a negative value indicates a counterclockwise rotation.|
| float px | X-axis coordinate of the rotation center, in physical pixels (px). |
| float py | Y-axis coordinate of the rotation center, in physical pixels (px). |

### OH_Drawing_MatrixTranslate()

```c
void OH_Drawing_MatrixTranslate(OH_Drawing_Matrix* matrix, float dx, float dy)
```

**Description**

Sets a matrix as an identity matrix and translates it by a given distance (dx, dy).<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| float dx | Horizontal translation distance, in physical pixels (px). A positive value indicates translation in the positive x-axis direction, and a negative value indicates translation in the negative x-axis direction. |
| float dy | Vertical translation distance, in physical pixels (px). A positive value indicates translation in the positive y-axis direction, and a negative value indicates translation in the negative y-axis direction. |

### OH_Drawing_MatrixScale()

```c
void OH_Drawing_MatrixScale(OH_Drawing_Matrix* matrix, float sx, float sy, float px, float py)
```

**Description**

Sets this matrix as an identity matrix and scales it with the factors (sx, sy) at the scale point (px, py).<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| float sx | Horizontal scale factor. If the value is negative, the matrix is first mirrored about x = px and then scaled. |
| float sy | Vertical scale factor. If the value is negative, the matrix is first mirrored about y = py and then scaled. |
| float px | X-coordinate of the scale center, in physical pixels (px). |
| float py | Y-coordinate of the scale center, in physical pixels (px). |

### OH_Drawing_MatrixInvert()

```c
bool OH_Drawing_MatrixInvert(OH_Drawing_Matrix* matrix, OH_Drawing_Matrix* inverse)
```

**Description**

Sets **inverse** to the inverse of the matrix and returns the result.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either **matrix** or **inverse** is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* inverse | Pointer to the inverse [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. You can call [OH_Drawing_MatrixCreate](capi-drawing-matrix-h.md#oh_drawing_matrixcreate) to create an inverse matrix object.|

**Return value**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the matrix is reversible and the passed-in **inverse** is inverted; returns **false** otherwise.|

### OH_Drawing_MatrixSetPolyToPoly()

```c
bool OH_Drawing_MatrixSetPolyToPoly(OH_Drawing_Matrix* matrix, const OH_Drawing_Point2D* src, const OH_Drawing_Point2D* dst, uint32_t count)
```

**Description**

Generates a transformation matrix by setting source points and destination points.<br>Both the number of source points and that of destination points must be in the range [0, 4]. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.<br>If **count** is less than 0 or greater than 4, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| const [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* src | Array of source points. If NULL is passed in, **count** must be 0.|
| const [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* dst | Array of destination points. The number of destination points must be the same as that of source points. If NULL is passed in, **count** must be 0.|
| uint32_t count | Number of source point arrays and destination point arrays. The value ranges from 0 to 4. If the value is 0, the matrix object is set to an identity matrix. |

**Return value**

| Type| Description|
| -- | -- |
| bool | Whether a corresponding matrix can be generated to complete the transformation. true indicates that the matrix is generated successfully, and false indicates that the corresponding matrix cannot be generated. |

### OH_Drawing_MatrixMapPoints()

```c
void OH_Drawing_MatrixMapPoints(const OH_Drawing_Matrix* matrix, const OH_Drawing_Point2D* src, OH_Drawing_Point2D* dst, int count)
```

**Description**

Maps a source point array to a destination point array by means of matrix transformation.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if any of **matrix**, **src**, or **dst** is NULL, or if **count** is less than or equal to 0.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the matrix object [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md). |
| const [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* src | Pointer to the source point array. The array length must be greater than or equal to count; otherwise, out-of-bounds access may occur. |
| [OH_Drawing_Point2D](capi-drawing-oh-drawing-point2d.md)* dst | Pointer to the destination point array. The array length must be greater than or equal to count; otherwise, out-of-bounds access may occur. |
| int count | Number of elements in the source point array and the destination point array. The value must be greater than 0. |

### OH_Drawing_MatrixMapRect()

```c
bool OH_Drawing_MatrixMapRect(const OH_Drawing_Matrix* matrix, const OH_Drawing_Rect* src, OH_Drawing_Rect* dst)
```

**Description**

Sets the destination rectangle to a new rectangle that is the smallest rectangle enclosing the new vertices to which the four source vertices are mapped by means of matrix transformation.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if any of **matrix**, **src**, or **dst** is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the matrix object [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md). |
| const [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* src | Pointer to the source rectangle [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md). |
| [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md)* dst | Pointer to the destination rectangle [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md), used to store the mapped result. |

**Return value**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the objects are equal; **false** otherwise.|

### OH_Drawing_MatrixIsEqual()

```c
bool OH_Drawing_MatrixIsEqual(OH_Drawing_Matrix* matrix, OH_Drawing_Matrix* other)
```

**Description**

Checks whether two matrices are equal.<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if either **matrix** or **other** is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to one [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* other | Pointer to the other [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the two matrices are equal; returns **false** otherwise.|

### OH_Drawing_MatrixIsIdentity()

```c
bool OH_Drawing_MatrixIsIdentity(OH_Drawing_Matrix* matrix)
```

**Description**

Checks whether a matrix is an identity matrix. An identity matrix is `[1 0 0; 0 1 0; 0 0 1]`.<br>To check whether two matrices are equal, use [OH_Drawing_MatrixIsEqual](#oh_drawing_matrixisequal).<br>This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget).<br>Returns OH_DRAWING_ERROR_INVALID_PARAMETER if **matrix** is NULL.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|

**Return value**

| Type| Description|
| -- | -- |
| bool | Returns **true** if the matrix is an identity matrix; returns **false** otherwise.|

### OH_Drawing_MatrixDestroy()

```c
void OH_Drawing_MatrixDestroy(OH_Drawing_Matrix* matrix)
```

**Description**

Destroys a matrix object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to an **OH_Drawing_Matrix** object.|

### OH_Drawing_MatrixPreConcat()

```c
OH_Drawing_ErrorCode OH_Drawing_MatrixPreConcat(OH_Drawing_Matrix* a, OH_Drawing_Matrix* b)
```

**Description**

Left-multiplies matrix a by matrix b. This is similar to [OH_Drawing_MatrixConcat](#oh_drawing_matrixconcat), except that OH_Drawing_MatrixConcat stores the result in a separate **total** matrix, whereas this method directly modifies matrix a.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* a | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object to be left-multiplied. After the left multiplication, this matrix is modified to the result of a × b. |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* b | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object used as the multiplier. |

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the left multiplication is successfully executed.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER if a or b is NULL. |

### OH_Drawing_MatrixIsAffine()

```c
OH_Drawing_ErrorCode OH_Drawing_MatrixIsAffine(const OH_Drawing_Matrix* matrix, bool* isAffine)
```

**Description**

Checks whether the existing matrix is an affine matrix, which includes transformations such as translation, rotation, and scaling.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| bool* isAffine | Whether the existing matrix is an affine matrix. It is used as an output parameter. **true** means yes; **false** otherwise.|

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Returns the execution result.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER if matrix or isAffine is NULL. |

### OH_Drawing_MatrixPreSkew()

```c
OH_Drawing_ErrorCode OH_Drawing_MatrixPreSkew(OH_Drawing_Matrix* matrix, float kx, float ky, float px, float py)
```

**Description**

Left-multiplies the current matrix by a matrix constructed by skewing around the center (px, py) with (kx, ky). This belongs to the same Pre series of methods as [OH_Drawing_MatrixPreRotate](#oh_drawing_matrixprerotate), [OH_Drawing_MatrixPreScale](#oh_drawing_matrixprescale), and [OH_Drawing_MatrixPreTranslate](#oh_drawing_matrixpretranslate).

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| float kx | Tilt on the X axis.|
| float ky | Tilt on the Y axis.|
| float px | X-coordinate of the skew center point, in physical pixels (px). |
| float py | Y-coordinate of the skew center point, in physical pixels (px). |

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER if matrix is a null pointer. |

### OH_Drawing_MatrixRectStaysRect()

```c
OH_Drawing_ErrorCode OH_Drawing_MatrixRectStaysRect(const OH_Drawing_Matrix* matrix, bool* isRectStaysRect)
```

**Description**

Checks whether a rectangle remains a rectangle after being mapped by the current matrix. This condition is satisfied when the matrix is an identity matrix or contains only affine transformations such as translation, scaling, and rotation by multiples of 90 degrees.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [const OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| bool* isRectStaysRect | Whether a rectangle stays a rectangle after being mapped by a matrix. It is used as an output parameter.<br>**true** means yes; **false** otherwise.|

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER if matrix or isRectStaysRect is NULL. |

### OH_Drawing_MatrixSetSinCos()

```c
OH_Drawing_ErrorCode OH_Drawing_MatrixSetSinCos(OH_Drawing_Matrix* matrix, float sinValue, float cosValue, float px, float py)
```

**Description**

Sets the matrix to rotate around the rotation center (px, py) by the specified sine and cosine values. This is similar to [OH_Drawing_MatrixRotate](#oh_drawing_matrixrotate), except that OH_Drawing_MatrixRotate directly takes an angle value, whereas this method takes sine and cosine values.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md)* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object.|
| float sinValue | Sine value of the rotation angle.|
| float cosValue | Cosine value of the rotation angle.|
| float px | X-axis coordinate of the rotation center.|
| float py | Y-axis coordinate of the rotation center.|

**Return value**

| Type| Description|
| -- | -- |
| [OH_Drawing_ErrorCode](capi-drawing-error-code-h.md#oh_drawing_errorcode) | Result code.<br>Returns OH_DRAWING_SUCCESS if the operation is successful.<br>Returns OH_DRAWING_ERROR_INCORRECT_PARAMETER if matrix is a null pointer. |