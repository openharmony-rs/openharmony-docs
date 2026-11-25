# SceneResources (System API)
<!--Kit: ArkGraphics 3D-->
<!--Subsystem: Graphics-->
<!--Owner: @jason_stark-->
<!--Designer: @zdustc-->
<!--Tester: @dongchao01-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=1c2fc501136ceec9ba29fd39d66bab83ae7d758a translatedAt=2026-11-23T09:05:10.135Z pushedAt=2026-11-24T12:35:21.112Z nl=1 -->

This module provides the common basic resource types in ArkGraphics 3D.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [SceneResources](js-apis-inner-scene-resources.md).

## Modules to Import

```ts
import { MaterialType, UnlitShadowAlphaMaterial, RenderTarget } from '@kit.ArkGraphics3D';
```

## MaterialType

Enumerates the material types in a scene. The material type defines how materials in a scene are rendered.

**System capability**: SystemCapability.ArkUi.Graphics3D

| Name| Value| Description|
| ---- | ---- | ---- |
| UNLIT_SHADOW_ALPHA<sup>23+</sup> | 100 | Draws only shadows. When the [Blend](js-apis-inner-scene-resources.md#blend20) property of the material is enabled, the material is blended with the background to simulate a transparent material effect.<br>**System API**: This is a system API.<br>**Model restriction**: This API can be used only in the stage model.|

## UnlitShadowAlphaMaterial<sup>23+</sup>

This material inherits from [Material](js-apis-inner-scene-resources.md#material) and draws only the surface shadows. When the [Blend](js-apis-inner-scene-resources.md#blend20) property is enabled, the material can be blended with the background to simulate transparency.

**System capability**: SystemCapability.ArkUi.Graphics3D

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| baseColor | [MaterialProperty](js-apis-inner-scene-resources.md#materialproperty20) | No| No| Color information of the shadow on the surface of a transparent material.|

## RenderTarget

Render target type. Inherits from [Image](js-apis-inner-scene-resources.md#image), used for offscreen rendering.

**Since:** 26.1.0

**System capability**: SystemCapability.ArkUi.Graphics3D

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

### getPixelMap

getPixelMap(): Promise\<image.PixelMap\>

Obtains from the render target object the PixelMap of the rendering result. The returned PixelMap is not editable. This API uses a promise to return the result asynchronously.

**Since:** 26.1.0

**System capability**: SystemCapability.ArkUi.Graphics3D

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type | Description |
| ---- | ---- |
| Promise\<[image.PixelMap](../apis-image-kit/arkts-apis-image-PixelMap.md)\> | Promise object, which returns the PixelMap corresponding to the rendering result. |

**Error codes**

For details about the following error codes, see [Graphics 3D Error Codes](errorcode-graphics3d.md).

| ID | Error Message |
| ---- | ---- |
| 25601006 | Expired or invalid resource. |

**Example**

```ts
import { Scene, Camera, RenderTargetParameters } from '@kit.ArkGraphics3D';
import { image } from '@kit.ImageKit';

function getPixelMapFromRenderTarget(): void {
  // Load scene resources. Supports .gltf and .glb formats. The path and file name can be customized based on the actual project resources.
  Scene.load($rawfile("gltf/CubeWithFloor/glTF/AnimatedCube.glb"), { offset: 0 })
    .then(async (result: Scene) => {
      if (!result.root) {
        return;
      }
      let sceneFactory = result.getResourceFactory();
      // Create an offscreen rendering camera for offscreen rendering. The main camera cannot be used.
      let offscreenCamera: Camera = await sceneFactory.createCamera({ name: "offscreenCamera" });
      offscreenCamera.position = { x: 0, y: 0, z: 3 };
      // Configure render target parameters. Set the render target size to 512*512 pixels.
      let params: RenderTargetParameters = {
        name: "snapshotTarget",
        size: { x: 512, y: 512 }
      };
      // Perform offscreen rendering on the current scene.
      let renderTargets = await result.snapshot([offscreenCamera], [params]);
      if (renderTargets.length > 0) {
        // Obtains from the render target object the PixelMap.
        let pixelMap: image.PixelMap = await renderTargets[0].getPixelMap();
        let imageInfo = await pixelMap.getImageInfo();
        console.info("PixelMap width: " + imageInfo.size.width);
        // Release the PixelMap.
        pixelMap.release();
      }
    }).catch((err: Error) => {
      console.error(`Failed to get pixel map. Message: ${err.message}`);
    });
}
```
