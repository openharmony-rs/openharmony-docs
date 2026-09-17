# encodeImage (System API)

## Modules to Import

```TypeScript
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
```

## encodeImage

```TypeScript
function encodeImage(srcImage: image.PixelMap, metadata: string): Promise<image.PixelMap>
```

Encodes metadata into an image. This API uses a promise to return the result.

**Since:** 18

**System capability:** SystemCapability.MultimodalAwareness.MetadataBinding

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| srcImage | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | Source image. |
| metadata | string | Yes | Metadata to be encoded. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)&gt; | Promise object, which is used to return the image with encoded metadata. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission check failed. A non-system application uses the system API. |
| [32100001](../errorcode-metadataBinding.md#32100001-file-creation-failed) | Internal handling failed. |
| [32100002](../errorcode-metadataBinding.md#32100002-encoding-failed) | Encode process fail. Possible causes:<br>1. Image processing error. <br>2. Channel coding error. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';

let captureImage: image.PixelMap | undefined = undefined;
let metadata: string = "";
let srcImage: image.PixelMap | undefined = undefined;
metadataBinding.encodeImage(srcImage, metadata).then((pixelMap: image.PixelMap) => {
  captureImage = pixelMap;
}).catch((error: BusinessError) => {
  console.error("encode image error" + error);
});
```
