# Geometry

几何节点类型，用于承载可渲染的网格数据，并支持可选的形变功能，继承自Node。

**继承/实现关系：** Geometry extends [Node](arkts-arkgraphics3d-scenenodes-node-i.md)

**起始版本：** 23

<!--Device-unnamed-export interface Geometry--><!--Device-unnamed-export interface Geometry-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## mesh

```TypeScript
readonly mesh: Mesh
```

网格属性。

**类型：** [Mesh](arkts-arkgraphics3d-sceneresources-mesh-i.md)

**起始版本：** 23

<!--Device-Geometry-readonly mesh: Mesh--><!--Device-Geometry-readonly mesh: Mesh-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## morpher

```TypeScript
readonly morpher?: Morpher
```

可选的形变器，用于为几何体添加基于顶点的形变或动画效果。若未设置，则该几何体不支持形变功能。

**类型：** [Morpher](arkts-arkgraphics3d-sceneresources-morpher-i.md)

**起始版本：** 23

<!--Device-Geometry-readonly morpher?: Morpher--><!--Device-Geometry-readonly morpher?: Morpher-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

