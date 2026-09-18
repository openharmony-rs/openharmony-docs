# TextClockConfiguration

You need a custom class to implement the **ContentModifier** API.

**Inheritance/Implementation:** TextClockConfiguration extends CommonConfiguration<TextClockConfiguration>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## started

```TypeScript
started: boolean
```

Whether the text clock is started.

**true**: The text clock is started.

**false**: The text clock is disabled.

Default value: **true**

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## timeValue

```TypeScript
timeValue: number
```

Time zone offset of the text clock in seconds from UTC.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## timeZoneOffset

```TypeScript
timeZoneOffset: number
```

Time zone offset of the text clock.

The value range is [-14, 12], indicating UTC+12 to UTC-12. A negative value indicates Eastern Standard Time, and a positive value indicates Western Standard Time. For example, **-8** indicates UTC+8. If the value is a floating point number within the value range, it is rounded off, with the decimal portion discarded.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
