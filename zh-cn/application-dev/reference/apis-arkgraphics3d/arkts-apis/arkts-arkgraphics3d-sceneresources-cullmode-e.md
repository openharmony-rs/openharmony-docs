# CullMode

用于设置基于物理渲染（PBR）材质的剔除模式枚举。通过控制剔除物体的正面或背面几何面片，提升渲染性能和视觉效果。

**起始版本：** 23

<!--Device-unnamed-export enum CullMode--><!--Device-unnamed-export enum CullMode-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## NONE

```TypeScript
NONE = 0
```

禁用剔除。

**起始版本：** 23

<!--Device-CullMode-NONE = 0--><!--Device-CullMode-NONE = 0-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## FRONT

```TypeScript
FRONT = 1
```

剔除正面几何面片。

**起始版本：** 23

<!--Device-CullMode-FRONT = 1--><!--Device-CullMode-FRONT = 1-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## BACK

```TypeScript
BACK = 2
```

剔除背面几何面片。

**起始版本：** 23

<!--Device-CullMode-BACK = 2--><!--Device-CullMode-BACK = 2-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

