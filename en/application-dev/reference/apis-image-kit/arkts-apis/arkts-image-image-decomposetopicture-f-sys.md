# decomposeToPicture (System API)

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## decomposeToPicture

```TypeScript
function decomposeToPicture(hdrPixelMap : PixelMap, options?: HdrDecomposeOptions): Promise<Picture | undefined>
```

Decomposes an HDR Pixelmap object to a Picture object which contains an SDR PixelMap and a gainmap. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hdrPixelMap | [PixelMap](arkts-image-image-pixelmap-i.md) | Yes | An HDR PixelMap, whose PixelMapFormat should be RGBA_F16\RGBA_1010102\YCBCR_P010\YCRCB_P010. |
| options | [HdrDecomposeOptions](arkts-image-image-hdrdecomposeoptions-i-sys.md) | No | The HDR decomposition configurations. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Picture](arkts-image-image-picture-i.md) &#124; undefined&gt; | Promise used to return the Picture object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications are not allowed to use system APIs. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation. hdrPixelMap's PixelMapFormat is not RGBA_F16\RGBA_1010102\YCBCR_P010\YCRCB_P010. |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. Possible cause: hdrPixelMap is empty. |
| [7600208](../errorcode-image.md#7600208-failed-to-decompose-an-hdr-image) | HDR image decomposition failed. Possible causes: 1. Decomposition processing is not supported. 2. Processing error occurs. |
| [7600301](../errorcode-image.md#7600301-memory-allocation-failure) | Alloc memory failed. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function DecomposeToPictureTest(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("test.jpg");
  let imageSource: image.ImageSource = image.createImageSource(rawFile);
  let decodingOptions: image.DecodingOptions = {
    desiredDynamicRange: image.DecodingDynamicRange.HDR,
  };
  let hdrPixelMap = await imageSource.createPixelMap(decodingOptions);
  // Set the gain map to full size and the pixel format to NV12.
  let options: image.HdrDecomposeOptions = {
    isFullSizeGainmap: true,
    desiredPixelFormat: image.PixelMapFormat.NV12,
  };
  let picture: image.Picture | undefined = await image.decomposeToPicture(hdrPixelMap, options);
  if (picture != undefined) {
    console.info('Decompose to picture with options successfully');
  } else {
    console.error('Decompose to picture with options failed');
  }
}
```
