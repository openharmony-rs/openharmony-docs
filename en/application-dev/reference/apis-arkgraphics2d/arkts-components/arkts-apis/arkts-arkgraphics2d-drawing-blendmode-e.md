# BlendMode

Enumerates the blend modes. A blend mode combines two colors (source color and destination color) in a specific way to create a new color. This is commonly used in graphics operations like overlaying, filtering, and masking. The blending process applies the same logic to the red, green, and blue color channels separately. The alpha channel, however, is handled according to the specific definitions of each blend mode. For brevity, the following abbreviations are used: s: source. d: destination. sa: source alpha. da: destination alpha. The following abbreviations are used in the calculation result: r: used when the calculation method is the same for the four channels (alpha, red, green, and blue channels). ra: used when only the alpha channel is manipulated. **rc**: used when the other three color channels are manipulated. The table below shows the effect of each blend mode, where the yellow rectangle is the source and the blue circle is the destination.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## CLEAR

```TypeScript
CLEAR = 0
```

r = 0, sets the destination pixels to fully transparent.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## SRC

```TypeScript
SRC = 1
```

r = s (all channels of the result equal those of the source), replaces the destination pixels with the source pixels.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## DST

```TypeScript
DST = 2
```

r = d (all channels of the result equal those of the destination), keeps the destination pixels unchanged.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## SRC_OVER

```TypeScript
SRC_OVER = 3
```

r = s + (1 - sa) * d, draws the source pixels over the destination pixels, considering the source's transparency.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## DST_OVER

```TypeScript
DST_OVER = 4
```

r = d + (1 - da) * s, draws the destination pixels over the source pixels, considering the destination's transparency.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## SRC_IN

```TypeScript
SRC_IN = 5
```

r = s * da, retains only the intersection of the source pixels with the opaque parts of the destination.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## DST_IN

```TypeScript
DST_IN = 6
```

r = d * sa, retains only the intersection of the destination pixels with the opaque parts of the source.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## SRC_OUT

```TypeScript
SRC_OUT = 7
```

r = s * (1 - da), retains the parts of the source pixels that do not overlap with the destination.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## DST_OUT

```TypeScript
DST_OUT = 8
```

r = d * (1 - sa), retains the parts of the destination pixels that do not overlap with the source.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## SRC_ATOP

```TypeScript
SRC_ATOP = 9
```

r = s * da + d * (1 - sa), covers the destination pixels with the source pixels, showing the source only in the opaque parts of the destination.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## DST_ATOP

```TypeScript
DST_ATOP = 10
```

r = d * sa + s * (1 - da), covers the source pixels with the destination pixels, showing the destination only in the opaque parts of the source.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## XOR

```TypeScript
XOR = 11
```

r = s * (1 - da) + d * (1 - sa), shows only the non-overlapping parts of the source and destination pixels.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## PLUS

```TypeScript
PLUS = 12
```

r = min(s + d, 1), adds the color values of the source and destination pixels.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## MODULATE

```TypeScript
MODULATE = 13
```

r = s * d, multiplies the color values of the source and destination pixels.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## SCREEN

```TypeScript
SCREEN = 14
```

r = s + d - s * d, inverts the color values of the source and destination pixels, multiplies them, and then inverts the result, typically producing a brighter outcome.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## OVERLAY

```TypeScript
OVERLAY = 15
```

Selectively applies **MULTIPLY** or **SCREEN** based on the brightness of the destination pixels, enhancing contrast.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## DARKEN

```TypeScript
DARKEN = 16
```

rc = s + d - max(s * da, d * sa), ra = s + (1 - sa) * d, takes the darker color values between the source and destination pixels.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## LIGHTEN

```TypeScript
LIGHTEN = 17
```

rc = s + d - min(s * da, d * sa), ra = s + (1 - sa) * d, takes the lighter color values between the source and destination pixels.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## COLOR_DODGE

```TypeScript
COLOR_DODGE = 18
```

Brightens the destination pixels by reducing contrast to reflect the source pixels.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## COLOR_BURN

```TypeScript
COLOR_BURN = 19
```

Darkens the destination pixels by increasing contrast to reflect the source pixels.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## HARD_LIGHT

```TypeScript
HARD_LIGHT = 20
```

Selectively applies **MULTIPLY** or **SCREEN** based on the brightness of the source pixels.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## SOFT_LIGHT

```TypeScript
SOFT_LIGHT = 21
```

Softly brightens or darkens the destination pixels based on the brightness of the source pixels.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## DIFFERENCE

```TypeScript
DIFFERENCE = 22
```

rc = s + d - 2 * (min(s * da, d * sa)), ra = s + (1 - sa) * d, calculates the difference between the color values of the source and destination pixels.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## EXCLUSION

```TypeScript
EXCLUSION = 23
```

rc = s + d - two(s * d), ra = s + (1 - sa) * d, similar to **DIFFERENCE** but with lower contrast.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## MULTIPLY

```TypeScript
MULTIPLY = 24
```

r = s * (1 - da) + d * (1 - sa) + s * d, multiplies the color values of the source and destination pixels, typically resulting in a darker outcome.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## HUE

```TypeScript
HUE = 25
```

Uses the hue of the source pixels and the saturation and brightness of the destination pixels.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## SATURATION

```TypeScript
SATURATION = 26
```

Uses the saturation of the source pixels and the hue and brightness of the destination pixels.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## COLOR

```TypeScript
COLOR = 27
```

Uses the hue and saturation of the source pixels and the brightness of the destination pixels.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## LUMINOSITY

```TypeScript
LUMINOSITY = 28
```

Uses the brightness of the source pixels and the hue and saturation of the destination pixels.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing
