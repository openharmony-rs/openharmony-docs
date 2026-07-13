# Node

定义Node接口.

**继承/实现关系：** Node extends [SceneResource](arkts-arkgraphics3d-sceneresource-i.md)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## getNodeByPath

```TypeScript
getNodeByPath(path: string): Node | null
```

通过路径获取节点.

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 要查询的节点路径 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Node | @syscap SystemCapability.ArkUi.Graphics3D |

## children

```TypeScript
readonly children: Container<Node>
```

节点的子节点.

**类型：** Container<Node>

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## layerMask

```TypeScript
readonly layerMask: LayerMask
```

节点图层掩码.

**类型：** LayerMask

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## nodeType

```TypeScript
readonly nodeType: NodeType
```

节点类型.

**类型：** NodeType

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## parent

```TypeScript
readonly parent: Node | null
```

节点的父节点.

**类型：** Node | null

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## path

```TypeScript
readonly path: string
```

节点路径.

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## position

```TypeScript
position: Position3
```

节点位置, 单位为世界坐标系下的场景单位（例如cm、m、km等）.

**类型：** Position3

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## rotation

```TypeScript
rotation: Quaternion
```

节点旋转.

**类型：** Quaternion

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## scale

```TypeScript
scale: Scale3
```

节点缩放.

**类型：** Scale3

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## visible

```TypeScript
visible: boolean
```

节点可见性标志.

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

