# DividerOptions

```TypeScript
declare interface DividerOptions
```

Define the divider configuration options.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

Color of the divider.

Default value: **'#33000000'**

**Type:** [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)

**Default:** '#33000000'

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## endMargin

```TypeScript
endMargin?: Dimension
```

Distance between the divider and the end edge of the text picker.

Default value: **0**

Unit: vp (default) or px.

Values less than 0 are invalid. The maximum value allowed is the width of the column. Percentages are not supported.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Default:** 0

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## startMargin

```TypeScript
startMargin?: Dimension
```

Distance between the divider and the start edge of the text picker.

Default value: **0**

Unit: vp (default) or px.

Values less than 0 are invalid. The maximum value allowed is the width of the column. Percentages are not supported.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Default:** 0

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: Dimension
```

Stroke width of the divider.

Default value: **2.0px**

Unit: vp (default) or px.

If the value is less than 0, the default value is used. The maximum value allowed is half the height of the column. Percentages are not supported.

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md)

**Default:** 2.0px

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
