# Scene (系统接口)
<!--Kit: ArkGraphics 3D-->
<!--Subsystem: Graphics-->
<!--Owner: @jason_stark-->
<!--Designer: @zdustc-->
<!--Tester: @zhangyue283-->
<!--Adviser: @ge-yafang-->

本模块作为ArkGraphics 3D基础模块，提供场景加载参数等数据类型和场景加载方法。

> **说明：**
>
> - 本模块首批接口从API version 12开始支持，后续版本的新增接口，采用上角标标记接口的起始版本。
> - 页面仅包含本模块的系统接口，其他公开接口参见[Scene](js-apis-inner-scene.md)。

## 导入模块

```ts
import { SceneLoadParams, Scene, RenderResourceFactory } from '@kit.ArkGraphics3D';
```

## SceneLoadParams

场景加载参数对象，用于指定加载3D模型资源时的额外配置选项。典型使用场景为从MP4容器文件中加载内嵌的glb模型。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| offset | number | 否 | 是 | 3D模型数据在资源文件中的起始偏移量，单位为字节。系统将从资源文件的该偏移位置定位并读取glb模型数据。例如，当glb模型嵌在MP4容器文件中时，可将此参数设置为glb数据在MP4文件中的起始字节位置，使系统能够正确提取并加载模型。取值必须大于或等于0。默认值为0，表示模型数据从文件起始位置开始。 |

## RenderResourceFactory

### createScene

createScene(uri: ResourceStr, param: SceneLoadParams): Promise\<Scene>

根据指定的资源路径和场景加载参数创建场景，使用Promise异步回调。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| uri | [ResourceStr](../apis-arkui/arkui-ts/ts-types.md#resourcestr) | 是 | 创建场景使用的资源路径。 |
| param | [SceneLoadParams](#sceneloadparams) | 是 | 场景加载参数。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| Promise\<[Scene](js-apis-inner-scene.md#scene-1)> | Promise对象，返回创建的场景对象。 |

**示例：**

```ts
import { Scene, SceneLoadParams, RenderContext, RenderResourceFactory } from '@kit.ArkGraphics3D';

function createSceneWithParams(): Promise<Scene> {
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (!renderContext) {
    return Promise.reject(new Error("RenderContext is null"));
  }
  const renderResourceFactory: RenderResourceFactory = renderContext.getRenderResourceFactory();
  // 创建场景并传入场景加载参数，路径和文件名可根据项目实际资源自定义
  let loadParams: SceneLoadParams = { offset: 0 };
  return renderResourceFactory.createScene($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"), loadParams);
}
```

## Scene

### load

static load(uri: ResourceStr, param: SceneLoadParams): Promise\<Scene>

根据指定的资源路径和场景加载参数加载资源，使用Promise异步回调。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| uri | [ResourceStr](../apis-arkui/arkui-ts/ts-types.md#resourcestr) | 是 | 待加载的模型文件资源路径。 |
| param | [SceneLoadParams](#sceneloadparams) | 是 | 场景加载参数。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| Promise\<[Scene](js-apis-inner-scene.md#scene-1)> | Promise对象，返回场景对象。 |

**示例：**

```ts
import { Scene, SceneLoadParams } from '@kit.ArkGraphics3D';

function loadModelWithParams(): Promise<Scene> {
  let loadParams: SceneLoadParams = { offset: 0 };
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"), loadParams);
  return scene;
}
```
