# VignetteSettings

边缘暗角设置。

**起始版本：** 23

<!--Device-unnamed-export interface VignetteSettings--><!--Device-unnamed-export interface VignetteSettings-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## intensity

```TypeScript
intensity?: double
```

作用强度，取值范围为[0, 1]，取值为0时无暗角效果，取值为1时为最大暗角强度，默认值为0.4。

**类型：** double

**默认值：** 0.4

**起始版本：** 23

<!--Device-VignetteSettings-intensity?: double--><!--Device-VignetteSettings-intensity?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## roundness

```TypeScript
roundness?: double
```

暗角的圆度，取值范围为[0, 1]，取值为0时暗角形状趋近矩形，取值为1时暗角形状趋近圆形，默认值为sqrt(0.5)（约0.707）。

**类型：** double

**默认值：** sqrt(0.5)

**起始版本：** 23

<!--Device-VignetteSettings-roundness?: double--><!--Device-VignetteSettings-roundness?: double-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

