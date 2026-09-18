# CommonShapeMethod

Implements the common shape methods.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## fill

```TypeScript
fill(color: ResourceColor): T
```

Sets the fill color of this shape, which determines its opacity, with black representing full transparency and white representing full opacity.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [ResourceColor](arkts-arkui-resourcecolor-t.md) | Yes | Fill color of the shape, which represents the opacity of the fill area. The black color indicates full transparency, while white indicates full opacity. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current object. |

## offset

```TypeScript
offset(offset: Position): T
```

Sets the coordinate offset relative to the component's layout position.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | Position | Yes | Coordinate offset relative to the component's layout position. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current object. |

## position

```TypeScript
position(position: Position): T
```

Sets the position of the shape.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | Position | Yes | Position of the shape. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current object. |
