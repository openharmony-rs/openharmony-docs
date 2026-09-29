# ColumnLayoutAlgorithmOptions

```TypeScript
interface ColumnLayoutAlgorithmOptions
```

Sets the spacing, main axis alignment method, cross axis alignment method, and main axis arrangement direction of the vertical linear layout algorithm.

**Since:** 24

<!--Device-unnamed-interface ColumnLayoutAlgorithmOptions--><!--Device-unnamed-interface ColumnLayoutAlgorithmOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems?: HorizontalAlign
```

Horizontal alignment mode of all child components.

Default value: **HorizontalAlign.Center**

Invalid values are treated as the default value.

**Type:** [HorizontalAlign](arkts-arkui-horizontalalign-e.md)

**Default:** HorizontalAlign.Center

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

<!--Device-ColumnLayoutAlgorithmOptions-alignItems?: HorizontalAlign--><!--Device-ColumnLayoutAlgorithmOptions-alignItems?: HorizontalAlign-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isReverse

```TypeScript
isReverse?: boolean
```

Whether to reverse the vertical arrangement of child components. **true** indicates to reverse the vertical arrangement of child components. The vertical direction is not affected by the common attribute **direction**. **false** indicates to arrange child components in the vertical direction in normal order.

Default value: **false**

Invalid values are treated as the default value.

**Type:** boolean

**Default:** false

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

<!--Device-ColumnLayoutAlgorithmOptions-isReverse?: boolean--><!--Device-ColumnLayoutAlgorithmOptions-isReverse?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## justifyContent

```TypeScript
justifyContent?: FlexAlign
```

Vertical alignment mode of all child components.

Default value: **FlexAlign.Start**

Invalid values are treated as the default value.

**Type:** [FlexAlign](arkts-arkui-flexalign-e.md)

**Default:** FlexAlign.Start

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

<!--Device-ColumnLayoutAlgorithmOptions-justifyContent?: FlexAlign--><!--Device-ColumnLayoutAlgorithmOptions-justifyContent?: FlexAlign-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: LengthMetrics
```

Vertical spacing between child components in a vertical layout.

Value range: a non-negative number.

Default value: **LengthMetrics.vp(0)**

Invalid values are treated as the default value.

**Type:** [LengthMetrics](arkts-arkui-graphics-lengthmetrics-c.md)

**Default:** LengthMetrics.vp(0)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

<!--Device-ColumnLayoutAlgorithmOptions-space?: LengthMetrics--><!--Device-ColumnLayoutAlgorithmOptions-space?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
