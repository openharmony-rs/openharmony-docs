# BrightnessBlenderParam（系统接口）

BrightnessBlender的参数列表，用于配置提亮效果的各项属性，包括灰度调整系数、饱和度和混合比例等参数。

**起始版本：** 12

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

灰度调整的三阶系数。 取值范围为[-20, 20]，超出边界会在实现时自动截断。

**类型：** number

**起始版本：** 12

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## degree

```TypeScript
degree: number
```

灰度调整的比例。 取值范围为[-20, 20]，超出边界会在实现时自动截断。

**类型：** number

**起始版本：** 12

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## fraction

```TypeScript
fraction: number
```

提亮效果的混合比例。 取值范围为[0, 1]，超出边界会在实现时自动截断。

**类型：** number

**起始版本：** 12

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## linearRate

```TypeScript
linearRate: number
```

灰度调整的线性系数。 取值范围为[-20, 20]，超出边界会在实现时自动截断。

**类型：** number

**起始版本：** 12

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## negativeCoefficient

```TypeScript
negativeCoefficient: [number, number, number]
```

基于基准饱和度的RGB负向调整参数。 每个number的取值范围为[-20, 20]，超出边界会在实现时自动截断。

**类型：** [number, number, number]

**起始版本：** 12

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## positiveCoefficient

```TypeScript
positiveCoefficient: [number, number, number]
```

基于基准饱和度的RGB正向调整参数。 每个number的取值范围为[-20, 20]，超出边界会在实现时自动截断。

**类型：** [number, number, number]

**起始版本：** 12

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## quadraticRate

```TypeScript
quadraticRate: number
```

灰度调整的二阶系数。 取值范围为[-20, 20]，超出边界会在实现时自动截断。

**类型：** number

**起始版本：** 12

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## saturation

```TypeScript
saturation: number
```

提亮的基准饱和度。 取值范围为[0, 20]，超出边界会在实现时自动截断。

**类型：** number

**起始版本：** 12

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。
