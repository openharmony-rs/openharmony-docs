# Node

3D场景由树状层次结构的节点组成，其中每个节点都实现了Node接口。继承自SceneResource。

**继承/实现关系：** Node extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**起始版本：** 23

<!--Device-unnamed-export interface Node--><!--Device-unnamed-export interface Node-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## getNodeByPath

```TypeScript
getNodeByPath(path: string): Node | null
```

根据路径获取节点，如果获取不到则返回空。

**起始版本：** 23

<!--Device-Node-getNodeByPath(path: string): Node | null--><!--Device-Node-getNodeByPath(path: string): Node | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 场景节点层次中的路径。每层之间使用'/'符号进行分割。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 返回节点对象。 |

**示例**

```TypeScript
import { Scene, Node } from '@kit.ArkGraphics3D';

function getNode(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.root) {
      // 查找节点
      let geo : Node | null = result.root.getNodeByPath("scene/node");
    }
  });
}
```

调用getNodeByPath时需传入节点路径参数path。可通过遍历节点树并打印各节点的属性获取可用的path值，示例如下：

```TypeScript
import { Scene, Node } from '@kit.ArkGraphics3D';

// 打印给定节点的树状结构，每行表示一个节点的路径。
function printNodeTreeInRelativePath(node: Node | null): void {
  if (!node) {
    return;
  }
  let basePath: string = node.path + node.name + '/';
  let printRelative = (n: Node | null): void => {
    if (!n) {
      return;
    }
    console.info(n.path.substring(basePath.length + 1) + n.name);
    for (let i = 0; i < n.children.count(); i++) {
      printRelative(n.children.get(i));
    }
  }
  for (let i = 0; i < node.children.count(); i++) {
    printRelative(node.children.get(i));
  }
}
```

## children

```TypeScript
readonly children: Container<Node>
```

节点的子节点，不存在则为空值。 为只读属性，表示不能替换整个children容器，但可以通过容器方法操作子节点（如append、insertAfter、remove或clear）。 如果append或insertAfter的节点已存在于容器中，容器会先移除该节点再插入，因此数量不会增加，看似“无效”；添加新节点才会真正增加子节点数量。

**类型：** [Container](arkts-arkgraphics3d-scenenodes-container-i.md)&lt;[Node](arkts-arkgraphics3d-scenenodes-node-i.md)&gt;

**起始版本：** 23

<!--Device-Node-readonly children: Container<Node>--><!--Device-Node-readonly children: Container<Node>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## layerMask

```TypeScript
readonly layerMask: LayerMask
```

节点的图层掩码。

**类型：** [LayerMask](arkts-arkgraphics3d-scenenodes-layermask-i.md)

**起始版本：** 23

<!--Device-Node-readonly layerMask: LayerMask--><!--Device-Node-readonly layerMask: LayerMask-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## nodeType

```TypeScript
readonly nodeType: NodeType
```

节点类型。

**类型：** [NodeType](arkts-arkgraphics3d-scenenodes-nodetype-e.md)

**起始版本：** 23

<!--Device-Node-readonly nodeType: NodeType--><!--Device-Node-readonly nodeType: NodeType-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## parent

```TypeScript
readonly parent: Node | null
```

节点的父节点，不存在则为空值。

**类型：** [Node](arkts-arkgraphics3d-scenenodes-node-i.md) \| null

**起始版本：** 23

<!--Device-Node-readonly parent: Node | null--><!--Device-Node-readonly parent: Node | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## path

```TypeScript
readonly path: string
```

节点路径。

**类型：** string

**起始版本：** 23

<!--Device-Node-readonly path: string--><!--Device-Node-readonly path: string-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## position

```TypeScript
position: Position3
```

节点位置，单位为世界坐标系下的场景单位（比如cm、m、km等）。

**类型：** [Position3](arkts-arkgraphics3d-position3-t.md)

**起始版本：** 23

<!--Device-Node-position: Position3--><!--Device-Node-position: Position3-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## rotation

```TypeScript
rotation: Quaternion
```

节点旋转角度。

**类型：** [Quaternion](arkts-arkgraphics3d-scenetypes-quaternion-i.md)

**起始版本：** 23

<!--Device-Node-rotation: Quaternion--><!--Device-Node-rotation: Quaternion-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## scale

```TypeScript
scale: Scale3
```

节点缩放。

**类型：** [Scale3](arkts-arkgraphics3d-scale3-t.md)

**起始版本：** 23

<!--Device-Node-scale: Scale3--><!--Device-Node-scale: Scale3-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## visible

```TypeScript
visible: boolean
```

节点是否可见。true表示该节点可见，false表示不可见。

**类型：** boolean

**起始版本：** 23

<!--Device-Node-visible: boolean--><!--Device-Node-visible: boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

