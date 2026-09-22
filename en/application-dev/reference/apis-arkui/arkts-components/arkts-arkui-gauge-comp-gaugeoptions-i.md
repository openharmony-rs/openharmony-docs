# GaugeOptions

```TypeScript
interface GaugeOptions
```

Provides gauge options.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## max

```TypeScript
max?: number
```

Maximum value of the current data segment.

Default value: **100**

**NOTE:** 

If the value of **max** is less than that of **min**, the default values **0** and **100** are used.

The values of **max** and **min** can be negative numbers.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## min

```TypeScript
min?: number
```

Minimum value of the current data segment.

Default value: **0**

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value: number
```

Current value of the gauge, that is, the position to which the indicator points in the gauge. It is used as the initial value of the gauge when it is created.

Default value: **0**

**NOTE:** 

If the value is not within the range defined by the **min** and **max** parameters, the value of **min** is used.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
