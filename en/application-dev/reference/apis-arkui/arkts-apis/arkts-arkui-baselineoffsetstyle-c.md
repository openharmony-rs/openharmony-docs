# BaselineOffsetStyle

```TypeScript
declare class BaselineOffsetStyle
```

Describes the text baseline offset object. It is suitable for scenarios that require fine-tuning the vertical position of text, such as aligning superscript and subscript text with normal text in chemical formulas and mathematical expressions.

**Since:** 12

<!--Device-unnamed-declare class BaselineOffsetStyle--><!--Device-unnamed-declare class BaselineOffsetStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: LengthMetrics)
```

A constructor used to create a text baseline offset style.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BaselineOffsetStyle-constructor(value: LengthMetrics)--><!--Device-BaselineOffsetStyle-constructor(value: LengthMetrics)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [LengthMetrics](arkts-arkui-lengthmetrics-t.md) | Yes | Setting item for the text baseline offset. If the unit value of **LengthMetrics** is **PERCENT**, this setting does not take effect. |

## baselineOffset

```TypeScript
readonly baselineOffset: number
```

Text baseline offset of the styled string.

Unit: [vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units)

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-BaselineOffsetStyle-readonly baselineOffset: number--><!--Device-BaselineOffsetStyle-readonly baselineOffset: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
