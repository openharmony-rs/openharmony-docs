# Matrix

Implements a matrix. A 3 x 3 matrix is shown as below.![matrix_3x3](../../../reference/apis-arkgraphics2d/figures/matrix3X3.PNG) Elements in the matrix from left to right and from top to bottom respectively represent a horizontal scale coefficient, a horizontal skew coefficient, a horizontal translation coefficient, a vertical skew coefficient, a vertical scale coefficient, a vertical translation coefficient, an X-axis perspective coefficient, a Y-axis perspective coefficient, and a perspective scale coefficient. If (x&lt;sub&gt;1&lt;/sub&gt;, y&lt;sub&gt;1&lt;/sub&gt;) is the source coordinate point, (x&lt;sub&gt;2&lt;/sub&gt;, y&lt;sub&gt;2&lt;/sub&gt;) is the coordinate point obtained by transforming the source coordinate point using the matrix, then the relationship between the two coordinate points is as follows:![matrix_xy](../../../reference/apis-arkgraphics2d/figures/matrix_xy.PNG)

> **NOTE:** 
> 
> - The initial APIs of this class are supported since API version 12.
> 
> - This module uses the physical pixel unit, px.
> 
> - The module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## constructor

```TypeScript
constructor()
```

Creates a **Matrix** object.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## constructor

```TypeScript
constructor(matrix: Matrix)
```

Copies a matrix.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| matrix | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | Yes | Matrix to be copied. |

## getAll

```TypeScript
getAll(): Array<number>
```

Obtains all element values of this matrix.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;number&gt; | Array of matrix values obtained. The length is 9. Each value is a floating point number. |

## getValue

```TypeScript
getValue(index: number): number
```

Obtains a matrix value of a given index, which ranges from 0 to 8.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index. The value is an integer ranging from 0 to 8. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Value obtained, which is an integer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## invert

```TypeScript
invert(matrix: Matrix): boolean
```

Inverts this matrix and returns the result.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| matrix | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | Yes | **Matrix** object used to store the inverted matrix. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** means that the matrix is revertible and the **matrix** object is set to its inverse, and **false** means that the matrix is not revertible and the **matrix** object remains unchanged. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## isAffine

```TypeScript
isAffine(): boolean
```

Checks whether the existing matrix is an affine matrix, which includes transformations such as translation, rotation, and scaling.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the existing matrix is an affine matrix. **true** means yes; **false** otherwise. |

## isEqual

```TypeScript
isEqual(matrix: Matrix): boolean
```

Checks whether two **OH_Drawing_Matrix** objects are equal.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| matrix | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | Yes | Matrix to compare. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Comparison result of the two matrices. The value **true** means that the two matrices are equal, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## isIdentity

```TypeScript
isIdentity(): boolean
```

Checks whether an **OH_Drawing_Matrix** object is an identity matrix:

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** means that the matrix is an identity matrix, and **false** means the opposite. |

## mapPoints

```TypeScript
mapPoints(src: Array<common2D.Point>): Array<common2D.Point>
```

Maps a source point array to a destination point array by means of matrix transformation.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | Array&lt;[common2D.Point](arkts-arkgraphics2d-common2d-point-i.md)&gt; | Yes | Array of source points. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[common2D.Point](arkts-arkgraphics2d-common2d-point-i.md)&gt; | Array of points obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## mapRadius

```TypeScript
mapRadius(radius: number): number
```

Returns the average radius of the ellipse formed after a circle with the specified **radius** is mapped by the existing matrix. The square of the average radius is the product of the major axis length and minor axis length of the ellipse. If the matrix contains perspective transformation, the result is meaningless.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | number | Yes | Radius of the circle used for calculation. The value is a floating point number. The absolute value is used if the number is negative. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Average radius after transformation. |

## mapRect

```TypeScript
mapRect(dst: common2D.Rect, src: common2D.Rect): boolean
```

Sets the destination rectangle to the bounding rectangle of the shape obtained after transforming the source rectangle with a matrix transformation. As shown in the figure below, the blue rectangle represents the source rectangle, and the yellow rectangle is the shape obtained after a matrix transformation is applied to the source rectangle. Since the edges of the yellow rectangle are not aligned with the coordinate axes, it cannot be represented by a rectangle object. To address this issue, a destination rectangle (black rectangle) is defined as the bounding rectangle.![mapRect](../../../reference/apis-arkgraphics2d/figures/zh-ch_matrix_mapRect.png)

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dst | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | **Rectangle** object, which is used to store the bounding rectangle. |
| src | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Source rectangle. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** means that the shape retains a rectangular form, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## postConcat

```TypeScript
postConcat(matrix: Matrix): void
```

Right-multiply the existing matrix by another matrix.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| matrix | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | Yes | Matrix used for calculation. |

## postRotate

```TypeScript
postRotate(degree: number, px: number, py: number): void
```

Post multiplies this matrix by a matrix that is derived from an identity matrix after it has been rotated by a given degree around the rotation point (px, py).

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| degree | number | Yes | Angle to rotate, in degrees. A positive number indicates a clockwise rotation, and a negative number indicates a counterclockwise rotation. The value is a floating point number. |
| px | number | Yes | X coordinate of the rotation point. The value is a floating point number. |
| py | number | Yes | Y coordinate of the rotation point. The value is a floating point number. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## postScale

```TypeScript
postScale(sx: number, sy: number, px: number, py: number): void
```

Post multiplies this matrix by a matrix that is derived from an identity matrix after it has been scaled with the coefficient (sx, sy) at the scale point (px, py).

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sx | number | Yes | Scale coefficient along the X axis. If a negative number is passed in, the matrix is mirrored around y = px before being scaled. The value is a floating point number. |
| sy | number | Yes | Scale coefficient along the Y axis. If a negative number is passed in, the matrix is mirrored around x = py before being scaled. The value is a floating point number. |
| px | number | Yes | X coordinate of the scale point. The value is a floating point number. |
| py | number | Yes | Y coordinate of the scale point. The value is a floating point number. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## postSkew

```TypeScript
postSkew(kx: number, ky: number, px: number, py: number): void
```

Right-multiply the existing matrix by a skew transformation matrix.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| kx | number | Yes | Amount of tilt on the X axis. The value is a floating point number. A positive number tilts the drawing rightwards along the positive direction of the Y axis, and a negative number tilts the drawing leftwards along the positive direction of the Y axis. |
| ky | number | Yes | Amount of tilt on the Y axis. The value is a floating point number. A positive number tilts the drawing downwards along the positive direction of the X axis, and a negative number tilts the drawing upwards along the positive direction of the X axis. |
| px | number | Yes | X coordinate of the shear center. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the center to the right of the coordinate origin, while a negative value places the center to the left. |
| py | number | Yes | Y coordinate of the shear center. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the center below the coordinate origin, while a negative value places the center above the coordinate origin. |

## postTranslate

```TypeScript
postTranslate(dx: number, dy: number): void
```

Post multiplies this matrix by a matrix that is derived from an identity matrix after it has been translated by a given distance (dx, dy).

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dx | number | Yes | Horizontal distance to translate. A positive number indicates a translation towards the positive direction of the X axis, and a negative number indicates a translation towards the negative direction of the X axis. The value is a floating point number. |
| dy | number | Yes | Vertical distance to translate. A positive number indicates a translation towards the positive direction of the Y axis, and a negative number indicates a translation towards the negative direction of the Y axis. The value is a floating point number. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## preConcat

```TypeScript
preConcat(matrix: Matrix): void
```

Preconcats the existing matrix with the passed-in matrix.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| matrix | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | Yes | **Matrix** object, which is on the right of a multiplication expression. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## preRotate

```TypeScript
preRotate(degree: number, px: number, py: number): void
```

Premultiplies this matrix by a matrix that is derived from an identity matrix after it has been rotated by a given degree around the rotation point (px, py).

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| degree | number | Yes | Angle to rotate, in degrees. A positive number indicates a clockwise rotation, and a negative number indicates a counterclockwise rotation. The value is a floating point number. |
| px | number | Yes | X coordinate of the rotation point. The value is a floating point number. |
| py | number | Yes | Y coordinate of the rotation point. The value is a floating point number. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## preScale

```TypeScript
preScale(sx: number, sy: number, px: number, py: number): void
```

Premultiplies this matrix by a matrix that is derived from an identity matrix after it has been scaled with the coefficient (sx, sy) at the scale point (px, py).

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sx | number | Yes | Scale coefficient along the X axis. If a negative number is passed in, the matrix is mirrored around y = px before being scaled. The value is a floating point number. |
| sy | number | Yes | Scale coefficient along the Y axis. If a negative number is passed in, the matrix is mirrored around x = py before being scaled. The value is a floating point number. |
| px | number | Yes | X coordinate of the scale point. The value is a floating point number. |
| py | number | Yes | Y coordinate of the scale point. The value is a floating point number. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## preSkew

```TypeScript
preSkew(kx: number, ky: number, px: number, py: number): void
```

Left-multiply the existing matrix by a skew transformation matrix.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| kx | number | Yes | Amount of tilt on the X axis. The value is a floating point number. A positive number tilts the drawing rightwards along the positive direction of the Y axis, and a negative number tilts the drawing leftwards along the positive direction of the Y axis. |
| ky | number | Yes | Amount of tilt on the Y axis. The value is a floating point number. A positive number tilts the drawing downwards along the positive direction of the X axis, and a negative number tilts the drawing upwards along the positive direction of the X axis. |
| px | number | Yes | X coordinate of the shear center. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the center to the right of the coordinate origin, while a negative value places the center to the left. |
| py | number | Yes | Y coordinate of the shear center. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the center below the coordinate origin, while a negative value places the center above the coordinate origin. |

## preTranslate

```TypeScript
preTranslate(dx: number, dy: number): void
```

Premultiplies this matrix by a matrix that is derived from an identity matrix after it has been translated by a given distance (dx, dy).

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dx | number | Yes | Horizontal distance to translate. A positive number indicates a translation towards the positive direction of the X axis, and a negative number indicates a translation towards the negative direction of the X axis. The value is a floating point number. |
| dy | number | Yes | Vertical distance to translate. A positive number indicates a translation towards the positive direction of the Y axis, and a negative number indicates a translation towards the negative direction of the Y axis. The value is a floating point number. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## rectStaysRect

```TypeScript
rectStaysRect(): boolean
```

Checks whether a rectangle stays a rectangle after being mapped by a matrix.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether a rectangle stays a rectangle after being mapped by a matrix. **true** means yes; false otherwise. |

## reset

```TypeScript
reset(): void
```

Resets this matrix to an identity matrix.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## setConcat

```TypeScript
setConcat(matrixA: Matrix, matrixB: Matrix): void
```

Updates the existing matrix with the product of two matrices.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| matrixA | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | Yes | Matrix A used for calculation. |
| matrixB | [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | Yes | Matrix B used for calculation. |

## setMatrix

```TypeScript
setMatrix(values: Array<number>): void
```

Sets parameters for this matrix.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| values | Array&lt;number&gt; | Yes | Floating-point array that holds the parameter values, with the array length set to 9. The values in the array respectively represent a horizontal scale coefficient, a horizontal skew coefficient, a horizontal translation coefficient, a vertical skew coefficient, a vertical scale coefficient, a vertical translation coefficient, an X-axis perspective coefficient, a Y-axis perspective coefficient, and a perspective scale coefficient, in ascending order of indexes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setMatrix

```TypeScript
setMatrix(matrix: Array<number> | Matrix): void
```

Updates the existing matrix with another matrix.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| matrix | Array&lt;number&gt; &#124; [Matrix](arkts-arkgraphics2d-drawing-matrix-c.md) | Yes | Array or matrix for the update. |

## setPolyToPoly

```TypeScript
setPolyToPoly(src: Array<common2D.Point>, dst: Array<common2D.Point>, count: number): boolean
```

Sets this matrix to a transformation matrix that maps the source point array to the destination point array. Both the number of source points and that of destination points must be in the range [0, 4].

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | Array&lt;[common2D.Point](arkts-arkgraphics2d-common2d-point-i.md)&gt; | Yes | Array of source points. The array length must be the same as the value of **count**. |
| dst | Array&lt;[common2D.Point](arkts-arkgraphics2d-common2d-point-i.md)&gt; | Yes | Array of destination points. The array length must be the same as the value of **count**. |
| count | number | Yes | Number of points in each array. The value is an integer. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** means that the setting is successful, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setRectToRect

```TypeScript
setRectToRect(src: common2D.Rect, dst: common2D.Rect, scaleToFit: ScaleToFit): boolean
```

Sets this matrix to a transformation matrix that maps a source rectangle to a destination rectangle.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Source rectangle. |
| dst | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Destination rectangle. |
| scaleToFit | [ScaleToFit](arkts-arkgraphics2d-drawing-scaletofit-e.md) | Yes | Mapping mode from the source rectangle to the target rectangle. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** means that the matrix can represent the mapping, and **false** means the opposite. If either the width or the height of the source rectangle is less than or equal to 0, the API returns **false** and sets the matrix to an identity matrix. If either the width or height of the destination rectangle is less than or equal to 0, the API returns **true** and sets the matrix to a matrix with all values **0**, except for a perspective scaling coefficient of **1**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## setRotation

```TypeScript
setRotation(degree: number, px: number, py: number): void
```

Sets this matrix as an identity matrix and rotates it by a given degree around the rotation point (px, py).

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| degree | number | Yes | Angle to rotate, in degrees. A positive number indicates a clockwise rotation, and a negative number indicates a counterclockwise rotation. The value is a floating point number. |
| px | number | Yes | X coordinate of the rotation point. The value is a floating point number. |
| py | number | Yes | Y coordinate of the rotation point. The value is a floating point number. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setScale

```TypeScript
setScale(sx: number, sy: number, px: number, py: number): void
```

Sets this matrix as an identity matrix and scales it with the coefficients (sx, sy) at the scale point (px, py).

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sx | number | Yes | Scale coefficient along the X axis. If a negative number is passed in, the matrix is mirrored around y = px before being scaled. The value is a floating point number. |
| sy | number | Yes | Scale coefficient along the Y axis. If a negative number is passed in, the matrix is mirrored around x = py before being scaled. The value is a floating point number. |
| px | number | Yes | X coordinate of the scale point. The value is a floating point number. |
| py | number | Yes | Y coordinate of the scale point. The value is a floating point number. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setSinCos

```TypeScript
setSinCos(sinValue: number, cosValue: number, px: number, py: number): void
```

Sets the matrix to rotate around the rotation center (px, py) with the specified sine and cosine values.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sinValue | number | Yes | Sine value of the rotation angle. Only if the sum of the squares of the sine and cosine values is **1**, the rotation transformation is performed. Otherwise, the matrix may contain other transformations such as translation and scaling. |
| cosValue | number | Yes | Cosine value of the rotation angle. Only if the sum of the squares of the sine and cosine values is **1**, the rotation transformation is performed. Otherwise, the matrix may contain other transformations such as translation and scaling. |
| px | number | Yes | X coordinate of the rotation center. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the center to the right of the coordinate origin, while a negative value places the center to the left. |
| py | number | Yes | Y coordinate of the rotation center. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the center below the coordinate origin, while a negative value places the center above the coordinate origin. |

## setSkew

```TypeScript
setSkew(kx: number, ky: number, px: number, py: number): void
```

Sets the skew coefficients of a matrix.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| kx | number | Yes | Amount of tilt on the X axis. The value is a floating point number. A positive number tilts the drawing rightwards along the positive direction of the Y axis, and a negative number tilts the drawing leftwards along the positive direction of the Y axis. |
| ky | number | Yes | Amount of tilt on the Y axis. The value is a floating point number. A positive number tilts the drawing downwards along the positive direction of the X axis, and a negative number tilts the drawing upwards along the positive direction of the X axis. |
| px | number | Yes | X coordinate of the shear center. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the center to the right of the coordinate origin, while a negative value places the center to the left. |
| py | number | Yes | Y coordinate of the shear center. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the center below the coordinate origin, while a negative value places the center above the coordinate origin. |

## setTranslation

```TypeScript
setTranslation(dx: number, dy: number): void
```

Sets this matrix as an identity matrix and translates it by a given distance (dx, dy).

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dx | number | Yes | Horizontal distance to translate. A positive number indicates a translation towards the positive direction of the X axis, and a negative number indicates a translation towards the negative direction of the X axis. The value is a floating point number. |
| dy | number | Yes | Vertical distance to translate. A positive number indicates a translation towards the positive direction of the Y axis, and a negative number indicates a translation towards the negative direction of the Y axis. The value is a floating point number. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |
