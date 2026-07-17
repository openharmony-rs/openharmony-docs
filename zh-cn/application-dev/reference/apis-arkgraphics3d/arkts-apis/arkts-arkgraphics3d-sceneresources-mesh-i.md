# Mesh

网格节点拥有的网格实例

**继承/实现关系：** Mesh extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**起始版本：** 12

<!--Device-unnamed-export interface Mesh extends SceneResource--><!--Device-unnamed-export interface Mesh extends SceneResource-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## aabb

```TypeScript
readonly aabb: Aabb
```

网格的轴对齐包围盒.

**类型：** Aabb

**起始版本：** 12

<!--Device-Mesh-readonly aabb: Aabb--><!--Device-Mesh-readonly aabb: Aabb-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## materialOverride

```TypeScript
materialOverride?: Material
```

覆盖子网格材质的材质.

**类型：** Material

**起始版本：** 12

<!--Device-Mesh-materialOverride?: Material--><!--Device-Mesh-materialOverride?: Material-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## subMeshes

```TypeScript
readonly subMeshes: SubMesh[]
```

网格的子网格.

**类型：** SubMesh[]

**起始版本：** 12

<!--Device-Mesh-readonly subMeshes: SubMesh[]--><!--Device-Mesh-readonly subMeshes: SubMesh[]-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

