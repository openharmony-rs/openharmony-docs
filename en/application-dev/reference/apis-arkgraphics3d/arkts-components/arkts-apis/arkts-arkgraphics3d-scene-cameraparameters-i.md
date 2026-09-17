# CameraParameters

Describes the camera parameters, which are used to define additional configuration options for camera initialization.

@interface CameraParameters

**Since:** 21

**System capability:** SystemCapability.ArkUi.Graphics3D

## msaa

```TypeScript
msaa?: boolean
```

Whether Multisample Anti-Aliasing (MSAA) is enabled for the camera. true if enabled, false otherwise. The default value is false.

**Type:** boolean

**Default:** false

**Since:** 22

**System capability:** SystemCapability.ArkUi.Graphics3D

## renderingPipeline

```TypeScript
renderingPipeline?: RenderingPipelineType
```

Initial rendering pipeline type. The default value is FORWARD_LIGHTWEIGHT.

**Type:** [RenderingPipelineType](arkts-arkgraphics3d-scenetypes-renderingpipelinetype-e.md)

**Default:** RenderingPipelineType.FORWARD_LIGHTWEIGHT

**Since:** 21

**System capability:** SystemCapability.ArkUi.Graphics3D
