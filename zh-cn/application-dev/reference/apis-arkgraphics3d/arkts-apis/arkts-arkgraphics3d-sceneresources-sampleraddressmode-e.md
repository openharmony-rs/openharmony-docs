# SamplerAddressMode

采样器寻址模式枚举，用于控制纹理坐标超出[0, 1]范围时的处理方式。

**起始版本：** 23

<!--Device-unnamed-export enum SamplerAddressMode--><!--Device-unnamed-export enum SamplerAddressMode-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## REPEAT

```TypeScript
REPEAT = 0
```

纹理坐标超出范围时，纹理会重复平铺。

**起始版本：** 23

<!--Device-SamplerAddressMode-REPEAT = 0--><!--Device-SamplerAddressMode-REPEAT = 0-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## MIRRORED_REPEAT

```TypeScript
MIRRORED_REPEAT = 1
```

纹理坐标超出范围时，纹理以镜像方式重复。

**起始版本：** 23

<!--Device-SamplerAddressMode-MIRRORED_REPEAT = 1--><!--Device-SamplerAddressMode-MIRRORED_REPEAT = 1-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## CLAMP_TO_EDGE

```TypeScript
CLAMP_TO_EDGE = 2
```

纹理坐标超出范围时，贴图边缘像素会被拉伸延伸。

**起始版本：** 23

<!--Device-SamplerAddressMode-CLAMP_TO_EDGE = 2--><!--Device-SamplerAddressMode-CLAMP_TO_EDGE = 2-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

