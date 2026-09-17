# Environment

Environment resource, which inherits from SceneResource.

@extends SceneResource @interface Environment

**Inheritance/Implementation:** Environment extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## backgroundType

```TypeScript
backgroundType: EnvironmentBackgroundType
```

Environment background type.

**Type:** [EnvironmentBackgroundType](arkts-arkgraphics3d-sceneresources-environmentbackgroundtype-e.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## environmentImage

```TypeScript
environmentImage?: Image | null
```

Environment image. The default value is undefined.

**Type:** [Image](arkts-arkgraphics3d-sceneresources-image-i.md) &#124; null

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## environmentMapFactor

```TypeScript
environmentMapFactor: Vec4
```

Environment map factor.

**Type:** [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md)

**Since:** 12

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

**System capability:** SystemCapability.ArkUi.Graphics3D

## indirectDiffuseFactor

```TypeScript
indirectDiffuseFactor: Vec4
```

Indirect diffuse factor.

**Type:** [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## indirectSpecularFactor

```TypeScript
indirectSpecularFactor: Vec4
```

Indirect specular factor.

**Type:** [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## irradianceCoefficients

```TypeScript
irradianceCoefficients?: Vec3[]
```

Irradiance coefficients. The default value is undefined.

**Type:** [Vec3](arkts-arkgraphics3d-scenetypes-vec3-i.md)[]

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## radianceImage

```TypeScript
radianceImage?: Image | null
```

Radiance image. The default value is undefined.

**Type:** [Image](arkts-arkgraphics3d-sceneresources-image-i.md) &#124; null

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D
