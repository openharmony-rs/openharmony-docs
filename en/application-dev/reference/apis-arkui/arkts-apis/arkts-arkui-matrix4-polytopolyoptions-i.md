# PolyToPolyOptions

Describes the configuration options for polygon-to-polygon transformation mapping.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## dst

```TypeScript
dst:Array<Point>
```

Coordinates of the destination point.

**Type:** Array&lt;[Point](arkts-arkui-matrix4-point-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dstIndex

```TypeScript
dstIndex?: number
```

Start index of the destination point coordinates.

Default value: **src.length/2**.

Value range: [0, +∞).

**Type:** number

**Default:** src.Length/2

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pointCount

```TypeScript
pointCount?:number
```

Number of used points. **0**: returns an identity matrix. **1**: returns a translation matrix. 2-4: returns a transformation matrix.

Default value: **0**.

Value range: [0, +∞).

**Type:** number

**Default:** 0

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: Array<Point>
```

Coordinates of the source point.

**Type:** Array&lt;[Point](arkts-arkui-matrix4-point-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## srcIndex

```TypeScript
srcIndex?: number
```

Start index of the source point coordinates.

Default value: **0**.

Value range: [0, +∞).

**Type:** number

**Default:** 0

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
