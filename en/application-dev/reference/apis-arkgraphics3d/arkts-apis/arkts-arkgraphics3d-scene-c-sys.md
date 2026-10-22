# Scene (System API)

```TypeScript
export declare class Scene
```

Describes a scene.

**Since:** 12

<!--Device-unnamed-export declare class Scene--><!--Device-unnamed-export declare class Scene-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

## load

```TypeScript
static load(uri: ResourceStr, param: SceneLoadParams):Promise<Scene>
```

Create a new scene from a SceneLoadParams.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Scene-static load(uri: ResourceStr, param: SceneLoadParams):Promise<Scene>--><!--Device-Scene-static load(uri: ResourceStr, param: SceneLoadParams):Promise<Scene>-End-->

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

<!--Del-->
**Examples**

```TypeScript
import { Scene, SceneLoadParams } from '@kit.ArkGraphics3D';

function loadModelWithParams(): Promise<Scene> {
  let loadParams: SceneLoadParams = { offset: 0 };
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"), loadParams);
  return scene;
}
```

<!--DelEnd-->

## snapshot

```TypeScript
snapshot(cameras: Camera[], params: RenderTargetParameters[]): Promise<RenderTarget[]>
```

take a snapshot for the current scene;

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-Scene-snapshot(cameras: Camera[], params: RenderTargetParameters[]): Promise<RenderTarget[]>--><!--Device-Scene-snapshot(cameras: Camera[], params: RenderTargetParameters[]): Promise<RenderTarget[]>-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cameras | [Camera](arkts-arkgraphics3d-scenenodes-camera-i.md)[] | Yes | the camera list used to render the snapshot. |
| params | [RenderTargetParameters](arkts-arkgraphics3d-scene-rendertargetparameters-i-sys.md)[] | Yes | the parameters for render target list. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RenderTarget](arkts-arkgraphics3d-sceneresources-rendertarget-i-sys.md)[]&gt; | Promise used to return a list of render target |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 25603001 |  |
| 25603002 |  |
| 25601002 |  |
| 25601004 |  |
