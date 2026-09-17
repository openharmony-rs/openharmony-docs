# Mesh

Mesh resource, which inherits from SceneResource.

@extends SceneResource @interface Mesh

**Inheritance/Implementation:** Mesh extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## aabb

```TypeScript
readonly aabb: Aabb
```

Axis aligned bounding box.

**Type:** [Aabb](arkts-arkgraphics3d-scenetypes-aabb-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## materialOverride

```TypeScript
materialOverride?: Material
```

Material. The default value is undefined.

**Type:** [Material](arkts-arkgraphics3d-sceneresources-material-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## subMeshes

```TypeScript
readonly subMeshes: SubMesh[]
```

Array of sub-meshes.

**Type:** [SubMesh](arkts-arkgraphics3d-sceneresources-submesh-i.md)[]

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D
