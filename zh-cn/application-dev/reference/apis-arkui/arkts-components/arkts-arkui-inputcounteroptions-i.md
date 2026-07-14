# InputCounterOptions

Define the ratio of characters entered by the the percentage of InputCounterOptions.

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## counterTextColor

```TypeScript
counterTextColor?: ColorMetrics
```

It is the color of counter when textField hasn't wanted to exceed the maximum character count.

**类型：** ColorMetrics

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## counterTextOverflowColor

```TypeScript
counterTextOverflowColor?: ColorMetrics
```

It is the color of counter when textField wants to exceed the maximum character count.

**类型：** ColorMetrics

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## highlightBorder

```TypeScript
highlightBorder?: boolean
```

If the current input character count reaches the maximum character count and users want to exceed the
normal input, the border will turn red. If this parameter is true, the red border displayed.

<p><strong>NOTE</strong>:
<br>Whether to highlight the text box border and character counter subscript in red.
<br>If options is not set, the text box border and character counter subscript turn red
<br>when the number of characters entered reaches the limit.
<br>If the character counter is displayed and thresholdPercentage is set to a valid value,
the text box border and character counter subscript turn red when the number of entered characters exceeds the limit.
<br>The value true (default) means to highlight the text box border and character counter subscript in red.
</p>

**类型：** boolean

**默认值：** true

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## thresholdPercentage

```TypeScript
thresholdPercentage?: number
```

It is the numerator bit of the percentage and used as a threshold. If the number of characters input
reaches the maximum number of characters multiplied by this threshold, the counter is displayed.

<p><strong>NOTE</strong>:
<br>Threshold percentage for displaying the character counter.
<br>The character counter is displayed when the number of characters that have been entered is greater than
the maximum number of characters multiplied by the threshold percentage value.
<br>When displayed, the character counter is in the following format:
<br>Number of characters that have been entered/Maximum number of characters allowed.
<br>It is visible when the number of characters entered is greater than
the character limit multiplied by the threshold percentage value.
<br>Value range: [1, 100]
<br>If the value is not an integer, it is rounded down to the nearest integer.
<br>If the value exceeds the valid value range, the character counter is not displayed.
<br>If the value is <em>undefined</em>, the character counter is displayed, but this parameter has no effect.
</p>

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

