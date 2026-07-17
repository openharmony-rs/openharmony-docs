# BlendMode

混合模式枚举。混合模式会将两种颜色（源色、目标色）以特定的方式混合生成一种新的颜色，通常用于叠加、滤镜和遮罩等图形操作场景。混合操作会分别作用于红、绿、蓝三个颜色通道，采用相同的混合逻辑，而透明度（Alpha通道）则根据各模式的定义另行处理。为简洁起见，我们使用以下缩写：

s : source 源的缩写。d : destination 目标的缩写。sa : source alpha 源透明度的缩写。da : destination alpha 目标透明度的缩写。

计算结果用如下缩写表示：

r : 如果4个通道（透明度、红、绿、蓝）的计算方式相同，用r表示。ra : 如果只操作透明度通道，用ra表示。rc : 如果操作3个颜色通道，用rc表示。

以黄色矩形为源图像，蓝色圆形为目标图像，各混合模式枚举生成的效果示意图请参考下表。

**起始版本：** 11

<!--Device-drawing-enum BlendMode--><!--Device-drawing-enum BlendMode-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## CLEAR

```TypeScript
CLEAR = 0
```

清除模式，r = 0，设置为全透明。

**起始版本：** 11

<!--Device-BlendMode-CLEAR = 0--><!--Device-BlendMode-CLEAR = 0-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## SRC

```TypeScript
SRC = 1
```

r = s（result的4个通道，都等于source的4个通道，即结果等于源。），使用源像素替换目标像素。

**起始版本：** 11

<!--Device-BlendMode-SRC = 1--><!--Device-BlendMode-SRC = 1-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## DST

```TypeScript
DST = 2
```

r = d（result的4个通道，都等于destination的4个通道，即结果等于目标。），保持目标像素不变。

**起始版本：** 11

<!--Device-BlendMode-DST = 2--><!--Device-BlendMode-DST = 2-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## SRC_OVER

```TypeScript
SRC_OVER = 3
```

r = s + (1 - sa) * d，在目标像素上方绘制源像素，考虑源像素的透明度。

**起始版本：** 11

<!--Device-BlendMode-SRC_OVER = 3--><!--Device-BlendMode-SRC_OVER = 3-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## DST_OVER

```TypeScript
DST_OVER = 4
```

r = d + (1 - da) * s，在源像素上方绘制目标像素，考虑目标像素的透明度。

**起始版本：** 11

<!--Device-BlendMode-DST_OVER = 4--><!--Device-BlendMode-DST_OVER = 4-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## SRC_IN

```TypeScript
SRC_IN = 5
```

r = s * da，仅保留源像素与目标不透明部分的交集。

**起始版本：** 11

<!--Device-BlendMode-SRC_IN = 5--><!--Device-BlendMode-SRC_IN = 5-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## DST_IN

```TypeScript
DST_IN = 6
```

r = d * sa，仅保留目标像素与源不透明部分的交集。

**起始版本：** 11

<!--Device-BlendMode-DST_IN = 6--><!--Device-BlendMode-DST_IN = 6-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## SRC_OUT

```TypeScript
SRC_OUT = 7
```

r = s * (1 - da)，保留源像素中不与目标重叠的部分。

**起始版本：** 11

<!--Device-BlendMode-SRC_OUT = 7--><!--Device-BlendMode-SRC_OUT = 7-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## DST_OUT

```TypeScript
DST_OUT = 8
```

r = d * (1 - sa)，保留目标像素中不与源重叠的部分。

**起始版本：** 11

<!--Device-BlendMode-DST_OUT = 8--><!--Device-BlendMode-DST_OUT = 8-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## SRC_ATOP

```TypeScript
SRC_ATOP = 9
```

r = s * da + d * (1 - sa)，源像素覆盖在目标像素上，仅在目标不透明部分显示源像素。

**起始版本：** 11

<!--Device-BlendMode-SRC_ATOP = 9--><!--Device-BlendMode-SRC_ATOP = 9-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## DST_ATOP

```TypeScript
DST_ATOP = 10
```

r = d * sa + s * (1 - da)，目标像素覆盖在源像素上，仅在源不透明部分显示目标像素。

**起始版本：** 11

<!--Device-BlendMode-DST_ATOP = 10--><!--Device-BlendMode-DST_ATOP = 10-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## XOR

```TypeScript
XOR = 11
```

r = s * (1 - da) + d * (1 - sa)，仅显示源像素和目标像素中不重叠的部分。

**起始版本：** 11

<!--Device-BlendMode-XOR = 11--><!--Device-BlendMode-XOR = 11-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## PLUS

```TypeScript
PLUS = 12
```

r = min(s + d, 1)，源和目标像素的颜色值相加。

**起始版本：** 11

<!--Device-BlendMode-PLUS = 12--><!--Device-BlendMode-PLUS = 12-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## MODULATE

```TypeScript
MODULATE = 13
```

r = s * d，源和目标像素的颜色值相乘。

**起始版本：** 11

<!--Device-BlendMode-MODULATE = 13--><!--Device-BlendMode-MODULATE = 13-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## SCREEN

```TypeScript
SCREEN = 14
```

滤色模式，r = s + d - s * d，反转源和目标像素的颜色值，相乘后再反转，结果通常更亮。

**起始版本：** 11

<!--Device-BlendMode-SCREEN = 14--><!--Device-BlendMode-SCREEN = 14-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## OVERLAY

```TypeScript
OVERLAY = 15
```

叠加模式，根据目标像素的亮度，选择性地应用MULTIPLY或SCREEN模式，增强对比度。

**起始版本：** 11

<!--Device-BlendMode-OVERLAY = 15--><!--Device-BlendMode-OVERLAY = 15-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## DARKEN

```TypeScript
DARKEN = 16
```

变暗模式，rc = s + d - max(s * da, d * sa), ra = s + (1 - sa) * d，取源和目标像素中较暗的颜色值。

**起始版本：** 11

<!--Device-BlendMode-DARKEN = 16--><!--Device-BlendMode-DARKEN = 16-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## LIGHTEN

```TypeScript
LIGHTEN = 17
```

变亮模式，rc = s + d - min(s * da, d * sa), ra = s + (1 - sa) * d，取源和目标像素中较亮的颜色值。

**起始版本：** 11

<!--Device-BlendMode-LIGHTEN = 17--><!--Device-BlendMode-LIGHTEN = 17-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## COLOR_DODGE

```TypeScript
COLOR_DODGE = 18
```

颜色减淡模式，通过减小对比度使目标像素变亮以反映源像素。

**起始版本：** 11

<!--Device-BlendMode-COLOR_DODGE = 18--><!--Device-BlendMode-COLOR_DODGE = 18-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## COLOR_BURN

```TypeScript
COLOR_BURN = 19
```

颜色加深模式，通过增加对比度使目标像素变暗以反映源像素。

**起始版本：** 11

<!--Device-BlendMode-COLOR_BURN = 19--><!--Device-BlendMode-COLOR_BURN = 19-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## HARD_LIGHT

```TypeScript
HARD_LIGHT = 20
```

强光模式，根据源像素的亮度，选择性地应用MULTIPLY或SCREEN模式。

**起始版本：** 11

<!--Device-BlendMode-HARD_LIGHT = 20--><!--Device-BlendMode-HARD_LIGHT = 20-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## SOFT_LIGHT

```TypeScript
SOFT_LIGHT = 21
```

柔光模式，根据源像素的亮度，柔和地变亮或变暗目标像素。

**起始版本：** 11

<!--Device-BlendMode-SOFT_LIGHT = 21--><!--Device-BlendMode-SOFT_LIGHT = 21-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## DIFFERENCE

```TypeScript
DIFFERENCE = 22
```

差值模式，rc = s + d - 2 * (min(s * da, d * sa)), ra = s + (1 - sa) * d，计算源和目标像素颜色值的差异。

**起始版本：** 11

<!--Device-BlendMode-DIFFERENCE = 22--><!--Device-BlendMode-DIFFERENCE = 22-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## EXCLUSION

```TypeScript
EXCLUSION = 23
```

排除模式，rc = s + d - two(s * d), ra = s + (1 - sa) * d，类似于DIFFERENCE，但对比度较低。

**起始版本：** 11

<!--Device-BlendMode-EXCLUSION = 23--><!--Device-BlendMode-EXCLUSION = 23-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## MULTIPLY

```TypeScript
MULTIPLY = 24
```

正片叠底，r = s * (1 - da) + d * (1 - sa) + s * d，源和目标像素的颜色值相乘，结果通常更暗。

**起始版本：** 11

<!--Device-BlendMode-MULTIPLY = 24--><!--Device-BlendMode-MULTIPLY = 24-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## HUE

```TypeScript
HUE = 25
```

色相模式，使用源像素的色相，目标像素的饱和度和亮度。

**起始版本：** 11

<!--Device-BlendMode-HUE = 25--><!--Device-BlendMode-HUE = 25-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## SATURATION

```TypeScript
SATURATION = 26
```

饱和度模式，使用源像素的饱和度，目标像素的色相和亮度。

**起始版本：** 11

<!--Device-BlendMode-SATURATION = 26--><!--Device-BlendMode-SATURATION = 26-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## COLOR

```TypeScript
COLOR = 27
```

颜色模式，使用源像素的色相和饱和度，目标像素的亮度。

**起始版本：** 11

<!--Device-BlendMode-COLOR = 27--><!--Device-BlendMode-COLOR = 27-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## LUMINOSITY

```TypeScript
LUMINOSITY = 28
```

亮度模式，使用源像素的亮度，目标像素的色相和饱和度。

**起始版本：** 11

<!--Device-BlendMode-LUMINOSITY = 28--><!--Device-BlendMode-LUMINOSITY = 28-End-->

**系统能力：** SystemCapability.Graphics.Drawing

