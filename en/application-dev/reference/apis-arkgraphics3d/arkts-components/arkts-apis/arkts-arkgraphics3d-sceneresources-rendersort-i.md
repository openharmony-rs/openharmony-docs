# RenderSort

Describes the order in which materials are rendered, controlling the sequence of drawing in the rendering pipeline.

@interface RenderSort

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## renderSortLayer

```TypeScript
renderSortLayer?: number
```

Rendering layer ID. A smaller value indicates an earlier rendering order. The value range is [0, 63]. The default layer ID is 32.

**Type:** number

**Default:** 32

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

## renderSortLayerOrder

```TypeScript
renderSortLayerOrder?: number
```

Rendering order of different objects within the same rendering layer. A smaller value indicates an earlier rendering order. The value range is [0, 255]. The default value is 0.

**Type:** number

**Default:** 0

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D
