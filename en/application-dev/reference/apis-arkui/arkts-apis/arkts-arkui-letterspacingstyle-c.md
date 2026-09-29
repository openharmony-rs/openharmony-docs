# LetterSpacingStyle

```TypeScript
declare class LetterSpacingStyle
```

Describes the text character spacing object. It is suitable for scenarios that require adjusting character spacing, such as widening the spacing of title text to enhance the visual effect and narrowing the spacing of dense text to save space.

**Since:** 12

<!--Device-unnamed-declare class LetterSpacingStyle--><!--Device-unnamed-declare class LetterSpacingStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: LengthMetrics)
```

A constructor used to create a text letter spacing style.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LetterSpacingStyle-constructor(value: LengthMetrics)--><!--Device-LetterSpacingStyle-constructor(value: LengthMetrics)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | Yes | Text character spacing setting. If the unit value of **LengthMetrics** is **PERCENT**, this setting does not take effect. |

## letterSpacing

```TypeScript
readonly letterSpacing: number
```

Text character spacing of the styled string.

Unit: [vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units)

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LetterSpacingStyle-readonly letterSpacing: number--><!--Device-LetterSpacingStyle-readonly letterSpacing: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
