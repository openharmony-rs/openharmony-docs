# SamplerFilter

Enumerates the filtering modes of a sampler. The filtering mode determines the interpolation method used when sampling textures, controlling how final pixel colors are calculated during texture scaling or deformation.

@enum { int }

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## NEAREST

```TypeScript
NEAREST = 0
```

Uses nearest-neighbor interpolation, which is fast but can result in jagged edges.

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## LINEAR

```TypeScript
LINEAR = 1
```

Uses linear interpolation, providing a smoother appearance but with a slight performance cost.

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D
