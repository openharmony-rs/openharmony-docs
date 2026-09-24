# GlassMarbleContentParam（系统接口）

```TypeScript
interface GlassMarbleContentParam
```

玻璃弹珠的内容参数。控制内容遮罩在玻璃形状内部的混合方式，包括内容遮罩本身、着色颜色、缩放、饱和度和色散。

**起始版本：** 26.0.1

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## contentDispersion

```TypeScript
contentDispersion: number
```

玻璃形状内部混合内容的色散。控制内容边缘的颜色分离程度。取值范围为[0, 1]；超出范围的值将在内部被截断。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## contentMask

```TypeScript
contentMask: Mask
```

用于在玻璃形状内部混合附加内容的内容遮罩。提供时，将对内容遮罩进行采样并与玻璃材质合成。

**类型：** [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## contentSaturation

```TypeScript
contentSaturation: number
```

玻璃形状内部混合内容的饱和度。取值范围为[0, 1]；超出范围的值将在内部被截断。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## contentScale

```TypeScript
contentScale: number
```

应用于玻璃形状内部混合内容的缩放系数。取值范围为[0, 1]；超出范围的值将在内部被截断。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## contentTintColor

```TypeScript
contentTintColor: Color
```

应用于玻璃形状内部混合内容的着色颜色。alpha通道用作原始内容颜色与着色颜色之间的混合系数。

**类型：** Color

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。
