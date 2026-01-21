# Interface (Image)
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @liyang_bryan-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

The **Image** class is used to obtain image content.

An Image instance is returned when [readNextImage](arkts-apis-image-ImageReceiver.md#readnextimage9) and [readLatestImage](arkts-apis-image-ImageReceiver.md#readlatestimage9) are called.

Image properties are set only when the Image instance is created and cannot be changed later. These properties do not affect the actual image content. You should always rely on the properties written by the image producer, that is, the content actually sent to the [ImageReceiver](./arkts-apis-image-ImageReceiver.md) by the data source.

Images occupy a large amount of memory. When you finish using an Image instance, call [release](#release9) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 9.

## Modules to Import

```ts
import { image } from '@kit.ImageKit';
```

## Properties

**System capability**: SystemCapability.Multimedia.Image.Core

| Name    | Type              | Read Only| Optional| Description                                              |
| -------- | ------------------ | ---- | ---- | -------------------------------------------------- |
| clipRect<sup>9+</sup> | [Region](arkts-apis-image-i.md#region8) | No  | No  | Image area to be cropped.                                |
| size<sup>9+</sup>     | [Size](arkts-apis-image-i.md#size)      | Yes  | No  | Image size.<br>If the Image object stores camera preview stream data (YUV image data), the width and height in **size** reflect the dimensions of the YUV image.<br>If the Image object stores camera capture stream data (JPEG image data), given that it is an encoded file, the width in **size** is the size of the JPEG file, while the height is set to **1**.<br>The type of data stored in the Image object depends on whether the application passes the surface ID in the receiver to a previewOutput or captureOutput object of the camera.<br>For details about the best practices of camera preview and photo capture, see [Dual-Channel Preview (ArkTS)](../../media/camera/camera-dual-channel-preview.md) and [Photo Capture Sample (ArkTS)](../../media/camera/camera-shooting-case.md).|
| format<sup>9+</sup>    | number             | Yes  | No  | Image format. For details, see [OH_NativeBuffer_Format](../apis-arkgraphics2d/capi-buffer-common-h.md#oh_nativebuffer_format).|
| timestamp<sup>12+</sup> | number         | Yes     | No  | Image timestamp. Timestamps, measured in nanoseconds, are usually monotonically increasing. The specific meaning and baseline of these timestamps are determined by the image producer, which is the camera in the camera preview and photo scenarios. As a result, images from different producers may carry timestamps with distinct meanings and baselines, making direct comparison between them infeasible. To obtain the generation time of a photo, you can use [getImageProperty](arkts-apis-image-ImageSource.md#getimageproperty11) to read the related Exif information.|

## getComponent<sup>9+</sup>

getComponent(componentType: ComponentType, callback: AsyncCallback\<Component>): void

Obtains the component buffer from the Image instance based on the color component type. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name       | Type                                   | Mandatory| Description                |
| ------------- | --------------------------------------- | ---- | -------------------- |
| componentType | [ComponentType](arkts-apis-image-e.md#componenttype9)        | Yes  | Color component type of the image. (Currently, only **ComponentType:JPEG** is supported. The format actually returned is determined by the producer, for example, camera.)   |
| callback      | AsyncCallback<[Component](arkts-apis-image-i.md#component9)> | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the component buffer obtained; otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetComponent(img : image.Image) {
  img.getComponent(image.ComponentType.JPEG, (err: BusinessError, component: image.Component) => {
    if (err) {
      console.error(`Failed to get the component.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in getting component.');
    }
  })
}
```

## getComponent<sup>9+</sup>

getComponent(componentType: ComponentType): Promise\<Component>

Obtains the component buffer from the Image instance based on the color component type. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name       | Type                            | Mandatory| Description            |
| ------------- | -------------------------------- | ---- | ---------------- |
| componentType | [ComponentType](arkts-apis-image-e.md#componenttype9) | Yes  | Color component type of the image. (Currently, only **ComponentType:JPEG** is supported. The format actually returned is determined by the producer, for example, camera.)|

**Return value**

| Type                             | Description                             |
| --------------------------------- | --------------------------------- |
| Promise<[Component](arkts-apis-image-i.md#component9)> | Promise used to return the component buffer.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetComponent(img : image.Image) {
  img.getComponent(image.ComponentType.JPEG).then((component: image.Component) => {
    console.info('Succeeded in getting component.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to get the component.code ${error.code},message is ${error.message}`);
  })
}
```

## release<sup>9+</sup>

release(callback: AsyncCallback\<void>): void

Releases this Image instance. This API uses an asynchronous callback to return the result.

The corresponding resources must be released before another image arrives.

Images occupy a large amount of memory. When you finish using an Image instance, call this API to free the memory promptly.

Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name  | Type                | Mandatory| Description          |
| -------- | -------------------- | ---- | -------------- |
| callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(img : image.Image) {
  img.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release the image instance.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in releasing the image instance.');
    }
  })
}
```

## release<sup>9+</sup>

release(): Promise\<void>

Releases this Image instance. This API uses a promise to return the result.

The corresponding resources must be released before another image arrives.

Images occupy a large amount of memory. When you finish using an Image instance, call this API to free the memory promptly.

Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.Core

**Return value**

| Type          | Description                 |
| -------------- | --------------------- |
| Promise\<void> |  Promise that returns no value.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(img : image.Image) {
  img.release().then(() => {
    console.info('Succeeded in releasing the image instance.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release the image instance.code ${error.code},message is ${error.message}`);
  })
}
```
<!--no_check-->