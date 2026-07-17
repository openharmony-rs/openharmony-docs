# BrightnessBlender（系统接口）

提亮混合器，用于将提亮效果添加到指定的组件上。在调用BrightnessBlender前，需要先通过createBrightnessBlender创建一个BrightnessBlender实例。

**起始版本：** 12

<!--Device-uiEffect-interface BrightnessBlender--><!--Device-uiEffect-interface BrightnessBlender-End-->

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

<!--Device-BrightnessBlender-cubicRate: double--><!--Device-BrightnessBlender-cubicRate: double-End-->

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

<!--Device-BrightnessBlender-degree: double--><!--Device-BrightnessBlender-degree: double-End-->

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

<!--Device-BrightnessBlender-fraction: double--><!--Device-BrightnessBlender-fraction: double-End-->

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

<!--Device-BrightnessBlender-linearRate: double--><!--Device-BrightnessBlender-linearRate: double-End-->

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

<!--Device-BrightnessBlender-negativeCoefficient: [double, double, double]--><!--Device-BrightnessBlender-negativeCoefficient: [double, double, double]-End-->

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

<!--Device-BrightnessBlender-positiveCoefficient: [double, double, double]--><!--Device-BrightnessBlender-positiveCoefficient: [double, double, double]-End-->

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

<!--Device-BrightnessBlender-quadraticRate: double--><!--Device-BrightnessBlender-quadraticRate: double-End-->

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

<!--Device-BrightnessBlender-saturation: double--><!--Device-BrightnessBlender-saturation: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

