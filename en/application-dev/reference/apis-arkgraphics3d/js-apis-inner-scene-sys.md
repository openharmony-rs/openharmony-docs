# Scene (System API)
<!--Kit: ArkGraphics 3D-->
<!--Subsystem: Graphics-->
<!--Owner: @jason_stark-->
<!--Designer: @zdustc-->
<!--Tester: @dongchao01-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=1c2fc501136ceec9ba29fd39d66bab83ae7d758a translatedAt=2026-11-23T09:06:32.633Z pushedAt=2026-11-24T12:43:56.179Z nl=1 -->

As the basic module of ArkGraphics 3D, this module provides data types such as scene load parameters and scene loading methods.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with the superscript to indicate their earliest API version.
> - This page contains only the system APIs of this module. For details about other public APIs, see [Scene](js-apis-inner-scene.md).

## Modules to Import

```ts
import { SceneLoadParams, RenderTargetParameters, Scene, RenderResourceFactory } from '@kit.ArkGraphics3D';
```

## SceneLoadParams

Scene loading parameters object, used to specify additional configuration options when loading 3D model resources. A typical use case is loading an embedded glb model from an MP4 container file.

**Since**: 26.0.0

**System capability**: SystemCapability.ArkUi.Graphics3D

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

| Name | Type | Read-Only | Optional | Description |
| ---- | ---- | ---- | ---- | ---- |
| offset | number | No | Yes | Start offset of the 3D model data in the resource file, in bytes. The system locates and reads the glb model data from this offset position in the resource file. For example, when the glb model is embedded in an MP4 container file, set this parameter to the start byte position of the glb data in the MP4 file so that the system can correctly extract and load the model. The value must be greater than or equal to 0. The default value is 0, indicating that the model data starts from the beginning of the file. |

## RenderTargetParameters

Render target parameter object, which inherits from [SceneResourceParameters](js-apis-inner-scene.md#sceneresourceparameters) and is used to describe the render target.

**Since:** 26.1.0

**System capability**: SystemCapability.ArkUi.Graphics3D

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

| Name | Type | Read-Only | Optional | Description |
| ---- | ---- | ---- | ---- | ---- |
| size | [Vec2](js-apis-inner-scene-types.md#vec2) | No | No | Size of the render target. x indicates the width and y indicates the height. The unit is pixel (px). The value must be greater than 0. When the value is a floating-point number, it is rounded down. |

## RenderResourceFactory

### createScene

createScene(uri: ResourceStr, param: SceneLoadParams): Promise\<Scene>

Creates a scene based on the specified resource path and scene load parameters. This API uses a promise to return the result.

This API is a time-consuming operation. During the execution of the asynchronous task, calling other APIs may be blocked until the asynchronous task is complete.

**Since**: 26.0.0

**System capability**: SystemCapability.ArkUi.Graphics3D

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| uri | [ResourceStr](../apis-arkui/arkui-ts/ts-types.md#resourcestr) | Yes | Resource path used to create the scene. |
| param | [SceneLoadParams](#sceneloadparams) | Yes | Scene load parameters. |

**Return value**

| Type | Description |
| ---- | ---- |
| Promise\<[Scene](js-apis-inner-scene.md#scene-1)> | Promise used to return the created scene object. |

**Example**

```ts
import { Scene, SceneLoadParams, RenderContext, RenderResourceFactory } from '@kit.ArkGraphics3D';

function createSceneWithParams(): Promise<Scene> {
  const renderContext: RenderContext | null = Scene.getDefaultRenderContext();
  if (!renderContext) {
    return Promise.reject(new Error("RenderContext is null"));
  }
  const renderResourceFactory: RenderResourceFactory = renderContext.getRenderResourceFactory();
  // Create the scene and pass in the scene loading parameters. The path and file name can be customized based on the actual project resources.
  let loadParams: SceneLoadParams = { offset: 0 };
  return renderResourceFactory.createScene($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"), loadParams);
}
```

## Scene

### load

static load(uri: ResourceStr, param: SceneLoadParams): Promise\<Scene>

Loads resources based on the specified resource path and scene load parameters. This API uses a promise to return the result.

This API is a time-consuming operation. During the execution of the asynchronous task, calling other APIs may be blocked until the asynchronous task is complete.

**Since**: 26.0.0

**System capability**: SystemCapability.ArkUi.Graphics3D

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| uri | [ResourceStr](../apis-arkui/arkui-ts/ts-types.md#resourcestr) | Yes | Resource path of the model file to load. |
| param | [SceneLoadParams](#sceneloadparams) | Yes | Scene load parameters. |

**Return value**

| Type | Description |
| ---- | ---- |
| Promise\<[Scene](js-apis-inner-scene.md#scene-1)> | Promise used to return the scene object. |

**Example**

```ts
import { Scene, SceneLoadParams } from '@kit.ArkGraphics3D';

function loadModelWithParams(): Promise<Scene> {
  let loadParams: SceneLoadParams = { offset: 0 };
  let scene: Promise<Scene> = Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"), loadParams);
  return scene;
}
```

### snapshot

snapshot(cameras: Camera[], params: RenderTargetParameters[]): Promise\<RenderTarget[]\>

Performs offscreen rendering on the current scene. Based on the camera list and render target parameter list passed in, the rendering result of each camera view is generated using offscreen rendering, and an asynchronous callback is returned through a Promise.

Each camera has a one-to-one correspondence with the render target parameters at the corresponding position. After rendering is complete, the [PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md) can be obtained through the returned [RenderTarget](js-apis-inner-scene-resources-sys.md#rendertarget) object.

**Since:** 26.1.0

**System capability**: SystemCapability.ArkUi.Graphics3D

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| cameras | [Camera](js-apis-inner-scene-nodes.md#camera)[] | Yes | Camera list used for offscreen rendering. Cameras in the list cannot be duplicated, and in onscreen rendering mode the list cannot contain the main camera of the scene (for details, see [Camera](js-apis-inner-scene-nodes.md#camera)). Offscreen rendering cameras occupy camera slots. For slot rules and the upper limit, see [Camera](js-apis-inner-scene-nodes.md#camera).<br>The system throws error code 25603001 when any of the following occurs:<br>- The camera array is empty;<br>- The camera array contains duplicate cameras;<br>- The camera array contains the main camera of the scene;<br>- After offscreen rendering, the total number of camera slots occupied by the scene exceeds the upper limit. |
| params | [RenderTargetParameters](#rendertargetparameters)[] | Yes | The render target parameter list has a one-to-one correspondence with the camera list and is used to specify information such as the size of each render target.<br>Error code 25603002 is thrown when the array length is inconsistent with the camera array length, and error code 25603001 is thrown when the width or height of the render target is less than or equal to 0.<br>The system first checks 25603002 (whether the camera array length is consistent with the render target parameter array length), and then checks 25603001 (the validity of array elements). |

**Return value**

| Type | Description |
| ---- | ---- |
| Promise\<[RenderTarget](js-apis-inner-scene-resources-sys.md#rendertarget)[]\> | Promise object that returns a list of render target objects, which has a one-to-one correspondence with the camera list passed in. |

**Error codes**

For details about the following error codes, see [Graphics 3D Error Codes](errorcode-graphics3d.md).

| ID | Error Message |
| ---- | ---- |
| 25601002 | Scene used after destruction. |
| 25601005 | Memory allocation failed. |
| 25603001 | Parameter exceeds the allowed range. |
| 25603002 | Input parameter type or count mismatch. |

**Example**

```ts
import { Scene, Camera, RenderTargetParameters } from '@kit.ArkGraphics3D';

function snapshotTest(): void {
  // Load scene resources. The .gltf and .glb formats are supported. The path and file name can be customized based on actual project resources.
  Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"), { offset: 0 })
    .then(async (result: Scene) => {
      if (!result.root) {
        return;
      }
      let sceneFactory = result.getResourceFactory();
      // Create an offscreen rendering camera for offscreen rendering. The main camera cannot be used.
      let offscreenCamera: Camera = await sceneFactory.createCamera({ name: "offscreenCamera" });
      offscreenCamera.position = { x: 0, y: 0, z: 3 };
      // Configure render target parameters and set the render target size to 512*512 pixels.
      let params: RenderTargetParameters = {
        name: "snapshotTarget",
        size: { x: 512, y: 512 }
      };
      // Declare a Camera array and a RenderTargetParameters array.
      let cameras: Camera[] = [offscreenCamera];
      let targetParams: RenderTargetParameters[] = [params];
      // Perform offscreen rendering on the current scene.
      let renderTargets = await result.snapshot(cameras, targetParams);
      if (renderTargets.length > 0) {
        console.info("Snapshot width: " + renderTargets[0].width);
      }
    }).catch((err: Error) => {
      console.error(`Failed to take snapshot. Message: ${err.message}`);
    });
}
```
