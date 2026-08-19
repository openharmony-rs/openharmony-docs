# RenderResourceFactory

用于创建可在共享RenderContext的多个场景（[Scene](arkts-arkgraphics3d-scene-c.md)）中共享的渲染资源。

**起始版本：** 23

<!--Device-unnamed-export interface RenderResourceFactory--><!--Device-unnamed-export interface RenderResourceFactory-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

## createScene

```TypeScript
createScene(uri: ResourceStr, param: SceneLoadParams): Promise<Scene>
```

根据指定的资源路径和场景加载参数创建场景，使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RenderResourceFactory-createScene(uri: ResourceStr, param: SceneLoadParams): Promise<Scene>--><!--Device-RenderResourceFactory-createScene(uri: ResourceStr, param: SceneLoadParams): Promise<Scene>-End-->

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | ResourceStr | 是 | 创建场景使用的资源路径。 |
| param | [SceneLoadParams](arkts-arkgraphics3d-scene-sceneloadparams-i-sys.md) | 是 | 场景加载参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Scene](arkts-arkgraphics3d-scene-c.md)&gt; | Promise对象，返回创建的场景对象。 |

**示例**

```TypeScript
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

