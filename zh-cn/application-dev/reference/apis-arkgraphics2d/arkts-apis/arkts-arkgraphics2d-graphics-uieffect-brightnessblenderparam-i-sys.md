# BrightnessBlenderParam（系统接口）

BrightnessBlender的参数列表，用于配置提亮效果的各项属性，包括灰度调整系数、饱和度和混合比例等参数。

**起始版本：** 23

<!--Device-unnamed-export declare interface BrightnessBlenderParam--><!--Device-unnamed-export declare interface BrightnessBlenderParam-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## cubicRate

```TypeScript
cubicRate: double
```

灰度调整的三阶系数。 取值范围为[-20, 20]，超出边界会在实现时自动截断。

**类型：** double

**起始版本：** 23

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-BrightnessBlenderParam-cubicRate: double--><!--Device-BrightnessBlenderParam-cubicRate: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## degree

```TypeScript
degree: double
```

灰度调整的比例。 取值范围为[-20, 20]，超出边界会在实现时自动截断。

**类型：** double

**起始版本：** 23

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-BrightnessBlenderParam-degree: double--><!--Device-BrightnessBlenderParam-degree: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## fraction

```TypeScript
fraction: double
```

提亮效果的混合比例。 取值范围为[0, 1]，超出边界会在实现时自动截断。

**类型：** double

**起始版本：** 23

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-BrightnessBlenderParam-fraction: double--><!--Device-BrightnessBlenderParam-fraction: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## linearRate

```TypeScript
linearRate: double
```

灰度调整的线性系数。 取值范围为[-20, 20]，超出边界会在实现时自动截断。

**类型：** double

**起始版本：** 23

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-BrightnessBlenderParam-linearRate: double--><!--Device-BrightnessBlenderParam-linearRate: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## negativeCoefficient

```TypeScript
negativeCoefficient: [double, double, double]
```

基于基准饱和度的RGB负向调整参数。 每个number的取值范围为[-20, 20]，超出边界会在实现时自动截断。

**类型：** [double, double, double]

**起始版本：** 23

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-BrightnessBlenderParam-negativeCoefficient: [double, double, double]--><!--Device-BrightnessBlenderParam-negativeCoefficient: [double, double, double]-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## positiveCoefficient

```TypeScript
positiveCoefficient: [double, double, double]
```

基于基准饱和度的RGB正向调整参数。 每个number的取值范围为[-20, 20]，超出边界会在实现时自动截断。

**类型：** [double, double, double]

**起始版本：** 23

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-BrightnessBlenderParam-positiveCoefficient: [double, double, double]--><!--Device-BrightnessBlenderParam-positiveCoefficient: [double, double, double]-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## quadraticRate

```TypeScript
quadraticRate: double
```

灰度调整的二阶系数。 取值范围为[-20, 20]，超出边界会在实现时自动截断。

**类型：** double

**起始版本：** 23

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-BrightnessBlenderParam-quadraticRate: double--><!--Device-BrightnessBlenderParam-quadraticRate: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## saturation

```TypeScript
saturation: double
```

提亮的基准饱和度。 取值范围为[0, 20]，超出边界会在实现时自动截断。

**类型：** double

**起始版本：** 23

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-BrightnessBlenderParam-saturation: double--><!--Device-BrightnessBlenderParam-saturation: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

