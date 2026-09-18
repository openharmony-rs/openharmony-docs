# BloomSettings

Describes the settings for bloom effects. It is unavailable when RenderingPipelineType is set to FORWARD_LIGHTWEIGHT.

@typedef BloomSettings

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D

## scaleFactor

```TypeScript
scaleFactor?: number
```

Scale factor. The value must be greater than 0. The default value is 1.0.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D

## scatter

```TypeScript
scatter?: number
```

Scatter amount. The value must be greater than 0. The default value is 1.0.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D

## thresholdHard

```TypeScript
thresholdHard?: number
```

Hard threshold. The value is a non-negative number. The default value is 1.0.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D

## thresholdSoft

```TypeScript
thresholdSoft?: number
```

Soft threshold. The value is a non-negative number. The default value is 2.0.

**Type:** number

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D
