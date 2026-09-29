# Environment

```TypeScript
export interface Environment extends SceneResource
```

Environment resource, which inherits from SceneResource.

@extends SceneResource @interface Environment

**Inheritance/Implementation:** Environment extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**Since:** 12

<!--Device-unnamed-export interface Environment extends SceneResource--><!--Device-unnamed-export interface Environment extends SceneResource-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## backgroundType

```TypeScript
backgroundType: EnvironmentBackgroundType
```

Environment background type.

**Type:** [EnvironmentBackgroundType](arkts-arkgraphics3d-sceneresources-environmentbackgroundtype-e.md)

**Since:** 12

<!--Device-Environment-backgroundType: EnvironmentBackgroundType--><!--Device-Environment-backgroundType: EnvironmentBackgroundType-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## environmentImage

```TypeScript
environmentImage?: Image | null
```

Environment image. The default value is undefined.

**Type:** [Image](arkts-arkgraphics3d-sceneresources-image-i.md) &#124; null

**Since:** 12

<!--Device-Environment-environmentImage?: Image | null--><!--Device-Environment-environmentImage?: Image | null-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## environmentMapFactor

```TypeScript
environmentMapFactor: Vec4
```

Environment map factor.

**Type:** [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md)

**Since:** 12

<!--Device-Environment-environmentMapFactor: Vec4--><!--Device-Environment-environmentMapFactor: Vec4-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## environmentRotation

```TypeScript
environmentRotation?: Quaternion
```

Rotation of the ambient light. The default value is undefined. The parameter must be a normalized quaternion.

**Type:** [Quaternion](arkts-arkgraphics3d-scenetypes-quaternion-i.md)

**Default:** undefined

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-Environment-environmentRotation?: Quaternion--><!--Device-Environment-environmentRotation?: Quaternion-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## indirectDiffuseFactor

```TypeScript
indirectDiffuseFactor: Vec4
```

Indirect diffuse factor.

**Type:** [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md)

**Since:** 12

<!--Device-Environment-indirectDiffuseFactor: Vec4--><!--Device-Environment-indirectDiffuseFactor: Vec4-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## indirectSpecularFactor

```TypeScript
indirectSpecularFactor: Vec4
```

Indirect specular factor.

**Type:** [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md)

**Since:** 12

<!--Device-Environment-indirectSpecularFactor: Vec4--><!--Device-Environment-indirectSpecularFactor: Vec4-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## irradianceCoefficients

```TypeScript
irradianceCoefficients?: Vec3[]
```

Irradiance coefficients. The default value is undefined.

**Type:** [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)[]

**Since:** 12

<!--Device-Environment-irradianceCoefficients?: Vec3[]--><!--Device-Environment-irradianceCoefficients?: Vec3[]-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## radianceImage

```TypeScript
radianceImage?: Image | null
```

Radiance image. The default value is undefined.

**Type:** [Image](arkts-arkgraphics3d-sceneresources-image-i.md) &#124; null

**Since:** 12

<!--Device-Environment-radianceImage?: Image | null--><!--Device-Environment-radianceImage?: Image | null-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D
