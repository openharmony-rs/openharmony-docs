# Class (RectUtils)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=d66ce495242bdf35b08a89dbf23cdf3929953623 translatedAt=2026-08-24T08:13:15.290Z pushedAt=2026-08-29T08:27:25.563Z -->

Provides tools for processing rectangles, supporting quick construction and basic attribute retrieval, boundary calculation and adjustment, translation and state determination, and boundary normalization of rectangles.

Use scenarios:

1. Quickly create rectangles and get their basic features, like making a new rectangle, copying one, and obtaining its width, height, and center point.

2. Boundary calculation and adjustment, such as determining the inclusion relationship, calculating and updating intersections and unions between rectangles, and updating boundary values.

3. Rectangle translation and state determination, such as translating a rectangle, moving a rectangle to a specified position, determining whether a rectangle is empty, and determining whether two rectangles are equal.

4. Rectangle boundary normalization, such as swapping and sorting the boundary values of a rectangle that is reversed.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 20.
>
> - This module uses the physical pixel unit, px.
>
> - This module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

## Modules to Import

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## makeEmpty<sup>20+</sup>

static makeEmpty(): common2D.Rect

Creates a rectangle with the top, bottom, left, and right boundary coordinates all being **0**.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type   | Description                      |
| ------- | ------------------------- |
| [common2D.Rect](js-apis-graphics-common2D.md#rect) | Created rectangle object.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeEmpty();
```

## makeLtrb<sup>20+</sup>

static makeLtrb(left: number, top: number, right: number, bottom: number): common2D.Rect

Creates a rectangle with specified top, bottom, left, and right boundaries.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| left   | number | Yes   | X-axis coordinate of the upper-left corner of the rectangle. This parameter is a floating-point number. 0 represents the coordinate origin, a negative value indicates that it is located to the left of the origin, and a positive value indicates that it is located to the right of the origin. The unit is physical pixel px. |
| top    | number | Yes   | Y-axis coordinate of the upper-left corner of the rectangle. This parameter is a floating-point number. 0 represents the coordinate origin, a negative value indicates that it is located above the origin, and a positive value indicates that it is located below the origin. The unit is physical pixel px. |
| right  | number | Yes   | X-axis coordinate of the lower-right corner of the rectangle. This parameter is a floating-point number. 0 represents the coordinate origin, a negative value indicates that it is located to the left of the origin, and a positive value indicates that it is located to the right of the origin. The unit is physical pixel px. |
| bottom | number | Yes   | Y-axis coordinate of the lower-right corner of the rectangle. This parameter is a floating-point number. 0 represents the coordinate origin, a negative value indicates that it is located above the origin, and a positive value indicates that it is located below the origin. The unit is physical pixel px. |

**Returns**

| Type   | Description                      |
| ------- | ------------------------- |
| [common2D.Rect](js-apis-graphics-common2D.md#rect) | Created rectangle.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(10, 10, 20, 20);
```

## makeCopy<sup>20+</sup>

static makeCopy(src: common2D.Rect): common2D.Rect

Copies a rectangle.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| src   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes  | Rectangle to be copied.|

**Returns**

| Type   | Description                      |
| ------- | ------------------------- |
| [common2D.Rect](js-apis-graphics-common2D.md#rect) | Created rectangle.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(10, 10, 20, 20);
let rect2 = drawing.RectUtils.makeCopy(rect);
console.info('rect2.left: ', rect2.left);
console.info('rect2.top: ', rect2.top);
console.info('rect2.right: ', rect2.right);
console.info('rect2.bottom: ', rect2.bottom);
```

## getWidth<sup>20+</sup>

static getWidth(rect: common2D.Rect): number

Obtains the width of a rectangle.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes   | Rectangle object whose width is to be obtained. |

**Returns**

| Type   | Description                      |
| ------- | ------------------------- |
| number | Returns the width of the rectangle. If the left boundary of the rectangle is greater than the right boundary, the obtained width is a negative value; if the left boundary is less than the right boundary, it is a positive value. The unit is physical pixels (px). |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(10, 10, 20, 20);
let width = drawing.RectUtils.getWidth(rect);
console.info('width:', width);
```

## getHeight<sup>20+</sup>

static getHeight(rect: common2D.Rect): number

Obtains the height of a rectangle.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes   | Rectangle object that needs to get the height. |

**Returns**

| Type   | Description                      |
| ------- | ------------------------- |
| number | Return the height of the rectangle. If the top boundary of the rectangle is greater than the bottom boundary, the obtained height is a negative value; if the top boundary is less than the bottom boundary, it is a positive value. The unit is physical pixel (px). |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(10, 10, 20, 20);
let height = drawing.RectUtils.getHeight(rect);
```

## centerX<sup>20+</sup>

static centerX(rect: common2D.Rect): number

Obtains the x-axis coordinate of the center of the rectangle. The x-axis coordinate of the center is half of the sum of the left and right boundaries of the rectangle.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes   | Rectangle object whose center x-axis coordinate needs to be obtained. |

**Returns**

| Type   | Description                      |
| ------- | ------------------------- |
| number | X-axis coordinate of the rectangle center. The unit is physical pixel (px). |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(20, 30, 30, 40);
let x = drawing.RectUtils.centerX(rect);
```

## centerY<sup>20+</sup>

static centerY(rect: common2D.Rect): number

Obtains the y-axis coordinate of the center of the rectangle. The y-axis coordinate of the center is half of the sum of the top and bottom boundaries of the rectangle.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes   | Rectangle object whose center y-axis coordinate needs to be obtained. |

**Returns**

| Type   | Description                      |
| ------- | ------------------------- |
| number | Returns the y-axis coordinate of the rectangle center. The unit is physical pixel px. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(20, 30, 30, 40);
let y = drawing.RectUtils.centerY(rect);
```

## contains<sup>20+</sup>

static contains(rect: common2D.Rect, other: common2D.Rect): boolean

Checks whether a rectangle completely contains another rectangle.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes   | Rectangle object used to determine whether it contains other rectangles. |
| other   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes  | Another rectangle object.|

**Returns**

| Type   | Description                      |
| ------- | ------------------------- |
| boolean | Whether the rectangle fully contains another rectangle. The value true indicates that other is inside rect or the two are equal; the value false indicates that other is not fully inside rect (that is, part of it is outside rect), or either rect or other is an empty rectangle. The left and top boundaries are inside the rectangle, while the right and bottom boundaries are not. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(10, 10, 20, 20);
let rect2 = drawing.RectUtils.makeLtrb(0, 0, 40, 40);
let isContains = drawing.RectUtils.contains(rect2, rect);
console.info('isContains: ', isContains);
```

## contains<sup>20+</sup>

static contains(rect: common2D.Rect, left: number, top: number, right: number, bottom: number): boolean

Checks whether a rectangle completely contains another rectangle (which is marked by the coordinates of the upper left and lower right corners).

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes   | Original rectangle object used to determine whether it contains the rectangle composed of the left, top, right, and bottom coordinates. |
| left   | number | Yes   | X-axis coordinate of the upper-left corner of the rectangle. This parameter is a floating-point number. 0 represents the coordinate origin, a negative value indicates that it is located to the left of the origin, and a positive value indicates that it is located to the right of the origin. The unit is physical pixel (px). |
| top    | number | Yes   | Y-axis coordinate of the upper-left corner of the rectangle. This parameter is a floating-point number. 0 represents the coordinate origin, a negative value indicates that it is located above the origin, and a positive value indicates that it is located below the origin. The unit is physical pixel (px). |
| right  | number | Yes   | X-axis coordinate of the lower-right corner of the rectangle. This parameter is a floating-point number. 0 represents the coordinate origin, a negative value indicates that it is located to the left of the origin, and a positive value indicates that it is located to the right of the origin. The unit is physical pixel (px). |
| bottom | number | Yes   | Y-axis coordinate of the lower-right corner of the rectangle. This parameter is a floating-point number. 0 represents the coordinate origin, a negative value indicates that it is located above the origin, and a positive value indicates that it is located below the origin. The unit is physical pixel (px). |

**Returns**

| Type   | Description                      |
| ------- | ------------------------- |
| boolean | Whether the rectangle fully contains the rectangle composed of the left, top, right, and bottom coordinates. true indicates that the rectangle composed of left, top, right, and bottom is completely inside the rect rectangle, or the two rectangles are completely equal. false indicates that the rectangle is not completely inside rect (that is, part of it is outside rect), or either rect or this rectangle is an empty rectangle. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(0, 0, 100, 100);
let isContains = drawing.RectUtils.contains(rect, 10, 20, 30, 40);
console.info('isContains: ', isContains);
```

## contains<sup>20+</sup>

static contains(rect: common2D.Rect, x: number, y: number): boolean

Checks whether a rectangle completely contains a specified point.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes   | Original rectangle object used to determine whether it contains the specified point. |
| x   | number | Yes   | X-axis coordinate of the point to be determined. This parameter is a floating-point number. 0 represents the coordinate origin, a negative value indicates that the point is located at the left of the origin, and a positive value indicates that the point is located at the right of the origin. The unit is physical pixel px. |
| y    | number | Yes  | Y-axis coordinate of the point to be determined. This parameter is a floating-point number. 0 represents the coordinate origin, a negative value indicates that the point is located above the origin, and a positive value indicates that the point is located below the origin. The unit is physical pixel px. |

**Returns**

| Type   | Description                      |
| ------- | ------------------------- |
| boolean | Whether the rectangle completely contains the point **(x, y)**. **true** means yes; **false** otherwise.  An empty rectangle does not contain any point.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(0, 0, 100, 100);
let isContains = drawing.RectUtils.contains(rect, 10, 20);
console.info('isContains: ', isContains);
```

## inset<sup>20+</sup>

static inset(rect: common2D.Rect, left: number, top: number, right: number, bottom: number): void

Adds the left, top, right, and bottom boundaries of the specified rectangle to the passed-in "Left, Top, Right, Bottom" values respectively.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes   | Original rectangle object whose boundary needs to be adjusted. |
| left   | number | Yes   | Value added to the left boundary of the rectangle (the x-axis coordinate of the upper-left corner of the rectangle). This parameter is a floating-point number. 0 indicates not performing any operation, a positive value indicates performing addition, and a negative value indicates performing subtraction. The unit is physical pixel (px). |
| top    | number | Yes   | Value added to the top boundary of the rectangle (the y-axis coordinate of the upper-left corner of the rectangle). This parameter is a floating-point number. 0 indicates not performing any operation, a positive value indicates performing addition, and a negative value indicates performing subtraction. The unit is physical pixel (px). |
| right  | number | Yes   | Value added to the right boundary of the rectangle (the x-axis coordinate of the lower-right corner of the rectangle). This parameter is a floating-point number. 0 indicates not performing any operation, a positive value indicates performing addition, and a negative value indicates performing subtraction. The unit is physical pixel (px). |
| bottom | number | Yes   | Value added to the bottom boundary of the rectangle (the y-axis coordinate of the lower-right corner of the rectangle). This parameter is a floating-point number. 0 indicates not performing any operation, a positive value indicates performing addition, and a negative value indicates performing subtraction. The unit is physical pixel (px). |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(10, 10, 20, 20);
drawing.RectUtils.inset(rect, 10, -20, 30, 60);
console.info('rect.left: ', rect.left);
console.info('rect.top: ', rect.top);
console.info('rect.right: ', rect.right);
console.info('rect.bottom: ', rect.bottom);
```

## intersect<sup>20+</sup>

static intersect(rect: common2D.Rect, other: common2D.Rect): boolean

Calculates the intersection of two rectangles and updates the intersection result to the rectangle represented by the first input parameter.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes  | Original rectangle used to calculate the intersection.|
| other   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes | Another rectangle used to calculate the intersection.|

**Returns**

| Type   | Description                      |
| ------- | ------------------------- |
| boolean | Whether two rectangles intersect. true indicates that the two rectangles intersect, and false indicates that they do not intersect, or that they only overlap at edges or touch at a point. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(0, 0, 20, 20);
let rect2 = drawing.RectUtils.makeLtrb(10, 10, 40, 40);
let isIntersect = drawing.RectUtils.intersect(rect, rect2);
console.info('isIntersect: ', isIntersect);
console.info('rect.left: ', rect.left);
console.info('rect.top: ', rect.top);
console.info('rect.right: ', rect.right);
console.info('rect.bottom: ', rect.bottom);
```

## isIntersect<sup>20+</sup>

static isIntersect(rect: common2D.Rect, other: common2D.Rect): boolean

Checks whether two rectangles intersect.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes   | Original rectangle used to determine whether they intersect. |
| other   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes  | Another rectangle used to determine whether they intersect. |

**Returns**

| Type   | Description                      |
| ------- | ------------------------- |
| boolean | Whether the two rectangles intersect. true indicates that the two rectangles intersect, and false indicates that they do not. If the two rectangles only overlap at edges or intersect at a point, false is returned. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(0, 0, 20, 20);
let rect2 = drawing.RectUtils.makeLtrb(10, 10, 40, 40);
let isIntersect = drawing.RectUtils.isIntersect(rect, rect2);
console.info('isIntersect:', isIntersect);
```

## union<sup>20+</sup>

static union(rect: common2D.Rect, other: common2D.Rect): void

Calculates the union area of two rectangles and updates the union result to the rectangle area represented by the first input parameter. If the rectangle of the first input parameter is empty, the union result is updated to the rectangle area represented by the second input parameter; if the rectangle of the second input parameter is empty, no operation is performed.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes  | Original rectangle used to calculate the union.|
| other   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes | Another rectangle used to calculate the union.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(0, 0, 20, 20);
let rect2 = drawing.RectUtils.makeLtrb(10, 10, 40, 40);
drawing.RectUtils.union(rect, rect2);
console.info('rect.left: ', rect.left);
console.info('rect.top: ', rect.top);
console.info('rect.right: ', rect.right);
console.info('rect.bottom: ', rect.bottom);
```

## isEmpty<sup>20+</sup>

static isEmpty(rect: common2D.Rect): boolean

Checks whether a rectangle is empty (the left boundary is greater than or equal to the right boundary or the top boundary is greater than or equal to the bottom boundary).

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description           |
| ------ | ------ | ---- | --------------  |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes   | Rectangle object used to determine whether it is empty. |

**Returns**

| Type   | Description                      |
| ------- | ------------------------- |
| boolean | Whether the rectangle is empty. true indicates that the rectangle is empty, and false indicates the opposite. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeEmpty();
let isEmpty = drawing.RectUtils.isEmpty(rect);
console.info('isEmpty:', isEmpty);
let rect2 = drawing.RectUtils.makeLtrb(0, 0, 20, 20);
isEmpty = drawing.RectUtils.isEmpty(rect2);
console.info('isEmpty:', isEmpty);
```

## offset<sup>20+</sup>

static offset(rect: common2D.Rect, dx: number, dy: number): void

Translates a rectangle.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes   | Rectangle area to be translated. |
| dx   | number | Yes    | Horizontal translation distance. This parameter is a floating-point number. 0 indicates no translation, a negative value indicates translation to the left, and a positive value indicates translation to the right. The unit is physical pixel (px). |
| dy    | number | Yes   | Vertical translation distance. This parameter is a floating-point number. 0 indicates no translation, a negative value indicates translation upward, and a positive value indicates translation downward. The unit is physical pixel (px). |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(0, 0, 20, 20);
drawing.RectUtils.offset(rect, 10, 20);
console.info('rect.left: ', rect.left);
console.info('rect.top: ', rect.top);
console.info('rect.right: ', rect.right);
console.info('rect.bottom: ', rect.bottom);
```

## offsetTo<sup>20+</sup>

static offsetTo(rect: common2D.Rect, newLeft: number, newTop: number): void

Translates a rectangle to a specified position.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes   | Rectangle area to be translated. |
| newLeft   | number | Yes   | X-axis coordinate of the corresponding position to translate to. This parameter is a floating-point number. 0 represents the coordinate origin, a negative value indicates located at the coordinate left of the origin, and a positive value indicates located at the coordinate right of the origin. The unit is physical pixel px. |
| newTop    | number | Yes   | Y-axis coordinate of the corresponding position to translate to. This parameter is a floating-point number. 0 represents the coordinate origin, a negative value indicates located at the coordinate above the origin, and a positive value indicates located at the coordinate below the origin. The unit is physical pixel px. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(20, 20, 40, 40);
drawing.RectUtils.offsetTo(rect, 10, 20);
console.info('rect.left: ', rect.left);
console.info('rect.top: ', rect.top);
console.info('rect.right: ', rect.right);
console.info('rect.bottom: ', rect.bottom);
```

## setRect<sup>20+</sup>

static setRect(rect: common2D.Rect, other: common2D.Rect): void

Assigns the existing rectangle with another rectangle.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes   | Original rectangle object to be assigned. |
| other   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes  | Another rectangle.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(10, 20, 30, 40);
let rect2 = drawing.RectUtils.makeEmpty();
drawing.RectUtils.setRect(rect2, rect);
console.info('rect2.left: ', rect2.left);
console.info('rect2.top: ', rect2.top);
console.info('rect2.right: ', rect2.right);
console.info('rect2.bottom: ', rect2.bottom);
```

## setLtrb<sup>20+</sup>

static setLtrb(rect: common2D.Rect, left: number, top: number, right: number, bottom: number): void

Updates the left, top, right, and bottom boundary values of the current rectangle using the passed-in "Left, Top, Right, Bottom" values.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes   | Original rectangle object whose boundary values need to be updated. |
| left   | number | Yes   | X-axis coordinate of the upper-left corner of the rectangle. This parameter is a floating-point number. 0 represents the coordinate origin, a negative value indicates that it is located at the coordinate left of the origin, and a positive value indicates that it is located at the coordinate right of the origin. The unit is physical pixel px. |
| top    | number | Yes   | Y-axis coordinate of the upper-left corner of the rectangle. This parameter is a floating-point number. 0 represents the coordinate origin, a negative value indicates that it is located at the coordinate above the origin, and a positive value indicates that it is located at the coordinate below the origin. The unit is physical pixel px. |
| right  | number | Yes   | X-axis coordinate of the lower-right corner of the rectangle. This parameter is a floating-point number. 0 represents the coordinate origin, a negative value indicates that it is located at the coordinate left of the origin, and a positive value indicates that it is located at the coordinate right of the origin. The unit is physical pixel px. |
| bottom | number | Yes   | Y-axis coordinate of the lower-right corner of the rectangle. This parameter is a floating-point number. 0 represents the coordinate origin, a negative value indicates that it is located at the coordinate above the origin, and a positive value indicates that it is located at the coordinate below the origin. The unit is physical pixel px. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeEmpty();
drawing.RectUtils.setLtrb(rect, 10, 20, 30, 60);
console.info('rect.left: ', rect.left);
console.info('rect.top: ', rect.top);
console.info('rect.right: ', rect.right);
console.info('rect.bottom: ', rect.bottom);
```

## setEmpty<sup>20+</sup>

static setEmpty(rect: common2D.Rect): void

Sets the left, right, top, and bottom boundaries of the rectangle to **0**.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description           |
| ------ | ------ | ---- | --------------  |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes  | Empty rectangle object.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(10, 20, 20, 30);
drawing.RectUtils.setEmpty(rect);
console.info('rect.left: ', rect.left);
console.info('rect.top: ', rect.top);
console.info('rect.right: ', rect.right);
console.info('rect.bottom: ', rect.bottom);
```

## sort<sup>20+</sup>

static sort(rect: common2D.Rect): void

If the rectangle is reversed (that is, the left boundary is greater than the right boundary or the top boundary is greater than the bottom boundary), the corresponding reversed boundary values are swapped (if the left boundary is greater than the right boundary, the left and right boundary values are swapped; if the top boundary is greater than the bottom boundary, the top and bottom boundary values are swapped), so that the top boundary is less than the bottom boundary (the left boundary is less than the right boundary).

If the rectangle is not inverted (that is, the left boundary is less than or equal to the right boundary and the top boundary is less than or equal to the bottom boundary), no operation is performed.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description           |
| ------ | ------ | ---- | --------------  |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes   | Rectangle object to be sorted by boundary. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(20, 40, 30, 30);
drawing.RectUtils.sort(rect);
console.info('rect.left: ', rect.left);
console.info('rect.top: ', rect.top);
console.info('rect.right: ', rect.right);
console.info('rect.bottom: ', rect.bottom);
```

## isEqual<sup>20+</sup>

static isEqual(rect: common2D.Rect, other: common2D.Rect): boolean

Checks whether two rectangles are equal.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes    | Original rectangle to be compared for equality. |
| other  | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes   | Another rectangle to be compared for equality. |

**Returns**

| Type   | Description                      |
| ------- | ------------------------- |
| boolean | Whether two rectangles are equal. **true** means yes; **false** otherwise.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let rect = drawing.RectUtils.makeLtrb(10, 20, 20, 30);
let rect2 = drawing.RectUtils.makeEmpty();
let isEqual = drawing.RectUtils.isEqual(rect, rect2);
console.info('isEqual:', isEqual);
```