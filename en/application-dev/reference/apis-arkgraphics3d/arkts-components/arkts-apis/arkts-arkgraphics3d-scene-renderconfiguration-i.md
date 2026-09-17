# RenderConfiguration

Describes the rendering configuration.

@interface RenderConfiguration

**Since:** 23

**System capability:** SystemCapability.ArkUi.Graphics3D

## shadowResolution

```TypeScript
shadowResolution?: Vec2
```

Global shadow map resolution, in pixels (px). The default value is undefined, indicating that the shadow map resolution is set to 1024 * 1024. The value must be greater than 0 for the parameter to take effect. If the input value is a floating-point number, it will be truncated to an integer; if the input value is less than or equal to 0, the input will be ignored, and the original configuration will be retained.

**Type:** [Vec2](arkts-arkgraphics3d-scenetypes-vec2-i.md)

**Default:** undefined

**Since:** 23

**System capability:** SystemCapability.ArkUi.Graphics3D

## softShadowConfig

```TypeScript
softShadowConfig?: SoftShadowConfig
```

param config for soft shadow, control the algorithm type and its configuration.

**Type:** [SoftShadowConfig](arkts-arkgraphics3d-scene-softshadowconfig-c.md)

**Default:** undefined

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D
