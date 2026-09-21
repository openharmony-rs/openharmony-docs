# GlassMarbleSphereParam（系统接口）

```TypeScript
interface GlassMarbleSphereParam
```

玻璃弹珠的球体形状参数。通过圆心位置和半径定义玻璃形状的几何结构，均采用相对于组件边界的归一化坐标。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## center

```TypeScript
center: [number, number]
```

球体形状的归一化圆心位置。[0, 0]表示组件边界的左上角，[1, 1]表示组件边界的右下角。超出[0, 1]范围的值将在内部被截断。

**类型：** [number, number]

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## radius

```TypeScript
radius: number
```

球体形状的归一化半径。取值范围为[0, 1]；超出范围的值将在内部被截断。值为1表示球的直径等于组件宽度和高度的较小值。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。
