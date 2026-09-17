# TextTimerConfiguration

Defines the **TextTimer** configuration used by the **ContentModifier** API.

You need a custom class to implement the **ContentModifier** API.

**Inheritance/Implementation:** TextTimerConfiguration extends CommonConfiguration<TextTimerConfiguration>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count: number
```

Timer duration, in milliseconds. It is effective only when **isCountDown** is **true**. The maximum value is 864000 00 ms (24 hours). If the value is between 0 and 86,400,000, it is used as the initial countdown time. Otherwise, the default value is used as the initial countdown time.

Default value: **60000**

**Type:** number

**Default:** 60000

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## elapsedTime

```TypeScript
elapsedTime: number
```

Elapsed time of the timer, in the minimum unit of the format.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isCountDown

```TypeScript
isCountDown: boolean
```

Whether the timer is a countdown.

**true**: The timer counts down, e.g., from 30s to 0s. **false**: The timer counts up, e.g., from 0s to 30s.

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## started

```TypeScript
started: boolean
```

Whether the timer has already started.

**true**: The timer has started. **false**: The timer has not started.

Default value: **false**

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## startTime

```TypeScript
startTime?: number
```

The start time of the timer.It is effective when isCountDown is false.

Default value: **0**

Unit: ms.

When the value is negative, the timer starts with a negative value and continues with a positive value after 0.

**Type:** number

**Default:** 0

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
