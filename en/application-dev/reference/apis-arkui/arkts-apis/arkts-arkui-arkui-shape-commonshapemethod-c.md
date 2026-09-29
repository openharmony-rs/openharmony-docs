# CommonShapeMethod

```TypeScript
declare class CommonShapeMethod<T>
```

A base class that provides common methods such as offset, fill, and position settings for shapes.

**Since:** 12

<!--Device-unnamed-declare class CommonShapeMethod<T>--><!--Device-unnamed-declare class CommonShapeMethod<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## fill

```TypeScript
fill(color: ResourceColor): T
```

Sets the fill color of a shape.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-CommonShapeMethod-fill(color: ResourceColor): T--><!--Device-CommonShapeMethod-fill(color: ResourceColor): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [ResourceColor](arkts-arkui-resourcecolor-t.md) | Yes | Opacity of the fill area of the shape. Black indicates fully transparent, and white indicates fully opaque. In the maskShape scenario, the fill color determines the opacity effect of the mask. |

**Return value:**

| Type | Description |
| --- | --- |
| T | The current object, used for chained calls. |

## offset

```TypeScript
offset(offset: Position): T
```

Sets the coordinate offset relative to the component's layout position.

> **NOTE:** 
> 
> - **offset()** sets a relative offset, while **position()** sets an absolute position. The two positioning mechanisms are different.
> 
> - You are advised to select one of the two positioning methods based on the scenario, and avoid using both at the same time, which may make the positioning result unpredictable.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-CommonShapeMethod-offset(offset: Position): T--><!--Device-CommonShapeMethod-offset(offset: Position): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | Position | Yes | Coordinate offset relative to the component's layout position. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current object, used for chained calls. |

## position

```TypeScript
position(position: Position): T
```

Sets the absolute position of a shape. Unlike **offset** (setting the relative offset), **position** sets absolute coordinates. Use **position** when the shape needs to be precisely positioned, and use **offset** when fine-tuning is needed based on the existing layout position.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-CommonShapeMethod-position(position: Position): T--><!--Device-CommonShapeMethod-position(position: Position): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | Position | Yes | Position of the shape. |

**Return value:**

| Type | Description |
| --- | --- |
| T | The current object for chained calls. |
