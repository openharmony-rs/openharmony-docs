# TextTimerOptions

Sets the options used to build the **TextTimer** component.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TextTimerController
```

**TextTimer** controller.

**Type:** [TextTimerController](arkts-arkui-texttimercontroller-c.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count?: number
```

Timer duration, in milliseconds. It is effective only when **isCountDown** is **true**. The maximum value is 864000 00 ms (24 hours). If 0 &lt; **count** &lt; 86400000, **count** is the initial value of the timer. Otherwise, the default value is used as the initial value.

Default value: **60000**

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isCountDown

```TypeScript
isCountDown?: boolean
```

Countdown switch.

**true**: The timer counts down (for example, from 30 seconds to 0 seconds).

**false**: The timer counts up (for example, from 0 seconds to 30 seconds).

Default value: **false**

**Type:** boolean

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

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

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
