# ColorfulBrightnessBlender（系统接口）

基于保持色相的提亮压暗混合器，用于将该提亮压暗效果添加到指定的组件上。该效果在对前景提亮或压暗时通过逐通道重建保持色相、并可增强饱和度，避免普通提亮压暗的去色问题；同时依据亮度差阈值保证前景与背景的对比度。在调用ColorfulBrightnessBlender前，需要先通过createColorfulBrightnessBlender创建一个ColorfulBrightnessBlender实例。

**起始版本：** 26.2.0

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## brightnessBlenderParam

```TypeScript
brightnessBlenderParam: BrightnessBlenderParam
```

提亮压暗的常规参数，用于配置亮度映射、饱和度曲线等基础属性。

**类型：** [BrightnessBlenderParam](arkts-arkgraphics2d-graphics-uieffect-brightnessblenderparam-i-sys.md)

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本26.2.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## options

```TypeScript
options?: ColorfulBrightnessBlenderOptions
```

提亮压暗的增强参数，用于控制提亮压暗方向、色彩增强强度、可读性阈值及HDR开关。

**类型：** [ColorfulBrightnessBlenderOptions](arkts-arkgraphics2d-uieffect-colorfulbrightnessblenderoptions-i-sys.md)

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本26.2.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。
