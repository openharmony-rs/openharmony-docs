# PathEffect

```TypeScript
class PathEffect
```

Implements a path effect.

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

## createComposePathEffect

```TypeScript
static createComposePathEffect(outer: PathEffect, inner: PathEffect): PathEffect
```

Creates a path effect by sequentially applying the inner effect and then the outer effect.

**Since:** 18

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| outer | [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | Yes | Path effect that is applied second, overlaying the first effect. |
| inner | [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | Yes | Inner path effect that is applied first. |

**Return value:**

| Type | Description |
| --- | --- |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | **PathEffect** object created. |

**Examples**

```TypeScript
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

## createCornerPathEffect

```TypeScript
static createCornerPathEffect(radius: number): PathEffect
```

Creates a path effect that transforms the sharp angle between line segments into a rounded corner with the specified radius.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | number | Yes | Radius of the rounded corner. The value must be greater than 0. The value is a floating point number. |

**Return value:**

| Type | Description |
| --- | --- |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | **PathEffect** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let effect = drawing.PathEffect.createCornerPathEffect(30);
  }
}
```

## createDashPathEffect

```TypeScript
static createDashPathEffect(intervals: Array<number>, phase: number): PathEffect
```

Creates a **PathEffect** object that converts a path into a dotted line.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| intervals | Array&lt;number&gt; | Yes | Array of the lengths of the ON (solid line) and OFF (blank) parts of the dashed path. The number of elements in the array must be an even number and greater than or equal to 2. The value of this parameter is a positive integer. |
| phase | number | Yes | Offset used during drawing. The value is a floating point number. |

**Return value:**

| Type | Description |
| --- | --- |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | **PathEffect** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
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

## createDiscretePathEffect

```TypeScript
static createDiscretePathEffect(segLength: number, dev: number, seedAssist?: number): PathEffect
```

Creates an effect that segments the path and scatters the segments in an irregular pattern along the path.

**Since:** 18

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| segLength | number | Yes | Distance along the path at which each segment is fragmented. The value is a floating point number. If a negative number or the value **0** is passed in, no effect is created. |
| dev | number | Yes | Maximum amount by which the end points of the segments can be randomly displaced during rendering. The value is a floating-point number. |
| seedAssist | number | No | Optional parameter to assist in generating a pseudo-random seed for the effect. The default value is **0**, and the value is a 32-bit unsigned integer. |

**Return value:**

| Type | Description |
| --- | --- |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | **PathEffect** object created. |

**Examples**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let effect = drawing.PathEffect.createDiscretePathEffect(100, -50, 0);
  }
}
```

## createPathDashEffect

```TypeScript
static createPathDashEffect(path: Path, advance: number, phase: number, style: PathDashStyle): PathEffect
```

Creates a dashed path effect based on the shape described by a path.

**Since:** 18

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path](arkts-arkgraphics2d-drawing-path-c.md) | Yes | Path that defines the shape to be used for filling each dash in the pattern. |
| advance | number | Yes | Distance between two consecutive dashes. The value is a floating point number greater than 0. Otherwise, an error code is thrown. |
| phase | number | Yes | Starting offset of the dash pattern. The value is a floating point number. The actual offset used is the absolute value of this value modulo the value of **advance**. |
| style | [PathDashStyle](arkts-arkgraphics2d-drawing-pathdashstyle-e.md) | Yes | Style of the dashed path effect. |

**Return value:**

| Type | Description |
| --- | --- |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | **PathEffect** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
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

## createSumPathEffect

```TypeScript
static createSumPathEffect(firstPathEffect: PathEffect, secondPathEffect: PathEffect): PathEffect
```

Creates an overlay path effect based on two distinct path effects. Different from **createComposePathEffect**, this API applies each effect separately and then displays them as a simple overlay.

**Since:** 18

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| firstPathEffect | [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | Yes | First path effect. |
| secondPathEffect | [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | Yes | Second path effect. |

**Return value:**

| Type | Description |
| --- | --- |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | **PathEffect** object created. |

**Examples**

```TypeScript
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
