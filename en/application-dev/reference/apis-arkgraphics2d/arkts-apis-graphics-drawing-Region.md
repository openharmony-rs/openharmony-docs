# Class (Region)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=d66ce495242bdf35b08a89dbf23cdf3929953623 translatedAt=2026-08-24T08:13:23.134Z pushedAt=2026-08-29T09:41:38.395Z -->

Region object, used to describe the region information of the drawn graphics. Region supports setting rectangular regions and path regions, and provides operations such as merge operations between regions, intersection determination, translation, and boundary retrieval.

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

## constructor<sup>20+</sup>

constructor()

Constructs a **Region** object.

**System capability**: SystemCapability.Graphics.Drawing

```ts
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
    canvas.drawRegion(region);
    canvas.detachPen();
  }
}
```

## constructor<sup>20+</sup>

constructor(region: Region)

Copies a **Region** object.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| region     | [Region](arkts-apis-graphics-drawing-Region.md) | Yes  | Region to be copied.|

**Example**

```ts
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

## constructor<sup>20+</sup>

constructor(left: number, top: number, right: number, bottom: number)

Constructs a rectangular region.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| left   | number | Yes   | Left side of the rectangular region (X-coordinate of the top-left corner of the rectangle). This parameter must be an integer. 0 indicates the coordinate origin, a negative value indicates located to the left of the coordinate origin, and a positive value indicates located to the right of the coordinate origin. Unit is physical pixels px.|
| top    | number | Yes   | Top side of the rectangular region (Y-coordinate of the top-left corner of the rectangle). This parameter must be an integer. 0 indicates the coordinate origin, a negative value indicates located above the coordinate origin, and a positive value indicates located below the coordinate origin. Unit is physical pixels px. |
| right  | number | Yes   | Right side of the rectangular region (X-coordinate of the bottom-right corner of the rectangle). This parameter must be an integer. 0 indicates the coordinate origin, a negative value indicates located to the left of the coordinate origin, and a positive value indicates located to the right of the coordinate origin. Unit is physical pixels px. |
| bottom | number | Yes   | Bottom side of the rectangular region (Y-coordinate of the bottom-right corner of the rectangle). This parameter must be an integer. 0 indicates the coordinate origin, a negative value indicates located above the coordinate origin, and a positive value indicates located below the coordinate origin. Unit is physical pixels px. |

**Example**

```ts
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

## isEqual<sup>20+</sup>

isEqual(other: Region): boolean

Determine whether the specified region is equal to the current region.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| other      | [Region](arkts-apis-graphics-drawing-Region.md) | Yes   | Other region object used for comparison with the current region. |

**Returns**

| Type   | Description          |
| ------- | -------------- |
| boolean | Check result. **true** if the source rectangle is equal to the destination rectangle; **false** otherwise.|

**Example**

```ts
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

## isComplex<sup>20+</sup>

isComplex(): boolean

Checks whether this region contains multiple rectangles.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type   | Description          |
| ------- | -------------- |
| boolean | Check result. **true** means yes; **false** otherwise.|

**Example**

```ts
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

## isEmpty<sup>20+</sup>

isEmpty(): boolean

Checks whether the existing region is empty.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type   | Description                   |
| ------- | --------------         |
| boolean | Returns the result of whether the current region is empty. true indicates the current region is empty, and false indicates the current region is not empty. |

**Example**

```ts
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

## getBounds<sup>20+</sup>

getBounds(): common2D.Rect

Obtains the boundaries of the existing region.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type   | Description          |
| ------- | -------------- |
| [common2D.Rect](js-apis-graphics-common2D.md#rect) | Bounding rectangle of this region.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let region = new drawing.Region();
let rect = region.getBounds();
```

## getBoundaryPath<sup>20+</sup>

getBoundaryPath(): Path

Obtains a new path that is the boundary of the existing region.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type   | Description          |
| ------- | -------------- |
| [Path](arkts-apis-graphics-drawing-Path.md)  | Path of the boundary of the existing region.|

**Example**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let region = new drawing.Region();
let path = region.getBoundaryPath();
```

## isPointContained<sup>12+</sup>

isPointContained(x: number, y: number): boolean

Checks whether a point is contained in this region.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| x      | number | Yes   | X-coordinate of the test point. This parameter must be an integer. When the input number has a decimal, the fractional part will be discarded. The unit is physical pixels (px). |
| y      | number | Yes   | Y-coordinate of the test point. This parameter must be an integer. When the input number has a decimal, the fractional part will be discarded. The unit is physical pixels (px). |

**Returns**

| Type   | Description          |
| ------- | -------------- |
| boolean | Check result. **true** means yes; **false** otherwise.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
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

## offset<sup>20+</sup>

offset(dx: number, dy: number): void

Translates a region.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| dx      | number | Yes   | Translation amount along the x-axis. A positive value indicates translation in the positive direction of the x-axis, and a negative value indicates translation in the negative direction of the x-axis. This parameter must be an integer. When the input number has a decimal, the fractional part will be discarded. The unit is physical pixels (px). |
| dy      | number | Yes   | Translation amount along the y-axis. A positive value indicates translation in the positive direction of the y-axis, and a negative value indicates translation in the negative direction of the y-axis. This parameter must be an integer. When the input number has a decimal, the fractional part will be discarded. The unit is physical pixels (px). |

**Example**

```ts
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

## isRegionContained<sup>12+</sup>

isRegionContained(other: Region): boolean

Checks whether another region is contained in this region.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| other      | [Region](arkts-apis-graphics-drawing-Region.md) | Yes   | Other region object used to determine whether it is within the current region. |

**Returns**

| Type   | Description          |
| ------- | -------------- |
| boolean | Check result. **true** means yes; **false** otherwise.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
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

## op<sup>12+</sup>

op(region: Region, regionOp: RegionOp): boolean

Performs an operation on this region and another region, and stores the resulting region in this **Region** object.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| region      | [Region](arkts-apis-graphics-drawing-Region.md) | Yes   | Specified region object used to perform an operation with the current region. |
| regionOp      | [RegionOp](arkts-apis-graphics-drawing-e.md#regionop12) | Yes   | Type of the region operation. |

**Returns**

| Type   | Description          |
| ------- | -------------- |
| boolean | Whether the region operation result successfully replaces the current region result. true indicates that the region operation result successfully replaces the current region, and false indicates that the region operation result fails to replace the current region. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
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

## quickReject<sup>12+</sup>

quickReject(left: number, top: number, right: number, bottom: number) : boolean

Quickly determines whether a rectangle and a region do not intersect. In fact, it compares whether the rectangle and the bounding rectangle of the region do not intersect. Therefore, when the bounding rectangles intersect but the actual regions do not, false is returned (that is, they are misjudged as intersecting).

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| left   | number | Yes   | Left side of the rectangular region (X-coordinate of the top-left corner of the rectangle). This parameter must be an integer. When the number has a fractional part, the fractional part will be discarded. The unit is physical pixels (px). |
| top    | number | Yes   | Top side of the rectangular region (Y-coordinate of the top-left corner of the rectangle). This parameter must be an integer. When the number has a fractional part, the fractional part will be discarded. The unit is physical pixels (px). |
| right  | number | Yes   | Right side of the rectangular region (X-coordinate of the bottom-right corner of the rectangle). This parameter must be an integer. When the number has a fractional part, the fractional part will be discarded. The unit is physical pixels (px). |
| bottom | number | Yes   | Bottom side of the rectangular region (Y-coordinate of the bottom-right corner of the rectangle). This parameter must be an integer. When the number has a fractional part, the fractional part will be discarded. The unit is physical pixels (px). |

**Returns**

| Type   | Description          |
| ------- | -------------- |
| boolean | Whether the rectangle does not intersect with the region. true indicates that the rectangle does not intersect with the region, and false indicates that the rectangle intersects with the region. true is also returned when the rectangle intersects with the region only at a point or an edge. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
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

## quickRejectRegion<sup>20+</sup>

quickRejectRegion(region: Region): boolean

Determines whether the current region does not intersect with the specified region. In fact, it compares whether the bounding rectangles of the two regions do not intersect. Therefore, when the bounding rectangles intersect but the actual regions do not, false is returned (that is, they are misjudged as intersecting).

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| region      | [Region](arkts-apis-graphics-drawing-Region.md) | Yes   | Specified region object used to determine whether it does not intersect with the current region. |

**Returns**

| Type   | Description          |
| ------- | -------------- |
| boolean | Whether the current region does not intersect with another region. The value true indicates that the regions do not intersect, and false indicates that they intersect. The value true is also returned when the two regions intersect only at a point or an edge. |

**Example**

```ts
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

## setPath<sup>12+</sup>

setPath(path: Path, clip: Region): boolean

Sets a region that matches the outline of a path within the cropping area.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| path      | [Path](arkts-apis-graphics-drawing-Path.md) | Yes   | Path object used to set the region outline. |
| clip      | [Region](arkts-apis-graphics-drawing-Region.md) | Yes   | Clip region object used to limit the valid range of the path outline. Only the part of the path within the clip region is used to set the region. |

**Returns**

| Type   | Description          |
| ------- | -------------- |
| boolean | Returns the result of whether the region setting is successful. true indicates successful setting, and false indicates failed setting. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
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

## setRegion<sup>20+</sup>

setRegion(region: Region): void

Sets the current region to the specified region.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| region      | [Region](arkts-apis-graphics-drawing-Region.md) | Yes   | Source region object used to set the content of the current region. |

**Example**

```ts
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

## setEmpty<sup>20+</sup>

setEmpty(): void

Set the existing region to empty.

**System capability**: SystemCapability.Graphics.Drawing

**Example**

```ts
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

## setRect<sup>12+</sup>

setRect(left: number, top: number, right: number, bottom: number): boolean

Sets a rectangle.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| left   | number | Yes   | Left side of the rectangular region (X-coordinate of the top-left corner of the rectangle). This parameter must be an integer. When the number has a fractional part, the fractional part will be discarded. The unit is physical pixels (px). |
| top    | number | Yes   | Top side of the rectangular region (Y-coordinate of the top-left corner of the rectangle). This parameter must be an integer. When the number has a fractional part, the fractional part will be discarded. The unit is physical pixels (px). |
| right  | number | Yes   | Right side of the rectangular region (X-coordinate of the bottom-right corner of the rectangle). This parameter must be an integer. When the number has a fractional part, the fractional part will be discarded. The unit is physical pixels (px). |
| bottom | number | Yes   | Bottom side of the rectangular region (Y-coordinate of the bottom-right corner of the rectangle). This parameter must be an integer. When the number has a fractional part, the fractional part will be discarded. The unit is physical pixels (px). |

**Returns**

| Type   | Description          |
| ------- | -------------- |
| boolean | Result of the setting operation. The value **true** means that the setting is successful, and **false** means the opposite.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
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

## isRect<sup>23+</sup>

isRect(): boolean

Checks whether this region is the same as a single rectangle.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Graphics.Drawing

**Returns**

| Type   | Description          |
| ------- | -------------- |
| boolean | Check result. **true** if this region is the same as a single rectangle; **false** otherwise.|

**Example**

```ts
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

## quickContains<sup>23+</sup>

quickContains(left: number, top: number, right: number, bottom: number): boolean

Checks whether this region is the same as a single rectangle and contains the specified rectangle.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| left   | number | Yes   | Left side of the rectangular region. This parameter must be an integer. When the input number has a decimal, the fractional part will be discarded. The unit is physical pixels (px). |
| top    | number | Yes   | Top side of the rectangular region. This parameter must be an integer. When the input number has a decimal, the fractional part will be discarded. The unit is physical pixels (px). |
| right  | number | Yes   | Right side of the rectangular region. This parameter must be an integer. When the input number has a decimal, the fractional part will be discarded. The unit is physical pixels (px). |
| bottom | number | Yes   | Bottom side of the rectangular region. This parameter must be an integer. When the input number has a decimal, the fractional part will be discarded. The unit is physical pixels (px). |

**Returns**

| Type   | Description          |
| ------- | -------------- |
| boolean | Returns the judgment result. true indicates that the current region is equivalent to a single rectangle and contains the specified rectangle; false indicates that the current region is not equivalent to a single rectangle or does not contain the specified rectangle. |

**Example**

```ts
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