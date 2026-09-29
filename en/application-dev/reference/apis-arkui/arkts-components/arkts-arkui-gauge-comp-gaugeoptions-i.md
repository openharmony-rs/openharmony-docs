# GaugeOptions

```TypeScript
interface GaugeOptions
```

Provides gauge options.

**Since:** 18

<!--Device-unnamed-interface GaugeOptions--><!--Device-unnamed-interface GaugeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## max

```TypeScript
max?: number
```

Maximum value of the current data segment.

Default value: 100

**Widget capability:** This API can be used in ArkTS cards since API version 9.

**NOTE:** 

When not passed, the default value is 100.

When min is greater than max, min is set to 0 and max is set to 100.

Both max and min support negative numbers.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-GaugeOptions-max?: number--><!--Device-GaugeOptions-max?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## min

```TypeScript
min?: number
```

Minimum value of the current data segment.

Default value: 0

**Widget capability:** This API can be used in ArkTS cards since API version 9.

**NOTE:** 

When not passed, the default value is 0.

When min is greater than max, min is set to 0 and max is set to 100.

Both max and min support negative numbers.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-GaugeOptions-min?: number--><!--Device-GaugeOptions-min?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: number
```

Current data value of the gauge, that is, the position to which the pointer points. Used to preset the initial value of the gauge when the component is created.

Default value: 0

**Widget capability:** This API can be used in ArkTS cards since API version 9.

**NOTE:** 

When value is not within the range of min and max, min is used as the actual value.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-GaugeOptions-value: number--><!--Device-GaugeOptions-value: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
