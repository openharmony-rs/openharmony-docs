# decodeImage (System API)

## Modules to Import

```TypeScript
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
```

## decodeImage

```TypeScript
function decodeImage(encodedImage: image.PixelMap): Promise<string>
```

Decodes the information carried in the image. This API uses a promise to return the result.

**Since:** 18

<!--Device-metadataBinding-function decodeImage(encodedImage: image.PixelMap): Promise<string>--><!--Device-metadataBinding-function decodeImage(encodedImage: image.PixelMap): Promise<string>-End-->

**System capability:** SystemCapability.MultimodalAwareness.MetadataBinding

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| encodedImage | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | Image with metadata encoded. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise object, which is used to return the encoded metadata of the image. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [32100001](../errorcode-metadataBinding.md#32100001-file-creation-failed) | Internal handling failed. |
| [32100003](../errorcode-metadataBinding.md#32100003-decoding-failed) | Decode process fail. Possible causes: <br>1. Image is not an encoded Image. <br>2. Image destroyed, decoding failed. |

<!--Del-->
**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { metadataBinding } from '@kit.MultimodalAwarenessKit';
import { BusinessError } from '@kit.BasicServicesKit';

// encodedImage must be obtained from an image processed by the encodeImage API.
let encodedImage: image.PixelMap | undefined = undefined;
let captureMetadata: string = '';
metadataBinding.decodeImage(encodedImage).then((metadata: string) => {
  // Save the metadata parsed from the image to the captureMetadata variable for later use.
  captureMetadata = metadata;
}).catch((error: BusinessError) => {
  console.error(`Failed to decode image. Code: ${error.code}, message: ${error.message}`);
});
```

<!--DelEnd-->
