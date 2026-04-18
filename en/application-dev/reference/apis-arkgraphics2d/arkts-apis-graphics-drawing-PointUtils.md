# Class (PointUtils)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

Provides tools for processing coordinate points.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this Class are supported since API version 26.0.0.
>
> - This module uses the physical pixel unit, px.
>
> - The module operates under a single-threaded model. The caller needs to manage thread safety and context state transitions.

## Modules to Import

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## negate

static negate(point: common2D.Point): void

Negates the coordinates of a point.

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| point   | [common2D.Point](js-apis-graphics-common2D.md#point12) | Yes  | Point to be negated.|

**Example**:

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

let point: common2D.Point = { x: 10, y: 20 };
drawing.PointUtils.negate(point);
console.info('point.x:', point.x);
console.info('point.y:', point.y);
```

## offset

static offset(point: common2D.Point, dx: number, dy: number): void

Offsets a specified coordinate point by a certain distance along the x-axis and y-axis.

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Graphics.Drawing

**Parameters**

| Name| Type   | Mandatory| Description          |
| ------ | ------ | ---- | -------------- |
| point   | [common2D.Point](js-apis-graphics-common2D.md#point12) | Yes  | Point to be offset.|
| dx   | number | Yes  | Horizontal distance to translate. A positive number indicates a translation towards the positive direction of the X axis, and a negative number indicates a translation towards the negative direction of the X axis. The value is a floating point number. The unit is physical pixel (px).|
| dy    | number | Yes  | Vertical distance to translate. A positive number indicates a translation towards the positive direction of the Y axis, and a negative number indicates a translation towards the negative direction of the Y axis. The value is a floating point number. The unit is physical pixel (px).|

**Example**:

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

let point: common2D.Point = { x: 10, y: 20 };
drawing.PointUtils.offset(point, 5, 10);
console.info('point.x:', point.x);
console.info('point.y:', point.y);
```
