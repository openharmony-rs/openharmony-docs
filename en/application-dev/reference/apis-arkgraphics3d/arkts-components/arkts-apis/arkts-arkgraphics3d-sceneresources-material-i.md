# Material

```TypeScript
export interface Material extends SceneResource
```

Material resource, which inherits from SceneResource.

@extends SceneResource @interface Material

**Inheritance/Implementation:** Material extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**Since:** 12

<!--Device-unnamed-export interface Material extends SceneResource--><!--Device-unnamed-export interface Material extends SceneResource-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## alphaCutoff

```TypeScript
alphaCutoff?: number
```

Threshold of the alpha channel. If the alpha of a pixel is greater than or equal to this threshold, the pixel is rendered; otherwise, the pixel is not rendered. Setting a value less than 1 enables this mode. The value range is [0, 1]. The default value is 1.

**Type:** number

**Since:** 20

<!--Device-Material-alphaCutoff?: double--><!--Device-Material-alphaCutoff?: double-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## blend

```TypeScript
blend?: Blend
```

Whether the material is transparent. The default value is false.

**Type:** [Blend](arkts-arkgraphics3d-sceneresources-blend-i.md)

**Default:** undefined

**Since:** 20

<!--Device-Material-blend?: Blend--><!--Device-Material-blend?: Blend-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## cullMode

```TypeScript
cullMode?: CullMode
```

Culling mode of the material, which can be used to determine whether to cull front or back faces. The default value is BACK.

**Type:** [CullMode](arkts-arkgraphics3d-sceneresources-cullmode-e.md)

**Since:** 20

<!--Device-Material-cullMode?: CullMode--><!--Device-Material-cullMode?: CullMode-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## materialType

```TypeScript
readonly materialType: MaterialType
```

Material type.

**Type:** [MaterialType](arkts-arkgraphics3d-sceneresources-materialtype-e.md)

**Since:** 12

<!--Device-Material-readonly materialType: MaterialType--><!--Device-Material-readonly materialType: MaterialType-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## polygonMode

```TypeScript
polygonMode?: PolygonMode
```

Polygon drawing mode of the model. The default value is FILL.

**Type:** [PolygonMode](arkts-arkgraphics3d-sceneresources-polygonmode-e.md)

**Default:** PolygonMode.FILL

**Since:** 23

<!--Device-Material-polygonMode?: PolygonMode--><!--Device-Material-polygonMode?: PolygonMode-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## renderSort

```TypeScript
renderSort?: RenderSort
```

Rendering order, which determines the rendering sequence of materials in the rendering pipeline. The default layer ID is 32, and the default order within the layer is 0.

**Type:** [RenderSort](arkts-arkgraphics3d-sceneresources-rendersort-i.md)

**Since:** 20

<!--Device-Material-renderSort?: RenderSort--><!--Device-Material-renderSort?: RenderSort-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## shadowReceiver

```TypeScript
shadowReceiver?: boolean
```

Whether the material receives shadows. true if the material receives shadows, false otherwise. The default is false.

**Type:** boolean

**Since:** 20

<!--Device-Material-shadowReceiver?: boolean--><!--Device-Material-shadowReceiver?: boolean-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D
