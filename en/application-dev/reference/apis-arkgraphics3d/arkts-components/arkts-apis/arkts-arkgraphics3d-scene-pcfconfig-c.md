# PCFConfig

Configuration class for soft shadows using the Percentage-Closer Filtering (PCF) algorithm.

**Inheritance/Implementation:** PCFConfig extends [SoftShadowConfig](arkts-arkgraphics3d-scene-softshadowconfig-c.md)

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUi.Graphics3D

## shadowSampleCount

```TypeScript
get shadowSampleCount(): number | undefined
```

Get the sample count number from shadow map used to render a shadow pixel. The value must be a positive integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

```TypeScript
set shadowSampleCount(value: number | undefined)
```

Set the sample count number from shadow map used to render a shadow pixel. Values outside the range are ignored and the previous value is retained.

**Type:** number

**Default:** 16

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

## shadowSampleRadius

```TypeScript
get shadowSampleRadius(): number | undefined
```

Get sample radius around the shadow edge, the unit is pixel.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

```TypeScript
set shadowSampleRadius(value: number | undefined)
```

Set sample radius around the shadow edge at pixel-level.

**Type:** number

**Default:** 5.0

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D
