# VignetteSettings

定义暗角参数.

**起始版本：** 22

<!--Device-unnamed-export interface VignetteSettings--><!--Device-unnamed-export interface VignetteSettings-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## intensity

```TypeScript
intensity?: number
```

控制暗边或亮边的强度.当intensity > 0时，边缘变暗且中心变亮，创建经典暗角效果.当intensity < 0时，中心变暗且边缘变亮，产生反向暗角效果.

**类型：** number

**默认值：** 0.4

**起始版本：** 22

<!--Device-VignetteSettings-intensity?: double--><!--Device-VignetteSettings-intensity?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## roundness

```TypeScript
roundness?: number
```

控制暗角在[0, 1]之间的圆度.较低的值将使暗角效果更接近方形.

**类型：** number

**默认值：** sqrt(0.5)

**起始版本：** 22

<!--Device-VignetteSettings-roundness?: double--><!--Device-VignetteSettings-roundness?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

