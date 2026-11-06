# Class (Lattice)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=cfa59f2ade5e74278a5dbd3dbd7bab536925f809 translatedAt=2026-08-24T08:00:03.425Z pushedAt=2026-08-29T03:17:46.763Z -->

Rectangular grid object. This object is used to divide an image into rectangular grids. It supports fixing specified grid areas, scaling the remaining grids to implement local stretching, customizing grid drawing types, filling grids with colors, and specifying the drawing boundary rectangle. After a Lattice object is created, it must be used together with the [Canvas.drawImageLattice](arkts-apis-graphics-drawing-Canvas.md#drawimagelattice18) method to implement local stretching drawing of an image.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 12.
>
> - This module uses the physical pixel unit, px.
>
> - This module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

## Modules to Import

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## createImageLattice<sup>12+</sup>

static createImageLattice(xDivs: Array\<number>, yDivs: Array\<number>, fXCount: number, fYCount: number, fBounds?: common2D.Rect \| null, fRectTypes?: Array\<RectType> \| null, fColors?: Array\<common2D.Color> \| null): Lattice

Creates a rectangular grid object. Divides the image into rectangular grids. The grids on both even columns and even rows are fixed. If the target grid is large enough, these fixed grids are drawn at their original size, and the remaining grids are scaled to fit the remaining space. If the target grid is too small to hold these fixed grids, all fixed grids are scaled down proportionally to fit the target grid.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name      | Type                                                               | Mandatory| Description                                                                              |
| ------------ | ------------------------------------------------------------------ | ---- | --------------------------------------------------------------------------------- |
| xDivs        | Array\<number>                                                     | Yes   | Array of X coordinate values used for dividing the image, in physical pixels (px). Each array element must be an integer. If a decimal is passed, the fractional part is directly discarded and the value is converted to an integer.                                             |
| yDivs        | Array\<number>                                                     | Yes   | Array of Y coordinate values used for dividing the image, in physical pixels (px). Each array element must be an integer. If a decimal is passed, the fractional part is directly discarded and the value is converted to an integer.                                             |
| fXCount      | number                                                             | Yes   | Number of elements in the X coordinate value array, which must match the length of the xDivs array. Based on function and performance considerations, the value range is [0, 5].                            |
| fYCount      | number                                                             | Yes   | Number of elements in the Y coordinate value array, which must match the length of the yDivs array. Based on function and performance considerations, the value range is [0, 5].                            |
| fBounds      | [common2D.Rect](js-apis-graphics-common2D.md#rect) \| null           | No   | Original bounding rectangle to be drawn. Pass this parameter when only a local region of the image needs to be drawn. When not passed, it defaults to the size of the original image rectangle. The rectangle parameters must be integers, in physical pixels (px). If a rectangle parameter is a decimal, the fractional part is directly discarded and the value is converted to an integer. |
| fRectTypes   | Array\<[RectType](arkts-apis-graphics-drawing-e.md#recttype12)> \| null                              | No   | Array of rectangle grid types used to specify the drawing type of each rectangle grid. It defaults to empty. If set, its size must be (fXCount + 1) * (fYCount + 1). |
| fColors      | Array\<[common2D.Color](js-apis-graphics-common2D.md#color)> \| null | No   | Array of colors used to fill the grids, specifying a fill color for each grid cell. Once set, the corresponding grid regions are filled with the specified color as a solid color, replacing the original image content. When not passed, it defaults to empty (the grids do not use custom color filling and the original image content is retained). If set, its size must be (fXCount + 1) * (fYCount + 1). |

**Returns**

| Type                      | Description                               |
| ------------------------- | ----------------------------------- |
| [Lattice](arkts-apis-graphics-drawing-Lattice.md)     | Returns the created rectangular grid object, which can be passed to drawing APIs to implement local stretching of an image -- fixed grids retain their original size, while the remaining grids adaptively scale to fill the remaining space.              |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**Example**

```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    let xDivs: Array<number> = [1, 2, 4];
    let yDivs: Array<number> = [1, 2, 4];
    let lattice = drawing.Lattice.createImageLattice(xDivs, yDivs, 3, 3); // The image is divided into lattices of (3 + 1) x (3 + 1). The blue rectangles in the figure below are fixed lattices.
  }
}
```

![Lattice.png](figures/Lattice.png)

## createImageLattice<sup>18+</sup>

static createImageLattice(xDivs: Array\<number>, yDivs: Array\<number>, fXCount: number, fYCount: number, fBounds?: common2D.Rect \| null, fRectTypes?: Array\<RectType> \| null, fColors?: Array\<number> \| null): Lattice

Creates a rectangular grid object. Divides the image into rectangular grids. The grids on both even columns and even rows are fixed. If the target grid is large enough, these fixed grids are drawn at their original size, and the remaining grids are scaled to fit the remaining space. If the target grid is too small to hold these fixed grids, all fixed grids are scaled down proportionally to fit the target grid.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name      | Type                                                               | Mandatory| Description                                                                              |
| ------------ | ------------------------------------------------------------------ | ---- | --------------------------------------------------------------------------------- |
| xDivs        | Array\<number>                                                     | Yes   | Array of X coordinate values used to divide the image, in physical pixels (px). Array elements must be integers. If a decimal is passed, the fractional part is directly discarded and the value is converted to an integer.                                             |
| yDivs        | Array\<number>                                                     | Yes   | Array of Y coordinate values used to divide the image, in physical pixels (px). Array elements must be integers. If a decimal is passed, the fractional part is directly discarded and the value is converted to an integer.                                             |
| fXCount      | number                                                             | Yes   | Number of elements in the X coordinate value array, which must match the length of the xDivs array. Based on function and performance considerations, the value range is [0, 5].                            |
| fYCount      | number                                                             | Yes   | Number of elements in the Y coordinate value array, which must match the length of the yDivs array. Based on function and performance considerations, the value range is [0, 5].                            |
| fBounds      | [common2D.Rect](js-apis-graphics-common2D.md#rect) \| null           | No   | Original boundary rectangle to draw. Pass this parameter when only a local area of the image needs to be drawn. When not passed, the default is the size of the original image rectangle. The rectangle parameters must be integers, in physical pixels (px) (if a rectangle parameter is a decimal, the fractional part is directly discarded and the value is converted to an integer). |
| fRectTypes   | Array\<[RectType](arkts-apis-graphics-drawing-e.md#recttype12)> \| null                              | No   | Array of rectangle grid types used to fill, which specifies the drawing type of each rectangle grid. The default is empty. If set, the size must be (fXCount + 1) * (fYCount + 1). |
| fColors      | Array\<number> \| null | No   | Array of colors used to fill the grids, which specifies the fill color for each grid cell. After being set, the corresponding grid area is filled with the specified color in solid color, replacing the original image content. The color is represented by a 32-bit unsigned integer in hexadecimal ARGB format, with a value range of [0, 4294967295]. When not passed, the default is empty (the grids do not use custom color filling and retain the original image content). If set, the size must be (fXCount + 1) * (fYCount + 1). |

**Returns**

| Type                      | Description                               |
| ------------------------- | ----------------------------------- |
| [Lattice](arkts-apis-graphics-drawing-Lattice.md)     | Returns the created rectangular grid object, which can be passed to the drawing API to implement partial stretching of the image: the fixed grid maintains its original size, and the remaining grids adaptively scale to fill the remaining space.              |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**Example**

```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    let xDivs: Array<number> = [1, 2, 4];
    let yDivs: Array<number> = [1, 2, 4];
    let colorArray: Array<number> = [0xffffffff, 0x44444444, 0x99999999, 0xffffffff, 0x44444444, 0x99999999, 0xffffffff, 0x44444444, 0x99999999, 0x44444444, 0x99999999, 0xffffffff, 0x44444444, 0x99999999, 0xffffffff, 0x44444444];
    let lattice = drawing.Lattice.createImageLattice(xDivs, yDivs, 3, 3, null, null, colorArray);
  }
}
```