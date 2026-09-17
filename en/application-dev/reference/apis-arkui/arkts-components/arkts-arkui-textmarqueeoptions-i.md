# TextMarqueeOptions

Describes the initialization options of the **Marquee** component.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: number
```

Time interval between scroll movements.

Default value: **0**

Unit: millisecond

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## marqueeStartPolicy

```TypeScript
marqueeStartPolicy?: MarqueeStartPolicy
```

Policy for starting the marquee. This attribute takes effect only when **start** is set to **true**.

Default value: **MarqueeStartPolicy.DEFAULT**

**Type:** [MarqueeStartPolicy](arkts-arkui-marqueestartpolicy-e.md)

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## marqueeUpdatePolicy

```TypeScript
marqueeUpdatePolicy?: MarqueeUpdatePolicy
```

Scrolling policy of the marquee after its attributes are updated.

This attribute takes effect when the marquee is in the playing state and the text width exceeds the width of the marquee component.

Default value: **MarqueeUpdatePolicy.DEFAULT**

**Type:** [MarqueeUpdatePolicy](arkts-arkui-marqueeupdatepolicy-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## spacing

```TypeScript
spacing?: LengthMetrics
```

Spacing between two marquee rounds. If the unit of **LengthMetrics** is **PERCENT**, the current setting does not take effect and the default value is used.

Default value: **48.0vp**

**Type:** [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## step

```TypeScript
step?: number
```

Step length of the scrolling animation text.

Default value: **4.0** (in vp)

**Type:** number

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
