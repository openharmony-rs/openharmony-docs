# LineHeightStyle

```TypeScript
declare class LineHeightStyle
```

Describes the text line height style.

**Since:** 12

<!--Device-unnamed-declare class LineHeightStyle--><!--Device-unnamed-declare class LineHeightStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

<a id="constructor1"></a>

## constructor

```TypeScript
constructor(lineHeight: LengthMetrics)
```

A constructor used to create a text line height style.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LineHeightStyle-constructor(lineHeight: LengthMetrics)--><!--Device-LineHeightStyle-constructor(lineHeight: LengthMetrics)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lineHeight | [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | Yes | Text line height setting. If the unit value of **LengthMetrics** is **PERCENT**, the current setting does not take effect. When the **value** of **LengthMetrics** is greater than 0, the text line height setting takes effect; otherwise, the text line height adapts to the font size. |

<a id="constructor2"></a>

## constructor

```TypeScript
constructor(lineHeight: LengthMetrics, lineHeightMultiple?: number)
```

A constructor used to create the text line height and multiple.

> **NOTE:** 
> 
> - When **lineHeightMultiple** is set together with **lineHeight** or [LineSpacingStyle](arkts-arkui-linespacingstyle-c.md),only **lineHeightMultiple** takes effect, and the line height is the product of the maximum font height of the line and the multiple.
> 
> - When **lineHeightMultiple** is less than 0 or **undefined**, it does not take effect, and **lineHeight** and [LineSpacingStyle](arkts-arkui-linespacingstyle-c.md) are used to set the line height and line spacing.
> 
> - When **lineHeightMultiple** is equal to 0, it is equivalent to setting it to 1.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LineHeightStyle-constructor(lineHeight: LengthMetrics, lineHeightMultiple?: number)--><!--Device-LineHeightStyle-constructor(lineHeight: LengthMetrics, lineHeightMultiple?: number)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lineHeight | [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | Yes | Text line height setting. When the value of **LengthMetrics** is greater than 0, the text line height setting takes effect; otherwise, the text line height adapts to the font size. |
| lineHeightMultiple | number | No | Multiple of the text line height. <br> decimals supported. <br>The value must be greater than or equal to 0. <br>**NOTE:** <br>When set together with **lineHeight** or [LineSpacingStyle](arkts-arkui-linespacingstyle-c.md), only **lineHeightMultiple** takes effect, and the line height is the product of the maximum font height of the line and the multiple. <br>It does not take effect when the value is less than 0 or **undefined**. <br>When the value is 0, it is equivalent to setting it to 1. |

## lineHeight

```TypeScript
readonly lineHeight: number
```

Text line height of the styled string.

Unit: [vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units)

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LineHeightStyle-readonly lineHeight: number--><!--Device-LineHeightStyle-readonly lineHeight: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineHeightMultiple

```TypeScript
readonly lineHeightMultiple?: number
```

Multiple of the text line height. The actual line height is the product of the maximum font height of the line and the multiple.

**Note:** When **lineHeightMultiple** is set together with **lineHeight** or [LineSpacingStyle](arkts-arkui-linespacingstyle-c.md), only **lineHeightMultiple** takes effect. **lineHeightMultiple** does not take effect when it is less than 0 or **undefined**. When **lineHeightMultiple** is 0, it is equivalent to setting it to 1.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LineHeightStyle-readonly lineHeightMultiple?: number--><!--Device-LineHeightStyle-readonly lineHeightMultiple?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
