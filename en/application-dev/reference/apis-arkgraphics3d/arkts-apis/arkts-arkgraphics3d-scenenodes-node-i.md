# Node

```TypeScript
export interface Node extends SceneResource
```

The 3D scene consists of nodes in a tree hierarchy, where each node implements a Node interface. This class inherits from SceneResource.

@extends SceneResource @interface Node

**Inheritance/Implementation:** Node extends [SceneResource](arkts-arkgraphics3d-sceneresources-sceneresource-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## getNodeByPath

```TypeScript
getNodeByPath(path: string): Node | null
```

Obtains a node by path. If no node is obtained, null is returned.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path in the scene node tree. Each layer is separated by a slash (/). |

**Return value:**

| Type | Description |
| --- | --- |
| [Node](arkts-arkgraphics3d-scenenodes-node-i.md) &#124; null | Returns the node object. |

**Examples**

```TypeScript
import { Scene, Node } from '@kit.ArkGraphics3D';

function getNode(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result && result.root) {
      // Search for a node.
      let geo : Node | null = result.root.getNodeByPath("scene/node");
    }
  });
}
```

When calling getNodeByPath, you need to pass in the node path parameter path. You can obtain the available path value by traversing the node tree and printing the attributes of each node. The following is an example:

```TypeScript
import { Scene, Node } from '@kit.ArkGraphics3D';

// Print the tree structure of the given node, with each line representing the path of a node.
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

Child node of the node and null if it does not exist. This is a read-only property, indicating that you cannot directly replace the entire children container. However, you can operate the child nodes using container methods like append, insertAfter, remove, or clear. If the node being appended or inserted already exists in the container, it is removed first and then reinserted. As a result, the total number of child nodes remains unchanged, making the operation seem ineffective. The count increases only when a new node is added.

**Type:** [Container](arkts-arkgraphics3d-scenenodes-container-i.md)&lt;[Node](arkts-arkgraphics3d-scenenodes-node-i.md)&gt;

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## layerMask

```TypeScript
readonly layerMask: LayerMask
```

Layer mask of a node.

**Type:** [LayerMask](arkts-arkgraphics3d-scenenodes-layermask-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## nodeType

```TypeScript
readonly nodeType: NodeType
```

Node type.

**Type:** [NodeType](arkts-arkgraphics3d-scenenodes-nodetype-e.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## parent

```TypeScript
readonly parent: Node | null
```

Parent node of the node and null if it does not exist.

**Type:** [Node](arkts-arkgraphics3d-scenenodes-node-i.md) &#124; null

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## path

```TypeScript
readonly path: string
```

Node path.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## position

```TypeScript
position: Position3
```

Node position, in scene units of the world coordinate system (for example, cm, m, or km).

**Type:** [Position3](arkts-arkgraphics3d-position3-t.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## rotation

```TypeScript
rotation: Quaternion
```

Rotation angle of a node.

**Type:** [Quaternion](arkts-arkgraphics3d-scenetypes-quaternion-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## scale

```TypeScript
scale: Scale3
```

Node scale.

**Type:** [Scale3](arkts-arkgraphics3d-scale3-t.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## visible

```TypeScript
visible: boolean
```

Whether a node is visible. true if visible, false otherwise.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D
