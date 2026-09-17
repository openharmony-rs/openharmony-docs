# ColorfulBrightnessBlenderOptions（系统接口）

基于保持色相的提亮压暗混合器的可选增强配置项，作为createColorfulBrightnessBlender的options参数传入。它在常规参数BrightnessBlenderParam之外，可进一步针对提亮或压暗方向、色彩增强强度、输入色彩影响度、与背景的对比度以及HDR开关进行精细调整，不传时各项采用默认值。

**起始版本：** 26.2.0

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## darkenWeight

```TypeScript
darkenWeight?: number
```

前景压暗权重，控制提亮压暗的方向与强度。取0时提亮前景，前景倾向亮于背景以保证可读性；取1时压暗前景，前景倾向暗于背景；0到1之间为提亮与压暗的过渡。默认值为1。取值范围为[0, 1]，超出边界会在实现时自动截断。

**类型：** number

**默认值：** 1

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本26.2.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## hdrEnabled

```TypeScript
hdrEnabled?: boolean
```

是否主动开启HDR。取true时主动开启HDR，结果亮度可超出SDR范围（&gt;1.0），在HDR设备上呈现更高亮度，适合HDR内容；取false时不主动开启HDR，结果限制在SDR范围（≤1.0），但当前景或背景本身为HDR时仍可能被动触发HDR。默认值为false。

**类型：** boolean

**默认值：** false

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本26.2.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## lumaDiff

```TypeScript
lumaDiff?: number
```

保证可读性的亮度差阈值，用于约束前景与背景之间的亮度差以保持足够对比度。取0时不强制额外亮度差，可读性约束最弱；值越大强制的亮度差越大、对比度越强；取1时强制最大亮度差。默认值为0。取值范围为[0, 1]，超出边界会在实现时自动截断。

**类型：** number

**默认值：** 0

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本26.2.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## tintedColorPercent

```TypeScript
tintedColorPercent?: number
```

输入色彩影响度，控制输入色参与提亮压暗计算的程度。取1时输入色完全参与计算，输出结果保留输入色的色彩倾向；取0时输入色不参与计算，输出结果不受输入色的影响，直接基于背景颜色做提亮压暗；0到1之间为两者的插值过渡。默认值为1。取值范围为[0, 1]，超出边界会在实现时自动截断。

**类型：** number

**默认值：** 1

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本26.2.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## vibrancyStrength

```TypeScript
vibrancyStrength?: number
```

色彩增强强度，控制对前景饱和度的增强程度。取0时不额外增强饱和度，前景保持原始饱和度；值越大饱和度增强越明显，取1时增强到最大、色彩最鲜艳。默认值为0。取值范围为[0, 1]，超出边界会在实现时自动截断。

**类型：** number

**默认值：** 0

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本26.2.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。
