# RectUtils

This module provides tools for processing rectangles. Use scenarios:

1. Quickly create rectangles and get their basic features, like making a new rectangle, copying one, and obtaining its width, height, and center point.
2. Calculate and adjust boundaries, such as obtaining the inclusion relationship, calculating and updating intersections and unions between rectangles, and updating boundary values.

> **NOTE:** 
> 
> - The initial APIs of this class are supported since API version 20.
> 
> - This module uses the physical pixel unit, px.
> 
> - This module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## centerX

```TypeScript
static centerX(rect: common2D.Rect): number
```

Obtains the X coordinate of the rectangle center.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Rectangle object. |

**Return value:**

| Type | Description |
| --- | --- |
| number | X coordinate of the rectangle center. |

## centerY

```TypeScript
static centerY(rect: common2D.Rect): number
```

Obtains the Y coordinate of the rectangle center.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Rectangle object. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Y coordinate of the rectangle center. |

## contains

```TypeScript
static contains(rect: common2D.Rect, other: common2D.Rect): boolean
```

Checks whether a rectangle completely contains another rectangle.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Rectangle object. |
| other | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Another rectangle object. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether a rectangle completely contains another rectangle. **true** means yes; **false** otherwise. An empty rectangle does not contain any other rectangle. |

## contains

```TypeScript
static contains(rect: common2D.Rect, left: number, top: number, right: number, bottom: number): boolean
```

Checks whether a rectangle completely contains another rectangle (which is marked by the coordinates of the upper left and lower right corners).

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Rectangle object. |
| left | number | Yes | X coordinate of the upper left corner of the rectangle. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the point to the right of the coordinate origin, while a negative value places the point to the left. |
| top | number | Yes | Y coordinate of the upper left corner of the rectangle. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the point below the coordinate origin, while a negative value places the point above the coordinate origin. |
| right | number | Yes | X coordinate of the lower right corner of the rectangle. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the point to the right of the coordinate origin, while a negative value places the point to the left. |
| bottom | number | Yes | Y coordinate of the lower right corner of the rectangle. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the point below the coordinate origin, while a negative value places the point above the coordinate origin. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether a rectangle completely contains another rectangle defined by the coordinates of its upper left and lower right corners. **true** means yes; **false** otherwise. An empty rectangle does not contain any other rectangle. |

## contains

```TypeScript
static contains(rect: common2D.Rect, x: number, y: number): boolean
```

Checks whether a rectangle completely contains a specified point.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Rectangle object. |
| x | number | Yes | X coordinate of a point. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the point to the right of the coordinate origin, while a negative value places the point to the left. |
| y | number | Yes | Y coordinate of a point. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the point below the coordinate origin, while a negative value places the point above the coordinate origin. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the rectangle completely contains the point **(x, y)**. **true** means yes; **false** otherwise. An empty rectangle does not contain any point. |

## getHeight

```TypeScript
static getHeight(rect: common2D.Rect): number
```

Obtains the height of a rectangle.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Rectangle object. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Height of the rectangle. If the top boundary is greater than the bottom, the height is negative. If the top boundary is less than the bottom, the height is positive. |

## getWidth

```TypeScript
static getWidth(rect: common2D.Rect): number
```

Obtains the width of a rectangle.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Rectangle object. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Width of a rectangle. If the left boundary is greater than the right, the width is negative. If the left boundary is less than the right, the width is positive. |

## inset

```TypeScript
static inset(rect: common2D.Rect, left: number, top: number, right: number, bottom: number): void
```

Adds the input left, top, right, and bottom values to the left, top, right, and bottom boundaries of a specified rectangle, respectively.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Rectangle object. |
| left | number | Yes | Value to be added to the left boundary of the rectangle (X coordinate of the upper left corner of the rectangle). The value is a floating point number. **0** indicates that no operation is performed. A positive number indicates addition, and a negative number indicates subtraction. |
| top | number | Yes | Value to be added to the top boundary of the rectangle (Y coordinate of the upper left corner of the rectangle). The value is a floating point number. **0** indicates that no operation is performed. A positive number indicates addition, and a negative number indicates subtraction. |
| right | number | Yes | Value to be added to the right boundary of the rectangle (X coordinate of the lower right corner of the rectangle). The value is a floating point number. **0** indicates that no operation is performed. A positive number indicates addition, and a negative number indicates subtraction. |
| bottom | number | Yes | Value to be added to the bottom boundary of the rectangle (Y coordinate of the lower right corner of the rectangle). The value is a floating point number. **0** indicates that no operation is performed. A positive number indicates addition, and a negative number indicates subtraction. |

## intersect

```TypeScript
static intersect(rect: common2D.Rect, other: common2D.Rect): boolean
```

Calculates the intersection of two rectangles and updates the intersection result to the rectangle represented by the first input parameter.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Original rectangle used to calculate the intersection. |
| other | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Another rectangle used to calculate the intersection. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether two rectangles have an intersection. **true** means yes; **false** otherwise. |

## isEmpty

```TypeScript
static isEmpty(rect: common2D.Rect): boolean
```

Checks whether a rectangle is empty (the left boundary is greater than or equal to the right boundary or the top boundary is greater than or equal to the bottom boundary).

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Rectangle object to be checked. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the rectangle is empty. **true** means yes; **false** otherwise. |

## isEqual

```TypeScript
static isEqual(rect: common2D.Rect, other: common2D.Rect): boolean
```

Checks whether two rectangles are equal.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Original rectangle. |
| other | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Another rectangle. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether two rectangles are equal. **true** means yes; **false** otherwise. |

## isIntersect

```TypeScript
static isIntersect(rect: common2D.Rect, other: common2D.Rect): boolean
```

Checks whether two rectangles intersect.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Original rectangle used to calculate the intersection. |
| other | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Another rectangle used to calculate the intersection. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether two rectangles have an intersection. **true** means yes; **false** otherwise. If the two rectangles only overlap on the edge or intersect at a point, **false** is returned. |

## makeCopy

```TypeScript
static makeCopy(src: common2D.Rect): common2D.Rect
```

Copies a rectangle.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Rectangle to be copied. |

**Return value:**

| Type | Description |
| --- | --- |
| [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Created rectangle. |

## makeEmpty

```TypeScript
static makeEmpty(): common2D.Rect
```

Creates a rectangle with the top, bottom, left, and right boundary coordinates all being **0**.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Created rectangle object. |

## makeLtrb

```TypeScript
static makeLtrb(left: number, top: number, right: number, bottom: number): common2D.Rect
```

Creates a rectangle with specified top, bottom, left, and right boundaries.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| left | number | Yes | X coordinate of the upper left corner of the rectangle. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the point to the right of the coordinate origin, while a negative value places the point to the left. |
| top | number | Yes | Y coordinate of the upper left corner of the rectangle. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the point below the coordinate origin, while a negative value places the point above the coordinate origin. |
| right | number | Yes | X coordinate of the lower right corner of the rectangle. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the point to the right of the coordinate origin, while a negative value places the point to the left. |
| bottom | number | Yes | Y coordinate of the lower right corner of the rectangle. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the point below the coordinate origin, while a negative value places the point above the coordinate origin. |

**Return value:**

| Type | Description |
| --- | --- |
| [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Created rectangle. |

## offset

```TypeScript
static offset(rect: common2D.Rect, dx: number, dy: number): void
```

Translates a rectangle.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Rectangle to be translated. |
| dx | number | Yes | Horizontal translation distance. The value is a floating point number. **0** indicates no translation. A negative value indicates translation to the left, and a positive value indicates translation to the right. |
| dy | number | Yes | Vertical translation distance. The value is a floating point number. **0** indicates no translation. A negative value indicates translation upwards, and a positive value indicates translation downwards. |

## offsetTo

```TypeScript
static offsetTo(rect: common2D.Rect, newLeft: number, newTop: number): void
```

Translates a rectangle to a specified position.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Rectangle to be translated. |
| newLeft | number | Yes | X coordinate of the position to which the rectangle is translated. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the point to the right of the coordinate origin, while a negative value places the point to the left. |
| newTop | number | Yes | Y coordinate of the position to which the rectangle is translated. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the point below the coordinate origin, while a negative value places the point above the coordinate origin. |

## setEmpty

```TypeScript
static setEmpty(rect: common2D.Rect): void
```

Sets the left, right, top, and bottom boundaries of the rectangle to **0**.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Empty rectangle object. |

## setLtrb

```TypeScript
static setLtrb(rect: common2D.Rect, left: number, top: number, right: number, bottom: number): void
```

Updates the top, bottom, left, and right boundary values of the existing rectangle using the input top, bottom, left, and right values, respectively.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Rectangle object. |
| left | number | Yes | X coordinate of the upper left corner of the rectangle. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the point to the right of the coordinate origin, while a negative value places the point to the left. |
| top | number | Yes | Y coordinate of the upper left corner of the rectangle. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the point below the coordinate origin, while a negative value places the point above the coordinate origin. |
| right | number | Yes | X coordinate of the lower right corner of the rectangle. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the point to the right of the coordinate origin, while a negative value places the point to the left. |
| bottom | number | Yes | Y coordinate of the lower right corner of the rectangle. The value is a floating point number. **0** indicates the coordinate origin. A positive value places the point below the coordinate origin, while a negative value places the point above the coordinate origin. |

## setRect

```TypeScript
static setRect(rect: common2D.Rect, other: common2D.Rect): void
```

Assigns the existing rectangle with another rectangle.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Original rectangle. |
| other | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Another rectangle. |

## sort

```TypeScript
static sort(rect: common2D.Rect): void
```

If the rectangle is reversed (that is, the left boundary is greater than the right boundary or the top boundary is greater than the bottom boundary), the top and bottom (left and right) boundary values of the rectangle are exchanged, so that the top boundary is less than the bottom boundary (the left boundary is less than the right boundary). If the rectangle is not reversed (that is, the left boundary is less than or equal to the right boundary or the top boundary is less than or equal to the bottom boundary), no operation is performed.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Rectangle object. |

## union

```TypeScript
static union(rect: common2D.Rect, other: common2D.Rect): void
```

Calculates the union of two rectangles and updates the union result to the rectangle represented by the first input parameter. If the first input parameter is empty, the union result is updated to the rectangle represented by the second input parameter. If the second input parameter is empty, no operation is performed.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Original rectangle used to calculate the union. |
| other | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | Another rectangle used to calculate the union. |
