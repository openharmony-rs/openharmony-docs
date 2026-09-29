# InputCounterOptions

```TypeScript
declare interface InputCounterOptions
```

Provides configuration options for the character counter.

**Since:** 11

<!--Device-unnamed-declare interface InputCounterOptions--><!--Device-unnamed-declare interface InputCounterOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## counterTextColor

```TypeScript
counterTextColor?: ColorMetrics
```

Sets the text color of the character counter in the component. When the number of characters entered by the user is greater than the maximum number of characters multiplied by the percentage value, the counter displays the current number of entered characters, and the text color of the counter is the color specified by counterTextColor. If counterTextColor is not set, the text color of the counter is the default color, which is gray.

**Type:** ColorMetrics

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-InputCounterOptions-counterTextColor?: ColorMetrics--><!--Device-InputCounterOptions-counterTextColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## counterTextOverflowColor

```TypeScript
counterTextOverflowColor?: ColorMetrics
```

Sets the text color of the character counter in the component when it overflows. When the number of characters entered by the user exceeds the maximum number of characters, the text color of the counter and the color of the border switch to the color specified by counterTextOverflowColor to remind the user that the input has exceeded the limit. If counterTextOverflowColor is not set, the text color of the counter and the border when overflowing is the default color, which is red.

**NOTE:** 

When the highlightBorder attribute of [InputCounterOptions](arkts-arkui-common-comp-inputcounteroptions-i.md) is set, the border color is changed synchronously.

**Type:** ColorMetrics

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-InputCounterOptions-counterTextOverflowColor?: ColorMetrics--><!--Device-InputCounterOptions-counterTextOverflowColor?: ColorMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## highlightBorder

```TypeScript
highlightBorder?: boolean
```

If InputCounterOptions is not set when the user sets the counter, the border and the counter subscript turn red when the current number of entered characters reaches the maximum number of characters. If the user sets the character counter to be displayed and the thresholdPercentage parameter value is within the valid value range, the border and the counter subscript turn red when the number of entered characters exceeds the maximum number of characters. If this parameter is true, a red border is displayed; if it is false, no red border is displayed.

Default value: true

**Type:** boolean

**Default:** true

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-InputCounterOptions-highlightBorder?: boolean--><!--Device-InputCounterOptions-highlightBorder?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## thresholdPercentage

```TypeScript
thresholdPercentage?: number
```

Percentage of the maximum number of characters that can be entered. The character counter displays the current number of entered characters/the maximum number of characters. When the number of entered characters is greater than the maximum number of characters multiplied by the percentage value, the character counter is displayed. The valid value range is [1,100]. When the value is a decimal, it is rounded down. If the set number is outside the valid value range, the character counter is not displayed. When set to undefined, the character counter is displayed, but this parameter is not effective.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-InputCounterOptions-thresholdPercentage?: number--><!--Device-InputCounterOptions-thresholdPercentage?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
