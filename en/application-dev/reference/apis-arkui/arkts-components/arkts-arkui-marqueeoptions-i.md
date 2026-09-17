# MarqueeOptions

Describes the initialization options of the **Marquee** component.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: number
```

The waiting time between each round of the marquee.

Default value: 0.

Unit: ms.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fromStart

```TypeScript
fromStart?: boolean
```

Whether the text scrolls from the start.

**true**: Scroll from the start.

**false**: Scroll from the end.

Default value: **true**.

**Type:** boolean

**Default:** 
- API version 18+: true

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## loop

```TypeScript
loop?: number
```

Number of times the marquee will scroll. If the value is less than or equal to **0**, the marquee will scroll continuously.

Default value: **-1**

**NOTE:** 

Regardless of the value, the marquee scrolls only once on an ArkTS widget.

**Type:** number

**Default:** 
- API version 18+: -1

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## spacing

```TypeScript
spacing?: LengthMetrics
```

The spacing between two rounds of marquee.

Default value is marquee width.

**Type:** [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: string
```

Text to scroll.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start: boolean
```

Whether to start scrolling.

**true**: yes; **false**: no

**NOTE:** 

This parameter cannot be used to restart scrolling that has been completed.

**Type:** boolean

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## step

```TypeScript
step?: number
```

Step length of the scrolling animation text. If the value is greater than the text width of the marquee, the default value is used.

Default value: **6**

Unit: vp

**Type:** number

**Default:** 
- API version 18+: 6

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
