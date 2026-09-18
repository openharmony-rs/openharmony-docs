# MaterialProperty

Defines the textures, property factors, and texture samplers used by a material.

@interface MaterialProperty

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## factor

```TypeScript
factor: Vec4
```

PBR property factor, with different meanings for different properties.

**Type:** [Vec4](arkts-arkgraphics3d-scenetypes-vec4-i.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## image

```TypeScript
image: Image | null
```

Texture map based on PBR properties to convey the texture information of the material.

**Type:** [Image](arkts-arkgraphics3d-sceneresources-image-i.md) &#124; null

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## sampler

```TypeScript
sampler?: Sampler
```

Texture sampler, with the default value set to LINEAR for magnification, minification, and mipmaps, and to REPEAT for U, V, and W directions.

**Type:** [Sampler](arkts-arkgraphics3d-sceneresources-sampler-i.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D
