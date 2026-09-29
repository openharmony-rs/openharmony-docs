# Mesh

```TypeScript
export interface Mesh extends SceneResource
```

Mesh resource, which inherits from SceneResource.

@extends SceneResource @interface Mesh

**Inheritance/Implementation:** Mesh extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**Since:** 12

<!--Device-unnamed-export interface Mesh extends SceneResource--><!--Device-unnamed-export interface Mesh extends SceneResource-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## aabb

```TypeScript
readonly aabb: Aabb
```

Axis aligned bounding box.

**Type:** [Aabb](arkts-arkgraphics3d-scenetypes-aabb-i.md)

**Since:** 12

<!--Device-Mesh-readonly aabb: Aabb--><!--Device-Mesh-readonly aabb: Aabb-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## materialOverride

```TypeScript
materialOverride?: Material
```

Material. The default value is undefined.

**Type:** [Material](arkts-arkgraphics3d-sceneresources-material-i.md)

**Since:** 12

<!--Device-Mesh-materialOverride?: Material--><!--Device-Mesh-materialOverride?: Material-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## subMeshes

```TypeScript
readonly subMeshes: SubMesh[]
```

Array of sub-meshes.

**Type:** [SubMesh](arkts-arkgraphics3d-sceneresources-submesh-i.md)[]

**Since:** 12

<!--Device-Mesh-readonly subMeshes: SubMesh[]--><!--Device-Mesh-readonly subMeshes: SubMesh[]-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D
