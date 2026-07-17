# createHdrDarkenBlender（系统接口）

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## createHdrDarkenBlender

```TypeScript
function createHdrDarkenBlender(hdrBrightnessRatio: number,
    grayscaleFactor?: [number, number, number]): HdrDarkenBlender
```

创建HdrDarkenBlender实例用于HDR图层的压暗混合效果。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-uiEffect-function createHdrDarkenBlender(hdrBrightnessRatio: double,
    grayscaleFactor?: [double, double, double]): HdrDarkenBlender--><!--Device-uiEffect-function createHdrDarkenBlender(hdrBrightnessRatio: double,
    grayscaleFactor?: [double, double, double]): HdrDarkenBlender-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hdrBrightnessRatio | number | 是 | HDR的提亮倍数。取值范围[1.0, 设备当前支持最大提亮倍数]。设置小于1.0的值时，按值为1.0处理；当值等于1.0时，为组件原本亮度；设置大于设备当前支持最大提亮倍数的值时，按值为设备当前支持最大提亮倍数处理，支持最大提亮倍数 = 设备最大亮度 / 设备默认亮度。 |
| grayscaleFactor | [number, number, number] | 否 | 将RGB颜色转换为灰度值，该公式可根据色域切换。三个分量均无边界限制。默认值为标准灰度权重[0.299, 0.587, 0.114]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [HdrDarkenBlender](arkts-arkgraphics2d-uieffect-hdrdarkenblender-i-sys.md) | 返回HDR压暗混合器，用于将压暗效果添加到指定的组件上。 |

**示例：**

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D'

// 创建HDR压暗混合器实例
let blender : uiEffect.HdrDarkenBlender = 
  uiEffect.createHdrDarkenBlender(1.3, [0.299, 0.587, 0.114])

@Entry
@Component
struct Example {
  build() { 
    RelativeContainer() { 
      Stack(){ 
          Text("TextWord") 
          Image($r("app.media.screenshot")) 
            .width("100%") 
            .height("100%") 
            .advancedBlendMode(blender) 
      } 
    } 
  } 
}

```

