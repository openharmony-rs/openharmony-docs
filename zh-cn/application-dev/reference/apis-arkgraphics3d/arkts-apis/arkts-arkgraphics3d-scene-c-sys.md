# Scene

用于设置场景。Scene采用树状层次结构组织场景节点，根节点（root）作为场景的入口。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUi.Graphics3D

## load

```TypeScript
static load(uri: ResourceStr, param: SceneLoadParams):Promise<Scene>
```

根据指定的资源路径和场景加载参数加载资源，使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUi.Graphics3D

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | ResourceStr | 是 | 待加载的模型文件资源路径。 |
| param | [SceneLoadParams](arkts-arkgraphics3d-scene-sceneloadparams-i-sys.md) | 是 | 场景加载参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Scene](arkts-arkgraphics3d-scene-c.md)&gt; | Promise对象，返回场景对象。 |

**示例**

```TypeScript
import { Scene, SceneLoadParams } from '@kit.ArkGraphics3D';

function loadModelWithParams(): Promise<Scene> {
  let loadParams: SceneLoadParams = { offset: 0 };
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"), loadParams);
  return scene;
}
```
