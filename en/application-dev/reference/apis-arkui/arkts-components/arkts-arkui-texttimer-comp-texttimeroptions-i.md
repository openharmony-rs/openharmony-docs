# TextTimerOptions

```TypeScript
interface TextTimerOptions
```

Sets the options used to build the **TextTimer** component.

**Since:** 8

<!--Device-unnamed-interface TextTimerOptions--><!--Device-unnamed-interface TextTimerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TextTimerController
```

Controller of the TextTimer, used to start, pause, and reset the timer programmatically. If this parameter is not passed, the timer can still be displayed normally but its state cannot be controlled through code.

**Type:** [TextTimerController](arkts-arkui-texttimer-comp-texttimercontroller-c.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-TextTimerOptions-controller?: TextTimerController--><!--Device-TextTimerOptions-controller?: TextTimerController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count?: number
```

Initial time of the timer, in milliseconds. This parameter takes effect when isCountDown is true.

Default value: 60000

Value range: (0, 86400000), that is, no more than 24 hours. If the value is out of the range, the default value is used.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-TextTimerOptions-count?: number--><!--Device-TextTimerOptions-count?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isCountDown

```TypeScript
isCountDown?: boolean
```

Countdown switch.

true: The timer counts down, for example, from 30 seconds to 0 seconds.

false: The timer counts up, for example, from 0 seconds to 30 seconds.

Default value: **false**

**Type:** boolean

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-TextTimerOptions-isCountDown?: boolean--><!--Device-TextTimerOptions-isCountDown?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## startTime

```TypeScript
startTime?: number
```

Initial time of the timer in count-up mode. This parameter takes effect only when isCountDown is false.

Value range: [−2147483648, 2147483647].

Default value: 0

Unit: ms

When the value is negative, the timer starts counting from the negative value and continues counting toward positive values after passing 0.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

<!--Device-TextTimerOptions-startTime?: number--><!--Device-TextTimerOptions-startTime?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
