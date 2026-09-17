# createPixelMap

## Modules to Import

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## createPixelMap

```TypeScript
function createPixelMap(colors: ArrayBuffer, options: image.InitializationOptions): Promise<PixelMap>
```

Create PixelMap by data buffer.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colors | ArrayBuffer | Yes | The image color buffer. |
| options | [image.InitializationOptions](arkts-image-image-initializationoptions-i.md) | Yes | Initialization options for PixelMap. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-sendableimage-pixelmap-i.md)&gt; | A Promise instance used to return the PixelMap object. |

**Examples**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMap() {
    const color: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to create. The value is calculated as follows: height * width *4.
    let opts: image.InitializationOptions = { editable: true, pixelFormat: 3, size: { height: 4, width: 6 } }
    sendableImage.createPixelMap(color, opts).then((pixelMap: sendableImage.PixelMap) => {
        console.info('Succeeded in creating pixelmap.');
    }).catch((error: BusinessError) => {
        console.error(`Failed to create pixelmap. code is ${error.code}, message is ${error.message}`);
    })
}
```
