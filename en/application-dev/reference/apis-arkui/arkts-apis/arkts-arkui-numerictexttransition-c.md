# NumericTextTransition

Implements a flip animation for numeric text. It applies only to positive integers (decimals and negative numbers are not supported). Gradient colors and text marquee mode are not supported. Text selection is not supported, and the copyOption property is ineffective. The flip animation fails if the text contains child components or is set via a styled string.

**NumericTextTransition** inherits from [ContentTransition](arkts-arkui-contenttransition-c.md).

**Inheritance/Implementation:** NumericTextTransition extends [ContentTransition](arkts-arkui-contenttransition-c.md)

**Since:** 20

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: NumericTextTransitionOptions)
```

A constructor used to create a **NumericTextTransition** object.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [NumericTextTransitionOptions](arkts-arkui-numerictexttransitionoptions-i.md) | No | Options of the numeric flip animation. The default value is inherited from [NumericTextTransitionOptions](arkts-arkui-numerictexttransitionoptions-i.md). |

## enableBlur

```TypeScript
enableBlur?: boolean
```

Whether to enable the blur effect for the flip animation.

Default value: **false**

**true**: Enable the blur effect.

**false**: Disable the blur effect.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## flipDirection

```TypeScript
flipDirection?: FlipDirection
```

Direction of the flip animation.

Default value: **FlipDirection.DOWN**

**Type:** [FlipDirection](arkts-arkui-flipdirection-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
