# Scene

```TypeScript
export declare class Scene
```

Describes a scene.

**Since:** 12

**System capability:** SystemCapability.ArkUi.Graphics3D

<a id="load-1"></a>

## load

```TypeScript
static load(uri: ResourceStr, param: SceneLoadParams):Promise<Scene>
```

Create a new scene from a SceneLoadParams.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | ResourceStr | Yes | the resource of creating a scene |
| param | [SceneLoadParams](arkts-arkgraphics3d-scene-sceneloadparams-i-sys.md) | Yes | the params for scene load |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Scene](arkts-arkgraphics3d-scene-c.md)&gt; | Promise used to return a scene |

**Examples**

```TypeScript
import { Scene, SceneLoadParams } from '@kit.ArkGraphics3D';

function loadModelWithParams(): Promise<Scene> {
  let loadParams: SceneLoadParams = { offset: 0 };
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"), loadParams);
  return scene;
}
```
