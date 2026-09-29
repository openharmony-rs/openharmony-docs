# MarqueeOptions

```TypeScript
interface MarqueeOptions
```

Describes the initialization options of the **Marquee** component.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

<!--Device-unnamed-interface MarqueeOptions--><!--Device-unnamed-interface MarqueeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: number
```

Sets the delay between two rounds of scrolling. +∞). A value less than 0 is equivalent to 0. Unit: millisecond. Default value: 0 Value Range: [0.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-MarqueeOptions-delay?: number--><!--Device-MarqueeOptions-delay?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fromStart

```TypeScript
fromStart?: boolean
```

Sets the scrolling direction of the text.

true: the text scrolls forward from the beginning; false: the text scrolls in reverse.

Default Value: true

**Type:** boolean

**Default:** 
- API version 18+: true

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-MarqueeOptions-fromStart?: boolean--><!--Device-MarqueeOptions-fromStart?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## loop

```TypeScript
loop?: number
```

Sets the loop count of repeated scrolling. When the value is less than or equal to 0, the scrolling loops infinitely.

Default Value: -1

**Note:** 

On ArkTS widgets, this parameter scrolls only once when visible regardless of the value set. When it is set to a finite number greater than 0 and playback is complete, you cannot reset the scroll count and restart playback by changing the start parameter.

**Type:** number

**Default:** 
- API version 18+: -1

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-MarqueeOptions-loop?: number--><!--Device-MarqueeOptions-loop?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## spacing

```TypeScript
spacing?: LengthMetrics
```

Spacing between two rounds of marquee scrolling. When the unit attribute of the LengthMetrics object is LengthUnit.PERCENT, this setting does not take effect and the default value is used.

Default Value: width of the Marquee component.

**Type:** LengthMetrics

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

<!--Device-MarqueeOptions-spacing?: LengthMetrics--><!--Device-MarqueeOptions-spacing?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: string
```

Text to be scrolled.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-MarqueeOptions-src: string--><!--Device-MarqueeOptions-src: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start: boolean
```

Controls whether the marquee enters the playing state.

true: play; false: do not play.

**Note:** 

When the loop parameter is set to a finite number greater than 0 and playback is complete, you cannot reset the scroll count and restart playback by changing the start parameter.

**Type:** boolean

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-MarqueeOptions-start: boolean--><!--Device-MarqueeOptions-start: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## step

```TypeScript
step?: number
```

Text step of the scrolling animation.

Value Range: [0, text width]. When step is greater than the text width of the Marquee, the default value is used.

Default Value: 6

Unit: [vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units)

**Type:** number

**Default:** 
- API version 18+: 6

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-MarqueeOptions-step?: number--><!--Device-MarqueeOptions-step?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
