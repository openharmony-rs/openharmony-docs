# Sampler

Describes the sampling modes used during texture sampling.

@interface { Sampler }

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## addressModeU

```TypeScript
addressModeU?: SamplerAddressMode
```

Sampling mode of the texture in the U (horizontal) direction. The default value is REPEAT.

**Type:** [SamplerAddressMode](arkts-arkgraphics3d-sceneresources-sampleraddressmode-e.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## addressModeV

```TypeScript
addressModeV?: SamplerAddressMode
```

Sampling mode of the texture in the V (vertical) direction. The default value is REPEAT.

**Type:** [SamplerAddressMode](arkts-arkgraphics3d-sceneresources-sampleraddressmode-e.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## magFilter

```TypeScript
magFilter?: SamplerFilter
```

Sampling mode when the texture is enlarged. The default value is LINEAR.

**Type:** [SamplerFilter](arkts-arkgraphics3d-sceneresources-samplerfilter-e.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## minFilter

```TypeScript
minFilter?: SamplerFilter
```

Sampling mode when the texture is reduced. The default value is LINEAR.

**Type:** [SamplerFilter](arkts-arkgraphics3d-sceneresources-samplerfilter-e.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## mipMapMode

```TypeScript
mipMapMode?: SamplerFilter
```

Sampling modes between different texture resolutions. The default value is LINEAR.

**Type:** [SamplerFilter](arkts-arkgraphics3d-sceneresources-samplerfilter-e.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D
