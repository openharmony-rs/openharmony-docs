# ScrollOptions

```TypeScript
declare interface ScrollOptions
```

Provides parameters for scrolling to a specific position in a scrollable container.

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## animation

```TypeScript
animation?: ScrollAnimationOptions | boolean
```

Animation configuration Anonymous Object Rectification.

<p>&lt;strong&gt;NOTE&lt;/strong&gt; <br>Currently, the &lt;em&gt;List&lt;/em&gt;, &lt;em&gt;Scroll&lt;/em&gt;, &lt;em&gt;Grid&lt;/em&gt;, and &lt;em&gt;WaterFlow&lt;/em&gt; support the &lt;em&gt;Boolean&lt;/em&gt; type and &lt;em&gt;ICurve&lt;/em&gt;. </p>

parameters and the boolean type enables default spring animation. [since 10 - 11] and the boolean type enables default spring animation. [since 12]

**Type:** [ScrollAnimationOptions](arkts-arkui-scroll-comp-scrollanimationoptions-i.md) &#124; boolean

**Default:** 
- API version 18+: ScrollAnimationOptions: { duration: 1000, curve: Curve.Ease, canOverScroll: false }

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## canOverScroll

```TypeScript
canOverScroll?: boolean
```

Set whether the scroll target position can over the boundary.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## xOffset

```TypeScript
xOffset: number | string
```

Horizontal scrolling offset. Anonymous Object Rectification.

<p>&lt;strong&gt;NOTE&lt;/strong&gt; <br>This parameter cannot be set in percentage. <br>This parameter takes effect only when the scroll axis is the x-axis. <br>Value range: Values less than 0 are treated as 0, and scrolling occurs without animation. Animated scrolling stops at the starting position by default. By setting the **animation** parameter, you can enable a bounce effect when the scrolling goes beyond the boundary. <br>If the parameter type is number, the unit is vp. </p>

**Type:** number &#124; string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## yOffset

```TypeScript
yOffset: number | string
```

Vertical scrolling offset. Anonymous Object Rectification.

<p>&lt;strong&gt;NOTE&lt;/strong&gt; <br>This parameter cannot be set in percentage. <br>This parameter takes effect only when the scroll axis is the y-axis. <br>Value range: Values less than 0 are treated as 0, and scrolling occurs without animation. Animated scrolling stops at the starting position by default. By setting the **animation** parameter, you can enable a bounce effect when the scrolling goes beyond the boundary.<br>If the parameter type is number, the unit is vp. </p>

**Type:** number &#124; string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
