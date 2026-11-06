# Class (PathEffect)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=cfa59f2ade5e74278a5dbd3dbd7bab536925f809 translatedAt=2026-08-24T08:05:27.471Z pushedAt=2026-08-31T07:16:10.557Z -->

A path effect object used to create various path effects, including dotted line, rounded corner, discrete, sum, and compose path effects. It can be applied to a pen through [Pen.setPathEffect](arkts-apis-graphics-drawing-Pen.md#setpatheffect12) to change the rendering style of a path when drawing it.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 12.
>
> - This module uses the physical pixel unit, px.
>
> - The module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

## Modules to Import

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## createDashPathEffect<sup>12+</sup>

static createDashPathEffect(intervals: Array\<number>, phase: number): PathEffect

Creates a **PathEffect** object that converts a path into a dotted line, generating evenly spaced dashes by specifying an array of ON/OFF lengths. When a custom shape is required to fill the dash segments, use [createPathDashEffect](#createpathdasheffect18).

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name    | Type          | Mandatory   | Description                                              |
| ---------- | ------------- | ------- | -------------------------------------------------- |
| intervals  | Array\<number> | Yes      | Array of the lengths of the ON (solid) and OFF (blank) parts of the dash. The number of array elements must be an even number greater than or equal to 2, and the elements must be positive integers. The unit is physical pixel (px). |
| phase      | number         | Yes      | Offset used during drawing to adjust the start position of the dash pattern along the path. This parameter is a floating-point number, and the offset produces a displacement effect relative to the dash pattern defined by intervals. The unit is physical pixel (px). |

**Returns**

| Type                     | Description                  |
| ------------------------- | --------------------- |
| [PathEffect](arkts-apis-graphics-drawing-PathEffect.md) | Creates a dashed path effect object, which can be applied to a pen through [Pen.setPathEffect](arkts-apis-graphics-drawing-Pen.md#setpatheffect12) to change the path rendering style. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let intervals = [10, 5];
    let effect = drawing.PathEffect.createDashPathEffect(intervals, 5);
  }
}
```

## createPathDashEffect<sup>18+</sup>

static createPathDashEffect(path: Path, advance: number, phase: number, style: PathDashStyle): PathEffect

Creates a dashed path effect object generated from the shape described by a path. Unlike [createDashPathEffect](#createdashpatheffect12), which uses an intervals array to specify ON/OFF lengths to create evenly spaced dashes, this API specifies the graphic shape of the dash segments through a Path.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name    | Type          | Mandatory   | Description                                              |
| ---------- | ------------- | ------- | -------------------------------------------------- |
| path  | [Path](arkts-apis-graphics-drawing-Path.md) | Yes| Path that defines the shape to be used for filling each dash in the pattern.|
| advance | number | Yes | Step length of the dash segment. The value must be greater than 0; otherwise, an error code is thrown. The unit is physical pixel (px). |
| phase | number | Yes | Offset of the shape within the dash segment relative to the dash step length. This parameter is a floating-point number. The effect is to first take the absolute value of the offset and then take the modulo of the step length. The unit is physical pixel (px). |
| style | [PathDashStyle](arkts-apis-graphics-drawing-e.md#pathdashstyle18) | Yes | Specifies the style of the dash effect, which determines how the dash segment shape is transformed along the path. |

**Returns**

| Type                     | Description                  |
| ------------------------- | --------------------- |
| [PathEffect](arkts-apis-graphics-drawing-PathEffect.md) | Returns the created dashed path effect object, which can be applied to a pen through [Pen.setPathEffect](arkts-apis-graphics-drawing-Pen.md#setpatheffect12) to change the path rendering style. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3. Parameter verification failed. |

**Example**

```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let pen = new drawing.Pen();
    const penColor: common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
    pen.setColor(penColor);
    pen.setStrokeWidth(10);
    pen.setAntiAlias(true);

    const path = new drawing.Path();
    path.moveTo(100, 100);
    path.lineTo(150, 50);
    path.lineTo(200, 100);

    const dashShapePath = new drawing.Path();
    dashShapePath.moveTo(0, 0);
    dashShapePath.lineTo(10, 0);
    dashShapePath.lineTo(20, 10);
    dashShapePath.lineTo(0, 10);

    let pathEffect: drawing.PathEffect = drawing.PathEffect.createPathDashEffect(dashShapePath, 50, -30,
        drawing.PathDashStyle.MORPH);
    pen.setPathEffect(pathEffect);

    canvas.attachPen(pen);
    canvas.drawPath(path);
    canvas.detachPen();
  }
}
```

## createSumPathEffect<sup>18+</sup>

static createSumPathEffect(firstPathEffect: PathEffect, secondPathEffect: PathEffect): PathEffect

Creates a path effect that superimposes two effects. Unlike [createComposePathEffect](#createcomposepatheffect18), this API applies the two effects independently and then simply overlays them.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name    | Type          | Mandatory   | Description                                              |
| ---------- | ------------- | ------- | -------------------------------------------------- |
| firstPathEffect | [PathEffect](arkts-apis-graphics-drawing-PathEffect.md) | Yes| First path effect.|
| secondPathEffect | [PathEffect](arkts-apis-graphics-drawing-PathEffect.md) | Yes| Second path effect.|

**Returns**

| Type                     | Description                  |
| ------------------------- | --------------------- |
| [PathEffect](arkts-apis-graphics-drawing-PathEffect.md) | Returns the created compose path effect object, which can be applied to a pen through [Pen.setPathEffect](arkts-apis-graphics-drawing-Pen.md#setpatheffect12) to change the path rendering style. |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let intervals = [10, 5];
    let firstPathEffect = drawing.PathEffect.createDashPathEffect(intervals, 5);
    let secondPathEffect = drawing.PathEffect.createDashPathEffect(intervals, 10);
    let effect = drawing.PathEffect.createSumPathEffect(firstPathEffect, secondPathEffect);
  }
}
```

## createCornerPathEffect<sup>12+</sup>

static createCornerPathEffect(radius: number): PathEffect

Creates a path effect object that turns the corners of a path into rounded corners with a specified radius. This effect inserts an arc segment with the specified radius at each corner of the path, replacing the original sharp corners with smooth rounded transitions.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name    | Type          | Mandatory   | Description                                              |
| ---------- | ------------- | ------- | -------------------------------------------------- |
| radius     | number        | Yes      | Radius of the corner. The value range is greater than 0. This parameter is a floating-point number, in physical pixels (px).                |

**Returns**

| Type                     | Description                  |
| ------------------------- | --------------------- |
| [PathEffect](arkts-apis-graphics-drawing-PathEffect.md) | Returns the created rounded corner path effect object, which can be applied to a pen through [Pen.setPathEffect](arkts-apis-graphics-drawing-Pen.md#setpatheffect12) to change the path rendering style. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let effect = drawing.PathEffect.createCornerPathEffect(30);
  }
}
```

## createDiscretePathEffect<sup>18+</sup>

static createDiscretePathEffect(segLength: number, dev: number, seedAssist?: number): PathEffect

Creates a path effect object that breaks a path into discrete line segments and randomly offsets their endpoints.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name    | Type          | Mandatory   | Description                                              |
| ---------- | ------------- | ------- | -------------------------------------------------- |
| segLength  | number        | Yes      | Length of each scatter operation along the path. This parameter is a floating-point number. A negative value or 0 has no effect. The unit is physical pixel (px). |
| dev        | number        | Yes      | Maximum deviation of the endpoint of each discrete line segment during drawing. This deviation is a floating-point number. The unit is physical pixel (px). |
| seedAssist | number        | No      | Pseudo-random seed used to generate the discrete effect, which affects the random distribution pattern of path scattering. Pass a specified seed value when a reproducible discrete effect is required. This parameter can be omitted when no specific random distribution pattern is required, and the default value is 0 when omitted. This parameter is a 32-bit unsigned integer. When the value is out of range, it is processed according to the 32-bit unsigned integer overflow wraparound rule. |

**Returns**

| Type                     | Description                  |
| ------------------------- | --------------------- |
| [PathEffect](arkts-apis-graphics-drawing-PathEffect.md) | Returns the created discrete path effect object, which can be applied to a pen through [Pen.setPathEffect](arkts-apis-graphics-drawing-Pen.md#setpatheffect12) to change the path rendering style. |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let effect = drawing.PathEffect.createDiscretePathEffect(100, -50, 0);
  }
}
```

## createComposePathEffect<sup>18+</sup>

static createComposePathEffect(outer: PathEffect, inner: PathEffect): PathEffect

Creates a composite path effect object that applies the inner path effect first and then the outer path effect.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type                       | Mandatory| Description                            |
| ------ | --------------------------- | ---- | -------------------------------- |
| outer  | [PathEffect](arkts-apis-graphics-drawing-PathEffect.md) | Yes   | The outer path effect in the compose path effect, which is superimposed after the inner path effect is applied and determines the final overlay effect. |
| inner  | [PathEffect](arkts-apis-graphics-drawing-PathEffect.md) | Yes   | The inner path effect in the compose path effect, which is first applied to the original path as the first-layer effect and is then superimposed by the outer path effect. |

**Returns**

| Type                     | Description                  |
| ------------------------- | --------------------- |
| [PathEffect](arkts-apis-graphics-drawing-PathEffect.md) | Returns the created composite path effect object, which can be applied to a pen through [Pen.setPathEffect](arkts-apis-graphics-drawing-Pen.md#setpatheffect12) to change the path rendering style. |

**Example**

```ts
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let outerPathEffect = drawing.PathEffect.createCornerPathEffect(100);
    let innerPathEffect = drawing.PathEffect.createCornerPathEffect(10);
    let effect = drawing.PathEffect.createComposePathEffect(outerPathEffect, innerPathEffect);
  }
}
```