# Scene

Describes a scene.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## cloneNode

```TypeScript
cloneNode(node: Node, parent: Node, name: string): Node | null
```

Clones a node in the current scene. Cross-scene node cloning is not supported.

**Since:** 23

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | Yes | Node to be cloned. |
| parent | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | Yes | Target parent node of the cloned node in the current scene. The cloned node and the target parent node must belong to the same scene. |
| name | string | Yes | Name of the cloned node, which can be customized and has no special requirements. |

**Return value:**

| Type | Description |
| --- | --- |
| [Node](arkts-arkgraphics3d-scenenodes-node-i.md) &#124; null | Returns the cloned node. If the operation fails, null is returned. |

**Examples**

```TypeScript
import { Scene, Node } from '@kit.ArkGraphics3D';

function CloneNode() {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.gltf"))
    .then(async (result: Scene) => {
      let node = result.getNodeByPath("rootNode_/Unnamed Node 1/AnimatedCube") as Node;
      let parent = result.root as Node;
      let name = "cloneNode_";
      let clone = result.cloneNode(node, parent, name);
      if (clone) {
        console.info("Succeeded in cloning node");
      } else {
        console.error("Failed to clone node");
      }
    });
}
```

## createComponent

```TypeScript
createComponent(node: Node, name: string): Promise<SceneComponent>
```

Creates a component and attaches it to a node. This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | Yes | Node to which the component will be attached. |
| name | string | Yes | Name of the component to create, which is defined by individual plugins. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SceneComponent](arkts-arkgraphics3d-scene-scenecomponent-i.md)&gt; | Promise used to return the SceneComponent object created. |

**Examples**

```TypeScript
import { Scene, SceneComponent } from '@kit.ArkGraphics3D';

function createComponentTest(): Promise<SceneComponent> {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  return Scene.load($rawfile("gltf/DamagedHelmet/glTF/DamagedHelmet.glb"))
    .then(scene => {
      if (!scene) {
        return Promise.reject(new Error("Failed to load scene"));
      }
      // RenderConfigurationComponent is an internal component of the engine. You do not need to install plugins when creating the component.
      return scene.createComponent(scene.root, "RenderConfigurationComponent");
    })
    .then(component => {
      if (!component) {
        return Promise.reject(new Error("Failed to create component"));
      }
      return component;
    });
}
```

## destroy

```TypeScript
destroy(): void
```

Destroys this scene and releases all scene resources.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Examples**

```TypeScript
import { Scene } from '@kit.ArkGraphics3D';

function destroy(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
         // Destroy the scene.
        result.destroy();
    }
  });
}
```

## getComponent

```TypeScript
getComponent(node: Node, name: string): SceneComponent | null
```

Obtains the component instance from a node based on the component name.

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | Yes | Node to which the component is attached. |
| name | string | Yes | Name of the component to obtain. The value must be a system predefined or registered custom component name, and follow the naming conventions. |

**Return value:**

| Type | Description |
| --- | --- |
| [SceneComponent](arkts-arkgraphics3d-scene-scenecomponent-i.md) &#124; null | SceneComponent object corresponding to the given name, or null if not found. |

**Examples**

```TypeScript
import { Scene } from '@kit.ArkGraphics3D';

function getComponentTest() {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  Scene.load($rawfile("gltf/DamagedHelmet/glTF/DamagedHelmet.glb"))
    .then(async (result: Scene | undefined) => {
      if (!result) {
        console.error("Failed to load scene");
        return;
      }
      console.info("TEST getComponentTest");
      let component = result.getComponent(result.root, "myComponent");
      if (component) {
        console.info("Succeeded in getting component");
      } else {
        console.error("Failed to get component");
      }
    });
}
```

## getDefaultRenderContext

```TypeScript
static getDefaultRenderContext(): RenderContext | null
```

Obtains the rendering context associated with the current graphics object.

**Since:** 20

**System capability:** SystemCapability.ArkUi.Graphics3D

**Return value:**

| Type | Description |
| --- | --- |
| [RenderContext](arkts-arkgraphics3d-scene-rendercontext-i.md) &#124; null | Rendering context associated with the current object, or null if no rendering context is associated. @static |

**Examples**

```TypeScript
import { Scene, RenderContext } from '@kit.ArkGraphics3D';

function getDefaultRenderContextTest() {
  console.info("TEST getDefaultRenderContextTest");
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (renderContext) {
    console.info("Succeeded in getting default render context");
  } else {
    console.error("Failed to get default render context");
  }
}
```

## getNodeByPath

```TypeScript
getNodeByPath(path: string, type?: NodeType): Node | null
```

Obtains a node by path.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path in the scene node tree. Each layer is separated by a slash (/). |
| type | [NodeType](arkts-arkgraphics3d-scenenodes-nodetype-e.md) | No | Expected type of the node to be returned. The default value is null. |

**Return value:**

| Type | Description |
| --- | --- |
| [Node](arkts-arkgraphics3d-scenenodes-node-i.md) &#124; null | Returns the instance of the requested node. Returns null if not found or if the type of the found node does not match the passed parameter. |

**Examples**

```TypeScript
import { Scene, Node } from '@kit.ArkGraphics3D';

function getNode(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
         // Search for a node in the specified path.
        let node : Node | null = result.getNodeByPath("rootNode_");
    }
  });
}
```

## getResourceFactory

```TypeScript
getResourceFactory(): SceneResourceFactory
```

Obtains the scene resource factory.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Return value:**

| Type | Description |
| --- | --- |
| [SceneResourceFactory](arkts-arkgraphics3d-scene-sceneresourcefactory-i.md) | Scene resource factory. |

**Examples**

```TypeScript
import { SceneResourceFactory, Scene } from '@kit.ArkGraphics3D';

function getFactory(): void {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
         // Obtain a SceneResourceFactory object.
        let sceneFactory: SceneResourceFactory = result.getResourceFactory();
    }
  });
}
```

## importNode

```TypeScript
importNode(name: string, node: Node, parent: Node | null): Node
```

Generally used for importing nodes from other scenes.

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the imported node, which can be customized and has no special requirements. |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | Yes | Node to be imported. |
| parent | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) &#124; null | Yes | Parent node of the imported node in the new scene. |

**Return value:**

| Type | Description |
| --- | --- |
| [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | Node to be imported. |

**Examples**

```TypeScript
import { Scene } from '@kit.ArkGraphics3D';

function ImportNodeTest() {
  Scene.load().then(async (result: Scene | undefined) => {
    if (!result) {
      return;
    }
    // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
    Scene.load($rawfile("gltf/AnimatedCube/glTF/AnimatedCube.glb"))
      .then(async (extScene: Scene) => {
        let extNode = extScene.getNodeByPath("rootNode_/Unnamed Node 1/AnimatedCube");
        console.info("TEST ImportNodeTest");
        let node = result.importNode("scene", extNode, result.root);
        if (node) {
          node.position.x = 5;
        }
      });
  });
}
```

## importScene

```TypeScript
importScene(name: string, scene: Scene, parent: Node | null): Node
```

Imports another scene into the current one.

**Since:** 18

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the root node of the imported scene, which can be customized and has no special requirements. |
| scene | [Scene](arkts-arkgraphics3d-scene-c.md) | Yes | Scene to import. |
| parent | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) &#124; null | Yes | Parent node of the imported scene in the new scene. |

**Return value:**

| Type | Description |
| --- | --- |
| [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | Root node of the imported scene. |

**Examples**

```TypeScript
import { Scene } from '@kit.ArkGraphics3D';

function ImportSceneTest() {
  Scene.load().then(async (result: Scene | undefined) => {
    if (!result) {
      return;
    }
    // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
    let content = await result.getResourceFactory().createScene($rawfile("gltf/DamagedHelmet/glTF/DamagedHelmet.glb"));
    console.info("TEST ImportSceneTest");
    result.importScene("helmet", content, null);
  });
}
```

## load

```TypeScript
static load(uri? : ResourceStr): Promise<Scene>
```

Loads a resource by path. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | ResourceStr | No | Path of the model file resource to load. The default value is undefined. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Scene](arkts-arkgraphics3d-scene-c.md)&gt; | Promise used to return the Scene object created. @static |

**Examples**

```TypeScript
Example 1: Load resources via rawfile (a relative path).
```

```TypeScript
Example 2: Load via an absolute path (from /data/storage/el2/base/files in the application sandbox directory).
```

```TypeScript
import { Scene, SceneLoadParams } from '@kit.ArkGraphics3D';

function loadModelWithParams(): Promise<Scene> {
  let loadParams: SceneLoadParams = { offset: 0 };
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"), loadParams);
  return scene;
}
```

## renderFrame

```TypeScript
renderFrame(params?: RenderParameters): boolean
```

Renders frames on demand, such as controlling the frame rate.

**Since:** 15

**System capability:** SystemCapability.ArkUi.Graphics3D

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [RenderParameters](arkts-arkgraphics3d-scene-renderparameters-i.md) | No | Rendering parameters. The default value is undefined. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Rendering result. The value true is returned if rendering is successfully scheduled; returns false otherwise. |

**Examples**

```TypeScript
import { Scene } from '@kit.ArkGraphics3D';

function RenderFrameTest() {
  // Load scene resources, which supports .gltf and .glb formats. The path and file name can be customized based on the specific project resources.
  Scene.load($rawfile("gltf/DamagedHelmet/glTF/DamagedHelmet.glb"))
    .then(async (result: Scene | undefined) => {
      if (!result) {
        return;
      }
      console.info("TEST RenderFrameTest");
      result.renderFrame({ alwaysRender: true });
  });
}
```

## animations

```TypeScript
get animations(): Animation[]
```

Animation objects in the 3D scene.

**Type:** [Animation](arkts-arkgraphics3d-sceneresources-animation-i.md)[]

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## environment

```TypeScript
get environment(): Environment
```

Environment object.

**Type:** [Environment](arkts-arkgraphics3d-sceneresources-environment-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

```TypeScript
set environment(value: Environment)
```

Environment object.

**Type:** [Environment](arkts-arkgraphics3d-sceneresources-environment-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

## renderConfiguration

```TypeScript
get renderConfiguration(): RenderConfiguration
```

Rendering configuration.

**Type:** [RenderConfiguration](arkts-arkgraphics3d-scene-renderconfiguration-i.md)

**Since:** 23

**System capability:** SystemCapability.ArkUi.Graphics3D

## root

```TypeScript
get root(): Node | null
```

Root node of the 3D scene tree.

**Type:** [Node](arkts-arkgraphics3d-scenenodes-node-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D
