# Class (Path)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=cfa59f2ade5e74278a5dbd3dbd7bab536925f809 translatedAt=2026-08-24T08:07:56.450Z pushedAt=2026-08-31T06:39:13.316Z -->

Path is a composite geometric path class provided by the Drawing module. It consists of basic primitives such as straight lines, arcs, conic curves, quadratic Bézier curves, and cubic Bézier curves, and supports path construction, transformation, Boolean operations, SVG path parsing and conversion, measurement, and segment extraction. When no fill type is set, the default fill type is WINDING, which can be modified through [setFillType](#setfilltype12).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This module uses the physical pixel unit, px.
>
> - The module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

## Modules to Import

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## constructor<sup>12+</sup>

constructor()

Constructs a path.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
```

## constructor<sup>12+</sup>

constructor(path: Path)

Constructs a copy of an existing path.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                                        | Mandatory| Description                           |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| path | [Path](arkts-apis-graphics-drawing-Path.md) | Yes  | Path to copy.                |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
path.moveTo(0, 0);
path.lineTo(0, 700);
path.lineTo(700, 0);
path.close();
let path1: drawing.Path = new drawing.Path(path);
```

## set<sup>20+</sup>

set(src: Path): void

Replaces the content of the current path with the specified path, making the current path exactly the same as the specified path.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                                        | Mandatory| Description                           |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| src | [Path](arkts-apis-graphics-drawing-Path.md) | Yes | Source path object used to replace the content of the current path. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';
let path: drawing.Path = new drawing.Path();
path.moveTo(0, 0);
path.lineTo(0, 700);
path.lineTo(700, 0);
path.close();
let path1: drawing.Path = new drawing.Path();
path1.set(path);
```

## moveTo

moveTo(x: number, y: number) : void

Sets the start point of a custom path. Unlike [rMoveTo](#rmoveto12), which uses relative coordinates, moveTo uses absolute coordinates to set the start point. When the path start point is fixed, moveTo is recommended; when the path needs to be dynamically constructed based on the current position, [rMoveTo](#rmoveto12) is recommended.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| x      | number | Yes   | X coordinate of the start point. The value is a floating-point number, in physical pixels (px). |
| y      | number | Yes   | Y coordinate of the start point. The value is a floating-point number, in physical pixels (px). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path = new drawing.Path();
path.moveTo(10, 10);
```

## lineTo

lineTo(x: number, y: number) : void

Adds a line segment from the last point of the path (defaults to (0, 0) if the path has no content) to the target point.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| x      | number | Yes   | X-coordinate of the target point. The value is a floating-point number, in px. |
| y      | number | Yes   | Y-coordinate of the target point. The value is a floating-point number, in px. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path = new drawing.Path();
path.moveTo(10, 10);
path.lineTo(10, 15);
```

## arcTo

arcTo(x1: number, y1: number, x2: number, y2: number, startDeg: number, sweepDeg: number): void

Adds an arc to the path. The arc is drawn as an angular arc: first specify a rectangular boundary and take its inscribed ellipse; then specify the start angle and sweep angle; finally, sweep from the start angle to intercept a portion of the ellipse circumference, which is the drawn arc. In addition, a line segment is added by default from the last point of the path (defaults to (0, 0) if the path has no content) to the start point of the arc. If you do not need the connecting line segment to be added automatically, use [addArc](#addarc12).

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type  | Mandatory| Description                      |
| -------- | ------ | ---- | -------------------------- |
| x1       | number | Yes  | X coordinate of the upper left corner of the rectangle. The value is a floating point number, in physical pixels (px). |
| y1       | number | Yes  | Y coordinate of the upper left corner of the rectangle. The value is a floating point number, in physical pixels (px). |
| x2       | number | Yes  | X coordinate of the lower right corner of the rectangle. The value is a floating point number, in physical pixels (px). |
| y2       | number | Yes  | Y coordinate of the lower right corner of the rectangle. The value is a floating point number, in physical pixels (px). |
| startDeg | number | Yes  | Start angle. The start direction (0°) of the angle is the positive direction of the x-axis. The unit is degree. |
| sweepDeg | number | Yes  | Sweep degree. A positive value indicates clockwise sweep, and a negative value indicates counterclockwise sweep. The actual sweep degree is the result of this parameter modulo 360. The unit is degree. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path = new drawing.Path();
path.moveTo(10, 10);
path.arcTo(10, 15, 10, 10, 10, 10);
```

## quadTo

quadTo(ctrlX: number, ctrlY: number, endX: number, endY: number): void

Adds a quadratic Bézier curve from the last point of the path (defaults to (0, 0) if the path has no content) to the target point.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                 |
| ------ | ------ | ---- | --------------------- |
| ctrlX  | number | Yes   | X coordinate of the control point. The value is a floating point number, in physical pixels (px). |
| ctrlY  | number | Yes   | Y coordinate of the control point. The value is a floating point number, in physical pixels (px). |
| endX   | number | Yes   | X coordinate of the target point. The value is a floating point number, in physical pixels (px). |
| endY   | number | Yes   | Y coordinate of the target point. The value is a floating point number, in physical pixels (px). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path = new drawing.Path();
path.moveTo(10, 10);
path.quadTo(10, 15, 10, 10);
```

## conicTo<sup>12+</sup>

conicTo(ctrlX: number, ctrlY: number, endX: number, endY: number, weight: number): void

Adds a conic curve to the current path from the last point of the path (defaults to (0, 0) if the path has no content) to the target point, with the control point at (ctrlX, ctrlY) and the target point at (endX, endY). Compared with [quadTo](#quadto), conicTo controls the curve shape more flexibly through the weight parameter: when the weight is 1, the effect is the same as quadTo; when the weight is not 1, it can precisely represent conic curve segments such as arcs and elliptical arcs. Use quadTo when only a standard quadratic Bézier curve is needed, and use conicTo when you need to precisely represent arcs or flexibly control the curve shape.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                 |
| ------ | ------ | ---- | --------------------- |
| ctrlX  | number | Yes   | X coordinate of the control point. The value is a floating point number, in px. |
| ctrlY  | number | Yes   | Y coordinate of the control point. The value is a floating point number, in px. |
| endX   | number | Yes   | X coordinate of the target point. The value is a floating point number, in px. |
| endY   | number | Yes   | Y coordinate of the target point. The value is a floating point number, in px. |
| weight | number | Yes  | Weight of the curve, which determines its shape. The larger the value, the closer of the curve to the control point. If the value is less than or equal to 0, this API has the same effect as [lineTo](#lineto). If the value is 1, it has the same effect as [quadTo](#quadto). The value is a floating point number.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const path = new drawing.Path();
path.conicTo(200, 400, 100, 200, 0);
```

## cubicTo

cubicTo(ctrlX1: number, ctrlY1: number, ctrlX2: number, ctrlY2: number, endX: number, endY: number): void

Adds a cubic Bézier curve from the last point of the path (defaults to (0, 0) if the path has no content) to the target point.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                       |
| ------ | ------ | ---- | --------------------------- |
| ctrlX1 | number | Yes | X coordinate of the first control point. The value is a floating-point number, in physical pixels (px). |
| ctrlY1 | number | Yes | Y coordinate of the first control point. The value is a floating-point number, in physical pixels (px). |
| ctrlX2 | number | Yes | X coordinate of the second control point. The value is a floating-point number, in physical pixels (px). |
| ctrlY2 | number | Yes | Y coordinate of the second control point. The value is a floating-point number, in physical pixels (px). |
| endX   | number | Yes | X coordinate of the target point. The value is a floating-point number, in physical pixels (px). |
| endY   | number | Yes | Y coordinate of the target point. The value is a floating-point number, in physical pixels (px). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path = new drawing.Path();
path.moveTo(10, 10);
path.cubicTo(100, 100, 80, 150, 300, 150);
```

## rMoveTo<sup>12+</sup>

rMoveTo(dx: number, dy: number): void

Sets the start point of the path relative to the last point of the current path (defaults to (0, 0) if the path has no content). Unlike [moveTo](#moveto), which uses absolute coordinates, rMoveTo uses an offset relative to the last point of the current path. When the path needs to be dynamically constructed based on the current position, relative coordinate methods (such as rMoveTo and rLineTo) are recommended; when the path start point is fixed, absolute coordinate methods are recommended.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| dx     | number | Yes   | Offset of the new start point of the path relative to the last point of the current path along the x-axis. A positive value indicates an offset toward the positive direction of the x-axis, and a negative value indicates an offset toward the negative direction of the x-axis. This parameter is a floating-point number, in physical pixels (px). |
| dy     | number | Yes   | Offset of the new start point of the path relative to the last point of the current path along the y-axis. A positive value indicates an offset toward the positive direction of the y-axis, and a negative value indicates an offset toward the negative direction of the y-axis. This parameter is a floating-point number, in physical pixels (px). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const path = new drawing.Path();
path.rMoveTo(10, 10);
```

## rLineTo<sup>12+</sup>

rLineTo(dx: number, dy: number): void

Adds a line segment from the last point of the path (defaults to (0, 0) if the path has no content) to the target point using a relative position. Unlike [lineTo](#lineto), which uses absolute coordinates, rLineTo specifies the target point using an offset relative to the last point of the current path. When the path needs to be dynamically constructed based on the current position, relative coordinate methods are recommended; when the target point position is fixed, absolute coordinate methods are recommended.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| dx     | number | Yes  | Offset of the target point relative to the last point of the current path along the x-axis. A positive value indicates an offset toward the positive direction of the x-axis, and a negative value indicates an offset toward the negative direction of the x-axis. This parameter is a floating-point number, in physical pixels (px). |
| dy     | number | Yes  | Offset of the target point relative to the last point of the current path along the y-axis. A positive value indicates an offset toward the positive direction of the y-axis, and a negative value indicates an offset toward the negative direction of the y-axis. This parameter is a floating-point number, in physical pixels (px). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const path = new drawing.Path();
path.rLineTo(400, 200);
```

## rQuadTo<sup>12+</sup>

rQuadTo(dx1: number, dy1: number, dx2: number, dy2: number): void

Adds a quadratic Bézier curve from the last point of the path (or (0, 0) if the path is empty) to the target point using relative positions. Unlike [quadTo](#quadto), which uses absolute coordinates, rQuadTo adds a quadratic Bézier curve to the current path using offsets relative to the last point of the current path. When the path needs to be built dynamically based on the current position, the relative coordinate method is recommended; when the target point of the path is fixed, the absolute coordinate method is recommended.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                 |
| ------ | ------ | ---- | --------------------- |
| dx1  | number | Yes   | Offset of the control point relative to the last point of the path along the x-axis. A positive value indicates an offset toward the positive direction of the x-axis, and a negative value indicates an offset toward the negative direction of the x-axis. This parameter is a floating-point number, in physical pixels (px). |
| dy1  | number | Yes   | Offset of the control point relative to the last point of the path along the y-axis. A positive value indicates an offset toward the positive direction of the y-axis, and a negative value indicates an offset toward the negative direction of the y-axis. This parameter is a floating-point number, in physical pixels (px). |
| dx2   | number | Yes   | Offset of the target point relative to the last point of the path along the x-axis. A positive value indicates an offset toward the positive direction of the x-axis, and a negative value indicates an offset toward the negative direction of the x-axis. This parameter is a floating-point number, in physical pixels (px). |
| dy2   | number | Yes   | Offset of the target point relative to the last point of the path along the y-axis. A positive value indicates an offset toward the positive direction of the y-axis, and a negative value indicates an offset toward the negative direction of the y-axis. This parameter is a floating-point number, in physical pixels (px). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const path = new drawing.Path();
path.rQuadTo(100, 0, 0, 200);
```

## rConicTo<sup>12+</sup>

rConicTo(ctrlX: number, ctrlY: number, endX: number, endY: number, weight: number): void

Adds a conic curve from the last point of the path (or (0, 0) if the path is empty) to the target point using relative positions. Unlike [conicTo](#conicto12), which uses absolute coordinates, rConicTo adds a conic curve to the current path using offsets relative to the last point of the current path. When the path needs to be built dynamically based on the current position, the relative coordinate method is recommended; when the target point of the path is fixed, the absolute coordinate method is recommended.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                 |
| ------ | ------ | ---- | --------------------- |
| ctrlX  | number | Yes   | X-axis offset of the control point relative to the last point of the path. A positive value indicates an offset toward the positive direction of the x-axis, and a negative value indicates an offset toward the negative direction of the x-axis. This parameter is a floating-point number, in physical pixels (px). |
| ctrlY  | number | Yes   | Y-axis offset of the control point relative to the last point of the path. A positive value indicates an offset toward the positive direction of the y-axis, and a negative value indicates an offset toward the negative direction of the y-axis. This parameter is a floating-point number, in physical pixels (px). |
| endX   | number | Yes   | X-axis offset of the end point relative to the last point of the path. A positive value indicates an offset toward the positive direction of the x-axis, and a negative value indicates an offset toward the negative direction of the x-axis. This parameter is a floating-point number, in physical pixels (px). |
| endY   | number | Yes   | Y-axis offset of the end point relative to the last point of the path. A positive value indicates an offset toward the positive direction of the y-axis, and a negative value indicates an offset toward the negative direction of the y-axis. This parameter is a floating-point number, in physical pixels (px). |
| weight | number | Yes   | Weight of the curve, which determines the shape of the curve. A larger value brings the curve closer to the control point. If the value is less than or equal to 0, it is equivalent to using [rLineTo](#rlineto12) to add a line segment to the end point. If the value is 1, it is equivalent to [rQuadTo](#rquadto12). This parameter is a floating-point number. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const path = new drawing.Path();
path.rConicTo(200, 400, 100, 200, 0);
```

## rCubicTo<sup>12+</sup>

rCubicTo(ctrlX1: number, ctrlY1: number, ctrlX2: number, ctrlY2: number, endX: number, endY: number): void

Adds a cubic Bézier curve from the last point of the path (or (0, 0) if the path is empty) to the target point using relative positions. Unlike [cubicTo](#cubicto), which uses absolute coordinates, rCubicTo adds a cubic Bézier curve to the current path using offsets relative to the last point of the current path. When the path needs to be built dynamically based on the current position, the relative coordinate method is recommended; when the target point of the path is fixed, the absolute coordinate method is recommended.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                       |
| ------ | ------ | ---- | --------------------------- |
| ctrlX1 | number | Yes | X-axis offset of the first control point relative to the last point of the path. A positive value indicates an offset toward the positive direction of the x-axis, and a negative value indicates an offset toward the negative direction of the x-axis. This parameter is a floating-point number. The unit is physical pixel (px). |
| ctrlY1 | number | Yes | Y-axis offset of the first control point relative to the last point of the path. A positive value indicates an offset toward the positive direction of the y-axis, and a negative value indicates an offset toward the negative direction of the y-axis. This parameter is a floating-point number. The unit is physical pixel (px). |
| ctrlX2 | number | Yes | X-axis offset of the second control point relative to the last point of the path. A positive value indicates an offset toward the positive direction of the x-axis, and a negative value indicates an offset toward the negative direction of the x-axis. This parameter is a floating-point number. The unit is physical pixel (px). |
| ctrlY2 | number | Yes | Y-axis offset of the second control point relative to the last point of the path. A positive value indicates an offset toward the positive direction of the y-axis, and a negative value indicates an offset toward the negative direction of the y-axis. This parameter is a floating-point number. The unit is physical pixel (px). |
| endX   | number | Yes | X-axis offset of the target point relative to the last point of the path. A positive value indicates an offset toward the positive direction of the x-axis, and a negative value indicates an offset toward the negative direction of the x-axis. This parameter is a floating-point number. The unit is physical pixel (px). |
| endY   | number | Yes | Y-axis offset of the target point relative to the last point of the path. A positive value indicates an offset toward the positive direction of the y-axis, and a negative value indicates an offset toward the negative direction of the y-axis. This parameter is a floating-point number. The unit is physical pixel (px). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const path = new drawing.Path();
path.rCubicTo(200, 0, 0, 200, -20, 0);
```

## addArc<sup>12+</sup>

addArc(rect: common2D.Rect, startAngle: number, sweepAngle: number): void

Adds an arc to the path. Unlike [arcTo](#arcto), addArc does not automatically add a connecting line segment from the last point of the path to the start point of the arc, and it specifies the rectangular boundary through a common2D.Rect object. If you need to automatically connect to the start point of the arc, use arcTo; if you only need to add an independent arc, use addArc.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name        | Type                                      | Mandatory  | Description                 |
| ----------- | ---------------------------------------- | ---- | ------------------- |
| rect        | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes   | Rectangular boundary that encapsulates the oval including the arc.     |
| startAngle   | number | Yes   | Start angle of the arc, in degrees. 0° indicates the positive direction of the x-axis. This parameter is a floating-point number. When the remainder of the angle divided by 90 is close to 0 and sweepAngle is not within (-360, 360), the entire ellipse is added instead of an arc. |
| sweepAngle   | number | Yes   | Sweep angle, in degrees. A positive value indicates the clockwise direction, and a negative value indicates the counterclockwise direction. When this parameter is not within (-360, 360) and the remainder of startAngle divided by 90 is close to 0, the entire ellipse is added instead of an arc; in other cases, the actual sweep angle is the remainder of this input parameter divided by 360. This parameter is a floating-point number. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

let path = new drawing.Path();
const rect: common2D.Rect = {left:100, top:100, right:500, bottom:500};
path.addArc(rect, 90, 180);
```

## addCircle<sup>12+</sup>

addCircle(x: number, y: number, radius: number, pathDirection?: PathDirection): void

Adds a circle to this path in the specified direction. The start point of the circle is (x + radius, y).

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name        | Type                                      | Mandatory  | Description                 |
| ----------- | ---------------------------------------- | ---- | ------------------- |
| x   | number | Yes   | X-coordinate of the center of the circle. The value is a floating point number, in units of physical pixels (px). |
| y   | number | Yes   | Y-coordinate of the center of the circle. The value is a floating point number, in units of physical pixels (px). |
| radius   | number | Yes   | Radius of the circle. The value must be greater than 0 and is a floating point number. If the value is less than or equal to 0, no effect is produced. The unit is physical pixel (px). |
| pathDirection   | [PathDirection](arkts-apis-graphics-drawing-e.md#pathdirection12)  | No   | Direction of the path. If not passed in, the default value is clockwise. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts

import { drawing } from '@kit.ArkGraphics2D';

let path = new drawing.Path();
path.addCircle(100, 200, 50, drawing.PathDirection.CLOCKWISE);
```

## addOval<sup>12+</sup>

addOval(rect: common2D.Rect, start: number, pathDirection?: PathDirection): void

Adds the inscribed ellipse of a rectangle to this path in the specified direction.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name        | Type                                      | Mandatory  | Description                 |
| ----------- | ---------------------------------------- | ---- | ------------------- |
| rect        | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes   | Rectangular boundary of the oval.     |
| start   | number | Yes   | Index of the initial point of the ellipse. The value is an integer greater than or equal to 0. 0, 1, 2, and 3 correspond to the top, right, bottom, and left points of the ellipse, respectively. If the value is greater than or equal to 4, the remainder of the value divided by 4 is used. |
| pathDirection   | [PathDirection](arkts-apis-graphics-drawing-e.md#pathdirection12)  | No   | Path direction. If this parameter is not passed, the direction is clockwise by default. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed.|

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

let path = new drawing.Path();
const rect: common2D.Rect = {left:100, top:100, right:500, bottom:500};
path.addOval(rect, 5, drawing.PathDirection.CLOCKWISE);
```

## addRect<sup>12+</sup>

addRect(rect: common2D.Rect, pathDirection?: PathDirection): void

Adds a rectangle to a path in the specified direction. The start point is the upper left corner of the rectangle.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name        | Type                                      | Mandatory  | Description                 |
| ----------- | ---------------------------------------- | ---- | ------------------- |
| rect        | [common2D.Rect](js-apis-graphics-common2D.md#rect) | Yes    | Outline of the rectangle to add to the path. The rect parameter must be a valid common2D.Rect object, with left less than right and top less than bottom.      |
| pathDirection   | [PathDirection](arkts-apis-graphics-drawing-e.md#pathdirection12)  | No   | Direction of the path. If not passed in, the default is clockwise. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed.|

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

let path = new drawing.Path();
const rect: common2D.Rect = {left:100, top:100, right:500, bottom:500};
path.addRect(rect, drawing.PathDirection.CLOCKWISE);
```

## addRoundRect<sup>12+</sup>

addRoundRect(roundRect: RoundRect, pathDirection?: PathDirection): void

Adds a rounded rectangle to a path in the specified direction. When the path direction is clockwise, the start point is at the intersection of the rounded rectangle's left boundary and its lower left corner. When the path direction is counterclockwise, the start point is at the intersection point between the left boundary and the upper left corner.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name        | Type                                      | Mandatory  | Description                 |
| ----------- | ---------------------------------------- | ---- | ------------------- |
| roundRect        | [RoundRect](arkts-apis-graphics-drawing-RoundRect.md) | Yes    | Rounded rectangle object to add to the path. It must be a valid RoundRect object.      |
| pathDirection   | [PathDirection](arkts-apis-graphics-drawing-e.md#pathdirection12)  | No   | Path direction. The default value is clockwise. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed.|

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

let path = new drawing.Path();
const rect: common2D.Rect = {left:100, top:100, right:500, bottom:500};
let roundRect = new drawing.RoundRect(rect, 50, 50);
path.addRoundRect(roundRect, drawing.PathDirection.CLOCKWISE);
```

## addPath<sup>12+</sup>

addPath(path: Path, matrix?: Matrix | null): void

Transforms the points in a path by a matrix and stores the resulting path in the current **Path** object.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name        | Type                                      | Mandatory  | Description                 |
| ----------- | ---------------------------------------- | ---- | ------------------- |
| path        | [Path](arkts-apis-graphics-drawing-Path.md) | Yes    | Source path object to be added to the current path. After matrix transformation, it is appended to the current path.      |
| matrix   | [Matrix](arkts-apis-graphics-drawing-Matrix.md) \| null  | No   | Matrix object used to transform the source path (for example, rotation, scaling, and translation). Pass this parameter when the source path needs to be geometrically transformed before being added to the current path. When the source path is added as is, this parameter can be omitted, in which case the identity matrix (that is, no transformation) is used by default. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

let path = new drawing.Path();
let matrix = new drawing.Matrix();
const rect: common2D.Rect = {left:100, top:100, right:500, bottom:500};
let roundRect = new drawing.RoundRect(rect, 50, 50);
path.addRoundRect(roundRect, drawing.PathDirection.CLOCKWISE);
let dstPath = new drawing.Path();
dstPath.addPath(path, matrix);
```

## transform<sup>12+</sup>

transform(matrix: Matrix): void

Transforms the points in a path by matrix.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name        | Type                                      | Mandatory  | Description                 |
| ----------- | ---------------------------------------- | ---- | ------------------- |
| matrix   | [Matrix](arkts-apis-graphics-drawing-Matrix.md)  | Yes   | Matrix object used to transform the path. The matrix defines the specific transformation parameters (such as scaling, rotation, and translation), and all points on the path are transformed according to this matrix. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

let path = new drawing.Path();
let matrix = new drawing.Matrix();
matrix.setScale(1.5, 1.5, 10, 10);
const rect: common2D.Rect = {left:100, top:100, right:500, bottom:500};
let roundRect = new drawing.RoundRect(rect, 50, 50);
path.addRoundRect(roundRect, drawing.PathDirection.CLOCKWISE);
path.transform(matrix);
```

## contains<sup>12+</sup>

contains(x: number, y: number): boolean

Determines whether the specified coordinate point is contained in the path. The determination rule follows [PathFillType](arkts-apis-graphics-drawing-e.md#pathfilltype12).

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| x      | number | Yes   | Coordinate on the x-axis. The value is a floating-point number, in physical pixels (px). |
| y      | number | Yes   | Coordinate on the y-axis. The value is a floating-point number, in physical pixels (px). |

**Returns**

| Type   | Description          |
| ------- | -------------- |
| boolean | Check result. The value **true** means that the coordinate point is included in the path, and **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

const path = new drawing.Path();
let rect : common2D.Rect = {left: 50, top: 50, right: 250, bottom: 250};
path.addRect(rect, drawing.PathDirection.CLOCKWISE);
console.info('test contains: ' + path.contains(0, 0));
console.info('test contains: ' + path.contains(60, 60));
```

## setLastPoint<sup>20+</sup>

setLastPoint(x: number, y: number): void

Modifies the position of the last point of the path.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| x      | number | Yes   | X-coordinate of the specified point. The value is a floating point number. 0 indicates the coordinate origin, a negative value indicates a position to the left of the coordinate origin, and a positive value indicates a position to the right of the coordinate origin. The unit is physical pixel (px). |
| y      | number | Yes   | Y-coordinate of the specified point. The value is a floating point number. 0 indicates the coordinate origin, a negative value indicates a position above the coordinate origin, and a positive value indicates a position below the coordinate origin. The unit is physical pixel (px). |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';
const path = new drawing.Path();
path.moveTo(0, 0);
path.lineTo(0, 700);
let isEmpty = path.isEmpty();
console.info('isEmpty:', isEmpty);
path.reset();
isEmpty = path.isEmpty();
console.info('isEmpty:', isEmpty);
path.setLastPoint(50, 50);
isEmpty = path.isEmpty();
console.info('isEmpty:', isEmpty);
```

## getLastPoint

getLastPoint(): common2D.Point

Obtains the coordinates of the last point of the path.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Graphics.Drawing

**Return value**

| Type                                               | Description                   |
| -------------------------------------------------- | ---------------------- |
| [common2D.Point](js-apis-graphics-common2D.md#point12) | Coordinates of the last point of the path. If the path is empty, **undefined** is returned. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';
const path = new drawing.Path();
path.moveTo(0, 0);
path.lineTo(100, 100);
let lastPoint = path.getLastPoint();
console.info('lastPoint.x:', lastPoint?.x);
console.info('lastPoint.y:', lastPoint?.y);
```

## setFillType<sup>12+</sup>

setFillType(pathFillType: PathFillType): void

Sets the fill type of the path, which determines how the inside of the path is defined.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name        | Type                                      | Mandatory  | Description                 |
| ----------- | ---------------------------------------- | ---- | ------------------- |
| pathFillType   | [PathFillType](arkts-apis-graphics-drawing-e.md#pathfilltype12)  | Yes   | Path fill type, which determines how the interior region of the path is defined. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const path = new drawing.Path();
path.setFillType(drawing.PathFillType.WINDING);
```

## getFillType<sup>20+</sup>

getFillType(): PathFillType

Obtains the fill type of a path.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type                                              | Description                  |
| -------------------------------------------------- | ---------------------- |
| [PathFillType](arkts-apis-graphics-drawing-e.md#pathfilltype12) | Fill type of the path, which determines how the interior region of the path is defined. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';
const path = new drawing.Path();
path.setFillType(drawing.PathFillType.WINDING);
let type = path.getFillType();
console.info('type :' + type);
```

## getBounds<sup>12+</sup>

getBounds(): common2D.Rect

Obtains the minimum bounding rectangle that encloses this path.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type                                              | Description                  |
| -------------------------------------------------- | ---------------------- |
| [common2D.Rect](js-apis-graphics-common2D.md#rect) | Minimum bounding rectangle.|

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

const path = new drawing.Path();
path.lineTo(50, 40);
let rect : common2D.Rect = {left: 0, top: 0, right: 0, bottom: 0};
rect = path.getBounds();
console.info('test rect.left: ' + rect.left);
console.info('test rect.top: ' + rect.top);
console.info('test rect.right: ' + rect.right);
console.info('test rect.bottom: ' + rect.bottom);
```

## addPolygon<sup>12+</sup>

addPolygon(points: Array\<common2D.Point>, close: boolean): void

Adds a polygon to this path.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| points | Array\<[common2D.Point](js-apis-graphics-common2D.md#point12)>   | Yes   | Array of coordinate points of the vertices of the polygon. The points are connected in array order to form continuous line segments. |
| close  | boolean                                                        | Yes  | Whether to close the path, that is, whether to add a line segment from the start point to the end point of the path. The value **true** means to close the path, and **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

let pointsArray = new Array<common2D.Point>();
const point1: common2D.Point = { x: 200, y: 200 };
const point2: common2D.Point = { x: 400, y: 200 };
const point3: common2D.Point = { x: 100, y: 400 };
const point4: common2D.Point = { x: 300, y: 400 };
pointsArray.push(point1);
pointsArray.push(point2);
pointsArray.push(point3);
pointsArray.push(point4);
const path = new drawing.Path();
path.addPolygon(pointsArray, false);
```

## offset<sup>12+</sup>

offset(dx: number, dy: number): Path

Offsets the path by dx along the x-axis and by dy along the y-axis, and saves the result in the returned path object.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| dx     | number        | Yes   | Offset along the x-axis. A positive value indicates an offset in the positive direction of the x-axis, and a negative value indicates an offset in the negative direction of the x-axis. This parameter is a floating-point number, in physical pixels (px). |
| dy     | number        | Yes   | Offset along the y-axis. A positive value indicates an offset in the positive direction of the y-axis, and a negative value indicates an offset in the negative direction of the y-axis. This parameter is a floating-point number, in physical pixels (px). |

**Returns**

| Type  | Description               |
| ------ | ------------------ |
| [Path](arkts-apis-graphics-drawing-Path.md) | New path generated.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const path = new drawing.Path();
path.moveTo(200, 200);
path.lineTo(300, 300);
const dstPath = path.offset(200, 200);
```

## op<sup>12+</sup>

op(path: Path, pathOp: PathOp): boolean

Combines the current path with path according to the specified path operation type, and saves the result in the current path.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| path    | [Path](arkts-apis-graphics-drawing-Path.md) | Yes  | Path object, which will be combined with the current path.|
| pathOp  | [PathOp](arkts-apis-graphics-drawing-e.md#pathop12)   | Yes    | Enum of the path operation type, used to specify the Boolean operation between two paths.    |

**Returns**

| Type  | Description               |
| ------ | ------------------ |
| boolean | Result of the path combination result. The value **true** means that the path combination is successful, and **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const path = new drawing.Path();
const path2 = new drawing.Path();
path.addCircle(100, 200, 100, drawing.PathDirection.CLOCKWISE);
console.info('get pathOp: ', path2.op(path, drawing.PathOp.DIFFERENCE));
```

## close

close(): void

Closes the path by adding a line segment from the last point to the start point of the path.

**System capability**: SystemCapability.Graphics.Drawing

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path = new drawing.Path();
path.moveTo(10, 10);
path.cubicTo(10, 10, 10, 10, 15, 15);
path.close();
```

## reset

reset(): void

Resets the path data.

**System capability**: SystemCapability.Graphics.Drawing

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path = new drawing.Path();
path.moveTo(10, 10);
path.cubicTo(10, 10, 10, 10, 15, 15);
path.reset();
```

## rewind<sup>20+</sup>

rewind(): void

Rewinds a path by clearing all its points and lines but reserves the memory space.

**System capability**: SystemCapability.Graphics.Drawing

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';
let path = new drawing.Path();
path.moveTo(10, 10);
path.lineTo(20, 20);
path.rewind();
let empty = path.isEmpty();
console.info('empty : ', empty);
```

## isEmpty<sup>20+</sup>

isEmpty(): boolean

Checks whether a path is empty.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type | Description|
| ------ | ---- |
| boolean | Whether a path is empty. **true** means yes; **false** otherwise.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';
let path = new drawing.Path();
path.moveTo(10, 10);
path.lineTo(20, 20);
let isEmpty = path.isEmpty();
console.info('isEmpty:', isEmpty);
```

## isRect<sup>20+</sup>

isRect(rect: common2D.Rect | null): boolean

Checks whether a path forms a rectangle.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| rect   | [common2D.Rect](js-apis-graphics-common2D.md#rect) \| null | Yes   | Rectangle object, used as an output parameter. When the path forms a rectangle, it is rewritten to the rectangle represented by the path; otherwise, it remains unchanged. It can be null, indicating that the rectangle represented by the path is not required. |

**Returns**

| Type | Description|
| ------ | ---- |
| boolean | Whether a path forms a rectangle. **true** means yes; **false** otherwise.|

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

let path = new drawing.Path();
path.moveTo(10, 10);
path.lineTo(20, 10);
let isRect = path.isRect(null);
console.info('isRect: ', isRect);
let rect: common2D.Rect = { left : 100, top : 100, right : 400, bottom : 500 };
path.lineTo(20, 20);
path.lineTo(10, 20);
path.lineTo(10, 10);
isRect = path.isRect(rect);
console.info('isRect: ', isRect);
```

## getLength<sup>12+</sup>

getLength(forceClosed: boolean): number

Obtains the path length.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type | Mandatory| Description    |
| ----- | ------ | ---- | --------- |
| forceClosed  | boolean | Yes | Whether the path is measured as a closed path. The value **true** means that the path is considered closed during measurement, and **false** means that the path is measured based on the actual closed status.|

**Returns**

| Type | Description|
| ------ | ---- |
| number | Path length, in physical pixels (px). |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path = new drawing.Path();
path.arcTo(20, 20, 180, 180, 180, 90);
let len = path.getLength(false);
console.info('path length = ' + len);
```

## getPositionAndTangent<sup>12+</sup>

getPositionAndTangent(forceClosed: boolean, distance: number, position: common2D.Point, tangent: common2D.Point): boolean

Obtains the coordinates and tangent at a distance from the start point of this path.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                                        | Mandatory| Description                           |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| forceClosed | boolean | Yes  | Whether the path is measured as a closed path. The value **true** means that the path is considered closed during measurement, and **false** means that the path is measured based on the actual closed status.                |
| distance | number | Yes | Distance from the start point of the path. A value less than 0 is treated as 0, and a value greater than the path length is treated as the path length. This parameter is a floating-point number, in physical pixels (px). |
| position | [common2D.Point](js-apis-graphics-common2D.md#point12) | Yes  | Coordinates obtained.                 |
| tangent | [common2D.Point](js-apis-graphics-common2D.md#point12) | Yes  | Tangent obtained, where **tangent.x** and **tangent.y** represent the cosine and sine of the tangent of the point, respectively.                |

**Returns**

| Type                 | Description          |
| --------------------- | -------------- |
| boolean |Whether the coordinates and tangent of the point at the distance from the start point of the path are successfully obtained. The value true indicates that the operation is successful, and the value false indicates that the operation fails, in which case position and tangent remain unchanged. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**Example**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
path.moveTo(0, 0);
path.lineTo(0, 700);
path.lineTo(700, 0);
let position: common2D.Point = { x: 0.0, y: 0.0 };
let tangent: common2D.Point = { x: 0.0, y: 0.0 };
if (path.getPositionAndTangent(false, 0.1, position, tangent)) {
  console.info('getPositionAndTangent-----position:  ' + position.x);
  console.info('getPositionAndTangent-----position:  ' + position.y);
  console.info('getPositionAndTangent-----tangent:  ' + tangent.x);
  console.info('getPositionAndTangent-----tangent:  ' + tangent.y);
}
```

## getSegment<sup>18+</sup>

getSegment(forceClosed: boolean, start: number, stop: number, startWithMoveTo: boolean, dst: Path): boolean

Extracts a segment of a path and appends it to a destination path.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                                        | Mandatory| Description                           |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| forceClosed | boolean | Yes  | Whether the path is measured as a closed path. The value **true** means that the path is considered closed during measurement, and **false** means that the path is measured based on the actual closed status.                |
| start | number | Yes | Distance from the start point of the path. The position at this distance from the start point of the path is the start point of the extracted path segment. A value less than 0 is treated as 0, and a value greater than or equal to stop causes the extraction to fail. This parameter is a floating-point number, in physical pixels (px). |
| stop | number | Yes | Distance from the start point of the path. The position at this distance from the start point of the path is the end point of the extracted path segment. A value less than or equal to start causes the extraction to fail, and a value greater than the path length is treated as the path length. This parameter is a floating-point number, in physical pixels (px). |
| startWithMoveTo | boolean | Yes | Whether to execute [moveTo](#moveto) on the target path to move to the start point of the extracted path segment. The value true means to execute moveTo, and false means not to execute moveTo. |
| dst | [Path](arkts-apis-graphics-drawing-Path.md) | Yes  | Destination path. If the extraction succeeds, the segment is appended to the path. If the extraction fails, nothing changes.              |

**Returns**

| Type                 | Description          |
| --------------------- | -------------- |
| boolean |Extraction result. The value **true** means that the extraction is successful, and **false** means the opposite.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
path.moveTo(0, 0);
path.lineTo(0, 700);
path.lineTo(700, 0);
let dstPath: drawing.Path = new drawing.Path();
console.info('getSegment-----result:  ' + path.getSegment(true, 10.0, 20.0, true, dstPath));
```

## isClosed<sup>12+</sup>

isClosed(): boolean

Checks whether a path is closed.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type                 | Description          |
| --------------------- | -------------- |
| boolean | Check result. The value **true** means that the path is closed, and **false** means the opposite.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
path.moveTo(0, 0);
path.lineTo(0, 700);
if (path.isClosed()) {
  console.info('path is closed.');
} else {
  console.info('path is not closed.');
}
```

## getMatrix<sup>12+</sup>

getMatrix(forceClosed: boolean, distance: number, matrix: Matrix, flags: PathMeasureMatrixFlags): boolean

Obtains a transformation matrix at the point that is distance away from the start point of the path, to represent the coordinates and orientation of that point.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                                        | Mandatory| Description                           |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| forceClosed | boolean | Yes  | Whether the path is measured as a closed path. The value **true** means that the path is considered closed during measurement, and **false** means that the path is measured based on the actual closed status.                 |
| distance | number | Yes | Distance from the start point of the path. A value less than 0 is treated as 0, and a value greater than the path length is treated as the path length. This parameter is a floating-point number, in physical pixels (px). |
| matrix | [Matrix](arkts-apis-graphics-drawing-Matrix.md) | Yes | Matrix object used to store the obtained transformation matrix, which represents the coordinate position and orientation information at the specified distance on the path. |
| flags | [PathMeasureMatrixFlags](arkts-apis-graphics-drawing-e.md#pathmeasurematrixflags12) | Yes | Enum of matrix information dimensions, used to specify which dimension information is included in the obtained matrix. |

**Returns**

| Type                 | Description          |
| --------------------- | -------------- |
| boolean | Whether the transformation matrix is obtained. The value **true** indicates that the operation is successful, and **false** indicates the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
path.moveTo(0, 0);
path.lineTo(0, 700);
let matrix = new drawing.Matrix();
if (path.getMatrix(false, 10, matrix, drawing.PathMeasureMatrixFlags.GET_TANGENT_MATRIX)) {
  console.info('path.getMatrix return true');
} else {
  console.info('path.getMatrix return false');
}
```

## buildFromSvgString<sup>12+</sup>

buildFromSvgString(str: string): boolean

Parses the path represented by an SVG string. Standard SVG path data commands (such as M, L, C, Q, A, Z and their relative coordinate forms) are supported. **false** is returned if parsing fails.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                                        | Mandatory| Description                           |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| str | string | Yes | String in the SVG path data format, used to describe the path to draw. Supports SVG path commands such as M/m, L/l, H/h, V/v, C/c, S/s, Q/q, T/t, A/a, and Z/z. For details about the syntax, see the SVG path data specification. If a string that does not conform to the SVG path format is passed in, parsing fails and the API returns false. |

**Returns**

| Type                 | Description          |
| --------------------- | -------------- |
| boolean | Result of the parsing operation. The value **true** means that the operation is successful, and **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
let svgString: string = "M150 100 L75 300 L225 300 Z";
if (path.buildFromSvgString(svgString)) {
  console.info('buildFromSvgString return true');
} else {
  console.info('buildFromSvgString return false');
}
```

## convertToSvgString

convertToSvgString(): string

Converts the path to an SVG string. The output string follows the SVG path data specification mapping.

**System capability**: SystemCapability.Graphics.Drawing

**Model restriction**: This API can be used only in the stage model.

**Since**: 26.0.0

**Return value**

| Type | Description |
| --------------------- | -------------- |
| string | SVG string converted from the path, describing the geometry of the current path in SVG path format. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
path.moveTo(0, 0);
path.lineTo(0, 700);
path.close();
let svgString = path.convertToSvgString();
console.info('svgString: ', svgString);
```

## getPointData

getPointData(): Array\<common2D.Point>

Obtains the point data of the path.

In a path primitive, point data exists as a sequence of numeric values that correspond one-to-one with verb commands, and is used to precisely specify the geometric coordinate positions of drawing operations.

The main types of point data include:

Endpoint coordinates: used together with commands such as [moveTo](#moveto) and [lineTo](#lineto) to define the target position of a line segment or movement.

Control point coordinates: used together with curve commands to define the shape of a Bézier curve (for example, a cubic curve requires two control points and one endpoint).

Closing point: usually no coordinates are provided separately; the path start point is implicitly used by the [close](#close) command.

**System capability**: SystemCapability.Graphics.Drawing

**Model restriction**: This API can be used only in the stage model.

**Since**: 26.0.0

**Return value**

| Type                  | Description           |
| --------------------- | -------------- |
|  Array\<[common2D.Point](js-apis-graphics-common2D.md#point12)> | Returns the array of point data of the path. Each element is a common2D.Point object whose x and y coordinates are floating-point numbers. The theoretical value range is all real numbers, but in practice it is limited by the valid range of the rendering coordinate system (for example, -2^31 to 2^31-1 or the visible screen area); values beyond the range may cause the graphics to be invisible or clipped.|

**Example**

```ts
import { drawing, common2D } from '@kit.ArkGraphics2D';
let path: drawing.Path = new drawing.Path();
path.moveTo(0, 0);
path.lineTo(100, 100);
path.quadTo(150, 150, 200, 100);
let pointData: Array<common2D.Point> = path.getPointData();
console.info('pointData size: ', pointData.length);
console.info('pointData[0].x: ', pointData[0].x);
console.info('pointData[0].y: ', pointData[0].y);
```

## getVerbData

getVerbData(): Array\<PathIteratorVerb>

Obtains the verb data of the path.

In a path primitive, the verb data describes the basic drawing actions during path construction.

The verb data exists in the form of an enum, with each value corresponding to a geometric operation type, for example:

[moveTo](#moveto): Moves the current drawing point to the specified coordinates without generating a line segment.

[lineTo](#lineto): Draws a straight line segment from the current point to the specified point.

[close](#close): Connects the current point to the start point of the path to form a closed area.

**System capability**: SystemCapability.Graphics.Drawing

**Model restriction**: This API can be used only in the stage model.

**Since**: 26.0.0

**Return value**

| Type                  | Description           |
| --------------------- | -------------- |
|Array\<[PathIteratorVerb](arkts-apis-graphics-drawing-e.md#pathiteratorverb18)>| Array of verb data of the path. Each array element corresponds to a basic drawing action type in the path and has a one-to-one correspondence with the point data.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
path.moveTo(0, 0);
path.lineTo(100, 100);
path.close();
let verbData: Array<drawing.PathIteratorVerb> = path.getVerbData();
console.info('verbData size: ', verbData.length);
console.info('verbData[0]: ', verbData[0]);
console.info('verbData[1]: ', verbData[1]);
```

## getConicWeightData

getConicWeightData(): Array\<number>

Obtains the conic weight data of the path.

In a path primitive, conic data is represented in the form of a rational Bézier curve, where each control point carries a weight value. The weight is a geometric parameter of the curve definition.

The main purposes are as follows:

Shape control: The larger the weight value, the closer the curve is to the corresponding control point. When the weight is 1, the curve degenerates into a standard Bézier curve. When the weight is 0, the control point has no effect.

Accurate representation of conic curves: By combining weights with quadratic Bézier curves, conic segments such as arcs, elliptical arcs, and parabolas can be accurately represented without using piecewise approximation or dedicated elliptical arc commands.

Data organization: Weights are usually stored in an array alongside the point data, corresponding to each control point in order, and are used together with the corresponding verb (for example, [conicTo](#conicto12)).

**System capability**: SystemCapability.Graphics.Drawing

**Model restriction**: This API can be used only in the stage model.

**Since**: 26.0.0

**Return value**

| Type                  | Description           |
| --------------------- | -------------- |
| Array\<number> | Floating-point type, with a value range of ≥ 0. When the value is 0.0, the control point is completely invalid, the curve does not pass through this point, and the curve is actually defined by the remaining control points. When the value is 1.0, the curve corresponding to this control point becomes a standard Bézier curve, and the weight produces no additional deformation effect. When the value is greater than 1, the larger the weight value, the closer the curve is to this control point. When the value is less than 1.0 but greater than 0.0, the curve is relatively farther away from this control point. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';
let path: drawing.Path = new drawing.Path();
path.moveTo(0, 0);
path.conicTo(100, 100, 200, 0, 0.5);
let conicWeightData: Array<number> = path.getConicWeightData();
console.info('conicWeightData size: ', conicWeightData.length);
console.info('conicWeightData[0]: ', conicWeightData[0]);
```

## getPathIterator<sup>18+</sup>

getPathIterator(): PathIterator

Obtains the operation iterator of this path.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type                 | Description          |
| --------------------- | -------------- |
| [PathIterator](arkts-apis-graphics-drawing-PathIterator.md) | Iterator object of a path, used to traverse the drawing commands and point data in the path. You can use the iterator to obtain the verb commands and corresponding coordinate points of the path one by one. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
let iter = path.getPathIterator();
```

## approximate<sup>20+</sup>

approximate(acceptableError: number): Array\<number>

Converts the existing path into an approximate path consisting of consecutive line segments.

> **NOTE**
>
> - When acceptableError is 0, the curve path is subdivided extremely finely, which severely affects performance and memory consumption. Setting the error value to 0 is not recommended.
> - When acceptableError is much larger than the path size, the path is extremely simplified, retaining only a few key points such as the start and end points of the path, which may lose the original shape.
> - For curves such as ellipses, when acceptableError is too large, the fitting result usually contains only the start and end points of the segmented Bézier curves of the ellipse, and the ellipse is extremely simplified into a polygon.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                                        | Mandatory| Description                           |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| acceptableError | number | Yes | Acceptable error of each line segment on the path. The value range is greater than or equal to 0. This parameter is a floating-point number. An error is reported if the value is less than 0. The unit is physical pixel (px). |

**Returns**

| Type                 | Description          |
| --------------------- | -------------- |
| Array\<number> | An array of points in the approximate path, which contains at least two points. Each point consists of three values:<br>1. Length ratio of the point to the start point of the path. The value range is [0.0, 1.0].<br>2. X coordinate of a point.<br>3. Y coordinate of a point.|

**Error codes**

For details about the following error code, see [Drawing and Display Error Codes](errorcode-drawing.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 25900001 | Parameter error.Possible causes: Incorrect parameter range. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
path.moveTo(100, 100);
path.lineTo(500, 500);
let points: number[] = path.approximate(0.5);
for (let i = 0; i < points.length; i += 3) {
  console.info('PathApproximate Fraction =' + points[i] + ', X =' + points[i + 1] + ', Y =' + points[i + 2] + '\n');
}
```

## interpolate<sup>20+</sup>

interpolate(other: Path, weight: number, interpolatedPath: Path): boolean

Interpolates between the current path and another path based on the given weight, and stores the result in the target path object. Interpolation succeeds only when the two paths have the same number of points. The target path is created based on the command structure of the current path.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                                        | Mandatory| Description                           |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| other | [Path](arkts-apis-graphics-drawing-Path.md) | Yes| Another path object.|
| weight | number | Yes | Interpolation weight, ranging from 0.0 to 1.0. The value is a floating-point number. |
| interpolatedPath | [Path](arkts-apis-graphics-drawing-Path.md) | Yes| Target path object used to store the interpolation result.|

**Returns**

| Type                 | Description          |
| --------------------- | -------------- |
| boolean | Whether interpolation is successful. **true** means yes; **false** otherwise.|

**Error codes**

For details about the following error code, see [Drawing and Display Error Codes](errorcode-drawing.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 25900001 | Parameter error.Possible causes: Incorrect parameter range. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
path.moveTo(50, 50);
path.lineTo(100, 100);
path.lineTo(200, 200);
let other: drawing.Path = new drawing.Path();
other.moveTo(80, 80);
other.lineTo(300, 300);
let interpolatedPath: drawing.Path = new drawing.Path();
if (path.interpolate(other, 0.0, interpolatedPath)) {
  console.info('interpolate return true');
} else {
  console.info('interpolate return false');
}
```

## isInterpolate<sup>20+</sup>

isInterpolate(other: Path): boolean

Checks whether the existing path and another path are compatible for interpolation in terms of structure and operation sequence. If the paths contain conic operations, the weight values of the operations must be the same.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name  | Type                                        | Mandatory| Description                           |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| other | [Path](arkts-apis-graphics-drawing-Path.md) | Yes| Another path object.|

**Returns**

| Type                 | Description          |
| --------------------- | -------------- |
| boolean | Whether the existing path and another path are compatible for interpolation. **true** means yes; **false** otherwise.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
path.moveTo(0, 0);
path.lineTo(100, 100);
let other: drawing.Path = new drawing.Path();
other.moveTo(0, 1);
other.lineTo(200, 200);
if (path.isInterpolate(other)) {
  console.info('isInterpolate return true');
} else {
  console.info('isInterpolate return false');
}
```

## isEqual

isEqual(path: Path): boolean

Checks whether the current path is equal to another path.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| path | [Path](arkts-apis-graphics-drawing-Path.md) | Yes | Another path object. |

**Return value**

| Type | Description |
| --------------------- | -------------- |
| boolean | Whether the current path is equal to another path. The value **true** indicates that the paths are equal, and **false** indicates that they are not equal. |

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
path.moveTo(0, 0);
path.lineTo(100, 100);
let other: drawing.Path = new drawing.Path();
other.moveTo(0, 0);
other.lineTo(100, 100);
if (path.isEqual(other)) {
  console.info('isEqual return true');
} else {
  console.info('isEqual return false');
}
```

## isInverseFillType<sup>23+</sup>

isInverseFillType(): boolean

Checks whether the fill type of the current path is an inverse fill type. For example, the fill types WINDING and EVEN_ODD are not inverse types, while INVERSE_WINDING and INVERSE_EVEN_ODD are inverse types.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type                 | Description          |
| --------------------- | -------------- |
| boolean | Whether the current path fill type is the inverse fill type. **true** means yes; **false** otherwise.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
path.setFillType(drawing.PathFillType.WINDING);
if (path.isInverseFillType()) {
  console.info('path is inverse FillType.');
} else {
  console.info('path is not inverse FillType.');
}
```

## toggleInverseFillType<sup>23+</sup>

toggleInverseFillType(): void

Switches the fill type of the path to its inverse type. For example, when the WINDING fill type is used, the fill type becomes INVERSE_WINDING after inversion; when the EVEN_ODD fill type is used, the fill type becomes INVERSE_EVEN_ODD after inversion, and vice versa.

**System capability**: SystemCapability.Graphics.Drawing

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
path.setFillType(drawing.PathFillType.WINDING);
path.toggleInverseFillType();
console.info('path fillType = ', path.getFillType());
```