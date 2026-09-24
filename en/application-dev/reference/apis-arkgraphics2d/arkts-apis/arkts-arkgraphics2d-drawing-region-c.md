# Region

```TypeScript
class Region
```

Describes a region, which is used to describe the region where the shape can be drawn.

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

## constructor

```TypeScript
constructor()
```

Constructs a **Region** object.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Examples**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region();
    region.setRect(200, 200, 400, 400);
    let region2 = new drawing.Region(region);
    canvas.drawRegion(region2);
    canvas.detachPen();
  }
}
```

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region(100, 100, 200, 200);
    canvas.drawRegion(region);
    canvas.detachPen();
  }
}
```

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor(region: Region)
```

Copies a **Region** object.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| region | [Region](arkts-arkgraphics2d-drawing-region-c.md) | Yes | Region to be copied. |

**Examples**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region();
    region.setRect(200, 200, 400, 400);
    let region2 = new drawing.Region(region);
    canvas.drawRegion(region2);
    canvas.detachPen();
  }
}
```

<a id="constructor-2"></a>

## constructor

```TypeScript
constructor(left: number, top: number, right: number, bottom: number)
```

Constructs a rectangular region.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| left | number | Yes | Left position of the rectangle (X coordinate of the upper left corner). The value must be an integer. **0** indicates the coordinate origin. A positive value places the point to the right of the coordinate origin, while a negative value places the point to the left. |
| top | number | Yes | Top position of the rectangle (Y coordinate of the upper left corner). The value must be an integer. **0** indicates the coordinate origin. A positive value places the point below the coordinate origin, while a negative value places the point above the coordinate origin. |
| right | number | Yes | Right position of the rectangle (X coordinate of the lower right corner). The value must be an integer. **0** indicates the coordinate origin. A positive value places the point to the right of the coordinate origin, while a negative value places the point to the left. |
| bottom | number | Yes | Bottom position of the rectangle (Y coordinate of the lower right corner). The value must be an integer. **0** indicates the coordinate origin. A positive value places the point below the coordinate origin, while a negative value places the point above the coordinate origin. |

**Examples**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region(100, 100, 200, 200);
    canvas.drawRegion(region);
    canvas.detachPen();
  }
}
```

## getBoundaryPath

```TypeScript
getBoundaryPath(): Path
```

Obtains a new path that is the boundary of the existing region.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [Path](arkts-arkgraphics2d-drawing-path-c.md) | Path of the boundary of the existing region. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let region = new drawing.Region();
let path = region.getBoundaryPath();
```

## getBounds

```TypeScript
getBounds(): common2D.Rect
```

Obtains the boundaries of the existing region.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Bounding rectangle of this region. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let region = new drawing.Region();
let rect = region.getBounds();
```

## isComplex

```TypeScript
isComplex(): boolean
```

Checks whether this region contains multiple rectangles.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. **true** means yes; **false** otherwise. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
import { RenderNode } from '@kit.ArkUI';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region();
    region.setRect(100, 100, 200, 200);
    region.op(new drawing.Region(220, 200, 280, 280), drawing.RegionOp.UNION);
    let flag: boolean = false;
    flag = region.isComplex();
    console.info('flag :', flag);
    canvas.drawRegion(region);
    canvas.detachPen();
  }
}
```

## isEmpty

```TypeScript
isEmpty(): boolean
```

Checks whether the existing region is empty.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. **true** means yes; **false** otherwise. |

**Examples**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region();
    let flag: boolean = region.isEmpty();
    console.info('flag: ', flag);
    region.setRect(100, 100, 400, 400);
    flag = region.isEmpty();
    console.info('flag: ', flag);
    canvas.drawRegion(region);
    canvas.detachPen();
  }
}
```

## isEqual

```TypeScript
isEqual(other: Region): boolean
```

Checks whether another region is equal to this region.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| other | [Region](arkts-arkgraphics2d-drawing-region-c.md) | Yes | **Region** object. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. **true** if the source rectangle is equal to the destination rectangle; **false** otherwise. |

**Examples**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region();
    let other = new drawing.Region();
    region.setRect(100, 100, 400, 400);
    other.setRect(150, 150, 250, 250);
    let flag: boolean = false;
    flag = region.isEqual(other);
    console.info('flag: ', flag);
    canvas.drawRegion(region);
    canvas.drawRegion(other);
    canvas.detachPen();
  }
}
```

## isPointContained

```TypeScript
isPointContained(x: number, y:number): boolean
```

Checks whether a point is contained in this region.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X coordinate of the point. The value must be an integer. If a decimal is passed in, the decimal part is rounded off. |
| y | number | Yes | Y coordinate of the point. The value must be an integer. If a decimal is passed in, the decimal part is rounded off. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. **true** means yes; **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

**Examples**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region();
    region.setRect(100, 100, 400, 400);
    let flag: boolean = false;
    flag = region.isPointContained(200, 200);
    console.info("region isPointContained : " + flag);
    canvas.drawPoint(200, 200);
    canvas.drawRegion(region);
    canvas.detachPen();
  }
}
```

## isRect

```TypeScript
isRect(): boolean
```

Checks whether this region is the same as a single rectangle.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. **true** if this region is the same as a single rectangle; **false** otherwise. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
import { RenderNode } from '@kit.ArkUI';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region();
    let flag: boolean = false;
    flag = region.isRect();
    console.info('flag :', flag);
    region.setRect(100, 100, 200, 200);
    flag = region.isRect();
    console.info('flag :', flag);
    let other = new drawing.Region(220, 200, 280, 280);
    region.op(other, drawing.RegionOp.UNION);
    flag = region.isRect();
    console.info('flag :', flag);
    canvas.drawRegion(region);
    canvas.detachPen();
  }
}
```

## isRegionContained

```TypeScript
isRegionContained(other: Region): boolean
```

Checks whether another region is contained in this region.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| other | [Region](arkts-arkgraphics2d-drawing-region-c.md) | Yes | **Region** object. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. **true** means yes; **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

**Examples**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region();
    let other = new drawing.Region();
    region.setRect(100, 100, 400, 400);
    other.setRect(150, 150, 250, 250);
    let flag: boolean = false;
    flag = region.isRegionContained(other);
    console.info("region isRegionContained : " + flag);
    canvas.drawRegion(region);
    canvas.drawRegion(other);
    canvas.detachPen();
  }
}
```

## offset

```TypeScript
offset(dx: number, dy: number): void
```

Translates a region.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dx | number | Yes | X offset. A positive number indicates an offset towards the positive direction of the X axis, and a negative number indicates an offset towards the negative direction of the X axis. The value is an integer. |
| dy | number | Yes | Y offset. A positive number indicates an offset towards the positive direction of the Y axis, and a negative number indicates an offset towards the negative direction of the Y axis. The value is an integer. |

**Examples**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region();
    region.setRect(100, 100, 400, 400);
    region.offset(10, 20);
    canvas.drawPoint(200, 200);
    canvas.drawRegion(region);
    canvas.detachPen();
  }
}
```

## op

```TypeScript
op(region: Region, regionOp: RegionOp): boolean
```

Performs an operation on this region and another region, and stores the resulting region in this **Region** object.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| region | [Region](arkts-arkgraphics2d-drawing-region-c.md) | Yes | **Region** object. |
| regionOp | [RegionOp](arkts-arkgraphics2d-drawing-regionop-e.md) | Yes | Operation mode of the region. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. The value **true** means that the resulting region is stored in the current **Region** object, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

**Examples**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region();
    region.setRect(200, 200, 400, 400);
    let othregion = new drawing.Region();
    othregion.setRect(110, 110, 240, 240);
    let flag: boolean = false;
    flag = region.op(othregion, drawing.RegionOp.REPLACE);
    console.info("region op : " + flag);
    canvas.drawRegion(region);
    canvas.detachPen();
  }
}
```

## quickContains

```TypeScript
quickContains(left: number, top: number, right: number, bottom: number): boolean
```

Checks whether this region is the same as a single rectangle and contains the specified rectangle.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| left | number | Yes | Left position of the rectangle. The value must be an integer. If a decimal is passed in, the decimal part is rounded off. |
| top | number | Yes | Top position of the rectangle. The value must be an integer. If a decimal is passed in, the decimal part is rounded off. |
| right | number | Yes | Right position of the rectangle. The value must be an integer. If a decimal is passed in, the decimal part is rounded off. |
| bottom | number | Yes | Bottom position of the rectangle. The value must be an integer. If a decimal is passed in, the decimal part is rounded off. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. **true** if the current region is the same as a single rectangle and contains the specified rectangle; **false** otherwise. |

**Examples**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
import { RenderNode } from '@kit.ArkUI';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region();
    let flag: boolean = false;
    flag = region.quickContains(10, 10, 100, 100);
    console.info('flag :', flag);
    let other = new drawing.Region();
    other.setRect(100, 100, 200, 200);
    flag = other.quickContains(10, 10, 100, 100);
    console.info('flag :', flag);
    canvas.drawRegion(region);
    canvas.drawRegion(other);
    canvas.detachPen();
  }
}
```

## quickReject

```TypeScript
quickReject(left: number, top: number, right: number, bottom: number): boolean
```

Checks whether a rectangle do not intersect with this region. Actually, this API determines whether the rectangle does not intersect with the bounding rectangle of the region, and therefore the result may not be accurate.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| left | number | Yes | Left position of the rectangle. The value must be an integer. If a decimal is passed in, the decimal part is rounded off. |
| top | number | Yes | Top position of the rectangle. The value must be an integer. If a decimal is passed in, the decimal part is rounded off. |
| right | number | Yes | Right position of the rectangle. The value must be an integer. If a decimal is passed in, the decimal part is rounded off. |
| bottom | number | Yes | Bottom position of the rectangle. The value must be an integer. If a decimal is passed in, the decimal part is rounded off. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. **true** means that the two do not intersect; **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

**Examples**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region();
    region.setRect(100, 100, 400, 400);
    let flag: boolean = false;
    flag = region.quickReject(50, 50, 70, 70);
    console.info("region quickReject : " + flag);
    canvas.drawRegion(region);
    canvas.detachPen();
  }
}
```

## quickRejectRegion

```TypeScript
quickRejectRegion(region: Region): boolean
```

Checks whether the existing region does not intersect with another region. Actually, the outer rectangles of the two regions are compared to determine whether they do not intersect. Therefore, there may be an error.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| region | [Region](arkts-arkgraphics2d-drawing-region-c.md) | Yes | **Region** object. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result. **true** if the regions do not intersect; **false** otherwise. The value **true** is returned only if the regions intersect with each other by point or edge. |

**Examples**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region();
    let region2 = new drawing.Region();
    region2.setRect(100, 100, 400, 400);
    let flag: boolean = false;
    flag = region.quickRejectRegion(region2);
    console.info("region quickRejectRegion: " + flag);
    canvas.drawRegion(region);
    canvas.detachPen();
  }
}
```

## setEmpty

```TypeScript
setEmpty(): void
```

Set the existing region to empty.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Examples**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    let region = new drawing.Region();
    region.setRect(100, 100, 200, 200);
    let isEmpty = region.isEmpty();
    console.info("isEmpty :" + isEmpty);
    region.setEmpty();
    isEmpty = region.isEmpty();
    console.info("isEmpty :" + isEmpty);
  }
}
```

## setPath

```TypeScript
setPath(path: Path, clip: Region): boolean
```

Sets a region that matches the outline of a path within the cropping area.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | [Path](arkts-arkgraphics2d-drawing-path-c.md) | Yes | **Path** object. |
| clip | [Region](arkts-arkgraphics2d-drawing-region-c.md) | Yes | **Region** object. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Result of the setting operation. The value **true** is returned if the corked status is successfully set; otherwise, **false** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

**Examples**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region();
    let path = new drawing.Path();
    region.setRect(100, 100, 400, 400);
    path.arcTo(50, 50, 300, 300, 0, 359);
    let flag: boolean = false;
    flag = region.setPath(path, region);
    console.info("region setPath : " + flag);
    canvas.drawRegion(region);
    canvas.detachPen();
  }
}
```

## setRect

```TypeScript
setRect(left: number, top: number, right: number, bottom: number): boolean
```

Sets a rectangle.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| left | number | Yes | Left position of the rectangle. The value must be an integer. If a decimal is passed in, the decimal part is rounded off. |
| top | number | Yes | Top position of the rectangle. The value must be an integer. If a decimal is passed in, the decimal part is rounded off. |
| right | number | Yes | Right position of the rectangle. The value must be an integer. If a decimal is passed in, the decimal part is rounded off. |
| bottom | number | Yes | Bottom position of the rectangle. The value must be an integer. If a decimal is passed in, the decimal part is rounded off. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Result of the setting operation. The value **true** means that the setting is successful, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

**Examples**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region();
    let flag: boolean = false;
    flag = region.setRect(50, 50, 300, 300);
    console.info("region setRect : " + flag);
    canvas.drawRegion(region);
    canvas.detachPen();
  }
}
```

## setRegion

```TypeScript
setRegion(region: Region): void
```

Sets the existing region to another region.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| region | [Region](arkts-arkgraphics2d-drawing-region-c.md) | Yes | Region to be set. |

**Examples**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region();
    region.setRect(100, 100, 200, 200);
    let region2 = new drawing.Region();
    region2.setRegion(region);
    canvas.drawRegion(region2);
    canvas.detachPen();
  }
}
```
