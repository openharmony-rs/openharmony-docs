# Morpher

Defines the deformation of 3D models by adjusting the weights of different deformation targets to create dynamic effects.

@interface Morpher

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## targets

```TypeScript
readonly targets: Record<string, number>
```

Used to store the names and weights of deformation targets. The weight value is usually within the range of [0.0, 1.0].

**Type:** Record&lt;string, number&gt;

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D
