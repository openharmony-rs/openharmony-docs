# Scene

用于设置场景。Scene采用树状层次结构组织场景节点，根节点（root）作为场景的入口。

**起始版本：** 23

<!--Device-unnamed-export declare class Scene--><!--Device-unnamed-export declare class Scene-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## cloneNode

```TypeScript
cloneNode(node: Node, parent: Node, name: string): Node | null
```

在当前所在场景中克隆节点，不支持跨场景克隆节点。

**起始版本：** 23

<!--Device-Scene-cloneNode(node: Node, parent: Node, name: string): Node | null--><!--Device-Scene-cloneNode(node: Node, parent: Node, name: string): Node | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 被克隆的节点。 |
| parent | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 被克隆的节点在当前所在场景中的目标父节点。被克隆的节点node和目标父节点parent需要属于同一个场景scene。 |
| name | string | 是 | 克隆节点的名称，由开发者自定义，无特殊要求。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 返回克隆节点。克隆失败则返回null。 |

**示例**

```TypeScript
import { Scene, Node } from '@kit.ArkGraphics3D';

function CloneNode() {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
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

在指定节点上创建新的组件，根据组件名称异步创建并附加到节点上，使用Promise异步回调。

**起始版本：** 23

<!--Device-Scene-createComponent(node: Node, name: string): Promise<SceneComponent>--><!--Device-Scene-createComponent(node: Node, name: string): Promise<SceneComponent>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 组件需要附加到的节点。 |
| name | string | 是 | 要创建的组件名称，由各插件定义有效名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[SceneComponent](arkts-arkgraphics3d-scene-scenecomponent-i.md)&gt; | Promise对象，返回新创建的场景组件。 |

**示例**

```TypeScript
import { Scene, SceneComponent } from '@kit.ArkGraphics3D';

function createComponentTest(): Promise<SceneComponent> {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  return Scene.load($rawfile("gltf/DamagedHelmet/glTF/DamagedHelmet.glb"))
    .then(scene => {
      if (!scene) {
        return Promise.reject(new Error("Failed to load scene"));
      }
      // RenderConfigurationComponent为引擎内置组件，创建时无需依赖插件
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

销毁场景，释放所有的场景资源。

**起始版本：** 23

<!--Device-Scene-destroy(): void--><!--Device-Scene-destroy(): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**示例**

```TypeScript
import { Scene } from '@kit.ArkGraphics3D';

function destroy(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
         // 销毁scene
        result.destroy();
    }
  });
}
```

## getComponent

```TypeScript
getComponent(node: Node, name: string): SceneComponent | null
```

根据指定的组件名称，从给定节点上获取对应的组件实例。

**起始版本：** 23

<!--Device-Scene-getComponent(node: Node, name: string): SceneComponent | null--><!--Device-Scene-getComponent(node: Node, name: string): SceneComponent | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 组件附加的节点。 |
| name | string | 是 | 需要获取的组件名称，必须为系统预定义或已注册的自定义组件名称，且需符合命名规范。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SceneComponent](arkts-arkgraphics3d-scene-scenecomponent-i.md) | 返回对应名称的组件对象，若未找到则返回null。 |

**示例**

```TypeScript
import { Scene } from '@kit.ArkGraphics3D';

function getComponentTest() {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
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

获取当前图形对象所关联的渲染上下文。

**起始版本：** 23

<!--Device-Scene-static getDefaultRenderContext(): RenderContext | null--><!--Device-Scene-static getDefaultRenderContext(): RenderContext | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderContext](arkts-arkgraphics3d-scene-rendercontext-i.md) | 返回当前对象关联的渲染上下文，若对象尚未关联任何渲染上下文，则返回null。 |

**示例**

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

通过路径获取节点。

**起始版本：** 23

<!--Device-Scene-getNodeByPath(path: string, type?: NodeType): Node | null--><!--Device-Scene-getNodeByPath(path: string, type?: NodeType): Node | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 场景节点层次中的路径。每层之间使用'/'符号进行分割。 |
| type | [NodeType](arkts-arkgraphics3d-scenenodes-nodetype-e.md) | 否 | 预期返回的节点类型。当需要确保返回特定类型的节点时传入此参数，不传入时返回路径上找到的第一个节点（不限制类型）。默认值为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 返回请求节点的实例，如果没有找到或者找到的节点类型与传入的参数不相符则返回空。 |

**示例**

```TypeScript
import { Scene, Node } from '@kit.ArkGraphics3D';

function getNode(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
         // 寻找指定路径的节点
        let node : Node | null = result.getNodeByPath("rootNode_");
    }
  });
}
```

## getResourceFactory

```TypeScript
getResourceFactory(): SceneResourceFactory
```

获取场景资源工厂对象。

**起始版本：** 23

<!--Device-Scene-getResourceFactory(): SceneResourceFactory--><!--Device-Scene-getResourceFactory(): SceneResourceFactory-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SceneResourceFactory](arkts-arkgraphics3d-scene-sceneresourcefactory-i.md) | 返回场景资源工厂对象。 |

**示例**

```TypeScript
import { SceneResourceFactory, Scene } from '@kit.ArkGraphics3D';

function getFactory(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then(async (result: Scene) => {
    if (result) {
         // 获得SceneResourceFactory对象
        let sceneFactory: SceneResourceFactory = result.getResourceFactory();
    }
  });
}
```

## importNode

```TypeScript
importNode(name: string, node: Node, parent: Node | null): Node
```

一般用于从其他场景导入节点。

**起始版本：** 23

<!--Device-Scene-importNode(name: string, node: Node, parent: Node | null): Node--><!--Device-Scene-importNode(name: string, node: Node, parent: Node | null): Node-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 导入节点后的名称，由开发者自定义，无特殊要求。 |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 被导入的节点。 |
| parent | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) \| null | 是 | 被导入节点在新场景中的父节点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 被导入的节点。 |

**示例**

```TypeScript
import { Scene } from '@kit.ArkGraphics3D';

function ImportNodeTest() {
  Scene.load().then(async (result: Scene | undefined) => {
    if (!result) {
      return;
    }
    // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
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

在当前场景中导入其他场景。

**起始版本：** 23

<!--Device-Scene-importScene(name: string, scene: Scene, parent: Node | null): Node--><!--Device-Scene-importScene(name: string, scene: Scene, parent: Node | null): Node-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 导入场景的根节点名称，由开发者自定义，无特殊要求。 |
| scene | [Scene](arkts-arkgraphics3d-scene-c.md) | 是 | 被导入的场景。 |
| parent | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) \| null | 是 | 被导入场景在新场景中的父节点。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 被导入场景的根节点。 |

**示例**

```TypeScript
import { Scene } from '@kit.ArkGraphics3D';

function ImportSceneTest() {
  Scene.load().then(async (result: Scene | undefined) => {
    if (!result) {
      return;
    }
    // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
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

通过传入的资源路径加载资源，使用Promise异步回调。 调用后，应该在Scene使用完毕时调用destroy释放资源，否则可能导致资源泄漏。

**起始版本：** 23

<!--Device-Scene-static load(uri? : ResourceStr): Promise<Scene>--><!--Device-Scene-static load(uri? : ResourceStr): Promise<Scene>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | ResourceStr | 否 | 待加载的模型文件资源路径，默认值为undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Scene](arkts-arkgraphics3d-scene-c.md)&gt; | Promise对象，返回场景对象。 |

**示例**

示例1：通过rawfile加载（相对路径）

```TypeScript
import { Scene } from '@kit.ArkGraphics3D';

function loadModel(): void {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"));
  scene.then((result: Scene) => {
    console.info("Scene loaded, root node: " + result.root?.name);
  });
}
```

示例2：通过绝对路径加载（从应用沙盒目录/data/storage/el2/base/files加载模型）

```TypeScript
import { common } from '@kit.AbilityKit';
import { fileIo } from '@kit.CoreFileKit';
import { Scene } from '@kit.ArkGraphics3D';

async function loadModelFromAbsolutePath(context: common.UIAbilityContext): Promise<void> {
  // 获取应用沙盒目录（Scene.load仅能读取应用自身写入的文件，不能读取hdc/adb push写入的文件）
  const appCtx = context.getApplicationContext();
  const filesDir = appCtx.filesDir; // /data/storage/el2/base/files

  // 从rawfile读取模型内容（实际使用中也可以替换为其他来源的数据）
  // 使用.glb文件更易于复制加载；若为.gltf，请将其.bin和贴图文件一并复制到同一目录
  const src = 'gltf/CubeWithFloor/glTF/AnimatedCube.glb';
  const load_uri = `${filesDir}/AnimatedCube.glb`;

  // 写入模型文件到应用沙盒目录，生成可被Scene.load(绝对路径)访问的实际文件
  const rawData = await context.resourceManager.getRawFileContent(src);
  const file = fileIo.openSync(load_uri, fileIo.OpenMode.CREATE | fileIo.OpenMode.TRUNC | fileIo.OpenMode.WRITE_ONLY);
  fileIo.writeSync(file.fd, rawData.buffer.slice(rawData.byteOffset, rawData.byteOffset + rawData.byteLength));
  fileIo.closeSync(file);

  // 使用绝对路径加载模型
  Scene.load(load_uri).then((scene: Scene) => {
    // 加载成功后的逻辑处理
  }).catch((err: Error) => {
    console.error(`Failed to load scene. Message: ${err.message}`);
  });
}
```

## renderFrame

```TypeScript
renderFrame(params?: RenderParameters): boolean
```

通过该接口可以实现按需渲染，例如控制渲染帧率。

**起始版本：** 23

<!--Device-Scene-renderFrame(params?: RenderParameters): boolean--><!--Device-Scene-renderFrame(params?: RenderParameters): boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [RenderParameters](arkts-arkgraphics3d-scene-renderparameters-i.md) | 否 | 渲染参数，默认值为undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 渲染被成功调度返回true，否则返回false。 |

**示例**

```TypeScript
import { Scene } from '@kit.ArkGraphics3D';

function RenderFrameTest() {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
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

