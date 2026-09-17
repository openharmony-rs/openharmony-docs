# ImageReceiver

The **ImageReceiver** class provides APIs to obtain the surface ID of a component, read the latest image, read the next image, and release the ImageReceiver instance. The ImageReceiver acts as the receiver and consumer of images. Its parameter properties do not actually affect the received images. The configuration of image properties should be done on the sending side (the producer), such as when creating a camera preview stream with [createPreviewOutput](../../apis-camera-kit/arkts-apis/arkts-camera-camera-cameramanager-i.md#createpreviewoutput). Before calling any APIs in ImageReceiver, you must use [image.createImageReceiver](arkts-image-image-createimagereceiver-f.md) to create an ImageReceiver instance. Since API version 23, you are advised to use [image.createImageReceiver](arkts-image-image-createimagereceiver-f.md) to create an **ImageReceiver** instance based on the passed [ImageReceiverOptions](arkts-image-image-imagereceiveroptions-i.md). Images occupy a large amount of memory. When you finish using an ImageReceiver instance, call [release](#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## getReceivingSurfaceId

```TypeScript
getReceivingSurfaceId(callback: AsyncCallback<string>): void
```

Obtains a surface ID for the camera or other components. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the surface ID obtained. Otherwise, **err** is an error object. |

## getReceivingSurfaceId

```TypeScript
getReceivingSurfaceId(): Promise<string>
```

Obtains a surface ID for the camera or other components. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the surface ID. |

## off('imageArrival')

```TypeScript
off(type: 'imageArrival', callback?: AsyncCallback<void>): void
```

Unregisters the callback function that is triggered when the buffer is released. This API uses an asynchronous callback to return the result.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'imageArrival' | Yes | Type of event, which is **'imageArrival'**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | No | Callback to unregister. |

## on('imageArrival')

```TypeScript
on(type: 'imageArrival', callback: AsyncCallback<void>): void
```

Listens for image arrival events. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'imageArrival' | Yes | Type of event to listen for. The value is fixed at **'imageArrival'**, which is triggered when an image is received. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

## readLatestImage

```TypeScript
readLatestImage(callback: AsyncCallback<Image>): void
```

Reads the latest image from the ImageReceiver instance. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API can be called to receive data only after the
> [on](#onimagearrival) callback is triggered.
> When the [Image](arkts-image-image-image-i.md) object returned by this API is no longer needed, call
> [release](arkts-image-image-image-i.md#release) to release the
> object. New data can be received only after the release.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Image](arkts-image-image-image-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the latest image obtained; otherwise, **err** is an error object. |

## readLatestImage

```TypeScript
readLatestImage(): Promise<Image>
```

Reads the latest image from the ImageReceiver instance. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API can be called to receive data only after the
> [on](#onimagearrival) callback is triggered.
> When the [Image](arkts-image-image-image-i.md) object returned by this API is no longer needed, call
> [release](arkts-image-image-image-i.md#release) to release the
> object. New data can be received only after the release.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Image](arkts-image-image-image-i.md)&gt; | Promise used to return the latest image. |

## readNextImage

```TypeScript
readNextImage(callback: AsyncCallback<Image>): void
```

Reads the next image from the ImageReceiver instance. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API can be called to receive data only after the
> [on](#onimagearrival) callback is triggered.
> When the [Image](arkts-image-image-image-i.md) object returned by this API is no longer needed, call
> [release](arkts-image-image-image-i.md#release) to release the
> object. New data can be received only after the release.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Image](arkts-image-image-image-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the next image obtained. Otherwise, **err** is an error object. |

## readNextImage

```TypeScript
readNextImage(): Promise<Image>
```

Reads the next image from the ImageReceiver instance. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API can be called to receive data only after the
> [on](#onimagearrival) callback is triggered.
> When the [Image](arkts-image-image-image-i.md) object returned by this API is no longer needed, call
> [release](arkts-image-image-image-i.md#release) to release the
> object. New data can be received only after the release.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Image](arkts-image-image-image-i.md)&gt; | Promise used to return the next image. |

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Releases this ImageReceiver instance. This API uses an asynchronous callback to return the result.

Images occupy a large amount of memory. When you finish using an ImageReceiver instance, call this API to free the memory promptly.

Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

## release

```TypeScript
release(): Promise<void>
```

Releases this ImageReceiver instance. This API uses a promise to return the result.

Images occupy a large amount of memory. When you finish using an ImageReceiver instance, call this API to free the memory promptly.

Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

## setMemoryName

```TypeScript
setMemoryName(name: string): void
```

Sets the memory name for the ImageReceiver instance. This API returns the result synchronously.

Only visible ASCII characters are supported. Spaces, newlines, tabs, and other control characters will be filtered out. If the filtered result consists entirely of digits, a prefix "ImageReceiver:" will be automatically prepended.The length of name must not exceed 256 bytes.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Memory name to set.<br>The maximum length is 256. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7900201](../errorcode-image.md#7900201-invalid-parameter) | Invalid parameter. Possible causes: &lt;ol&gt;&lt;li&gt;Name is empty.&lt;/li&gt; &lt;li&gt;Name contains no visible characters after filtering.&lt;/li&gt; &lt;li&gt;The length of name exceeds 256 bytes.&lt;/li&gt; &lt;li&gt;Ensure the name parameter contains visible ASCII characters.&lt;/li&gt;&lt;/ol&gt; |

## capacity

```TypeScript
readonly capacity: number
```

Maximum number of images that can be accessed at the same time. This parameter is used only as an expected value. The actual capacity is determined by the device hardware.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

## format

```TypeScript
readonly format: ImageFormat
```

Image format. The value is an enum value of [ImageFormat](arkts-image-image-imageformat-e.md). (Currently, only **ImageFormat:JPEG** is supported. The format actually returned depends on the producer, for example, camera.)

**Type:** [ImageFormat](arkts-image-image-imageformat-e.md)

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

## size

```TypeScript
readonly size: Size
```

Image size. This parameter does not affect the size of the received image. The actual returned size is determined by the producer, for example, the camera.

**Type:** Size

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver
