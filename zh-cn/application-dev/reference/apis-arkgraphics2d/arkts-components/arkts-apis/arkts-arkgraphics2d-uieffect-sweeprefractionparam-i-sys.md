# SweepRefractionParam（系统接口）

创建 SweepRefractionMask 的必选参数。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## chromaDelta

```TypeScript
chromaDelta: number
```

设置色散偏移量。取值范围为 [0, 0.5]，超出范围的值在实现时会被截断。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## edgeThickness

```TypeScript
edgeThickness: number
```

设置棱镜的归一化边缘厚度。取值范围为 [1, 1000]，超出范围的值在实现时会被截断。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## maskRadius

```TypeScript
maskRadius: number
```

设置棱镜遮罩的归一化半径。取值范围为 [0, 10]，超出范围的值在实现时会被截断。当 maskRadius等于1.0时, 等于组件宽度。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## refractAmount

```TypeScript
refractAmount: number
```

设置棱镜的折射强度。取值范围为 [0, 1]，超出范围的值在实现时会被截断。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## rippleWidth

```TypeScript
rippleWidth: number
```

设置扫光波纹的宽度。取值范围为 [0.01, 1]，超出范围的值在实现时会被截断。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## sweepOffset

```TypeScript
sweepOffset: number
```

设置扫光的位置偏移。取值范围为 [-2, 2]，超出范围的值在实现时会被截断。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。
