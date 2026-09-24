# ScaleOptions

```TypeScript
declare interface ScaleOptions
```

Defines the options of scale.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## centerX

```TypeScript
centerX?: number | string
```

X coordinate of the transformation center point (anchor). The value can be of the string type, for example, **'50'** and **'50%'**.

Unit: vp

**Type:** number &#124; string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## centerY

```TypeScript
centerY?: number | string
```

Y coordinate of the transformation center point (anchor). The value can be of the string type, for example, **'50'** and **'50%'**.

Unit: vp

**Type:** number &#124; string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x?: number
```

Scale ratio along the x-axis. x &gt; 1: The component is scaled up along the x-axis. 0 &lt; x &lt; 1: The component is scaled down along the x-axis. x &lt; 0: The component is scaled in the reverse direction of the x-axis.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y?: number
```

Scale ratio along the y-axis. y &gt; 1: The component is scaled up along the y-axis. 0 &lt; y &lt; 1: The component is scaled down along the y-axis. y &lt; 0: The component is scaled in the reverse direction of the y-axis.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## z

```TypeScript
z?: number
```

Scale ratio along the z-axis. z &gt; 1: The component is scaled up along the z-axis. <br>0 &lt; z &lt; 1: The component is scaled down along the z-axis. <br>z &lt; 0: The component is scaled in the reverse direction of the z-axis.

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
