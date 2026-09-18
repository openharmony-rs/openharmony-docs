# LineHeightStyle

Describes the text line height style.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(lineHeight: LengthMetrics)
```

A constructor used to create a text line height style.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lineHeight | [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | Yes | Text line height options. If **value** of **LengthMetrics** is less than or equal to 0, the text line height is unlimited and automatically adapts to the font size. |

## constructor

```TypeScript
constructor(lineHeight: LengthMetrics, lineHeightMultiple?: number)
```

A constructor used to create a text line height and multiple.

> **NOTE:** 
> 
> - When **lineHeightMultiple** is set together with **lineHeight** or [LineSpacingStyle](arkts-arkui-linespacingstyle-c.md),only **lineHeightMultiple** takes effect. The line height is the product of the highest font height in the line and the multiplier.
> 
> - When **lineHeightMultiple** is less than 0 or **undefined**, it does not take effect. Use **lineHeight** and [LineSpacingStyle](arkts-arkui-linespacingstyle-c.md) to set the line height and line spacing.
> 
> - When **lineHeightMultiple** is set to 0, it is equivalent to setting it to 1.

**Since**: 26.0.0

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lineHeight | [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | Yes | Text line height options. If **value** of **LengthMetrics** is less than or equal to 0, the text line height is unlimited and automatically adapts to the font size. |
| lineHeightMultiple | number | No | Multiplier for the text line height.<br>Value range: 0, +∞). Decimals are supported. |

## lineHeight

```TypeScript
readonly lineHeight: number
```

Text line height of the styled string.

Unit: [vp

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineHeightMultiple

```TypeScript
readonly lineHeightMultiple?: number
```

Multiplier for the text line height. The effective line height is the product of the highest font height in the line and the multiplier.

**Since**: 26.0.0

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
