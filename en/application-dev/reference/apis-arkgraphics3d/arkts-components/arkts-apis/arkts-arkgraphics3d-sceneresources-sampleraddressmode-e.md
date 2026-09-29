# SamplerAddressMode

```TypeScript
export enum SamplerAddressMode
```

Enumerates the sampler addressing modes, which are used to control how texture coordinates are handled when they go beyond the [0, 1] range.

@enum { int }

**Since:** 20

<!--Device-unnamed-export enum SamplerAddressMode--><!--Device-unnamed-export enum SamplerAddressMode-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## REPEAT

```TypeScript
REPEAT = 0
```

The texture repeats when the coordinates exceed the range.

**Since:** 20

<!--Device-SamplerAddressMode-REPEAT = 0--><!--Device-SamplerAddressMode-REPEAT = 0-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## MIRRORED_REPEAT

```TypeScript
MIRRORED_REPEAT = 1
```

The texture mirrors and repeats when the coordinates exceed the range.

**Since:** 20

<!--Device-SamplerAddressMode-MIRRORED_REPEAT = 1--><!--Device-SamplerAddressMode-MIRRORED_REPEAT = 1-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## CLAMP_TO_EDGE

```TypeScript
CLAMP_TO_EDGE = 2
```

The edge pixels of the texture are stretched when the coordinates exceed the range.

**Since:** 20

<!--Device-SamplerAddressMode-CLAMP_TO_EDGE = 2--><!--Device-SamplerAddressMode-CLAMP_TO_EDGE = 2-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D
