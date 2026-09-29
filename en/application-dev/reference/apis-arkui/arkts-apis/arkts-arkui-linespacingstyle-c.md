# LineSpacingStyle

```TypeScript
declare class LineSpacingStyle
```

Describes the text line spacing object. It is suitable for scenarios that require adjusting the spacing between lines within a paragraph, such as improving text reading comfort and adjusting document layout density.

**Since:** 26.0.0

<!--Device-unnamed-declare class LineSpacingStyle--><!--Device-unnamed-declare class LineSpacingStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(lineSpacing: LengthMetrics, options?: LineSpacingOptions)
```

A constructor used to create the text line spacing. If this API is not used to set the value, the default line spacing is **0.0**. When the value of **LengthMetrics** is less than 0, the default value **0.0** is used. When it is set together with **lineHeightMultiple** of [LineHeightStyle](arkts-arkui-lineheightstyle-c.md) and **lineHeightMultiple** takes effect, this parameter does not take effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LineSpacingStyle-constructor(lineSpacing: LengthMetrics, options?: LineSpacingOptions)--><!--Device-LineSpacingStyle-constructor(lineSpacing: LengthMetrics, options?: LineSpacingOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lineSpacing | [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | Yes | Text line spacing.<br>Value range: [0, +∞). |
| options | [LineSpacingOptions](arkts-arkui-linespacingoptions-i.md) | No | Line spacing configuration options. |

## lineSpacing

```TypeScript
readonly lineSpacing: number
```

Text line spacing.

Value range: [0, +∞)

Unit: [vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units)

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LineSpacingStyle-readonly lineSpacing: number--><!--Device-LineSpacingStyle-readonly lineSpacing: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
readonly options?: LineSpacingOptions
```

Line spacing configuration options.

**Type:** [LineSpacingOptions](arkts-arkui-linespacingoptions-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-LineSpacingStyle-readonly options?: LineSpacingOptions--><!--Device-LineSpacingStyle-readonly options?: LineSpacingOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
