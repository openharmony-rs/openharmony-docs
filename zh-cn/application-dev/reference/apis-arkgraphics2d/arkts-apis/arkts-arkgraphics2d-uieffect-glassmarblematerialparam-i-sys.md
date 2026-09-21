# GlassMarbleMaterialParam（系统接口）

```TypeScript
interface GlassMarbleMaterialParam
```

玻璃弹珠的材质参数。控制材质属性（背景色、透明度、反射贴图、阴影、焦散）以及形状缩放。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## averageBgColor

```TypeScript
averageBgColor: Color
```

平均背景色，不使用alpha通道。

**类型：** Color

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## causticEdgeSoftness

```TypeScript
causticEdgeSoftness: number
```

焦散（聚焦光线）的边缘柔和度。取值范围为[0, 1]；0产生硬边缘，1产生完全柔和的边缘。超出范围的值将在内部被截断。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## causticOffset

```TypeScript
causticOffset: number
```

焦散（聚焦光线）的垂直偏移量，按形状半径归一化。取值范围为[-1, 1]；超出范围的值将在内部被截断。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## causticOpacity

```TypeScript
causticOpacity: number
```

焦散（聚焦光线）的整体透明度。取值范围为[0, 1]；超出范围的值将在内部被截断。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## causticRadius

```TypeScript
causticRadius: number
```

焦散（聚焦光线）的半径，按形状半径归一化。取值范围为[0, 1]；超出范围的值将在内部被截断。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## opacity

```TypeScript
opacity: number
```

玻璃效果的整体透明度。取值范围为[0, 1]；0表示完全透明，1表示完全不透明。超出范围的值将在内部被截断。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## reflectionMap

```TypeScript
reflectionMap: image.PixelMap
```

用于玻璃表面环境反射的反射贴图。通过image模块创建为PixelMap实例。

**类型：** [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## shadowEdgeSoftness

```TypeScript
shadowEdgeSoftness: number
```

阴影的边缘柔和度。取值范围为[0, 1]；0产生硬边缘，1产生完全柔和的边缘。超出范围的值将在内部被截断。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## shadowOffset

```TypeScript
shadowOffset: number
```

阴影的垂直偏移量，按形状半径归一化。取值范围为[-1, 1]；超出范围的值将在内部被截断。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## shadowOpacity

```TypeScript
shadowOpacity: number
```

阴影的整体透明度。取值范围为[0, 1]；超出范围的值将在内部被截断。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## shadowRadius

```TypeScript
shadowRadius: number
```

阴影的半径，按形状半径归一化。取值范围为[0, 1]；超出范围的值将在内部被截断。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## shapeScale

```TypeScript
shapeScale: number
```

应用于玻璃形状的缩放系数。取值范围为[0, 1]；超出范围的值将在内部被截断。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。
