# PointUtils

This class offers a comprehensive set of operations for handling common2D Point objects.

**Since:** 26.0.0

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## negate

```TypeScript
static negate(point: common2D.Point): void
```

Negates the point's coordinates.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| point | [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md) | Yes | Specifies the point to be negated. |

## offset

```TypeScript
static offset(point: common2D.Point, dx: number, dy: number): void
```

Offsets the point's coordinates by dx, dy.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| point | [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md) | Yes | Specifies the point to be offset. |
| dx | number | Yes | Indicates the distance to offset on the x-axis in pixels. |
| dy | number | Yes | Indicates the distance to offset on the y-axis in pixels. |
