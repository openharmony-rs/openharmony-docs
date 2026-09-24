# ScrollAnimationOptions

```TypeScript
declare interface ScrollAnimationOptions
```

Provides parameters for customizing scroll animations.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## canOverScroll

```TypeScript
canOverScroll?: boolean
```

Whether to enable overscroll.

<p>&lt;strong&gt;NOTE&lt;/strong&gt; <br> Scrolling can exceed the boundary and initiate a bounce animation when this parameter is set to &lt;em&gt;true&lt;/em&gt;, and the component's &lt;em&gt;edgeEffect&lt;/em&gt; attribute is set to EdgeEffect.Spring. </p>

**Type:** boolean

**Default:** false

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | ICurve
```

Scrolling curve.

**Type:** Curve &#124; ICurve

**Default:** Curve.Ease

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

Scrolling duration.

<p>&lt;strong&gt;NOTE&lt;/strong&gt; <br>Scrolling duration.<br>Default value: **1000**<br>Unit: ms <br>**NOTE:** <br>A value less than 0 evaluates to the default value. </p>

**Type:** number

**Default:** 1000

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
