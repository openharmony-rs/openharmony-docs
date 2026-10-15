# Image

```TypeScript
interface Image
```

The **Image** class is used to obtain image content.

An Image instance is returned when [readNextImage](arkts-image-image-imagereceiver-i.md#readnextimage1) and [readLatestImage](arkts-image-image-imagereceiver-i.md#readlatestimage1) are called.

Image properties are initialized only during image creation and cannot be changed later. These properties do not affect the actual image content. You should always rely on the properties written by the image producer, that is, the content actually sent to the [ImageReceiver](arkts-image-image-imagereceiver-i.md) by the data source. Images occupy a large amount of memory. When you finish using an Image instance, call [release](#release1) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 9

<!--Device-image-interface Image--><!--Device-image-interface Image-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## getBufferData

```TypeScript
getBufferData(): ImageBufferData | null
```

Obtains ImageBufferData from an image.

> **NOTE:** 
> 
> **byteBuffer** in **ImageBufferData** is a shallow copy of the internal buffer. When the lifecycle of an image
> ends, do not perform any operations on **byteBuffer**, as this may lead to undefined behavior.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-Image-getBufferData(): ImageBufferData | null--><!--Device-Image-getBufferData(): ImageBufferData | null-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ImageBufferData](arkts-image-image-imagebufferdata-i.md) &#124; null | Struct that encapsulates the image data buffer. If no struct is obtained, **null** is returned. |

**Examples**

```TypeScript
function GetBufferData(img: image.Image) {
  const bufferData = img.getBufferData();
  if (bufferData == null) {
    console.error('Failed to get the bufferData: bufferData is null.');
    return;
  }
  console.info('Succeeded in getting bufferData.');
}
```

<a id="getcomponent1"></a>

## getComponent

```TypeScript
getComponent(componentType: ComponentType, callback: AsyncCallback<Component>): void
```

Obtains the component buffer from the Image instance based on the color component type. This API uses an asynchronous callback to return the result.

**Since:** 9

<!--Device-Image-getComponent(componentType: ComponentType, callback: AsyncCallback<Component>): void--><!--Device-Image-getComponent(componentType: ComponentType, callback: AsyncCallback<Component>): void-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| componentType | [ComponentType](arkts-image-image-componenttype-e.md) | Yes | Component type. (Currently, only **ComponentType:JPEG** is supported. The actual format is determined by the producer, for example, camera.) |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Component](arkts-image-image-component-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the component buffer obtained; otherwise, **err** is an error object. |

**Examples**

```TypeScript
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

<a id="getcomponent2"></a>

## getComponent

```TypeScript
getComponent(componentType: ComponentType): Promise<Component>
```

Obtains the component buffer from the Image instance based on the color component type. This API uses a promise to return the result.

**Since:** 9

<!--Device-Image-getComponent(componentType: ComponentType): Promise<Component>--><!--Device-Image-getComponent(componentType: ComponentType): Promise<Component>-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| componentType | [ComponentType](arkts-image-image-componenttype-e.md) | Yes | Component type. (Currently, only **ComponentType:JPEG** is supported. The actual format is determined by the producer, for example, camera.) |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Component](arkts-image-image-component-i.md)&gt; | Promise used to return the component buffer. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetComponent(img : image.Image) {
  img.getComponent(image.ComponentType.JPEG).then((component: image.Component) => {
    console.info('Succeeded in getting component.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to get the component.code ${error.code},message is ${error.message}`);
  })
}
```

## getMetadata

```TypeScript
getMetadata(key: HdrMetadataKey): HdrMetadataValue | null
```

Obtains the HDR metadata from an image based on the HDR metadata type.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-Image-getMetadata(key: HdrMetadataKey): HdrMetadataValue | null--><!--Device-Image-getMetadata(key: HdrMetadataKey): HdrMetadataValue | null-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | [HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md) | Yes | HDR metadata key. |

**Return value:**

| Type | Description |
| --- | --- |
| [HdrMetadataValue](arkts-image-image-hdrmetadatavalue-t.md) &#124; null | Value of the HDR metadata key. If the image does not have HDR metadata, **null** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-invalid-parameter) | Invalid parameter. |
| [7600302](../errorcode-image.md#7600302-memory-copy-failure) | Memory copy failed. |

**Examples**

```TypeScript
async function GetMetadata(img : image.Image) {
  try {
    let staticMetadata = img.getMetadata(image.HdrMetadataKey.HDR_STATIC_METADATA);
    console.info(`getMetadata:${staticMetadata}`);
  } catch (err) {
    console.error('Failed to getMetadata.' + err);
  }
}
```

<a id="release1"></a>

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Releases this Image instance. This API uses an asynchronous callback to return the result.

The corresponding resources must be released before another image arrives.

Images occupy a large amount of memory. When you finish using an Image instance, call this API to free the memory promptly.

Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 9

<!--Device-Image-release(callback: AsyncCallback<void>): void--><!--Device-Image-release(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
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

<a id="release2"></a>

## release

```TypeScript
release(): Promise<void>
```

Releases this Image instance. This API uses a promise to return the result.

The corresponding resources must be released before another image arrives.

Images occupy a large amount of memory. When you finish using an Image instance, call this API to free the memory promptly.

Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 9

<!--Device-Image-release(): Promise<void>--><!--Device-Image-release(): Promise<void>-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(img : image.Image) {
  img.release().then(() => {
    console.info('Succeeded in releasing the image instance.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release the image instance.code ${error.code},message is ${error.message}`);
  })
}
```

## clipRect

```TypeScript
clipRect: Region
```

Image area to be cropped.

**Type:** [Region](arkts-image-image-region-i.md)

**Since:** 9

<!--Device-Image-clipRect: Region--><!--Device-Image-clipRect: Region-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

## colorSpace

```TypeScript
readonly colorSpace: colorSpaceManager.ColorSpace
```

Color space of the image.

**Type:** [colorSpaceManager.ColorSpace](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-colorspacemanager-colorspace-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-Image-readonly colorSpace: colorSpaceManager.ColorSpace--><!--Device-Image-readonly colorSpace: colorSpaceManager.ColorSpace-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

## format

```TypeScript
readonly format: number
```

Image format. For details, see [OH_NativeBuffer_Format](../../../reference/apis-arkgraphics2d/c-apis/capi-buffer-common-h.md#oh_nativebuffer_format).

**Type:** number

**Since:** 9

<!--Device-Image-readonly format: int--><!--Device-Image-readonly format: int-End-->

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

**Since:** 9

<!--Device-Image-readonly size: Size--><!--Device-Image-readonly size: Size-End-->

**System capability:** SystemCapability.Multimedia.Image.Core

## timestamp

```TypeScript
readonly timestamp: number
```

Image timestamp. Timestamps, measured in nanoseconds, are usually monotonically increasing. The specific meaning and baseline of these timestamps are determined by the image producer, which is the camera in the camera preview and photo scenarios. As a result, images from different producers may carry timestamps with distinct meanings and baselines, making direct comparison between them infeasible. To obtain the generation time of a photo, you can use [getImageProperty](arkts-image-image-imagesource-i.md#getimageproperty1) to read the related Exif information.

**Type:** number

**Since:** 12

<!--Device-Image-readonly timestamp: long--><!--Device-Image-readonly timestamp: long-End-->

**System capability:** SystemCapability.Multimedia.Image.Core
