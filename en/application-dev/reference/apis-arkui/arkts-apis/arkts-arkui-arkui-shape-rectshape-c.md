# RectShape

```TypeScript
export declare class RectShape extends BaseShape<RectShape>
```

Represents a rectangle shape used in the **clipShape** and **maskShape** APIs.

This API inherits from [BaseShape](arkts-arkui-arkui-shape-baseshape-c.md).

**Inheritance/Implementation:** RectShape extends BaseShape<RectShape>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: RectShapeOptions | RoundRectShapeOptions)
```

A constructor used to create a **RectShape** object.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RectShapeOptions](arkts-arkui-arkui-shape-rectshapeoptions-i.md) &#124; [RoundRectShapeOptions](arkts-arkui-arkui-shape-roundrectshapeoptions-i.md) | No | Rectangle parameters. |

## radius

```TypeScript
radius(radius: number | string | Array<number | string>): RectShape
```

Sets the radius of the rectangle border corners.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | number &#124; string &#124; Array&lt;number &#124; string&gt; | Yes | Radius of the rectangle border corners. When an array is provided, it should contain exactly four elements, corresponding to the radius of the upper left, upper right, lower left, and lower right corners of the rectangle, respectively. If more than four elements are contained, only the first four are accepted.<br> When the parameter type is number, the valid value range is [0, +∞). When the parameter type is string, the value must conform to the [Length](arkts-arkui-length-t.md) type specification.<br>Unit: vp.<br>If the value is invalid, 0 vp is used. |

**Return value:**

| Type | Description |
| --- | --- |
| [RectShape](arkts-arkui-arkui-shape-rectshape-c.md) | **RectShape** object. |

## radiusHeight

```TypeScript
radiusHeight(rHeight: number | string): RectShape
```

Sets the radius height of the rectangle border corners.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rHeight | number &#124; string | Yes | Radius height of the rectangle border corners.<br> When the parameter type is number, the valid value range is [0, +∞). When the parameter type is string, the value must conform to the [Length](arkts-arkui-length-t.md) type specification.<br>Unit: vp.<br>If the value is invalid, 0 vp is used. |

**Return value:**

| Type | Description |
| --- | --- |
| [RectShape](arkts-arkui-arkui-shape-rectshape-c.md) | **RectShape** object. |

## radiusWidth

```TypeScript
radiusWidth(rWidth: number | string): RectShape
```

Sets the radius width of the rectangle border corners.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rWidth | number &#124; string | Yes | Radius width of the rectangle border corners.<br> When the parameter type is number, the valid value range is [0, +∞). When the parameter type is string, the value must conform to the [Length](arkts-arkui-length-t.md) type specification.<br>Unit: vp.<br>If the value is invalid, 0 vp is used. |

**Return value:**

| Type | Description |
| --- | --- |
| [RectShape](arkts-arkui-arkui-shape-rectshape-c.md) | **RectShape** object. |
