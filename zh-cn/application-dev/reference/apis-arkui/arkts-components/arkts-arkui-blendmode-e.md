# BlendMode

混合模式。

> **说明：**  
>  
> blendMode枚举中，s表示源像素，d表示目标像素，sa表示源像素透明度，da表示目标像素透明度，r表示混合后像素，ra表示混合后像素透明度。

**起始版本：** 12

<!--Device-unnamed-declare enum BlendMode--><!--Device-unnamed-declare enum BlendMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NONE

```TypeScript
NONE = 0
```

将上层图像直接覆盖到下层图像上，不进行任何混合操作。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-NONE = 0--><!--Device-BlendMode-NONE = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## CLEAR

```TypeScript
CLEAR = 1
```

将源像素覆盖的目标像素清除为完全透明。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-CLEAR = 1--><!--Device-BlendMode-CLEAR = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SRC

```TypeScript
SRC = 2
```

r = s，只显示源像素。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-SRC = 2--><!--Device-BlendMode-SRC = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DST

```TypeScript
DST = 3
```

r = d，只显示目标像素。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-DST = 3--><!--Device-BlendMode-DST = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SRC_OVER

```TypeScript
SRC_OVER = 4
```

r = s + (1 - sa) * d，将源像素按照透明度进行混合，覆盖在目标像素上。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-SRC_OVER = 4--><!--Device-BlendMode-SRC_OVER = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DST_OVER

```TypeScript
DST_OVER = 5
```

r = d + (1 - da) * s，将目标像素按照透明度进行混合，覆盖在源像素上。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-DST_OVER = 5--><!--Device-BlendMode-DST_OVER = 5-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SRC_IN

```TypeScript
SRC_IN = 6
```

r = s * da，只显示源像素中与目标像素重叠的部分。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-SRC_IN = 6--><!--Device-BlendMode-SRC_IN = 6-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DST_IN

```TypeScript
DST_IN = 7
```

r = d * sa，只显示目标像素中与源像素重叠的部分。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-DST_IN = 7--><!--Device-BlendMode-DST_IN = 7-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SRC_OUT

```TypeScript
SRC_OUT = 8
```

r = s * (1 - da)，只显示源像素中与目标像素不重叠的部分。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-SRC_OUT = 8--><!--Device-BlendMode-SRC_OUT = 8-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DST_OUT

```TypeScript
DST_OUT = 9
```

r = d * (1 - sa), retains the parts of the destination pixels that do not overlap with the source.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-DST_OUT = 9--><!--Device-BlendMode-DST_OUT = 9-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SRC_ATOP

```TypeScript
SRC_ATOP = 10
```

r = s * da + d * (1 - sa)，在源像素和目标像素重叠的地方绘制源像素，在源像素和目标像素不重叠的地方绘制目标像素。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-SRC_ATOP = 10--><!--Device-BlendMode-SRC_ATOP = 10-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DST_ATOP

```TypeScript
DST_ATOP = 11
```

r = d * sa + s * (1 - da): The part of the target pixels that overlap with the source pixels and the part of the source pixels that do not overlap with the target pixels are displayed.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-DST_ATOP = 11--><!--Device-BlendMode-DST_ATOP = 11-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## XOR

```TypeScript
XOR = 12
```

r = s * (1 - da) + d * (1 - sa)，在源像素和目标像素重叠的地方不显示像素，不重叠的地方显示源像素和目标像素。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-XOR = 12--><!--Device-BlendMode-XOR = 12-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## PLUS

```TypeScript
PLUS = 13
```

r = min(s + d, 1):New pixels resulting from adding the source pixels to the target pixels are displayed.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-PLUS = 13--><!--Device-BlendMode-PLUS = 13-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MODULATE

```TypeScript
MODULATE = 14
```

r = s * d，将源像素与目标像素进行乘法运算，并将结果作为新的像素值。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-MODULATE = 14--><!--Device-BlendMode-MODULATE = 14-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SCREEN

```TypeScript
SCREEN = 15
```

r = s + d - s * d，将两个图像的像素值相加，然后减去它们的乘积来实现混合。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-SCREEN = 15--><!--Device-BlendMode-SCREEN = 15-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## OVERLAY

```TypeScript
OVERLAY = 16
```

根据目标像素来决定使用MULTIPLY混合模式还是SCREEN混合模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-OVERLAY = 16--><!--Device-BlendMode-OVERLAY = 16-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DARKEN

```TypeScript
DARKEN = 17
```

rc = s + d - max(s * da, d * sa), ra = kSrcOver，当两个颜色重叠时，较暗的颜色会覆盖较亮的颜色。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-DARKEN = 17--><!--Device-BlendMode-DARKEN = 17-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LIGHTEN

```TypeScript
LIGHTEN = 18
```

rc = s + d - min(s * da, d * sa), ra = kSrcOver，将源图像和目标图像中的像素进行比较，选取两者中较亮的像素作为最终的混合结果。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-LIGHTEN = 18--><!--Device-BlendMode-LIGHTEN = 18-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## COLOR_DODGE

```TypeScript
COLOR_DODGE = 19
```

使目标像素变得更亮来反映源像素。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-COLOR_DODGE = 19--><!--Device-BlendMode-COLOR_DODGE = 19-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## COLOR_BURN

```TypeScript
COLOR_BURN = 20
```

使目标像素变得更暗来反映源像素。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-COLOR_BURN = 20--><!--Device-BlendMode-COLOR_BURN = 20-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## HARD_LIGHT

```TypeScript
HARD_LIGHT = 21
```

根据源像素的值来决定目标像素变得更亮或者更暗。根据源像素来决定使用MULTIPLY混合模式还是SCREEN混合模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-HARD_LIGHT = 21--><!--Device-BlendMode-HARD_LIGHT = 21-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SOFT_LIGHT

```TypeScript
SOFT_LIGHT = 22
```

根据源像素来决定使用LIGHTEN混合模式还是DARKEN混合模式。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-SOFT_LIGHT = 22--><!--Device-BlendMode-SOFT_LIGHT = 22-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DIFFERENCE

```TypeScript
DIFFERENCE = 23
```

rc = s + d - 2 * (min(s * da, d * sa)), ra = kSrcOver: The final pixel is the result of subtracting the darker of the two pixels (source and target) from the lighter one.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-DIFFERENCE = 23--><!--Device-BlendMode-DIFFERENCE = 23-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## EXCLUSION

```TypeScript
EXCLUSION = 24
```

rc = s + d - 2 * (s * d), ra = kSrcOver，对比源像素和目标像素，亮度更高的像素减去亮度更低的像素，产生柔和的效果。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-EXCLUSION = 24--><!--Device-BlendMode-EXCLUSION = 24-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MULTIPLY

```TypeScript
MULTIPLY = 25
```

r = s * (1 - da) + d * (1 - sa) + s * d，将源图像与目标图像进行乘法混合，得到一张新的图像。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-MULTIPLY = 25--><!--Device-BlendMode-MULTIPLY = 25-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## HUE

```TypeScript
HUE = 26
```

保留源图像的亮度和饱和度，但会使用目标图像的色调来替换源图像的色调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-HUE = 26--><!--Device-BlendMode-HUE = 26-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SATURATION

```TypeScript
SATURATION = 27
```

保留目标像素的亮度和色调，但会使用源像素的饱和度来替换目标像素的饱和度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-SATURATION = 27--><!--Device-BlendMode-SATURATION = 27-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## COLOR

```TypeScript
COLOR = 28
```

保留源像素的饱和度和色调，但会使用目标像素的亮度来替换源像素的亮度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-COLOR = 28--><!--Device-BlendMode-COLOR = 28-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LUMINOSITY

```TypeScript
LUMINOSITY = 29
```

保留目标像素的色调和饱和度，但会用源像素的亮度替换目标像素的亮度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BlendMode-LUMINOSITY = 29--><!--Device-BlendMode-LUMINOSITY = 29-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

