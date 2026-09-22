# TipsOptions

```TypeScript
declare interface TipsOptions
```

Defines the parameters of the tooltip.

**Since:** 19

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## appearingTime

```TypeScript
appearingTime?: number
```

Delay before the tooltip appears. The maximum delay is 4000 ms. Values exceeding 4000 ms are capped at 4000 ms.

Default value: **700**.

Unit: ms.

**Type:** number

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## appearingTimeWithContinuousOperation

```TypeScript
appearingTimeWithContinuousOperation?: number
```

Delay before the tooltip appears when multiple tooltips are displayed consecutively. The maximum delay is 4000 ms. Values exceeding 4000 ms are capped at 4000 ms.

Default value: **300**.

Unit: ms.

**Type:** number

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## arrowHeight

```TypeScript
arrowHeight?: Dimension
```

Height of the tooltip arrow.

Default value: **8**.

Unit: vp.

**NOTE:** 

Percentage values are not supported.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Default:** 8.0_vp.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## arrowPointPosition

```TypeScript
arrowPointPosition?: ArrowPointPosition
```

Position of the tooltip arrow relative to its parent component. Available positions are **Start**, **Center**, and **End**, in both vertical and horizontal directions. These positions are within the parent component area and do not exceed its boundaries or cover rounded corners.

Default value: **ArrowPointPosition.CENTER**.

**Type:** [ArrowPointPosition](../arkts-apis/arkts-arkui-arrowpointposition-e.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## arrowWidth

```TypeScript
arrowWidth?: Dimension
```

Width of the tooltip arrow. If the set width exceeds the length of the edge minus twice the tooltip's corner radius, the arrow is not drawn.

Default value: **16**.

Unit: vp.

**NOTE:** 

Percentage values are not supported.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Default:** 16.0_vp.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disappearingTime

```TypeScript
disappearingTime?: number
```

Delay before the tooltip disappears. The maximum delay is 4000 ms. Values exceeding 4000 ms are capped at 4000 ms.

Default value: **300**.

Unit: ms.

**Type:** number

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disappearingTimeWithContinuousOperation

```TypeScript
disappearingTimeWithContinuousOperation?: number
```

Delay before the tooltip disappears when multiple tooltips are displayed consecutively. The maximum delay is 4000 ms. Values exceeding 4000 ms are capped at 4000 ms.

Default value: **0**.

Unit: ms.

**Type:** number

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableArrow

```TypeScript
enableArrow?: boolean
```

Whether to display the tooltip arrow.

Default value: **true**.

**true**: yes. **false**: no.

**NOTE:** 

If the available space on the screen is insufficient, the tooltip will cover part of the component and the arrow will not be displayed.

**Type:** boolean

**Default:** true

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## showAtAnchor

```TypeScript
showAtAnchor?: TipsAnchorType
```

Anchor type of the tooltip.

Default value: **TipsAnchorType.TARGET**.

**NOTE:** 

If the anchor type of the tooltip is **TipsAnchorType.CURSOR**, the tooltip does not display an arrow.

**Type:** [TipsAnchorType](../arkts-apis/arkts-arkui-tipsanchortype-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

Set system-styled materials for tips. Different materials have different effects, which can influence backgroundColor, border, shadow, and other visual attributes of tips.

**Type:** [SystemUiMaterial](arkts-arkui-common-comp-systemuimaterial-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
