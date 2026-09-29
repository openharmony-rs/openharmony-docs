# TextMarqueeOptions

```TypeScript
declare interface TextMarqueeOptions
```

Describes the initialization options of the **Marquee** component.

**Since:** 18

<!--Device-unnamed-declare interface TextMarqueeOptions--><!--Device-unnamed-declare interface TextMarqueeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: number
```

Time interval between scroll movements.

The value range is [0, +∞). If the value is a negative number, the default value is used.

Default value: **0**

Unit: millisecond

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextMarqueeOptions-delay?: number--><!--Device-TextMarqueeOptions-delay?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fadeout

```TypeScript
fadeout?: boolean
```

Whether to apply a fade-out effect when the text is too long.

**true** to apply a fade-out effect when the text is too long, **false** otherwise.

When this parameter is set to **true**: if the text content exceeds the display range, a fade-out effect is applied to the edges of the partially visible text; if text is partially visible at both ends, the fade-out effect is applied to both ends. The **clip** attribute is automatically locked to **true** and cannot be set to **false**.

Default value: **false**

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextMarqueeOptions-fadeout?: boolean--><!--Device-TextMarqueeOptions-fadeout?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fromStart

```TypeScript
fromStart?: boolean
```

Whether the text scrolls from the start.

**true** to scroll from the start, **false** to scroll in reverse.

Default value: **true**

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextMarqueeOptions-fromStart?: boolean--><!--Device-TextMarqueeOptions-fromStart?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## loop

```TypeScript
loop?: number
```

Number of times the marquee will scroll. If the value is less than or equal to **0**, the marquee will scroll continuously.

Default value: **-1**

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextMarqueeOptions-loop?: number--><!--Device-TextMarqueeOptions-loop?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## marqueeStartPolicy

```TypeScript
marqueeStartPolicy?: MarqueeStartPolicy
```

Policy for starting the marquee. This attribute takes effect only when **start** is set to **true**.

Default value: **MarqueeStartPolicy.ON_FOCUS** for TVs and **MarqueeStartPolicy.DEFAULT** for other devices

**Type:** [MarqueeStartPolicy](arkts-arkui-text-comp-marqueestartpolicy-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextMarqueeOptions-marqueeStartPolicy?: MarqueeStartPolicy--><!--Device-TextMarqueeOptions-marqueeStartPolicy?: MarqueeStartPolicy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## marqueeUpdatePolicy

```TypeScript
marqueeUpdatePolicy?: MarqueeUpdatePolicy
```

Scrolling policy of the marquee after its attributes are updated.

This attribute takes effect when the marquee is in the playing state and the text width exceeds the width of the marquee component.

Default value: **MarqueeUpdatePolicy.DEFAULT**

**Type:** [MarqueeUpdatePolicy](arkts-arkui-text-comp-marqueeupdatepolicy-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextMarqueeOptions-marqueeUpdatePolicy?: MarqueeUpdatePolicy--><!--Device-TextMarqueeOptions-marqueeUpdatePolicy?: MarqueeUpdatePolicy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## spacing

```TypeScript
spacing?: LengthMetrics
```

Spacing between two rounds of the marquee. Unit: vp. When the unit attribute of the LengthMetrics object is LengthUnit.PERCENT, the current setting does not take effect and the default value is used.

Default value: 48.0vp

**Atomic service API:** Since API version 23, this API can be used in atomic services.

**Type:** LengthMetrics

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TextMarqueeOptions-spacing?: LengthMetrics--><!--Device-TextMarqueeOptions-spacing?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start: boolean
```

Whether to start the marquee.

**true**: Start the marquee. **false**: Do not start the marquee.

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextMarqueeOptions-start: boolean--><!--Device-TextMarqueeOptions-start: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## step

```TypeScript
step?: number
```

Step length of the scrolling animation text.

Unit: vp

Value range: (0, Text width]. If this parameter is set to a value less than or equal to 0, the default value is used.

Default value: **4.0** (in vp)

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-TextMarqueeOptions-step?: number--><!--Device-TextMarqueeOptions-step?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
