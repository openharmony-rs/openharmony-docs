# Lattice

Lattice object. which is used to divide an image by lattice.

> **NOTE:** 
> 
> - The initial APIs of this class are supported since API version 12.
> 
> - This module uses the physical pixel unit, px.
> 
> - This module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## createImageLattice

```TypeScript
static createImageLattice(xDivs: Array<number>, yDivs: Array<number>, fXCount: number, fYCount: number,
        fBounds?: common2D.Rect | null, fRectTypes?: Array<RectType> | null, fColors?: Array<common2D.Color> | null): Lattice
```

Divides the image into lattices. The lattices on both even columns and even rows are fixed, and they are drawn at their original size if the target is large enough. If the target is too small to hold the fixed lattices, all the fixed lattices are scaled down to fit the target, and the lattices that are not on even columns and even rows are scaled to accommodate the remaining space.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| xDivs | Array&lt;number&gt; | Yes | Array of X coordinates used to divide the image. The value is an integer. |
| yDivs | Array&lt;number&gt; | Yes | Array of Y coordinates used to divide the image. The value is an integer. |
| fXCount | number | Yes | Size of the array that holds the X coordinates. The value range is [0, 5]. |
| fYCount | number | Yes | Size of the array that holds the Y coordinates. The value range is [0, 5]. |
| fBounds | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) &#124; null | No | Source bounds to draw. The rectangle parameter must be an integer. The default value is the rectangle size of the original image. If the rectangle parameter is a decimal, the decimal part is discarded and converted into an integer. |
| fRectTypes | Array&lt;[RectType](arkts-arkgraphics2d-drawing-recttype-e.md)&gt; &#124; null | No | Array that holds the rectangle types. The default value is null. If this parameter is specified, the array size must be (fXCount + 1) * (fYCount + 1). |
| fColors | Array&lt;[common2D.Color](arkts-arkgraphics2d-common2d-color-i.md)&gt; &#124; null | No | Array that holds the colors used to fill the lattices. The default value is null. If this parameter is specified, the array size must be (fXCount + 1) * (fYCount + 1). |

**Return value:**

| Type | Description |
| --- | --- |
| [Lattice](arkts-arkgraphics2d-drawing-lattice-c.md) | **Lattice** object obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createImageLattice

```TypeScript
static createImageLattice(xDivs: Array<number>, yDivs: Array<number>, fXCount: number, fYCount: number,
        fBounds?: common2D.Rect | null, fRectTypes?: Array<RectType> | null, fColors?: Array<number> | null): Lattice
```

Divides the image into lattices. The lattices on both even columns and even rows are fixed, and they are drawn at their original size if the target is large enough. If the target is too small to hold the fixed lattices, all the fixed lattices are scaled down to fit the target, and the lattices that are not on even columns and even rows are scaled to accommodate the remaining space.

**Since:** 18

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| xDivs | Array&lt;number&gt; | Yes | Array of X coordinates used to divide the image. The value is an integer. |
| yDivs | Array&lt;number&gt; | Yes | Array of Y coordinates used to divide the image. The value is an integer. |
| fXCount | number | Yes | Size of the array that holds the X coordinates. The value range is [0, 5]. |
| fYCount | number | Yes | Size of the array that holds the Y coordinates. The value range is [0, 5]. |
| fBounds | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) &#124; null | No | Source bounds to draw. The rectangle parameter must be an integer. The default value is the rectangle size of the original image. If the rectangle parameter is a decimal, the decimal part is discarded and converted into an integer. |
| fRectTypes | Array&lt;[RectType](arkts-arkgraphics2d-drawing-recttype-e.md)&gt; &#124; null | No | Array that holds the rectangle types. The default value is null. If this parameter is specified, the array size must be (fXCount + 1) * (fYCount + 1). |
| fColors | Array&lt;number&gt; &#124; null | No | Array that holds the colors used to fill the lattices. Each color is represented by a 32-bit unsigned integer in hexadecimal ARGB format. The default value is null. If this parameter is specified, the array size must be (fXCount + 1) * (fYCount + 1). |

**Return value:**

| Type | Description |
| --- | --- |
| [Lattice](arkts-arkgraphics2d-drawing-lattice-c.md) | **Lattice** object obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
