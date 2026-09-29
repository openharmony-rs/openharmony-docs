# DividerOptions

```TypeScript
declare interface DividerOptions
```

Define the divider configuration options.

**Since:** 12

<!--Device-unnamed-declare interface DividerOptions--><!--Device-unnamed-declare interface DividerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Color of the divider.

Default value: '#33000000'

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** '#33000000'

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DividerOptions-color?: ResourceColor--><!--Device-DividerOptions-color?: ResourceColor-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## endMargin

```TypeScript
endMargin?: Dimension
```

Distance between the divider and the end side of the TextPicker.

Default value: 0

Unit: vp by default, or px if specified.

Value range: [0, +∞). If endMargin is less than 0, it is invalid. The maximum value cannot exceed the TextPicker column width. The percentage type is not supported.

**Note:** When startMargin + endMargin exceeds the component width, they are set to 0.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Default:** 0

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DividerOptions-endMargin?: Dimension--><!--Device-DividerOptions-endMargin?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## startMargin

```TypeScript
startMargin?: Dimension
```

Distance between the divider and the start side of the TextPicker.

Default value: 0

Unit: vp by default, or px if specified.

Value range: [0, +∞). If startMargin is less than 0, it is invalid. The maximum value cannot exceed the TextPicker column width. The percentage type is not supported.

**Note:** When startMargin + endMargin exceeds the component width, they are set to 0.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Default:** 0

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DividerOptions-startMargin?: Dimension--><!--Device-DividerOptions-startMargin?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Dimension
```

Line width of the divider.

Default value: 2.0px

Unit: vp by default, or px if specified.

Value range: [0, +∞). If strokeWidth is less than 0, the default value is used. The maximum value cannot exceed half of the column height. The percentage type is not supported.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Default:** 2.0px

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DividerOptions-strokeWidth?: Dimension--><!--Device-DividerOptions-strokeWidth?: Dimension-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
