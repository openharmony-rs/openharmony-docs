# BrightnessBlenderParam（系统接口）

BrightnessBlender参数列表。

**起始版本：** 12

<!--Device-unnamed-export declare interface BrightnessBlenderParam--><!--Device-unnamed-export declare interface BrightnessBlenderParam-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## cubicRate

```TypeScript
cubicRate: number
```

灰度调整的三阶系数。 取值范围[-20, 20]。

**类型：** number

**起始版本：** 12

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-BrightnessBlenderParam-cubicRate: double--><!--Device-BrightnessBlenderParam-cubicRate: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## degree

```TypeScript
degree: number
```

灰度调整的比例。 取值范围[-20, 20]。

**类型：** number

**起始版本：** 12

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-BrightnessBlenderParam-degree: double--><!--Device-BrightnessBlenderParam-degree: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## fraction

```TypeScript
fraction: number
```

提亮效果的混合比例。 取值范围[0, 1]，超出边界会在实现时自动截断。

**类型：** number

**起始版本：** 12

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-BrightnessBlenderParam-fraction: double--><!--Device-BrightnessBlenderParam-fraction: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## linearRate

```TypeScript
linearRate: number
```

灰度调整的线性系数。 取值范围[-20, 20]。

**类型：** number

**起始版本：** 12

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-BrightnessBlenderParam-linearRate: double--><!--Device-BrightnessBlenderParam-linearRate: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## negativeCoefficient

```TypeScript
negativeCoefficient: [number, number, number]
```

基于基准饱和度的RGB负向调整参数。 每个number的取值范围[-20, 20]。

**类型：** [number, number, number]

**起始版本：** 12

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-BrightnessBlenderParam-negativeCoefficient: [double, double, double]--><!--Device-BrightnessBlenderParam-negativeCoefficient: [double, double, double]-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## positiveCoefficient

```TypeScript
positiveCoefficient: [number, number, number]
```

基于基准饱和度的RGB正向调整参数。 每个number的取值范围[-20, 20]。

**类型：** [number, number, number]

**起始版本：** 12

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-BrightnessBlenderParam-positiveCoefficient: [double, double, double]--><!--Device-BrightnessBlenderParam-positiveCoefficient: [double, double, double]-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## quadraticRate

```TypeScript
quadraticRate: number
```

灰度调整的二阶系数。 取值范围[-20, 20]。

**类型：** number

**起始版本：** 12

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-BrightnessBlenderParam-quadraticRate: double--><!--Device-BrightnessBlenderParam-quadraticRate: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## saturation

```TypeScript
saturation: number
```

提亮的基准饱和度。 取值范围[0, 20]。

**类型：** number

**起始版本：** 12

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-BrightnessBlenderParam-saturation: double--><!--Device-BrightnessBlenderParam-saturation: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

