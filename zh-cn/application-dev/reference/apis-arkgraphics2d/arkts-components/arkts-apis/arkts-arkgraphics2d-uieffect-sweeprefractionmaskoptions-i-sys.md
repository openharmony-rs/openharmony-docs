# SweepRefractionMaskOptions（系统接口）

创建 SweepRefractionMask 的可选参数。

**起始版本：** 26.1.0

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## cornerRadius

```TypeScript
cornerRadius?: number
```

棱镜形状的归一化圆角半径，仅在 shapeType 为 ROUNDED_RECT 时生效。取值范围为 [0, 1]，超出范围的值将在实现时被截断。当 cornerRadius 为 1.0 时，等于组件高度。

**类型：** number

**默认值：** {0.16}

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## prismHeight

```TypeScript
prismHeight?: number
```

棱镜的归一化高度。取值范围为 [0.01, 2]，超出范围的值将在实现时被截断。当 prismHeight 为 1.0 时，等于组件高度。

**类型：** number

**默认值：** {1.0}

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## prismWidth

```TypeScript
prismWidth?: number
```

棱镜的归一化宽度。取值范围为 [0.01, 2]，超出范围的值将在实现时被截断。当 prismWidth 为 1.0 时，等于组件宽度。

**类型：** number

**默认值：** {1.0}

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## shapeType

```TypeScript
shapeType?: PrismShapeType
```

棱镜形状类型。

**类型：** [PrismShapeType](arkts-arkgraphics2d-uieffect-prismshapetype-e-sys.md)

**默认值：** {PrismShapeType.ROUNDED_RECT}

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## sweepCenterX

```TypeScript
sweepCenterX?: number
```

扫光中心的归一化 X 坐标。取值范围为 [0, 1]，超出范围的值将在实现时被截断。0.0 表示左边缘，1.0 表示右边缘，默认值为 0.0。

**类型：** number

**默认值：** {0.0}

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## sweepCenterY

```TypeScript
sweepCenterY?: number
```

扫光中心的归一化 Y 坐标。取值范围为 [0, 1]，超出范围的值将在实现时被截断。0.0 表示上边缘，1.0 表示下边缘，默认值为 0.0。

**类型：** number

**默认值：** {0.0}

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。
