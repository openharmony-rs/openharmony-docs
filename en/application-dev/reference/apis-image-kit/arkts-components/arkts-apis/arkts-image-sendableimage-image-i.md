# Image

```TypeScript
interface Image extends lang.ISendable
```

Provides APIs for basic image operations, including obtaining image information and reading and writing image data.

An Image instance is returned when [readNextImage](arkts-image-sendableimage-imagereceiver-i.md#readnextimage) and [readLatestImage](arkts-image-sendableimage-imagereceiver-i.md#readlatestimage) are called. This class inherits from [ISendable](../../../arkts-utils/arkts-sendable.md#isendable).

Images occupy a large amount of memory. When you finish using an Image instance, call [release](arkts-image-sendableimage-pixelmap-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Inheritance/Implementation:** Image extends [lang.ISendable](../../apis-arkts/arkts-apis/arkts-arkts-lang-isendable-i.md)

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## getComponent

```TypeScript
getComponent(componentType: image.ComponentType): Promise<image.Component>
```

Obtains the component buffer from the Image instance based on the color component type. This API uses a promise to return the result. The thread that runs **getComponent** is insecure.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| componentType | [image.ComponentType](arkts-image-image-componenttype-e.md) | Yes | Color component type of the image. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[image.Component](arkts-image-image-component-i.md)&gt; | Promise used to return the component buffer. |

**Examples**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

async function GetComponent() {
  let size: image.Size = {
    height: 8192,
    width: 8
  }
  let receiver: sendableImage.ImageReceiver = sendableImage.createImageReceiver(size, image.ImageFormat.JPEG, 8);
  let img = await receiver.readNextImage();
  img.getComponent(image.ComponentType.JPEG).then((component: image.Component) => {
    console.info('Succeeded in getting an image component.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to get an image component. Code: ${error.code}, message: ${error.message}.`);
  })
}
```

## release

```TypeScript
release(): Promise<void>
```

Releases this Image instance. This API uses a promise to return the result.

The corresponding resources must be released before another image arrives.

Images occupy a large amount of memory. When you finish using an Image instance, call this API to free the memory promptly.

Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Examples**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

async function Release() {
  let size: image.Size = {
    height: 8192,
    width: 8
  }
  let receiver: sendableImage.ImageReceiver = sendableImage.createImageReceiver(size, image.ImageFormat.JPEG, 8);
  let img = await receiver.readNextImage();
  img.release().then(() => {
    console.info('Succeeded in releasing an image.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release an image. Code: ${error.code}, message: ${error.message}.`);
  })
}
```

## clipRect

```TypeScript
clipRect: Region
```

Image area to be cropped.

**Type:** [Region](arkts-image-sendableimage-region-i.md)

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## format

```TypeScript
readonly format: number
```

Image format. For details, see [OH_NativeBuffer_Format](../../../reference/apis-arkgraphics2d/c-apis/capi-buffer-common-h.md#oh_nativebuffer_format).

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## size

```TypeScript
readonly size: Size
```

Image size.

If the Image object stores camera preview stream data (YUV image data), the width and height in **size** reflect the dimensions of the YUV image.

If the Image object stores camera capture stream data (JPEG image data), given that it is an encoded file, the width in **size** is the size of the JPEG file, while the height is set to **1**.

The type of data stored in the Image object depends on whether the application passes the surface ID in the receiver to a previewOutput or captureOutput object of the camera.

For details about the best practices of camera preview and photo capture, see [Dual-Channel Preview (ArkTS)](../../../media/camera/camera-dual-channel-preview.md) and [Photo Capture Sample (ArkTS)](../../../media/camera/camera-shooting-case.md).

**Type:** Size

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core

## timestamp

```TypeScript
readonly timestamp: number
```

Image timestamp. Timestamps, measured in nanoseconds, are usually monotonically increasing. The specific meaning and baseline of these timestamps are determined by the image producer, which is the camera in the camera preview and photo scenarios. As a result, images from different producers may carry timestamps with distinct meanings and baselines, making direct comparison between them infeasible. To obtain the generation time of a photo, you can use [getImageProperty](arkts-image-image-imagesource-i.md#getimageproperty) to read the related Exif information.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.Core
