# LineSpacingStyle

Describes the text line spacing style.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(lineSpacing: LengthMetrics, options?: LineSpacingOptions)
```

A constructor used to create a text line spacing style.

**Since**: 26.0.0

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lineSpacing | [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | Yes | Text line spacing.<br>Default value: **0.0**<br>Value range: [0, +∞) <br>**NOTE:** If **value** of **LengthMetrics** is less than 0, the default value **0.0** is used. |
| options | [LineSpacingOptions](arkts-arkui-linespacingoptions-i.md) | No | Line spacing options.<br>Default value: **{ onlyBetweenLines: false }** |

## lineSpacing

```TypeScript
readonly lineSpacing: number
```

Text line spacing.

Value range: 0, +∞)

Unit: [vp

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## options

```TypeScript
readonly options?: LineSpacingOptions
```

Line spacing options.

**Type:** [LineSpacingOptions](arkts-arkui-linespacingoptions-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
