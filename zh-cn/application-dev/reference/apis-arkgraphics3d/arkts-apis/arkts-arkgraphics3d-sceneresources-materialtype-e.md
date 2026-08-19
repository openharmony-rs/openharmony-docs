# MaterialType

场景中物体材质类型枚举，定义材质的渲染方式。

**起始版本：** 23

<!--Device-unnamed-export enum MaterialType--><!--Device-unnamed-export enum MaterialType-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## SHADER

```TypeScript
SHADER = 1
```

材质由着色器定义。

**起始版本：** 23

<!--Device-MaterialType-SHADER = 1--><!--Device-MaterialType-SHADER = 1-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## METALLIC_ROUGHNESS

```TypeScript
METALLIC_ROUGHNESS = 2
```

采用基于物理渲染（PBR）的金属-粗糙度模型，通过金属度与粗糙度参数，模拟更真实的材质光照效果。

**起始版本：** 23

<!--Device-MaterialType-METALLIC_ROUGHNESS = 2--><!--Device-MaterialType-METALLIC_ROUGHNESS = 2-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## UNLIT

```TypeScript
UNLIT = 3
```

不受光照影响的材质。

**起始版本：** 23

<!--Device-MaterialType-UNLIT = 3--><!--Device-MaterialType-UNLIT = 3-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## OCCLUSION

```TypeScript
OCCLUSION = 4
```

遮挡材质，能够遮挡场景中的其他物体但不会遮挡环境。

**起始版本：** 23

<!--Device-MaterialType-OCCLUSION = 4--><!--Device-MaterialType-OCCLUSION = 4-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

