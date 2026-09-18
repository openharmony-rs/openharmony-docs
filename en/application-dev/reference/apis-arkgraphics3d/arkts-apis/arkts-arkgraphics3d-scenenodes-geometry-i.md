# Geometry

Geometric node type that holds renderable mesh data and supports optional deformation features. It inherits from Node.

@extends Node @interface Geometry

**Inheritance/Implementation:** Geometry extends [Node](arkts-arkgraphics3d-scenenodes-node-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## mesh

```TypeScript
readonly mesh: Mesh
```

Mesh property.

**Type:** [Mesh](arkts-arkgraphics3d-sceneresources-mesh-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## morpher

```TypeScript
readonly morpher?: Morpher
```

Optional morpher that adds vertex-based deformation or animation effects to the geometry. If this parameter is not specified, the geometry does not support deformation.

**Type:** [Morpher](arkts-arkgraphics3d-sceneresources-morpher-i.md)

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D
