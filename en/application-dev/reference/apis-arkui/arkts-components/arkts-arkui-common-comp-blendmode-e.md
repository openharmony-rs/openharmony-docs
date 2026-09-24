# BlendMode

```TypeScript
declare enum BlendMode
```

Blend mode.

> **NOTE:** 
> 
> In the **blendMode** enums, **s** indicates the source pixel, **d** indicates the target pixel, **sa** indicates
> the opacity of the source pixel, **da** indicates the opacity of the target pixel, **r** indicates the pixel after
> blending, and **ra** indicates the opacity of the pixel after blending.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

The top image is superimposed on the bottom image without any blending.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## CLEAR

```TypeScript
CLEAR = 1
```

The target pixels covered by the source pixels are erased by being turned to completely transparent.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SRC

```TypeScript
SRC = 2
```

r = s: Only the source pixels are displayed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DST

```TypeScript
DST = 3
```

r = d: Only the target pixels are displayed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SRC_OVER

```TypeScript
SRC_OVER = 4
```

r = s + (1 - sa) * d: The source pixels are blended based on opacity and cover the target pixels.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DST_OVER

```TypeScript
DST_OVER = 5
```

r = d + (1 - da) * s: The target pixels are blended based on opacity and cover on the source pixels.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SRC_IN

```TypeScript
SRC_IN = 6
```

r = s * da: Only the part of the source pixels that overlap with the target pixels is displayed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DST_IN

```TypeScript
DST_IN = 7
```

r = d * sa: Only the part of the target pixels that overlap with the source pixels is displayed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SRC_OUT

```TypeScript
SRC_OUT = 8
```

r = s * (1 - da): Only the part of the source pixels that do not overlap with the target pixels is displayed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DST_OUT

```TypeScript
DST_OUT = 9
```

r = d * (1 - sa): Only the part of the target pixels that do not overlap with the source pixels is displayed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SRC_ATOP

```TypeScript
SRC_ATOP = 10
```

r = s * da + d * (1 - sa): The part of the source pixels that overlap with the target pixels is displayed and the part of the target pixels that do not overlap with the source pixels are displayed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DST_ATOP

```TypeScript
DST_ATOP = 11
```

r = d * sa + s * (1 - da): The part of the target pixels that overlap with the source pixels and the part of the source pixels that do not overlap with the target pixels are displayed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## XOR

```TypeScript
XOR = 12
```

r = s * (1 - da) + d * (1 - sa). The pixel is not displayed where the source pixel overlaps the target pixel, and the source pixel and target pixel are displayed where the source pixel does not overlap the target pixel.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PLUS

```TypeScript
PLUS = 13
```

r = min(s + d, 1): New pixels resulting from adding the source pixels to the target pixels are displayed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MODULATE

```TypeScript
MODULATE = 14
```

r = s * d: New pixels resulting from multiplying the source pixels with the target pixels are displayed.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SCREEN

```TypeScript
SCREEN = 15
```

r = s + d - s * d: Pixels are blended by adding the source pixels to the target pixels and subtracting the product of their multiplication.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## OVERLAY

```TypeScript
OVERLAY = 16
```

The MULTIPLY or SCREEN mode is used based on the target pixels.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DARKEN

```TypeScript
DARKEN = 17
```

rc = s + d - max(s * da, d * sa), ra = kSrcOver: When two colors overlap, whichever is darker is used.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## LIGHTEN

```TypeScript
LIGHTEN = 18
```

rc = s + d - min(s * da, d * sa), ra = kSrcOver: The darker of the pixels (source and target) is used.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## COLOR_DODGE

```TypeScript
COLOR_DODGE = 19
```

The colors of the target pixels are lightened to reflect the source pixels.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## COLOR_BURN

```TypeScript
COLOR_BURN = 20
```

The colors of the target pixels are darkened to reflect the source pixels.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## HARD_LIGHT

```TypeScript
HARD_LIGHT = 21
```

The MULTIPLY or SCREEN mode is used, depending on the source pixels.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SOFT_LIGHT

```TypeScript
SOFT_LIGHT = 22
```

The LIGHTEN or DARKEN mode is used, depending on the source pixels.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## DIFFERENCE

```TypeScript
DIFFERENCE = 23
```

rc = s + d - 2 * (min(s * da, d * sa)), ra = kSrcOver: The final pixel is the result of subtracting the darker of the two pixels (source and target) from the lighter one.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## EXCLUSION

```TypeScript
EXCLUSION = 24
```

rc = s + d - two(s * d), ra = kSrcOver: The final pixel is similar to **DIFFERENCE**, but with less contrast.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## MULTIPLY

```TypeScript
MULTIPLY = 25
```

r = s * (1 - da) + d * (1 - sa) + s * d: The final pixel is the result of multiplying the source pixel by the target pixel.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## HUE

```TypeScript
HUE = 26
```

The resultant image is created with the luminance and saturation of the source image and the hue of the target image.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SATURATION

```TypeScript
SATURATION = 27
```

The resultant image is created with the luminance and hue of the target image and the saturation of the source image.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## COLOR

```TypeScript
COLOR = 28
```

The resultant image is created with the saturation and hue of the source image and the luminance of the target image.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## LUMINOSITY

```TypeScript
LUMINOSITY = 29
```

The resultant image is created with the saturation and hue of the target image and the luminance of the source image.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
