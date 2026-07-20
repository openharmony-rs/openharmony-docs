# createBrightnessBlender（系统接口）

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

<a id="createbrightnessblender"></a>
## createBrightnessBlender

```TypeScript
function createBrightnessBlender(param: BrightnessBlenderParam): BrightnessBlender
```

创建BrightnessBlender实例用于给组件添加提亮效果。

**起始版本：** 12

**卡片能力：** 从API版本22开始，该接口支持在ArkTS卡片中使用。

<!--Device-uiEffect-function createBrightnessBlender(param: BrightnessBlenderParam): BrightnessBlender--><!--Device-uiEffect-function createBrightnessBlender(param: BrightnessBlenderParam): BrightnessBlender-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | [BrightnessBlenderParam](arkts-arkgraphics2d-graphics-uieffect-brightnessblenderparam-i-sys.md) | 是 | 实现提亮效果的参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [BrightnessBlender](arkts-arkgraphics2d-uieffect-brightnessblender-i-sys.md) | 返回设置了提亮效果参数的BrightnessBlender。 |

**示例：**

```TypeScript
// 创建BrightnessBlender实例用于给组件添加提亮效果
let blender : uiEffect.BrightnessBlender =
  uiEffect.createBrightnessBlender({cubicRate:1.0, quadraticRate:1.0, linearRate:1.0, degree:1.0, saturation:1.0,
    positiveCoefficient:[2.3, 4.5, 2.0], negativeCoefficient:[0.5, 2.0, 0.5], fraction:0.0})

```

