# RectShape

```TypeScript
export declare class RectShape extends BaseShape<RectShape>
```

Represents a rectangle shape used in the **clipShape** and **maskShape** APIs.

This API inherits from [BaseShape](arkts-arkui-arkui-shape-baseshape-c.md).

**Inheritance/Implementation:** RectShape extends BaseShape&lt;RectShape&gt;

**Since:** 12

<!--Device-unnamed-export declare class RectShape extends BaseShape<RectShape>--><!--Device-unnamed-export declare class RectShape extends BaseShape<RectShape>-End-->

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

> **NOTE:** 
> 
> - **radius**, **radiusWidth**, and **radiusHeight** in the constructor parameters set the same properties as
> **radius()**, **radiusWidth()**, and **radiusHeight()**.
> 
> - A method call overrides the corresponding property value set in the constructor.
> 
> - You are advised to set the initial parameters through the constructor first, and then perform additional configuration or overriding through the methods.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-RectShape-constructor(options?: RectShapeOptions | RoundRectShapeOptions)--><!--Device-RectShape-constructor(options?: RectShapeOptions | RoundRectShapeOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [RectShapeOptions](arkts-arkui-arkui-shape-rectshapeoptions-i.md) &#124; [RoundRectShapeOptions](arkts-arkui-arkui-shape-roundrectshapeoptions-i.md) | No | Rectangle parameters. If not passed in, the default size is used, with a default width of 0 vp, a default height of 0 vp, and a default corner radius of 0 vp. |

## radius

```TypeScript
radius(radius: number | string | Array<number | string>): RectShape
```

Sets the radius of the rectangle border corners. After setting, the arc width and height of each corner are equal (circular arc). Unlike **radiusWidth** or **radiusHeight**, which sets the arc width or height separately (allowing the elliptical arc), **radius** can specify the radius values of the four corners separately through an array. Use **radius** when circular corners are required, and use **radiusWidth** and **radiusHeight** when elliptical corners are required.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-RectShape-radius(radius: number | string | Array<number | string>): RectShape--><!--Device-RectShape-radius(radius: number | string | Array<number | string>): RectShape-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | number &#124; string &#124; Array&lt;number &#124; string&gt; | Yes | Corner radius of the rectangle shape. Only the first four elements of the array are accepted, which represent the corner radii of the top-left, top-right, bottom- left, and bottom-right corners of the rectangle, respectively. <br>If the type is number, the value range is [0, +∞); if the type is string, the value is specified by [Length](arkts-arkui-length-t.md). <br>Unit: vp <br>If the value is abnormal, 0 vp is used. |

**Return value:**

| Type | Description |
| --- | --- |
| [RectShape](arkts-arkui-arkui-shape-rectshape-c.md) | **RectShape** object with the width of the corner radius set, which can be used for chained calls to further configure the rectangle shape. |

## radiusHeight

```TypeScript
radiusHeight(rHeight: number | string): RectShape
```

Sets the radius height of the rectangle border corners.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-RectShape-radiusHeight(rHeight: number | string): RectShape--><!--Device-RectShape-radiusHeight(rHeight: number | string): RectShape-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rHeight | number &#124; string | Yes | Height of the corner radius of the rectangle shape. If the type is number, the value range is [0, +∞); if the type is string, the value is specified by [Length](arkts-arkui-length-t.md). Unit: vp. If the value is abnormal, 0 vp is used. |

**Return value:**

| Type | Description |
| --- | --- |
| [RectShape](arkts-arkui-arkui-shape-rectshape-c.md) | **RectShape** object with the height of the corner radius set, which can be used for chained calls to further configure the rectangle shape. |

## radiusWidth

```TypeScript
radiusWidth(rWidth: number | string): RectShape
```

Sets the radius width of the rectangle border corners.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-RectShape-radiusWidth(rWidth: number | string): RectShape--><!--Device-RectShape-radiusWidth(rWidth: number | string): RectShape-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rWidth | number &#124; string | Yes | Width of the corner radius of the rectangle shape. <br>If the type is number, the value range is [0, +∞); if the type is string, the value is specified by [Length](arkts-arkui-length-t.md). <br>Unit: vp <br>If the value is abnormal, 0 vp is used. |

**Return value:**

| Type | Description |
| --- | --- |
| [RectShape](arkts-arkui-arkui-shape-rectshape-c.md) | **RectShape** object with the corner radius set, which can be used for chained calls to further configure the rectangle shape. |
