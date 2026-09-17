# createPixelMapFromSurface

## Modules to Import

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## createPixelMapFromSurface

```TypeScript
function createPixelMapFromSurface(surfaceId: string, region: image.Region): Promise<PixelMap>
```

Creates a PixelMap object from surface id.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| surfaceId | string | Yes | surface id. |
| region | [image.Region](arkts-image-image-region-i.md) | Yes | The region to surface. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-sendableimage-pixelmap-i.md)&gt; | Returns the instance if the operation is successful. Otherwise, an exception will be thrown. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [62980115](../errorcode-image.md#62980115-invalid-image-parameter) | If the image parameter invalid. |
| [62980105](../errorcode-image.md#62980105-failure-in-obtaining-image-data) | Failed to get the data. |
| [62980178](../errorcode-image.md#62980178-failure-in-creating-a-pixelmap) | Failed to create the PixelMap. |

**Examples**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMapFromSurface(surfaceId: string) {
  let region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  sendableImage.createPixelMapFromSurface(surfaceId, region).then(() => {
    console.info('Succeeded in creating pixelmap from Surface');
  }).catch((error: BusinessError) => {
    console.error(`Failed to create pixelmap. code is ${error.code}, message is ${error.message}`);
  });
}
```
