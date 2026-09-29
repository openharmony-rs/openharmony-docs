# PolyToPolyOptions

```TypeScript
export interface PolyToPolyOptions
```

Describes the configuration options for polygon-to-polygon transformation mapping.

**Since:** 12

<!--Device-matrix4-export interface PolyToPolyOptions--><!--Device-matrix4-export interface PolyToPolyOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { matrix4 } from '@kit.ArkUI';
```

## dst

```TypeScript
dst:Array<Point>
```

Vertex coordinates of the target polygon, used to define the target shape of the transformation mapping.

**Type:** Array&lt;[Point](arkts-arkui-matrix4-point-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PolyToPolyOptions-dst:Array<Point>--><!--Device-PolyToPolyOptions-dst:Array<Point>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dstIndex

```TypeScript
dstIndex?: number
```

Start index of the destination point coordinates, used to specify the position in the **dst** array from which destination point obtaining starts.

Default value: **src.length/2**

Value range: [0, +∞)

**Type:** number

**Default:** src.Length/2

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PolyToPolyOptions-dstIndex?: number--><!--Device-PolyToPolyOptions-dstIndex?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pointCount

```TypeScript
pointCount?:number
```

Number of used points. Prerequisite: The number of points in the **src** and **dst** arrays must be no less than the value of **pointCount**. If the number of used points is 0, the identity matrix is returned. If the number is 1, one source point and one destination point are used, and a translation matrix that translates the source point to the destination point is returned. If the number is 2, an affine transformation matrix (including rotation, scaling, and translation) is returned. If the number is 3, an affine transformation matrix (including rotation, scaling, translation, and shearing) is returned. If the number is 4, a perspective transformation matrix is returned. The value does not take effect when it is out of range.

Default value: **0**

Value range: [0, +∞)

**Type:** number

**Default:** 0

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PolyToPolyOptions-pointCount?:number--><!--Device-PolyToPolyOptions-pointCount?:number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: Array<Point>
```

Vertex coordinates of the source polygon, used to define the start shape of the transformation mapping.

**Type:** Array&lt;[Point](arkts-arkui-matrix4-point-i.md)&gt;

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PolyToPolyOptions-src: Array<Point>--><!--Device-PolyToPolyOptions-src: Array<Point>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## srcIndex

```TypeScript
srcIndex?: number
```

Start index of the source point coordinates, used to specify the position in the **src** array from which point obtaining starts. This parameter is passed when the source point needs to be obtained from a specific position in the **src** array. If not passed, the point is obtained from index 0.

Default value: **0**

Value range: [0, +∞)

**Type:** number

**Default:** 0

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PolyToPolyOptions-srcIndex?: number--><!--Device-PolyToPolyOptions-srcIndex?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
