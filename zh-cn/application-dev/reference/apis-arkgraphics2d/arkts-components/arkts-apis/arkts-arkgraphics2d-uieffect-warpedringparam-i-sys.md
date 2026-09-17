# WarpedRingParam（系统接口）

WarpedRingParam 用于指定光环的半径、宽度、变化量、旋转、3D 朝向和噪声演化。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## baseHalfWidth

```TypeScript
baseHalfWidth: number
```

定义光环厚度的一半，从中心线到任一侧边缘测量。该值无限制，推荐范围为 [0, 0.5]。小于 0 的值无实际效果。调整该效果时，建议使用 0.01 的步长以获得更好的效果。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## noiseEvolution

```TypeScript
noiseEvolution: number
```

定义噪声图案随时间的演化。该值无限制，持续动画化该值可产生动态噪声效果。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## radius

```TypeScript
radius: number
```

定义光环的半径，从光环中心到其厚度中点测量。该值无限制，推荐范围为 [0, 1]。小于 0 的值无实际效果。设为 1 时，光环的直径等于组件宽度和高度中的较小值。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## rotate3DProgress

```TypeScript
rotate3DProgress: number
```

定义光环 3D 朝向循环的进度。输入值会对 1 取模，映射到 [0, 1) 范围内。值为 0 表示初始位置，值为 1 表示完成一次完整旋转后的位置。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## rotateAngle

```TypeScript
rotateAngle: number
```

定义光环绕其中心旋转的角度。该值无限制，推荐范围为 [-2π, 2π]。正值表示顺时针旋转，负值表示逆时针旋转。与 noiseEvolution 配合使用时，可使噪声沿光环圆周流动。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## widthVariation

```TypeScript
widthVariation: number
```

定义沿光环圆周方向的变化量。该值无限制，推荐范围为 [0, 1]。小于 0 的值无实际效果。值越接近 0，光环越接近圆形。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。
