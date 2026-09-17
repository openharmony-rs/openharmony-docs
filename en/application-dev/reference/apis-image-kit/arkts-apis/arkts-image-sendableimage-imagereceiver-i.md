# ImageReceiver

Image receiver class. You can use it to obtain the surface ID of a component, read the latest image and the next image, and release **ImageReceiver** instances.

Before calling any APIs in ImageReceiver, you must create an ImageReceiver instance.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

## Modules to Import

```TypeScript
import { sendableImage } from '@kit.ImageKit';
```

## getReceivingSurfaceId

```TypeScript
getReceivingSurfaceId(): Promise<string>
```

Obtains a surface ID for the camera or other components. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Asynchronously returns the surface ID. |

**Examples**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

async function GetReceivingSurfaceId() {
  let size: image.Size = {
    height: 8192,
    width: 8
  }
  let receiver: sendableImage.ImageReceiver = sendableImage.createImageReceiver(size, image.ImageFormat.JPEG, 8);
  receiver.getReceivingSurfaceId().then((id: string) => {
    console.info('Succeeded in getting the ReceivingSurfaceId.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to get the ReceivingSurfaceId.code ${error.code}, message is ${error.message}`);
  })
}
```

## on('imageArrival')

```TypeScript
on(type: 'imageArrival', callback: AsyncCallback<void>): void
```

Listens for image arrival events. This API uses an asynchronous callback to return the result.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'imageArrival' | Yes | Type of event to listen for. The value is fixed at **'imageArrival'**, which is triggered when an image is received. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback invoked for the event. |

**Examples**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { image } from '@kit.ImageKit';

async function On() {
  let size: image.Size = {
    height: 8192,
    width: 8
  }
  let receiver: sendableImage.ImageReceiver = sendableImage.createImageReceiver(size, image.ImageFormat.JPEG, 8);
  receiver.on('imageArrival', () => {
    // Implement the callback logic when an image is received.
  })
}
```

## readLatestImage

```TypeScript
readLatestImage(): Promise<Image>
```

Reads the latest image from the ImageReceiver instance. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API can be called to receive data only after the [on](#onimagearrival) callback is
> triggered. When the [Image](arkts-image-sendableimage-imagesource-i.md) object returned by this API is no longer needed,
> call [release](arkts-image-sendableimage-pixelmap-i.md#release) to release the object. New data can be received only after
> the release.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Image](arkts-image-sendableimage-image-i.md)&gt; | Promise used to return the latest image. |

**Examples**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

async function ReadLatestImage() {
  let size: image.Size = {
    height: 8192,
    width: 8
  }
  let receiver: sendableImage.ImageReceiver = sendableImage.createImageReceiver(size, image.ImageFormat.JPEG, 8);
  receiver.readLatestImage().then((img: sendableImage.Image) => {
    console.info('Succeeded in reading the latest image.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to read the latest image. Code: ${error.code}, message: ${error.message}.`);
  })
}
```

## readNextImage

```TypeScript
readNextImage(): Promise<Image>
```

Reads the next image from the ImageReceiver instance. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API can be called to receive data only after the [on](#onimagearrival) callback is
> triggered. When the [Image](arkts-image-sendableimage-imagesource-i.md) object returned by this API is no longer needed,
> call [release](arkts-image-sendableimage-pixelmap-i.md#release) to release the object. New data can be received only after
> the release.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Image](arkts-image-sendableimage-image-i.md)&gt; | Promise used to return the next image. |

**Examples**

```TypeScript
import { sendableImage } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { image } from '@kit.ImageKit';

async function ReadNextImage() {
  let size: image.Size = {
    height: 8192,
    width: 8
  }
  let receiver: sendableImage.ImageReceiver = sendableImage.createImageReceiver(size, image.ImageFormat.JPEG, 8);
  receiver.readNextImage().then((img: sendableImage.Image) => {
    console.info('Succeeded in reading the next image.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to read the next image. Code: ${error.code}, message: ${error.message}.`);
  })
}
```

## release

```TypeScript
release(): Promise<void>
```

Releases this ImageReceiver instance. This API uses a promise to return the result. Images occupy a large amount of memory. When you finish using an ImageReceiver instance, call this API to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

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
  receiver.release().then(() => {
    console.info('Succeeded in releasing an image receiver.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release an image receiver. Code: ${error.code}, message: ${error.message}.`);
  })
}
```

## capacity

```TypeScript
readonly capacity: number
```

Maximum number of images that can be accessed at the same time. This parameter is used only as an expected value.

The actual capacity is determined by the device hardware.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

## format

```TypeScript
readonly format: image.ImageFormat
```

Image format.

**Type:** [image.ImageFormat](arkts-image-image-imageformat-e.md)

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

## size

```TypeScript
readonly size: image.Size
```

Image size.

**Type:** [image.Size](arkts-image-image-size-i.md)

**Since:** 12

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver
