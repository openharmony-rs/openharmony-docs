# TextClockOptions

```TypeScript
declare interface TextClockOptions
```

Options used to build the **TextClock** component.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer
> element's

**Since:** 18

<!--Device-unnamed-declare interface TextClockOptions--><!--Device-unnamed-declare interface TextClockOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller?: TextClockController
```

Binds a controller to control the state of the text clock. Pass this parameter when the start and stop of the clock need to be controlled by code. If it is not passed, the clock still runs and displays normally, but its start and stop cannot be controlled by code.

**Type:** [TextClockController](arkts-arkui-textclock-comp-textclockcontroller-c.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-TextClockOptions-controller?: TextClockController--><!--Device-TextClockOptions-controller?: TextClockController-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## timeZoneOffset

```TypeScript
timeZoneOffset?: number
```

Sets the time zone offset, in hours.

The value ranges from -14 to 12, indicating the range from UTC+12 to UTC-12, where a negative value indicates an east time zone and a positive value indicates a west time zone. For example, UTC+8 is -8. When the value is a floating-point number within this range, it is rounded to an integer, with the decimal part discarded.

For countries or regions that span the International Date Line, use -13 (UTC+13) and -14 (UTC+14) to ensure that the entire country or region is in the same time zone. When the value is outside the range, the time zone offset of the current system is used.

Default value: the time zone offset of the current system

When the value is a floating-point number in the set { 9.5, 3.5, -3.5, -4.5, -5.5, -5.75, -6.5, -9.5, -10.5, -12.75}, it is not rounded.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

<!--Device-TextClockOptions-timeZoneOffset?: number--><!--Device-TextClockOptions-timeZoneOffset?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
