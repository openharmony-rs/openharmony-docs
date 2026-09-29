# TextTimerConfiguration

```TypeScript
declare interface TextTimerConfiguration extends CommonConfiguration<TextTimerConfiguration>
```

Defines the **TextTimer** configuration used by the **ContentModifier** API.

You need a custom class to implement the **ContentModifier** API.

**Inheritance/Implementation:** TextTimerConfiguration extends CommonConfiguration<TextTimerConfiguration>

**Since:** 12

<!--Device-unnamed-declare interface TextTimerConfiguration extends CommonConfiguration<TextTimerConfiguration>--><!--Device-unnamed-declare interface TextTimerConfiguration extends CommonConfiguration<TextTimerConfiguration>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count: number
```

Initial time of the timer, in milliseconds. This parameter takes effect when isCountDown is set to true.

Default Value: 60000

Value Range: (0, 86400000), that is, no more than 24 hours. If the value is out of the range, the default value is used.

**Type:** number

**Default:** 60000

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextTimerConfiguration-count: number--><!--Device-TextTimerConfiguration-count: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## elapsedTime

```TypeScript
elapsedTime: number
```

Elapsed time of the timer, in the minimum unit of the configured format.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextTimerConfiguration-elapsedTime: number--><!--Device-TextTimerConfiguration-elapsedTime: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isCountDown

```TypeScript
isCountDown: boolean
```

Whether to count down.

true: The timer counts down, for example, from 30 seconds~0 seconds; false: The timer counts up, for example, from 0 seconds~30 seconds.

Default Value: false

**Type:** boolean

**Default:** false

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextTimerConfiguration-isCountDown: boolean--><!--Device-TextTimerConfiguration-isCountDown: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## started

```TypeScript
started: boolean
```

Whether the timer has started.

true: The timer has started; false: The timer has not started.

Default Value: false

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextTimerConfiguration-started: boolean--><!--Device-TextTimerConfiguration-started: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## startTime

```TypeScript
startTime?: number
```

Initial time of the timer in the count-up mode. This parameter takes effect only when isCountDown is set to false.

Value Range: [-2147483648, 2147483647]. Negative values are supported.

Default Value: 0

Unit: ms

When the value is negative, the timer starts counting from the negative value, passes 0, and then continues counting toward positive values.

**Type:** number

**Default:** 0

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-TextTimerConfiguration-startTime?: number--><!--Device-TextTimerConfiguration-startTime?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
