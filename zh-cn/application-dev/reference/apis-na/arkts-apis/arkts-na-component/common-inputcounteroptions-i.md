# InputCounterOptions

Define the ratio of characters entered by the the percentage of InputCounterOptions.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface InputCounterOptions--><!--Device-unnamed-export declare interface InputCounterOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## counterTextColor

```TypeScript
counterTextColor?: ColorMetrics
```

It is the color of counter when textField hasn't wanted to exceed the maximum character count.

**类型：** ColorMetrics

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputCounterOptions-counterTextColor?: ColorMetrics--><!--Device-InputCounterOptions-counterTextColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## counterTextOverflowColor

```TypeScript
counterTextOverflowColor?: ColorMetrics
```

It is the color of counter when textField wants to exceed the maximum character count.

**类型：** ColorMetrics

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputCounterOptions-counterTextOverflowColor?: ColorMetrics--><!--Device-InputCounterOptions-counterTextOverflowColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## highlightBorder

```TypeScript
highlightBorder?: boolean
```

If the current input character count reaches the maximum character count and users want to exceed the normal input, the border will turn red. If this parameter is true, the red border displayed. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_NOTE\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_: \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_Whether to highlight the text box border and character counter subscript in red. \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_If options is not set, the text box border and character counter subscript turn red \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_when the number of characters entered reaches the limit. \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_If the character counter is displayed and thresholdPercentage is set to a valid value, the text box border and character counter subscript turn red when the number of entered characters exceeds the limit. \_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_The value true (default) means to highlight the text box border and character counter subscript in red. \_\_\_HTML\_TAG\_DESC\_USD\_8\_\_\_

**类型：** boolean

**默认值：** true

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputCounterOptions-highlightBorder?: boolean--><!--Device-InputCounterOptions-highlightBorder?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## thresholdPercentage

```TypeScript
thresholdPercentage?: double
```

It is the numerator bit of the percentage and used as a threshold. If the number of characters input reaches the maximum number of characters multiplied by this threshold, the counter is displayed. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_NOTE\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_: \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_Threshold percentage for displaying the character counter. \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_The character counter is displayed when the number of characters that have been entered is greater than the maximum number of characters multiplied by the threshold percentage value. \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_When displayed, the character counter is in the following format: \_\_\_HTML\_TAG\_DESC\_USD\_6\_\_\_Number of characters that have been entered/Maximum number of characters allowed. \_\_\_HTML\_TAG\_DESC\_USD\_7\_\_\_It is visible when the number of characters entered is greater than the character limit multiplied by the threshold percentage value. \_\_\_HTML\_TAG\_DESC\_USD\_8\_\_\_Value range: [1, 100] \_\_\_HTML\_TAG\_DESC\_USD\_9\_\_\_If the value is not an integer, it is rounded down to the nearest integer. \_\_\_HTML\_TAG\_DESC\_USD\_10\_\_\_If the value exceeds the valid value range, the character counter is not displayed. \_\_\_HTML\_TAG\_DESC\_USD\_11\_\_\_If the value is \_\_\_HTML\_TAG\_DESC\_USD\_12\_\_\_undefined\_\_\_HTML\_TAG\_DESC\_USD\_13\_\_\_, the character counter is displayed, but this parameter has no effect. \_\_\_HTML\_TAG\_DESC\_USD\_14\_\_\_

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-InputCounterOptions-thresholdPercentage?: double--><!--Device-InputCounterOptions-thresholdPercentage?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

