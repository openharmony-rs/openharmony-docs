# Scene (System API)

<!--Kit: ArkGraphics 3D-->
<!--Subsystem: Graphics-->
<!--Owner: @jason_stark-->
<!--Designer: @zdustc-->
<!--Tester: @zhangyue283-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=be289c7f6118451a090e297ed8b07aa5ccf2fe06 translatedAt=2026-08-20T12:26:33.451Z pushedAt=2026-08-21T09:06:52.893Z -->

As the basic module of ArkGraphics 3D, this module provides data types such as scene load parameters and scene loading methods.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with the superscript to indicate their earliest API version.
> - This page contains only the system APIs of this module. For details about other public APIs, see [Scene](js-apis-inner-scene.md).

## Modules to Import

```ts
import { SceneLoadParams, Scene, RenderResourceFactory } from '@kit.ArkGraphics3D';
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

## RenderResourceFactory

### createScene

createScene(uri: ResourceStr, param: SceneLoadParams): Promise\<Scene>

Creates a scene based on the specified resource path and scene load parameters. This API uses a promise to return the result.

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