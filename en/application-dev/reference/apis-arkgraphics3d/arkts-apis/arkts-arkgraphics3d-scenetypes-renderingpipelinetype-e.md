# RenderingPipelineType

Enumerates the rendering pipeline types.

@enum { int }

**Since:** 21

**System capability:** SystemCapability.ArkUi.Graphics3D

## FORWARD_LIGHTWEIGHT

```TypeScript
FORWARD_LIGHTWEIGHT = 0
```

Lightweight forward rendering pipeline that directly renders to the back buffer. It supports per-pixel effects (for example, tone mapping), but not complex effects (for example, bloom), in shaders.

**Since:** 21

**System capability:** SystemCapability.ArkUi.Graphics3D

## FORWARD

```TypeScript
FORWARD = 1
```

High-quality forward rendering pipeline designed for complex visual effects (for example, bloom).

**Since:** 21

**System capability:** SystemCapability.ArkUi.Graphics3D
