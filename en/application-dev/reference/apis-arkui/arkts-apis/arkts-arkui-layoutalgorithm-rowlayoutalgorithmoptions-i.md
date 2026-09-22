# RowLayoutAlgorithmOptions

```TypeScript
interface RowLayoutAlgorithmOptions
```

Sets the spacing, main axis alignment method, cross axis alignment method, and main axis arrangement direction of the horizontal linear layout algorithm.

**Since:** 24

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems?: VerticalAlign
```

Vertical alignment mode of all child components.

Default value: **VerticalAlign.Center**

Invalid values are treated as the default value.

**Type:** [VerticalAlign](arkts-arkui-verticalalign-e.md)

**Default:** VerticalAlign.Center

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isReverse

```TypeScript
isReverse?: boolean
```

Whether to reverse the horizontal arrangement of child components. **true** indicates to reverse the horizontal arrangement of child components. The horizontal direction is affected by the common attribute [direction](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#direction). If the [direction](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#direction) attribute takes effect, the child components are arranged based on **direction** and then are reversed based on **isReverse**. **false** indicates to arrange child components in the horizontal direction in normal order.

Default value: **false**

Invalid values are treated as the default value.

**Type:** boolean

**Default:** false

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## justifyContent

```TypeScript
justifyContent?: FlexAlign
```

Horizontal alignment mode of all child components.

Default value: **FlexAlign.Start**

Invalid values are treated as the default value.

**Type:** [FlexAlign](arkts-arkui-flexalign-e.md)

**Default:** FlexAlign.Start

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: LengthMetrics
```

Horizontal spacing between child components in a horizontal layout.

Value range: a non-negative number.

Default value: **LengthMetrics.vp(0)**

Invalid values are treated as the default value.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Default:** LengthMetrics.vp(0)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
