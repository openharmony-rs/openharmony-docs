# InputCounterOptions

```TypeScript
declare interface InputCounterOptions
```

Provides configuration options for the character counter.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## counterTextColor

```TypeScript
counterTextColor?: ColorMetrics
```

Text color of the character counter. When the input character count exceeds the maximum limit multiplied by the specified percentage, the counter displays the current count text using this color. If **counterTextColor** is not set, the default gray color is used.

**Type:** ColorMetrics

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## counterTextOverflowColor

```TypeScript
counterTextOverflowColor?: ColorMetrics
```

Text color of the character counter when the maximum limit is exceeded. When the user input exceeds the maximum character count, both the counter text and border switch to this color to indicate overflow. If **counterTextOverflowColor** is not set, the default red color is used.

**NOTE:** 

The border color is changed only when the **highlightBorder** attribute of [InputCounterOptions](arkts-arkui-common-comp-inputcounteroptions-i.md) is set.

**Type:** ColorMetrics

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## highlightBorder

```TypeScript
highlightBorder?: boolean
```

Whether to highlight the text box border and character counter subscript in red. If **InputCounterOptions** is not set, the text box border and character counter subscript turn red when the number of characters entered reaches the limit. If the character counter is displayed and **thresholdPercentage** is set to a valid value, the text box border and character counter subscript turn red when the number of entered characters exceeds the limit. If this parameter is **true**, the red border is displayed; if **false**, it is not displayed.

**Type:** boolean

**Default:** true

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## thresholdPercentage

```TypeScript
thresholdPercentage?: number
```

Threshold percentage for displaying the character counter. The character counter is displayed when the number of characters that have been entered is greater than the maximum number of characters multiplied by the threshold percentage value. When displayed, the character counter is in the following format: Number of characters that have been entered/Maximum number of characters allowed. It is visible when the number of characters entered is greater than the character limit multiplied by the threshold percentage value. Value range: [1, 100]. If the value is not an integer, it is rounded down to the nearest integer. If the value exceeds the valid value range, the character counter is not displayed. If the value is **undefined**, the character counter is displayed, but this parameter has no effect.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
