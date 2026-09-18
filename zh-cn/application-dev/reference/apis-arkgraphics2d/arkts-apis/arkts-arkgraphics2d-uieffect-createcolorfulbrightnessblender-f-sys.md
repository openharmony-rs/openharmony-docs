# createColorfulBrightnessBlender（系统接口）

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## createColorfulBrightnessBlender

```TypeScript
function createColorfulBrightnessBlender(brightnessBlenderParam: BrightnessBlenderParam,
    options?: ColorfulBrightnessBlenderOptions): ColorfulBrightnessBlender
```

创建ColorfulBrightnessBlender实例，用于给组件添加基于保持色相的提亮压暗效果。该效果在对前景提亮或压暗时通过逐通道重建保持色相、并可增强饱和度，避免普通提亮压暗的去色问题。

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本26.2.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| brightnessBlenderParam | [BrightnessBlenderParam](arkts-arkgraphics2d-graphics-uieffect-brightnessblenderparam-i-sys.md) | 是 | 提亮压暗的常规参数，用于配置亮度映射、饱和度曲线等基础属性。 |
| options | [ColorfulBrightnessBlenderOptions](arkts-arkgraphics2d-uieffect-colorfulbrightnessblenderoptions-i-sys.md) | 否 | 提亮压暗的增强参数，用于控制提亮压暗方向、色彩增强强度、可读性阈值及HDR开关。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColorfulBrightnessBlender](arkts-arkgraphics2d-uieffect-colorfulbrightnessblender-i-sys.md) | 返回基于保持色相的提亮压暗混合器。 |

**示例**

```TypeScript
import { uiEffect } from "@kit.ArkGraphics2D"

let blender : uiEffect.ColorfulBrightnessBlender =
  uiEffect.createColorfulBrightnessBlender({
    cubicRate:1.0,
    quadraticRate:1.0,
    linearRate:1.0,
    degree:1.0,
    saturation:1.0,
    positiveCoefficient:[2.3, 4.5, 2.0],
    negativeCoefficient:[0.5, 2.0, 0.5],
    fraction:0.0}, {
    darkenWeight: 0.6,
    vibrancyStrength: 0.5,
    lumaDiff: 0.4,
    hdrEnabled: true,
    tintedColorPercent: 1.0})

@Entry
@Component
struct example {
  build() {
    RelativeContainer() {
      Image($r("app.media.backgroundImage"))
        .width("100%")
        .height("100%")
      
      Text("Hello world")
        .fontSize(100)
        .fontColor(Color.Red)
        .fontWeight(900)
        .position({x: 50, y: 200})
        .advancedBlendMode(blender)
    }
  }
}
```
