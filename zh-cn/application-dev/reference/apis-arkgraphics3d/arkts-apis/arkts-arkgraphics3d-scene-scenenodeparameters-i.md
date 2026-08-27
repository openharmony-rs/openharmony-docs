# SceneNodeParameters

场景节点参数对象，用于提供场景节点层次中的名称和路径。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## name

```TypeScript
name: string
```

要创建的节点名称，可由开发者自定义填写，用于标识场景节点。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## path

```TypeScript
path?: string
```

场景节点层次中的路径。用于指定创建的相机、灯光或节点在场景节点层次中的放置位置。 每层之间使用'/'符号进行分割。如果未提供，则将其设置为根节点的子节点。默认值为undefined。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

**示例**

```TypeScript
import { SceneNodeParameters, SceneResourceFactory, Scene, Node } from '@kit.ArkGraphics3D';

function createNodePromise() : Promise<Node> {
  return new Promise((resolve, reject) => {
    // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
    let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
    scene.then(async (result: Scene) => {
      let sceneFactory: SceneResourceFactory = result.getResourceFactory();

      // 创建SceneNodeParameters类型变量并以此创建node
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
