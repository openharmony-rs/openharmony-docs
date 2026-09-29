# TextClockConfiguration

```TypeScript
declare interface TextClockConfiguration extends CommonConfiguration<TextClockConfiguration>
```

You need a custom class to implement the **ContentModifier** API.

**Inheritance/Implementation:** TextClockConfiguration extends CommonConfiguration<TextClockConfiguration>

**Since:** 12

<!--Device-unnamed-declare interface TextClockConfiguration extends CommonConfiguration<TextClockConfiguration>--><!--Device-unnamed-declare interface TextClockConfiguration extends CommonConfiguration<TextClockConfiguration>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## started

```TypeScript
started: boolean
```

Whether the text clock is started.

**true**: The text clock is started.

**false**: The text clock is stopped.

Default value: **true**

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextClockConfiguration-started: boolean--><!--Device-TextClockConfiguration-started: boolean-End-->

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

<!--Device-TextClockConfiguration-timeValue: number--><!--Device-TextClockConfiguration-timeValue: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## timeZoneOffset

```TypeScript
timeZoneOffset: number
```

Time zone offset of the current text clock.

The value range is [-14, 12], indicating from UTC+12 to UTC-12, where a negative value indicates an east time zone and a positive value indicates a west time zone. For example, UTC+8 is -8. When the set value is a floating-point number within this range, it is rounded by discarding the decimal part. However, no rounding is performed when the set value is a floating-point number in the set { 9.5, 3.5, -3.5, -4.5, -5.5, -5.75, -6.5, -9.5, -10.5, -12.75 }. When the set value is outside the value range, the time zone offset of the current system is used.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TextClockConfiguration-timeZoneOffset: number--><!--Device-TextClockConfiguration-timeZoneOffset: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
