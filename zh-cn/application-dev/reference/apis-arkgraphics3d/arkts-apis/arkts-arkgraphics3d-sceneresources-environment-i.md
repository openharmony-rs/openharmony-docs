# Environment

环境类型，继承自SceneResource。@extends SceneResource @interface Environment

**继承/实现关系：** Environment extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## backgroundType

```TypeScript
backgroundType: EnvironmentBackgroundType
```

环境背景类型。

**类型：** [EnvironmentBackgroundType](arkts-arkgraphics3d-sceneresources-environmentbackgroundtype-e.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## environmentImage

```TypeScript
environmentImage?: Image | null
```

环境图片，默认为undefined。

**类型：** [Image](arkts-arkgraphics3d-sceneresources-image-i.md) \| null

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## environmentMapFactor

```TypeScript
environmentMapFactor: Vec4
```

环境地图系数。

**类型：** [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## environmentRotation

```TypeScript
environmentRotation?: Quaternion
```

环境光的旋转，默认为undefined，接收参数需为归一化后的四元数。

**类型：** [Quaternion](arkts-arkgraphics3d-scenetypes-quaternion-i.md)

**默认值：** undefined

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

## indirectDiffuseFactor

```TypeScript
indirectDiffuseFactor: Vec4
```

间接散射系数。

**类型：** [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## indirectSpecularFactor

```TypeScript
indirectSpecularFactor: Vec4
```

间接反射系数。

**类型：** [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## irradianceCoefficients

```TypeScript
irradianceCoefficients?: Vec3[]
```

辐射系数，默认为undefined。

**类型：** [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)[]

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## radianceImage

```TypeScript
radianceImage?: Image | null
```

辐射图片，默认为undefined。

**类型：** [Image](arkts-arkgraphics3d-sceneresources-image-i.md) \| null

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D
