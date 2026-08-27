# RaycastResult

射线检测命中结果对象，包含被射线击中的3D物体详细信息。

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## centerDistance

```TypeScript
centerDistance: number
```

命中物体包围盒中心到相机中心的距离，单位为世界坐标系下的场景单位（比如cm、m、km等），取值范围大于0。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## hitPosition

```TypeScript
hitPosition: Position3
```

射线与物体碰撞点的精确世界坐标（{x: number, y: number, z: number}），单位为世界坐标系下的场景单位（比如cm、m、km等）。

**类型：** [Position3](arkts-arkgraphics3d-position3-t.md)

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## node

```TypeScript
node: Node
```

被射线击中的3D场景节点，可通过该节点操作目标物体（如移动、旋转、隐藏）。

**类型：** [Node](arkts-arkgraphics3d-scenenodes-node-i.md)

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D
