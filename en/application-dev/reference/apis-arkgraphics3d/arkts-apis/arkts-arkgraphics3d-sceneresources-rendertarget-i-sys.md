# RenderTarget (System API)

```TypeScript
export interface RenderTarget extends Image
```

render target object, used for offscreen rendering

**Inheritance/Implementation:** RenderTarget extends [Image](arkts-arkgraphics3d-sceneresources-image-i.md)

**Since:** 26.1.0

<!--Device-unnamed-export interface RenderTarget extends Image--><!--Device-unnamed-export interface RenderTarget extends Image-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

## getPixelMap

```TypeScript
getPixelMap(): Promise<image.PixelMap>
```

get a pixel map object from RenderTarget

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-RenderTarget-getPixelMap(): Promise<image.PixelMap>--><!--Device-RenderTarget-getPixelMap(): Promise<image.PixelMap>-End-->

**System capability:** SystemCapability.ArkUi.Graphics3D

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise used to return a pixel map |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 25601006 | - Possible Cause: -- try to get a PixelMap from a destroyed RenderTarget |
