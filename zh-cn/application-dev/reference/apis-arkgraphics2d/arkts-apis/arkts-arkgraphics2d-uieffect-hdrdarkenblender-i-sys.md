# HdrDarkenBlender（系统接口）

支持HDR的压暗混合器，用于将压暗效果添加到指定的组件上。在调用HdrDarkenBlender前，需要先通过createHdrDarkenBlender创建一个HdrDarkenBlender实例。

**起始版本：** 26.0.0

<!--Device-uiEffect-interface HdrDarkenBlender--><!--Device-uiEffect-interface HdrDarkenBlender-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## grayscaleFactor

```TypeScript
grayscaleFactor?: [number, number, number]
```

将RGB颜色转换为灰度值，该公式可根据色域切换。三个分量均无边界限制。默认值为标准灰度权重[0.299, 0.587, 0.114]。

**类型：** [number, number, number]

**默认值：** [0.299, 0.587, 0.114]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HdrDarkenBlender-grayscaleFactor?: [double, double, double]--><!--Device-HdrDarkenBlender-grayscaleFactor?: [double, double, double]-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

## hdrBrightnessRatio

```TypeScript
hdrBrightnessRatio: number
```

HDR的提亮倍数。取值范围[1.0, 设备当前支持最大提亮倍数]。设置小于1.0的值时，按值为1.0处理；当值等于1.0时，为组件原本亮度；设置大于设备当前支持最大提亮倍数的值时，按值为设备当前支持最大提亮倍数处理，支持最大提亮倍数 = 设备最大亮度 / 设备默认亮度。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HdrDarkenBlender-hdrBrightnessRatio: double--><!--Device-HdrDarkenBlender-hdrBrightnessRatio: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**系统接口：** 此接口为系统接口。

