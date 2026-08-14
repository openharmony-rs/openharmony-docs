# createBrightnessBlender（系统接口）

## createBrightnessBlender

```TypeScript
function createBrightnessBlender(param: BrightnessBlenderParam): BrightnessBlender
```

创建BrightnessBlender实例用于给组件添加提亮效果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-uiEffect-function createBrightnessBlender(param: BrightnessBlenderParam): BrightnessBlender--><!--Device-uiEffect-function createBrightnessBlender(param: BrightnessBlenderParam): BrightnessBlender-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [BrightnessBlenderParam](arkts-arkgraphics2d-graphics-uieffect-brightnessblenderparam-i-sys.md) | 是 | 实现提亮效果的参数，包含灰度调整系数、饱和度、混合比例等配置项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BrightnessBlender](arkts-arkgraphics2d-uieffect-brightnessblender-i-sys.md) | 返回提亮效果的BrightnessBlender混合器。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
let blender : uiEffect.BrightnessBlender =
  uiEffect.createBrightnessBlender({cubicRate:1.0, quadraticRate:1.0, linearRate:1.0, degree:1.0, saturation:1.0,
    positiveCoefficient:[2.3, 4.5, 2.0], negativeCoefficient:[0.5, 2.0, 0.5], fraction:0.0})
```

ArkTS-Sta示例：

```TypeScript
import { Entry, Component, Context, Column, Color, Stack, State, Row, Text, $r } from '@kit.ArkUI'
import uiEffect from '@ohos.graphics.uiEffect'
import { BrightnessBlenderParam } from '@ohos.graphics.uiEffect'
import type common2D from '@ohos.graphics.common2D'

@Entry
@Component
struct BackgroundColorBlender {
  @State bgOptions: uiEffect.Blender = uiEffect.createBrightnessBlender({
    cubicRate: 0.5, quadraticRate: 0.5, linearRate: 0.5, degree: 0.5, saturation: 0.5,
    positiveCoefficient: [1.0, 1.0, 1.0] as [double, double, double],
    negativeCoefficient: [1.0, 1.0, 1.0] as [double, double ,double],
    fraction: 0.5
  } as BrightnessBlenderParam)

  build() {
    Stack() {
      Column() {
        Text("BrightnessBlender").fontSize(50).fontColor(Color.Red)
      }.backgroundColor(Color.Blue)
      .visualEffect(uiEffect.createEffect().backgroundColorBlender(this.bgOptions))
    }
  }
}
```

