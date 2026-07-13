# createHdrBrightnessBlender（系统接口）

## createHdrBrightnessBlender

```TypeScript
function createHdrBrightnessBlender(param: BrightnessBlenderParam): HdrBrightnessBlender
```

创建HdrBrightnessBlender实例用于给组件添加支持HDR的提亮效果。

**起始版本：** 20

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | BrightnessBlenderParam | 是 | 实现提亮效果的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| HdrBrightnessBlender | 返回具有提亮效果的混合器（支持HDR）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | 权限校验失败，非系统应用调用系统接口。 |

**示例：**

```TypeScript
import { uiEffect } from "@kit.ArkGraphics2D"

let blender : uiEffect.HdrBrightnessBlender =
  uiEffect.createHdrBrightnessBlender({cubicRate:1.0, quadraticRate:1.0, linearRate:1.0, degree:1.0, saturation:1.0,
    positiveCoefficient:[2.3, 4.5, 2.0], negativeCoefficient:[0.5, 2.0, 0.5], fraction:0.0})

@Entry
@Component
struct example {
  build() {
    RelativeContainer() {
      Image($r("app.media.screenshot"))
        .width("100%")
        .height("100%")
        .advancedBlendMode(blender)
    }
  }
}

```

