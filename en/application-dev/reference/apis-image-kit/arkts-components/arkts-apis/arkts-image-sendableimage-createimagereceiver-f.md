# createImageReceiver

## Modules to Import

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## createImageReceiver

```TypeScript
function createImageReceiver(size: image.Size, format: image.ImageFormat, capacity: number): ImageReceiver
```

Creates an ImageReceiver instance based on the specified image size, format, and capacity.

Images occupy a large amount of memory. When you finish using an ImageReceiver instance, call [release](arkts-image-sendableimage-pixelmap-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | [image.Size](arkts-image-image-size-i.md) | Yes | Default size of the image. |
| format | [image.ImageFormat](arkts-image-image-imageformat-e.md) | Yes | Image format, which is a constant of **image.ImageFormat**. (Currently, only **ImageFormat:JPEG** is supported.) |
| capacity | number | Yes | Maximum number of images that can be accessed at the same time. This parameter is used only as an expected value. The actual capacity is determined by the device hardware. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageReceiver](arkts-image-sendableimage-imagereceiver-i.md) | ImageReceiver instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | The parameter check failed. |

**Examples**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { image } from '@kit.ImageKit';

async function CreateImageReceiver() {
    let size: image.Size = {
        height: 8192,
        width: 8
    } 
    let receiver: sendableImage.ImageReceiver = sendableImage.createImageReceiver(size, image.ImageFormat.JPEG, 8);
}
```
