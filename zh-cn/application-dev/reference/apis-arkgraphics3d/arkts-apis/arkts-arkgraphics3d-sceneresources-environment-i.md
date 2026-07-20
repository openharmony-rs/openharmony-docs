# Environment

环境资源.

**继承/实现关系：** Environment extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**起始版本：** 12

<!--Device-unnamed-export interface Environment extends SceneResource--><!--Device-unnamed-export interface Environment extends SceneResource-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## backgroundType

```TypeScript
backgroundType: EnvironmentBackgroundType
```

环境背景类型.

**类型：** EnvironmentBackgroundType

**起始版本：** 12

<!--Device-Environment-backgroundType: EnvironmentBackgroundType--><!--Device-Environment-backgroundType: EnvironmentBackgroundType-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## environmentImage

```TypeScript
environmentImage?: Image | null
```

环境图像.

**类型：** Image \| null

**起始版本：** 12

<!--Device-Environment-environmentImage?: Image | null--><!--Device-Environment-environmentImage?: Image | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## environmentMapFactor

```TypeScript
environmentMapFactor: Vec4
```

环境贴图因子.

**类型：** Vec4

**起始版本：** 12

<!--Device-Environment-environmentMapFactor: Vec4--><!--Device-Environment-environmentMapFactor: Vec4-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## environmentRotation

```TypeScript
environmentRotation?: Quaternion
```

环境旋转

**类型：** Quaternion

**默认值：** Quaternion {x:0, y:0, z:0, w:1} 单位四元数（无旋转）

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Environment-environmentRotation?: Quaternion--><!--Device-Environment-environmentRotation?: Quaternion-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## indirectDiffuseFactor

```TypeScript
indirectDiffuseFactor: Vec4
```

环境间接漫反射因子.

**类型：** Vec4

**起始版本：** 12

<!--Device-Environment-indirectDiffuseFactor: Vec4--><!--Device-Environment-indirectDiffuseFactor: Vec4-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## indirectSpecularFactor

```TypeScript
indirectSpecularFactor: Vec4
```

环境间接镜面反射因子.

**类型：** Vec4

**起始版本：** 12

<!--Device-Environment-indirectSpecularFactor: Vec4--><!--Device-Environment-indirectSpecularFactor: Vec4-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## irradianceCoefficients

```TypeScript
irradianceCoefficients?: Vec3[]
```

辐射系数（九个Vec3的数组）.

**类型：** Vec3[]

**起始版本：** 12

<!--Device-Environment-irradianceCoefficients?: Vec3[]--><!--Device-Environment-irradianceCoefficients?: Vec3[]-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## radianceImage

```TypeScript
radianceImage?: Image | null
```

环境辐射图像.

**类型：** Image \| null

**起始版本：** 12

<!--Device-Environment-radianceImage?: Image | null--><!--Device-Environment-radianceImage?: Image | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

