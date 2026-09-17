# convertToPixelMap

## Modules to Import

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## convertToPixelMap

```TypeScript
function convertToPixelMap(pixelmap: PixelMap): image.PixelMap
```

Creates a image PixelMap from sendable image PixelMap.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pixelmap | [PixelMap](arkts-image-sendableimage-pixelmap-i.md) | Yes | the src pixelmap. |

**Return value:**

| Type | Description |
| --- | --- |
| [image.PixelMap](arkts-image-image-pixelmap-i.md) | Returns the instance if the operation is successful. Otherwise, an exception will be thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | If the image parameter invalid. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980104](../errorcode-image.md#62980104-image-initialization-error) | Failed to initialize the internal object. |

**Examples**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { image } from '@kit.ImageKit';

async function ConvertToPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to create. The value is calculated as follows: height * width *4.
  let opts: image.InitializationOptions = { editable: true, pixelFormat: 3, size: { height: 4, width: 6 } }
  let sendablePixelMap : sendableImage.PixelMap = sendableImage.createPixelMapSync(color, opts);
  let pixelMap : image.PixelMap = sendableImage.convertToPixelMap(sendablePixelMap);
  return pixelMap;
}
```
