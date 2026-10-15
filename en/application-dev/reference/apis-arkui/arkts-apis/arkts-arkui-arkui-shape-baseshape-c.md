# BaseShape

```TypeScript
declare class BaseShape<T> extends CommonShapeMethod<T>
```

This API inherits from [CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md).

**Inheritance/Implementation:** BaseShape extends CommonShapeMethod&lt;T&gt;

**Since:** 12

<!--Device-unnamed-declare class BaseShape<T> extends CommonShapeMethod<T>--><!--Device-unnamed-declare class BaseShape<T> extends CommonShapeMethod<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## height

```TypeScript
height(height: Length): T
```

Sets the height of a shape.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-BaseShape-height(height: Length): T--><!--Device-BaseShape-height(height: Length): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| height | [Length](arkts-arkui-length-t.md) | Yes | Height of the shape.<br>Unit: vp <br>If the value is invalid, 0 vp is used. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current object, used for chained calls. |

## size

```TypeScript
size(size: SizeOptions): T
```

Sets the size of a shape, including both the width and height.

> **NOTE:** 
> 
> - **size()** is equivalent to calling **width()** and **height()** simultaneously to set the width and height.
> 
> - A method called later overrides the corresponding property set by a method called earlier. For example, if
> **size({width:100, height:200})** is called first and then **width(50)** is called, the final width is 50 and the
> height remains 200.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-BaseShape-size(size: SizeOptions): T--><!--Device-BaseShape-size(size: SizeOptions): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | [SizeOptions](arkts-arkui-sizeoptions-i.md) | Yes | Size of the shape. <br>When the type of **width** and **height** is number, the value range is [0, +∞). When the type is string, the value is specified by [Length](arkts-arkui-length-t.md). <br>Unit: vp <br>If the value is invalid, 0 vp is used. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current object, used for chained calls. |

## width

```TypeScript
width(width: Length): T
```

Sets the width of a shape.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-BaseShape-width(width: Length): T--><!--Device-BaseShape-width(width: Length): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | [Length](arkts-arkui-length-t.md) | Yes | Width of the shape.<br>Unit: vp <br>If the value is invalid, 0 vp is used. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current object, used for chained calls. |
