# BlendMode

Enum for BlendMode. Blend modes for compositing current component with overlapping content. Use overlapping content as dst, current component as src.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum BlendMode--><!--Device-unnamed-export declare enum BlendMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

The top image is superimposed on the bottom image without any blending.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-NONE = 0--><!--Device-BlendMode-NONE = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CLEAR

```TypeScript
CLEAR = 1
```

The target pixels covered by the source pixels are erased by being turned to completely transparent.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-CLEAR = 1--><!--Device-BlendMode-CLEAR = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SRC

```TypeScript
SRC = 2
```

r = s: Only the source pixels are displayed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-SRC = 2--><!--Device-BlendMode-SRC = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DST

```TypeScript
DST = 3
```

r = d

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-DST = 3--><!--Device-BlendMode-DST = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SRC_OVER

```TypeScript
SRC_OVER = 4
```

r = s + (1 - sa) * d: The source pixels are blended based on opacity and cover the target pixels.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-SRC_OVER = 4--><!--Device-BlendMode-SRC_OVER = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DST_OVER

```TypeScript
DST_OVER = 5
```

r = d + (1 - da) * s: The target pixels are blended based on opacity and cover on the source pixels.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-DST_OVER = 5--><!--Device-BlendMode-DST_OVER = 5-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SRC_IN

```TypeScript
SRC_IN = 6
```

r = s * da: Only the part of the source pixels that overlap with the target pixels is displayed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-SRC_IN = 6--><!--Device-BlendMode-SRC_IN = 6-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DST_IN

```TypeScript
DST_IN = 7
```

r = d * sa: Only the part of the target pixels that overlap with the source pixels is displayed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-DST_IN = 7--><!--Device-BlendMode-DST_IN = 7-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SRC_OUT

```TypeScript
SRC_OUT = 8
```

r = s * (1 - da)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-SRC_OUT = 8--><!--Device-BlendMode-SRC_OUT = 8-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DST_OUT

```TypeScript
DST_OUT = 9
```

r = d * (1 - sa), retains the parts of the destination pixels that do not overlap with the source.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-DST_OUT = 9--><!--Device-BlendMode-DST_OUT = 9-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SRC_ATOP

```TypeScript
SRC_ATOP = 10
```

r = s * da + d * (1 - sa): The part of the source pixels that overlap with the target pixels is displayed and the part of the target pixels that do not overlap with the source pixels are displayed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-SRC_ATOP = 10--><!--Device-BlendMode-SRC_ATOP = 10-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DST_ATOP

```TypeScript
DST_ATOP = 11
```

r = d * sa + s * (1 - da): The part of the target pixels that overlap with the source pixels and the part of the source pixels that do not overlap with the target pixels are displayed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-DST_ATOP = 11--><!--Device-BlendMode-DST_ATOP = 11-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## XOR

```TypeScript
XOR = 12
```

r = s * (1 - da) + d * (1 - sa)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-XOR = 12--><!--Device-BlendMode-XOR = 12-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PLUS

```TypeScript
PLUS = 13
```

r = min(s + d, 1): New pixels resulting from adding the source pixels to the target pixels are displayed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-PLUS = 13--><!--Device-BlendMode-PLUS = 13-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MODULATE

```TypeScript
MODULATE = 14
```

r = s * d

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-MODULATE = 14--><!--Device-BlendMode-MODULATE = 14-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SCREEN

```TypeScript
SCREEN = 15
```

r = s + d - s * d

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-SCREEN = 15--><!--Device-BlendMode-SCREEN = 15-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## OVERLAY

```TypeScript
OVERLAY = 16
```

multiply or screen, depending on destination

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-OVERLAY = 16--><!--Device-BlendMode-OVERLAY = 16-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DARKEN

```TypeScript
DARKEN = 17
```

rc = s + d - max(s * da, d * sa), ra = kSrcOver

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-DARKEN = 17--><!--Device-BlendMode-DARKEN = 17-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LIGHTEN

```TypeScript
LIGHTEN = 18
```

rc = s + d - min(s * da, d * sa), ra = kSrcOver

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-LIGHTEN = 18--><!--Device-BlendMode-LIGHTEN = 18-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## COLOR_DODGE

```TypeScript
COLOR_DODGE = 19
```

brighten destination to reflect source

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-COLOR_DODGE = 19--><!--Device-BlendMode-COLOR_DODGE = 19-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## COLOR_BURN

```TypeScript
COLOR_BURN = 20
```

darken destination to reflect source

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-COLOR_BURN = 20--><!--Device-BlendMode-COLOR_BURN = 20-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## HARD_LIGHT

```TypeScript
HARD_LIGHT = 21
```

multiply or screen, depending on source

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-HARD_LIGHT = 21--><!--Device-BlendMode-HARD_LIGHT = 21-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SOFT_LIGHT

```TypeScript
SOFT_LIGHT = 22
```

The LIGHTEN or DARKEN mode is used, depending on the source pixels.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-SOFT_LIGHT = 22--><!--Device-BlendMode-SOFT_LIGHT = 22-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DIFFERENCE

```TypeScript
DIFFERENCE = 23
```

rc = s + d - 2 * (min(s * da, d * sa)), ra = kSrcOver: The final pixel is the result of subtracting the darker of the two pixels (source and target) from the lighter one.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-DIFFERENCE = 23--><!--Device-BlendMode-DIFFERENCE = 23-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EXCLUSION

```TypeScript
EXCLUSION = 24
```

rc = s + d - two(s * d), ra = kSrcOver

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-EXCLUSION = 24--><!--Device-BlendMode-EXCLUSION = 24-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MULTIPLY

```TypeScript
MULTIPLY = 25
```

r = s * (1 - da) + d * (1 - sa) + s * d: The final pixel is the result of multiplying the source pixel by the target pixel.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-MULTIPLY = 25--><!--Device-BlendMode-MULTIPLY = 25-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## HUE

```TypeScript
HUE = 26
```

hue of source with saturation and luminosity of destination

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-HUE = 26--><!--Device-BlendMode-HUE = 26-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SATURATION

```TypeScript
SATURATION = 27
```

saturation of source with hue and luminosity of destination

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-SATURATION = 27--><!--Device-BlendMode-SATURATION = 27-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## COLOR

```TypeScript
COLOR = 28
```

hue and saturation of source with luminosity of destination

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-COLOR = 28--><!--Device-BlendMode-COLOR = 28-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LUMINOSITY

```TypeScript
LUMINOSITY = 29
```

luminosity of source with hue and saturation of destination

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BlendMode-LUMINOSITY = 29--><!--Device-BlendMode-LUMINOSITY = 29-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

