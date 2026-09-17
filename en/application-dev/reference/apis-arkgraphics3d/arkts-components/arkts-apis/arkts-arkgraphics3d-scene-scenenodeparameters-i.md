# SceneNodeParameters

Describes the scene node parameters, which are used to provide the name and path in the scene node tree.

@typedef SceneNodeParameters

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## name

```TypeScript
name: string
```

Name of the scene node. It is customizable.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## path

```TypeScript
path?: string
```

Path in the scene node tree. It specifies the position of the created camera, light, or node in the scene node tree. Each layer is separated by a slash (/). If not provided, it is set as a child node of the root node. The default value is undefined.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Examples**

```TypeScript
import { SceneNodeParameters, SceneResourceFactory, Scene, Node } from '@kit.ArkGraphics3D';

function createNodePromise() : Promise<Node> {
  return new Promise((resolve, reject) => {
    // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
    let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
    scene.then(async (result: Scene) => {
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();

      // Create a variable of the SceneNodeParameters type and use it to create a node.
      let sceneNodeParameter: SceneNodeParameters = { name: "empty_node",
        path:"/rootNode_/empty_node" };
      let node: Node = await sceneFactory.createNode(sceneNodeParameter);
      resolve(node);
    }).catch((err: Error) => {
      console.error(`Failed to load scene. Message: ${err.message}`);
      reject(err);
    });
  });
}
```
