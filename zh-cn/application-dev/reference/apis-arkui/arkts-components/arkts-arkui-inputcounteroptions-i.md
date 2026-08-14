# InputCounterOptions

Define the ratio of characters entered by the the percentage of InputCounterOptions.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

<!--Device-unnamed-declare interface InputCounterOptions--><!--Device-unnamed-declare interface InputCounterOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## counterTextColor

```TypeScript
counterTextColor?: ColorMetrics
```

It is the color of counter when textField hasn't wanted to exceed the maximum character count.

**类型：** ColorMetrics

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-InputCounterOptions-counterTextColor?: ColorMetrics--><!--Device-InputCounterOptions-counterTextColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## counterTextOverflowColor

```TypeScript
counterTextOverflowColor?: ColorMetrics
```

It is the color of counter when textField wants to exceed the maximum character count.

**类型：** ColorMetrics

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-InputCounterOptions-counterTextOverflowColor?: ColorMetrics--><!--Device-InputCounterOptions-counterTextOverflowColor?: ColorMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## highlightBorder

```TypeScript
highlightBorder?: boolean
```

If the current input character count reaches the maximum character count and users want to exceed the normal input, the border will turn red. If this parameter is true, the red border displayed. &lt;p&gt;&lt;strong&gt;NOTE&lt;/strong&gt;: &lt;br&gt;Whether to highlight the text box border and character counter subscript in red. &lt;br&gt;If options is not set, the text box border and character counter subscript turn red &lt;br&gt;when the number of characters entered reaches the limit. &lt;br&gt;If the character counter is displayed and thresholdPercentage is set to a valid value, the text box border and character counter subscript turn red when the number of entered characters exceeds the limit. &lt;br&gt;The value true (default) means to highlight the text box border and character counter subscript in red. &lt;/p&gt;

**类型：** boolean

**默认值：** true

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InputCounterOptions-highlightBorder?: boolean--><!--Device-InputCounterOptions-highlightBorder?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## thresholdPercentage

```TypeScript
thresholdPercentage?: number
```

It is the numerator bit of the percentage and used as a threshold. If the number of characters input reaches the maximum number of characters multiplied by this threshold, the counter is displayed. &lt;p&gt;&lt;strong&gt;NOTE&lt;/strong&gt;: &lt;br&gt;Threshold percentage for displaying the character counter. &lt;br&gt;The character counter is displayed when the number of characters that have been entered is greater than the maximum number of characters multiplied by the threshold percentage value. &lt;br&gt;When displayed, the character counter is in the following format: &lt;br&gt;Number of characters that have been entered/Maximum number of characters allowed. &lt;br&gt;It is visible when the number of characters entered is greater than the character limit multiplied by the threshold percentage value. &lt;br&gt;Value range: [1, 100] &lt;br&gt;If the value is not an integer, it is rounded down to the nearest integer. &lt;br&gt;If the value exceeds the valid value range, the character counter is not displayed. &lt;br&gt;If the value is &lt;em&gt;undefined&lt;/em&gt;, the character counter is displayed, but this parameter has no effect. &lt;/p&gt;

**类型：** number

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-InputCounterOptions-thresholdPercentage?: number--><!--Device-InputCounterOptions-thresholdPercentage?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

