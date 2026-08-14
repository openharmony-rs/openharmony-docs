# Scene

定义3D场景.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class Scene--><!--Device-unnamed-export declare class Scene-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## cloneNode

```TypeScript
cloneNode(node: Node, parent: Node, name: string): Node | null
```

克隆以输入节点为根节点的节点或子树

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Scene-cloneNode(node: Node, parent: Node, name: string): Node | null--><!--Device-Scene-cloneNode(node: Node, parent: Node, name: string): Node | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 要克隆的输入节点 |
| parent | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 克隆节点将被设置为其子节点的父节点 |
| name | string | 是 | 克隆节点的名称 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 克隆结果，如果克隆失败则返回null. |

## 示例

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
        console.info("cloneNode success");
      } else {
        console.error("cloneNode failed");
      }
    });
}
```

## createComponent

```TypeScript
createComponent(node: Node, name: string): Promise<SceneComponent>
```

创建新组件.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Scene-createComponent(node: Node, name: string): Promise<SceneComponent>--><!--Device-Scene-createComponent(node: Node, name: string): Promise<SceneComponent>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 组件附加到的节点 |
| name | string | 是 | 要加载的组件名称. 有效名称由各插件定义. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[SceneComponent](arkts-arkgraphics3d-scene-scenecomponent-i.md)&gt; | 新添加的组件. |

## 示例

```TypeScript
import { Scene, SceneComponent } from '@kit.ArkGraphics3D';

function createComponentTest(): Promise<SceneComponent> {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  return Scene.load($rawfile("gltf/DamagedHelmet/glTF/DamagedHelmet.glb"))
    .then(scene => {
      if (!scene) {
        return Promise.reject(new Error("Scene load failed"));
      }
      // RenderConfigurationComponent为引擎内置组件，创建时无需依赖插件
      return scene.createComponent(scene.root, "RenderConfigurationComponent");
    })
    .then(component => {
      if (!component) {
        return Promise.reject(new Error("createComponent failed"));
      }
      return component;
    });
}
```

## destroy

```TypeScript
destroy(): void
```

释放所有原生场景资源. 所有TS引用将变为undefined.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Scene-destroy(): void--><!--Device-Scene-destroy(): void-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## 示例

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

通过名称获取组件.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Scene-getComponent(node: Node, name: string): SceneComponent | null--><!--Device-Scene-getComponent(node: Node, name: string): SceneComponent | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 组件附加到的节点. |
| name | string | 是 | 组件名称 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SceneComponent](arkts-arkgraphics3d-scene-scenecomponent-i.md) |  |

## 示例

```TypeScript
import { Scene } from '@kit.ArkGraphics3D';

function getComponentTest() {
  // 加载场景资源，支持.gltf和.glb格式，路径和文件名可根据项目实际资源自定义
  Scene.load($rawfile("gltf/DamagedHelmet/glTF/DamagedHelmet.glb"))
    .then(async (result: Scene | undefined) => {
      if (!result) {
        console.error("Scene load failed");
        return;
      }
      console.info("TEST getComponentTest");
      let component = result.getComponent(result.root, "myComponent");
      if (component) {
        console.info("getComponent success");
      } else {
        console.warn("Component not found");
      }
    });
}
```

## getDefaultRenderContext

```TypeScript
static getDefaultRenderContext(): RenderContext | null
```

获取默认渲染上下文

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Scene-static getDefaultRenderContext(): RenderContext | null--><!--Device-Scene-static getDefaultRenderContext(): RenderContext | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RenderContext](arkts-arkgraphics3d-scene-rendercontext-i.md) | 默认RenderContext实例 |

## 示例

```TypeScript
import { Scene, RenderContext } from '@kit.ArkGraphics3D';

function getDefaultRenderContextTest() {
  console.info("TEST getDefaultRenderContextTest");
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (renderContext) {
    console.info("getDefaultRenderContext success");
  } else {
    console.error("RenderContext is null");
  }
}
```

## getNodeByPath

```TypeScript
getNodeByPath(path: string, type?: NodeType): Node | null
```

通过路径获取节点.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Scene-getNodeByPath(path: string, type?: NodeType): Node | null--><!--Device-Scene-getNodeByPath(path: string, type?: NodeType): Node | null-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 节点路径 |
| type | [NodeType](arkts-arkgraphics3d-scenenodes-nodetype-e.md) | 否 | 验证节点类型，如果不匹配则返回null |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 如果通过路径找到节点 |

## 示例

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

获取资源工厂.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Scene-getResourceFactory(): SceneResourceFactory--><!--Device-Scene-getResourceFactory(): SceneResourceFactory-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SceneResourceFactory](arkts-arkgraphics3d-scene-sceneresourcefactory-i.md) | 如果通过路径找到节点 |

## 示例

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

将节点导入场景. 原始节点可能来自另一个场景. 节点将被克隆，导入后对旧节点的修改将不可见.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Scene-importNode(name: string, node: Node, parent: Node | null): Node--><!--Device-Scene-importNode(name: string, node: Node, parent: Node | null): Node-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 新创建节点的名称. |
| node | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 是 | 要导入的节点. |
| parent | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) \| null | 是 | 父节点，根节点为null |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 新创建的节点. |

## 示例

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

将场景作为节点导入场景. 节点层级将出现在父节点下. 场景中的所有动画将被复制.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Scene-importScene(name: string, scene: Scene, parent: Node | null): Node--><!--Device-Scene-importScene(name: string, scene: Scene, parent: Node | null): Node-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 新创建节点的名称 |
| scene | [Scene](arkts-arkgraphics3d-scene-c.md) | 是 | The scene to be imported. |
| parent | [Node](arkts-arkgraphics3d-scenenodes-node-i.md) \| null | 是 | 父节点，根节点为null |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Node](arkts-arkgraphics3d-scenenodes-node-i.md) | 新创建的节点. |

## 示例

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

通过传入的资源路径加载资源，使用Promise异步回调。 调用后，应该在Scene使用完毕时调用[destroy](#destroy)释放资源，否则可能导致资源泄漏。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

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

## 示例

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
  }).catch((error: string) => {
    console.error('Scene load failed: ' + error);
  });
}
```

## renderFrame

```TypeScript
renderFrame(params?: RenderParameters): boolean
```

为所有活动相机渲染新帧.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Scene-renderFrame(params?: RenderParameters): boolean--><!--Device-Scene-renderFrame(params?: RenderParameters): boolean-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [RenderParameters](arkts-arkgraphics3d-scene-renderparameters-i.md) | 否 | 渲染参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果渲染被调度则返回true，否则返回false |

## 示例

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

