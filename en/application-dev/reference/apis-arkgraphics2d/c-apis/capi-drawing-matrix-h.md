# drawing_matrix.h

## Overview

This file declares the functions related to the matrix in the drawing module.

**Library**: libnative_drawing.so

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 8

**Related module**: [Drawing](capi-drawing.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Drawing_ScaleToFit](#oh_drawing_scaletofit) | OH_Drawing_ScaleToFit | Defines an enum for the matrix scaling modes. |

### Function

| Name | Description |
| -- | -- |
| [OH_Drawing_Matrix* OH_Drawing_MatrixCreate(void)](#oh_drawing_matrixcreate) | Creates an **OH_Drawing_Matrix** object. |
| [OH_Drawing_Matrix* OH_Drawing_MatrixCopy(const OH_Drawing_Matrix* matrix)](#oh_drawing_matrixcopy) | Creates a copy of a matrix object. |
| [OH_Drawing_Matrix* OH_Drawing_MatrixCreateRotation(float deg, float x, float y)](#oh_drawing_matrixcreaterotation) | Creates an **OH_Drawing_Matrix** with the rotation attribute. The matrix is obtained by rotating an identity matrix by a given degree around the rotation point (x, y). |
| [OH_Drawing_Matrix* OH_Drawing_MatrixCreateScale(float sx, float sy, float px, float py)](#oh_drawing_matrixcreatescale) | Creates an **OH_Drawing_Matrix** with the scale attribute. The matrix is obtained by scaling an identity matrix with the factor (sx, sy) at the rotation point (px, py). |
| [OH_Drawing_Matrix* OH_Drawing_MatrixCreateTranslation(float dx, float dy)](#oh_drawing_matrixcreatetranslation) | Creates an **OH_Drawing_Matrix** with the translation attribute. The matrix is obtained by translating the identity matrix by the distance (dx, dy). |
| [void OH_Drawing_MatrixSetMatrix(OH_Drawing_Matrix* matrix, float scaleX, float skewX, float transX, float skewY, float scaleY, float transY, float persp0, float persp1, float persp2)](#oh_drawing_matrixsetmatrix) | Sets matrix parameters for an **OH_Drawing_Matrix** object. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **OH_Drawing_Matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [bool OH_Drawing_MatrixSetRectToRect(OH_Drawing_Matrix* matrix, const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, OH_Drawing_ScaleToFit stf)](#oh_drawing_matrixsetrecttorect) | Scales a matrix to map a source rectangle to a destination rectangle. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If any of **matrix**, **src**, and **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_MatrixPreRotate(OH_Drawing_Matrix* matrix, float degree, float px, float py)](#oh_drawing_matrixprerotate) | Premultiplies this matrix by a matrix that is derived from an identity matrix after it has been rotated by a given degree around the rotation point (px, py). This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_MatrixPreScale(OH_Drawing_Matrix* matrix, float sx, float sy, float px, float py)](#oh_drawing_matrixprescale) | Premultiplies a matrix by an identity matrix that scales with the factor (sx, sy) at the scale point (px, py). |
| [void OH_Drawing_MatrixPreTranslate(OH_Drawing_Matrix* matrix, float dx, float dy)](#oh_drawing_matrixpretranslate) | Premultiplies this matrix by a matrix that is derived from an identity matrix after it has been translated by a given distance (dx, dy). This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_MatrixPostRotate(OH_Drawing_Matrix* matrix, float degree, float px, float py)](#oh_drawing_matrixpostrotate) | Post multiplies this matrix by a matrix that is derived from an identity matrix after it has been rotated by a given degree around the rotation point (px, py). This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_MatrixPostScale(OH_Drawing_Matrix* matrix, float sx, float sy, float px, float py)](#oh_drawing_matrixpostscale) | Post multiplies a matrix by an identity matrix that scales with the factor (sx, sy) at the scale point (px, py). This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_MatrixPostTranslate(OH_Drawing_Matrix* matrix, float dx, float dy)](#oh_drawing_matrixposttranslate) | Post multiplies this matrix by a matrix that is derived from an identity matrix after it has been translated by a given distance (dx, dy). This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_MatrixReset(OH_Drawing_Matrix* matrix)](#oh_drawing_matrixreset) | Resets a matrix to an identity matrix. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_MatrixConcat(OH_Drawing_Matrix* total, const OH_Drawing_Matrix* a, const OH_Drawing_Matrix* b)](#oh_drawing_matrixconcat) | Multiplies two matrices to produce a new matrix. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If any of **total**, **a**, and **b** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_MatrixGetAll(OH_Drawing_Matrix* matrix, float value[9])](#oh_drawing_matrixgetall) | Obtains all element values of a matrix. |
| [OH_Drawing_ErrorCode OH_Drawing_MatrixPreConcat(OH_Drawing_Matrix* a, OH_Drawing_Matrix* b)](#oh_drawing_matrixpreconcat) | Left-multiplies matrix a by matrix b. |
| [float OH_Drawing_MatrixGetValue(OH_Drawing_Matrix* matrix, int index)](#oh_drawing_matrixgetvalue) | Obtains a matrix value of a given index, which ranges from 0 to 8. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **index** is less than 0 or greater than 8, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [void OH_Drawing_MatrixRotate(OH_Drawing_Matrix* matrix, float degree, float px, float py)](#oh_drawing_matrixrotate) | Sets this matrix as an identity matrix and rotates it by a given degree around the rotation point (px, py). This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_MatrixTranslate(OH_Drawing_Matrix* matrix, float dx, float dy)](#oh_drawing_matrixtranslate) | Sets a matrix as an identity matrix and translates it by a given distance (dx, dy). This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [void OH_Drawing_MatrixScale(OH_Drawing_Matrix* matrix, float sx, float sy, float px, float py)](#oh_drawing_matrixscale) | Sets a matrix as an identity matrix and scales it with the factor (sx, sy) at the rotation point (px, py). This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [bool OH_Drawing_MatrixInvert(OH_Drawing_Matrix* matrix, OH_Drawing_Matrix* inverse)](#oh_drawing_matrixinvert) | Inverts a matrix and returns the result. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **matrix** or **inverse** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [bool OH_Drawing_MatrixSetPolyToPoly(OH_Drawing_Matrix* matrix, const OH_Drawing_Point2D* src, const OH_Drawing_Point2D* dst, uint32_t count)](#oh_drawing_matrixsetpolytopoly) | Generates a transformation matrix by setting source points and destination points. Both the number of source points and that of destination points must be in the range [0, 4]. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **count** is less than 0 or greater than 4, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned. |
| [void OH_Drawing_MatrixMapPoints(const OH_Drawing_Matrix* matrix, const OH_Drawing_Point2D* src, OH_Drawing_Point2D* dst, int count)](#oh_drawing_matrixmappoints) | Maps a source point array to a destination point array by means of matrix transformation. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If any of **matrix**, **src**, and **dst** is NULL or **count** is less than or equal to 0, **<br>OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [bool OH_Drawing_MatrixMapRect(const OH_Drawing_Matrix* matrix, const OH_Drawing_Rect* src, OH_Drawing_Rect* dst)](#oh_drawing_matrixmaprect) | Maps a rectangle to the smallest rectangle that can enclose the vertices to which the four source vertices are mapped by means of matrix transformation. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If any of **matrix**, **src**, and **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [bool OH_Drawing_MatrixIsEqual(OH_Drawing_Matrix* matrix, OH_Drawing_Matrix* other)](#oh_drawing_matrixisequal) | Checks whether two **OH_Drawing_Matrix** objects are equal. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **matrix** or **other** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [bool OH_Drawing_MatrixIsIdentity(OH_Drawing_Matrix* matrix)](#oh_drawing_matrixisidentity) | Checks whether an **OH_Drawing_Matrix** object is an identity matrix. An identity matrix is as follows: \| 1 0 0 \|\| 0 1 0 \|\| 0 0 1 \|. This API may return an error code. For details, see [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) . If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. |
| [OH_Drawing_ErrorCode OH_Drawing_MatrixIsAffine(const OH_Drawing_Matrix* matrix, bool* isAffine)](#oh_drawing_matrixisaffine) | Checks whether the existing matrix is an affine matrix, which includes transformations such as translation, rotation, and scaling. |
| [OH_Drawing_ErrorCode OH_Drawing_MatrixPreSkew(OH_Drawing_Matrix* matrix, float kx, float ky, float px, float py)](#oh_drawing_matrixpreskew) | Left multiplies the current matrix by a matrix constructed based on (px, py) and (kx, ky). |
| [OH_Drawing_ErrorCode OH_Drawing_MatrixRectStaysRect(const OH_Drawing_Matrix* matrix, bool* isRectStaysRect)](#oh_drawing_matrixrectstaysrect) | Checks whether the rectangle remains rectangular after being mapped by the current matrix. This condition is met when the matrix is an identity matrix or contains only affine transformations such as translation, scaling, and rotation by 90 degrees. |
| [OH_Drawing_ErrorCode OH_Drawing_MatrixSetSinCos(OH_Drawing_Matrix* matrix, float sinValue, float cosValue, float px, float py)](#oh_drawing_matrixsetsincos) | Sets the matrix to rotate around the rotation center (px, py) with the specified sine and cosine values. |
| [void OH_Drawing_MatrixDestroy(OH_Drawing_Matrix* matrix)](#oh_drawing_matrixdestroy) | Destroys an **OH_Drawing_Matrix** object and reclaims the memory occupied by the object. |

## Enum type description

### OH_Drawing_ScaleToFit

```c
enum OH_Drawing_ScaleToFit
```

**Description**

Defines an enum for the matrix scaling modes.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

| Enum item | Description |
| -- | -- |
| SCALE_TO_FIT_FILL | Scales the source rectangle both horizontally and vertically to exactly match the destination rectangle. |
| SCALE_TO_FIT_START | Scales the source rectangle and aligns it to the left and top edges of the destination rectangle. |
| SCALE_TO_FIT_CENTER | Scales the source rectangle and aligns it to the center of the destination rectangle. |
| SCALE_TO_FIT_END | Scales the source rectangle and aligns it to the right and bottom edges of the destination rectangle. |


## Function description

### OH_Drawing_MatrixCreate()

```c
OH_Drawing_Matrix* OH_Drawing_MatrixCreate(void)
```

**Description**

Creates an **OH_Drawing_Matrix** object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Matrix* | Returns the pointer to the <b>OH_Drawing_Matrix</b> object created. |

### OH_Drawing_MatrixCopy()

```c
OH_Drawing_Matrix* OH_Drawing_MatrixCopy(const OH_Drawing_Matrix* matrix)
```

**Description**

Creates a copy of a matrix object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object to be copied. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Matrix* | Returns the pointer to the <b>OH_Drawing_Matrix</b> object created. |

### OH_Drawing_MatrixCreateRotation()

```c
OH_Drawing_Matrix* OH_Drawing_MatrixCreateRotation(float deg, float x, float y)
```

**Description**

Creates an **OH_Drawing_Matrix** with the rotation attribute. The matrix is obtained by rotating an identity matrix by a given degree around the rotation point (x, y).

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| float deg | Angle to rotate, in degrees. A positive value indicates a clockwise rotation, and a negative value indicates a counterclockwise rotation. |
| float x | Coordinate point on the X axis. |
| float y | Coordinate point on the Y axis. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Matrix* | Returns the pointer to the <b>OH_Drawing_Matrix</b> object created. |

### OH_Drawing_MatrixCreateScale()

```c
OH_Drawing_Matrix* OH_Drawing_MatrixCreateScale(float sx, float sy, float px, float py)
```

**Description**

Creates an **OH_Drawing_Matrix** with the scale attribute. The matrix is obtained by scaling an identity matrix with the factor (sx, sy) at the rotation point (px, py).

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| float sx | Scale factor on the X axis. If a negative number is passed in, the matrix is mirrored around y = px before being scaled. The value is a floating point number. |
| float sy | Scale factor on the Y axis. If a negative number is passed in, the matrix is mirrored around x = py before being scaled. The value is a floating point number. |
| float px | Coordinate point on the X axis. |
| float py | Coordinate point on the Y axis. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Matrix* | Returns the pointer to the <b>OH_Drawing_Matrix</b> object created. |

### OH_Drawing_MatrixCreateTranslation()

```c
OH_Drawing_Matrix* OH_Drawing_MatrixCreateTranslation(float dx, float dy)
```

**Description**

Creates an **OH_Drawing_Matrix** with the translation attribute. The matrix is obtained by translating the identity matrix by the distance (dx, dy).

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| float dx | Distance to translate on the X axis. A positive number indicates a translation towards the positive direction of the X axis, and a negative number indicates a translation towards the negative direction of the X axis. The value is a floating point number. |
| float dy | Distance to translate on the Y axis. A positive number indicates a translation towards the positive direction of the Y axis, and a negative number indicates a translation towards the negative direction of the Y axis. The value is a floating point number. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_Matrix* | Returns the pointer to the <b>OH_Drawing_Matrix</b> object created. |

### OH_Drawing_MatrixSetMatrix()

```c
void OH_Drawing_MatrixSetMatrix(OH_Drawing_Matrix* matrix, float scaleX, float skewX, float transX, float skewY, float scaleY, float transY, float persp0, float persp1, float persp2)
```

**Description**

Sets matrix parameters for an **OH_Drawing_Matrix** object. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **OH_Drawing_Matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to an **OH_Drawing_Matrix** object. |
| float scaleX | Scale factor on the X axis. |
| float skewX | Skew factor on the X axis. |
| float transX | Translation coefficient on the X axis. |
| float skewY | Skew factor on the Y axis. |
| float scaleY | Scale factor on the Y axis. |
| float transY | Translation coefficient on the Y axis. |
| float persp0 | Perspective coefficient of the X axis. |
| float persp1 | Perspective coefficient of the Y axis. |
| float persp2 | Perspective scale coefficient. |

### OH_Drawing_MatrixSetRectToRect()

```c
bool OH_Drawing_MatrixSetRectToRect(OH_Drawing_Matrix* matrix, const OH_Drawing_Rect* src, const OH_Drawing_Rect* dst, OH_Drawing_ScaleToFit stf)
```

**Description**

Scales a matrix to map a source rectangle to a destination rectangle. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If any of **matrix**, **src**, and **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| const OH_Drawing_Rect* src | Pointer to the [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) object of the mapping source. |
| const OH_Drawing_Rect* dst | Pointer to the [OH_Drawing_Rect](capi-drawing-oh-drawing-rect.md) object of the mapping destination. |
| [OH_Drawing_ScaleToFit](capi-drawing-matrix-h.md#oh_drawing_scaletofit) stf | Scaling mode. For details about the available options, see [OH_Drawing_ScaleToFit](capi-drawing-matrix-h.md#oh_drawing_scaletofit). |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if dst is empty, and sets matrix to:  \| 0 0 0 \|  \| 0 0 0 \|  \| 0 0 1 \| |

### OH_Drawing_MatrixPreRotate()

```c
void OH_Drawing_MatrixPreRotate(OH_Drawing_Matrix* matrix, float degree, float px, float py)
```

**Description**

Premultiplies this matrix by a matrix that is derived from an identity matrix after it has been rotated by a given degree around the rotation point (px, py). This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| float degree | Angle to rotate, in degrees. A positive value indicates a clockwise rotation, and a negative value indicates a counterclockwise rotation. |
| float px | X coordinate of the rotation point. |
| float py | Y coordinate of the rotation point. |

### OH_Drawing_MatrixPreScale()

```c
void OH_Drawing_MatrixPreScale(OH_Drawing_Matrix* matrix, float sx, float sy, float px, float py)
```

**Description**

Premultiplies a matrix by an identity matrix that scales with the factor (sx, sy) at the scale point (px, py).

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| float sx | Scale factor on the X axis. If a negative number is passed in, the matrix is mirrored around y = px before being scaled. The value is a floating point number. |
| float sy | Scale factor on the Y axis. If a negative number is passed in, the matrix is mirrored around x = py before being scaled. The value is a floating point number. |
| float px | X coordinate of the scale point. |
| float py | Y coordinate of the scale point. |

### OH_Drawing_MatrixPreTranslate()

```c
void OH_Drawing_MatrixPreTranslate(OH_Drawing_Matrix* matrix, float dx, float dy)
```

**Description**

Premultiplies this matrix by a matrix that is derived from an identity matrix after it has been translated by a given distance (dx, dy). This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| float dx | Horizontal distance to translate. A positive number indicates a translation towards the positive direction of the X axis, and a negative number indicates a translation towards the negative direction of the X axis. The value is a floating point number. |
| float dy | Vertical distance to translate. A positive number indicates a translation towards the positive direction of the Y axis, and a negative number indicates a translation towards the negative direction of the Y axis. The value is a floating point number. |

### OH_Drawing_MatrixPostRotate()

```c
void OH_Drawing_MatrixPostRotate(OH_Drawing_Matrix* matrix, float degree, float px, float py)
```

**Description**

Post multiplies this matrix by a matrix that is derived from an identity matrix after it has been rotated by a given degree around the rotation point (px, py). This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| float degree | Angle to rotate, in degrees. A positive value indicates a clockwise rotation, and a negative value indicates a counterclockwise rotation. |
| float px | X coordinate of the rotation point. |
| float py | Y coordinate of the rotation point. |

### OH_Drawing_MatrixPostScale()

```c
void OH_Drawing_MatrixPostScale(OH_Drawing_Matrix* matrix, float sx, float sy, float px, float py)
```

**Description**

Post multiplies a matrix by an identity matrix that scales with the factor (sx, sy) at the scale point (px, py). This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| float sx | Scale factor on the X axis. If a negative number is passed in, the matrix is mirrored around y = px before being scaled. The value is a floating point number. |
| float sy | Scale factor on the Y axis. If a negative number is passed in, the matrix is mirrored around x = py before being scaled. The value is a floating point number. |
| float px | X coordinate of the scale point. |
| float py | Y coordinate of the scale point. |

### OH_Drawing_MatrixPostTranslate()

```c
void OH_Drawing_MatrixPostTranslate(OH_Drawing_Matrix* matrix, float dx, float dy)
```

**Description**

Post multiplies this matrix by a matrix that is derived from an identity matrix after it has been translated by a given distance (dx, dy). This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| float dx | Horizontal distance to translate. A positive number indicates a translation towards the positive direction of the X axis, and a negative number indicates a translation towards the negative direction of the X axis. The value is a floating point number. |
| float dy | Vertical distance to translate. A positive number indicates a translation towards the positive direction of the Y axis, and a negative number indicates a translation towards the negative direction of the Y axis. The value is a floating point number. |

### OH_Drawing_MatrixReset()

```c
void OH_Drawing_MatrixReset(OH_Drawing_Matrix* matrix)
```

**Description**

Resets a matrix to an identity matrix. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |

### OH_Drawing_MatrixConcat()

```c
void OH_Drawing_MatrixConcat(OH_Drawing_Matrix* total, const OH_Drawing_Matrix* a, const OH_Drawing_Matrix* b)
```

**Description**

Multiplies two matrices to produce a new matrix. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If any of **total**, **a**, and **b** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* total | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| const OH_Drawing_Matrix* a | Pointer to [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object a. |
| const OH_Drawing_Matrix* b | Pointer to [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object b. |

### OH_Drawing_MatrixGetAll()

```c
OH_Drawing_ErrorCode OH_Drawing_MatrixGetAll(OH_Drawing_Matrix* matrix, float value[9])
```

**Description**

Obtains all element values of a matrix.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| float value[9] | Array used to store the obtained element values. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the error code.  Returns [OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode) if the operation is successful.  Returns [OH_DRAWING_ERROR_INVALID_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) if matrix or value is nullptr. |

### OH_Drawing_MatrixPreConcat()

```c
OH_Drawing_ErrorCode OH_Drawing_MatrixPreConcat(OH_Drawing_Matrix* a, OH_Drawing_Matrix* b)
```

**Description**

Left-multiplies matrix a by matrix b.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* a | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| OH_Drawing_Matrix* b | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the error code.  Returns [OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode) if the operation is successful.  Returns [OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) if a or b is nullptr. |

### OH_Drawing_MatrixGetValue()

```c
float OH_Drawing_MatrixGetValue(OH_Drawing_Matrix* matrix, int index)
```

**Description**

Obtains a matrix value of a given index, which ranges from 0 to 8. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **index** is less than 0 or greater than 8, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| int index | Index, which ranges from 0 to 8. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns value corresponding to index.Returns 0 if out of range. |

### OH_Drawing_MatrixRotate()

```c
void OH_Drawing_MatrixRotate(OH_Drawing_Matrix* matrix, float degree, float px, float py)
```

**Description**

Sets this matrix as an identity matrix and rotates it by a given degree around the rotation point (px, py). This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| float degree | Angle to rotate, in degrees. A positive value indicates a clockwise rotation, and a negative value indicates a counterclockwise rotation. |
| float px | Coordinate point on the X axis. |
| float py | Coordinate point on the Y axis. |

### OH_Drawing_MatrixTranslate()

```c
void OH_Drawing_MatrixTranslate(OH_Drawing_Matrix* matrix, float dx, float dy)
```

**Description**

Sets a matrix as an identity matrix and translates it by a given distance (dx, dy). This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| float dx | Distance to translate on the X axis. A positive number indicates a translation towards the positive direction of the X axis, and a negative number indicates a translation towards the negative direction of the X axis. The value is a floating point number. |
| float dy | Distance to translate on the Y axis. A positive number indicates a translation towards the positive direction of the Y axis, and a negative number indicates a translation towards the negative direction of the Y axis. The value is a floating point number. |

### OH_Drawing_MatrixScale()

```c
void OH_Drawing_MatrixScale(OH_Drawing_Matrix* matrix, float sx, float sy, float px, float py)
```

**Description**

Sets a matrix as an identity matrix and scales it with the factor (sx, sy) at the rotation point (px, py). This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| float sx | Scale factor on the X axis. If a negative number is passed in, the matrix is mirrored around y = px before being scaled. The value is a floating point number. |
| float sy | Scale factor on the Y axis. If a negative number is passed in, the matrix is mirrored around x = py before being scaled. The value is a floating point number. |
| float px | Coordinate point on the X axis. |
| float py | Coordinate point on the Y axis. |

### OH_Drawing_MatrixInvert()

```c
bool OH_Drawing_MatrixInvert(OH_Drawing_Matrix* matrix, OH_Drawing_Matrix* inverse)
```

**Description**

Inverts a matrix and returns the result. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **matrix** or **inverse** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| OH_Drawing_Matrix* inverse | Pointer to the inverse [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. You can call [OH_Drawing_MatrixCreate](capi-drawing-matrix-h.md#oh_drawing_matrixcreate) to create an inverse matrix object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the matrix is not nullptr and can be inverted;  returns false if the matrix is nullptr or cannot be inverted. |

### OH_Drawing_MatrixSetPolyToPoly()

```c
bool OH_Drawing_MatrixSetPolyToPoly(OH_Drawing_Matrix* matrix, const OH_Drawing_Point2D* src, const OH_Drawing_Point2D* dst, uint32_t count)
```

**Description**

Generates a transformation matrix by setting source points and destination points. Both the number of source points and that of destination points must be in the range [0, 4]. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned. If **count** is less than 0 or greater than 4, **OH_DRAWING_ERROR_PARAMETER_OUT_OF_RANGE** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| const OH_Drawing_Point2D* src | Array of source points. If NULL is passed in, **count** must be 0. |
| const OH_Drawing_Point2D* dst | Array of destination points. The number of destination points must be the same as that of source points. If NULL is passed in, **count** must be 0. |
| uint32_t count | Number of source points or destination points. If 0 is passed in, the matrix is set to an identity matrix. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if matrix is constructed successfully. |

### OH_Drawing_MatrixMapPoints()

```c
void OH_Drawing_MatrixMapPoints(const OH_Drawing_Matrix* matrix, const OH_Drawing_Point2D* src, OH_Drawing_Point2D* dst, int count)
```

**Description**

Maps a source point array to a destination point array by means of matrix transformation. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If any of **matrix**, **src**, and **dst** is NULL or **count** is less than or equal to 0, **<br>OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| const OH_Drawing_Point2D* src | Array of source points. |
| OH_Drawing_Point2D* dst | Array of destination points. The number of destination points must be the same as that of source points. |
| int count | Number of source points or destination points. |

### OH_Drawing_MatrixMapRect()

```c
bool OH_Drawing_MatrixMapRect(const OH_Drawing_Matrix* matrix, const OH_Drawing_Rect* src, OH_Drawing_Rect* dst)
```

**Description**

Maps a rectangle to the smallest rectangle that can enclose the vertices to which the four source vertices are mapped by means of matrix transformation. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If any of **matrix**, **src**, and **dst** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| const OH_Drawing_Rect* src | Source rectangle. |
| OH_Drawing_Rect* dst | Destination rectangle. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the mapped src is equal to the dst; returns false is not equal. |

### OH_Drawing_MatrixIsEqual()

```c
bool OH_Drawing_MatrixIsEqual(OH_Drawing_Matrix* matrix, OH_Drawing_Matrix* other)
```

**Description**

Checks whether two **OH_Drawing_Matrix** objects are equal. This API may return an error code. For details, call [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget). If either **matrix** or **other** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to one [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| OH_Drawing_Matrix* other | Pointer to the other [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if the two matrices are equal; returns false if not equal. |

### OH_Drawing_MatrixIsIdentity()

```c
bool OH_Drawing_MatrixIsIdentity(OH_Drawing_Matrix* matrix)
```

**Description**

Checks whether an **OH_Drawing_Matrix** object is an identity matrix. An identity matrix is as follows: \| 1 0 0 \|\| 0 1 0 \|\| 0 0 1 \|. This API may return an error code. For details, see [OH_Drawing_ErrorCodeGet](capi-drawing-error-code-h.md#oh_drawing_errorcodeget) . If **matrix** is NULL, **OH_DRAWING_ERROR_INVALID_PARAMETER** is returned.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns true if matrix is identity; returns false if not identity. |

### OH_Drawing_MatrixIsAffine()

```c
OH_Drawing_ErrorCode OH_Drawing_MatrixIsAffine(const OH_Drawing_Matrix* matrix, bool* isAffine)
```

**Description**

Checks whether the existing matrix is an affine matrix, which includes transformations such as translation, rotation, and scaling.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| bool* isAffine | Whether the existing matrix is an affine matrix. It is used as an output parameter. **true** means yes; **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the error code.  Returns [OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode) if the operation is successful.  Returns [OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) if matrix or isAffine is nullptr. |

### OH_Drawing_MatrixPreSkew()

```c
OH_Drawing_ErrorCode OH_Drawing_MatrixPreSkew(OH_Drawing_Matrix* matrix, float kx, float ky, float px, float py)
```

**Description**

Left multiplies the current matrix by a matrix constructed based on (px, py) and (kx, ky).

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| float kx | Tilt on the X axis. |
| float ky | Tilt on the Y axis. |
| float px | X-coordinate of the tilt center. |
| float py | Y-coordinate of the tilt center. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the error code.  Returns [OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode) if the operation is successful.  Returns [OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) if matrix is nullptr. |

### OH_Drawing_MatrixRectStaysRect()

```c
OH_Drawing_ErrorCode OH_Drawing_MatrixRectStaysRect(const OH_Drawing_Matrix* matrix, bool* isRectStaysRect)
```

**Description**

Checks whether the rectangle remains rectangular after being mapped by the current matrix. This condition is met when the matrix is an identity matrix or contains only affine transformations such as translation, scaling, and rotation by 90 degrees.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| const OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| bool* isRectStaysRect | Whether a rectangle stays a rectangle after being mapped by a matrix. It is used as an output parameter. **true** means yes; **false** otherwise. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the error code.  Returns [OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode) if the operation is successful.  Returns [OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) if matrix or isRectStaysRect is nullptr. |

### OH_Drawing_MatrixSetSinCos()

```c
OH_Drawing_ErrorCode OH_Drawing_MatrixSetSinCos(OH_Drawing_Matrix* matrix, float sinValue, float cosValue, float px, float py)
```

**Description**

Sets the matrix to rotate around the rotation center (px, py) with the specified sine and cosine values.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to the [OH_Drawing_Matrix](capi-drawing-oh-drawing-matrix.md) object. |
| float sinValue | Sine value of the rotation angle. |
| float cosValue | Cosine value of the rotation angle. |
| float px | X-axis coordinate of the rotation center. |
| float py | Y-axis coordinate of the rotation center. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Drawing_ErrorCode | Returns the error code.  Returns [OH_DRAWING_SUCCESS](capi-drawing-error-code-h.md#oh_drawing_errorcode) if the operation is successful.  Returns [OH_DRAWING_ERROR_INCORRECT_PARAMETER](capi-drawing-error-code-h.md#oh_drawing_errorcode) if matrix is nullptr. |

### OH_Drawing_MatrixDestroy()

```c
void OH_Drawing_MatrixDestroy(OH_Drawing_Matrix* matrix)
```

**Description**

Destroys an **OH_Drawing_Matrix** object and reclaims the memory occupied by the object.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeDrawing

**Since**: 11

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_Drawing_Matrix* matrix | Pointer to an **OH_Drawing_Matrix** object. |


