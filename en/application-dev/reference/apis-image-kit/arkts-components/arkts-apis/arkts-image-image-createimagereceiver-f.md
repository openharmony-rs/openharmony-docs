# createImageReceiver

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## createImageReceiver

```TypeScript
function createImageReceiver(width: number, height: number, format: number, capacity: number): ImageReceiver
```

Creates an ImageReceiver instance by specifying the image width, height, format, and capacity. The ImageReceiver acts as the receiver and consumer of images. Its parameter properties do not actually affect the received images. The configuration of image properties should be done on the sending side (the producer), such as when creating a camera preview stream with [createPreviewOutput](../../apis-camera-kit/arkts-apis/arkts-camera-camera-cameramanager-i.md#createpreviewoutput). Images occupy a large amount of memory. When you finish using an ImageReceiver instance, call [release](arkts-image-image-imagereceiver-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [createImageReceiver](arkts-image-image-createimagereceiver-f.md)(size: Size, format: ImageFormat, capacity: number)

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | number | Yes | Default image width, in px. This parameter does not affect the width of the received image. The actual width is determined by the producer, for example, the camera. |
| height | number | Yes | Default image height, in px. This parameter does not affect the height of the received image. The actual height is determined by the producer, for example, the camera. |
| format | number | Yes | Image format, which is a constant of [ImageFormat](arkts-image-image-imageformat-e.md). (Currently, only **ImageFormat:JPEG** is supported. The format actually returned is determined by the producer, for example, camera.) |
| capacity | number | Yes | Maximum number of images that can be accessed at the same time. This parameter is used only as an expected value. The actual capacity is determined by the device hardware. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageReceiver](arkts-image-image-imagereceiver-i.md) | ImageReceiver instance. |

**Examples**

```TypeScript
let receiver: image.ImageReceiver = image.createImageReceiver(8192, 8192, image.ImageFormat.JPEG, 8);
```


<a id="createimagereceiver-1"></a>

## createImageReceiver

```TypeScript
function createImageReceiver(size: Size, format: ImageFormat, capacity: number): ImageReceiver
```

Creates an ImageReceiver instance by specifying the image size, format, and capacity. The ImageReceiver acts as the receiver and consumer of images. Its parameter properties do not actually affect the received images. The configuration of image properties should be done on the sending side (the producer), such as when creating a camera preview stream with [createPreviewOutput](../../apis-camera-kit/arkts-apis/arkts-camera-camera-cameramanager-i.md#createpreviewoutput). Images occupy a large amount of memory. When you finish using an ImageReceiver instance, call [release](arkts-image-image-imagereceiver-i.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | Size | Yes | Default size of the image. This parameter does not affect the size of the received image. The actual returned size is determined by the producer, for example, the camera. |
| format | [ImageFormat](arkts-image-image-imageformat-e.md) | Yes | Image format, which is a constant of [ImageFormat](arkts-image-image-imageformat-e.md). (Currently, only **ImageFormat:JPEG** is supported. The format actually returned is determined by the producer, for example, camera.) |
| capacity | number | Yes | Maximum number of images that can be accessed at the same time. This parameter is used only as an expected value. The actual capacity is determined by the device hardware. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageReceiver](arkts-image-image-imagereceiver-i.md) | ImageReceiver instance. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types; |

**Examples**

```TypeScript
let size: image.Size = {
  height: 8192,
  width: 8192
}
let receiver: image.ImageReceiver = image.createImageReceiver(size, image.ImageFormat.JPEG, 8);
```


<a id="createimagereceiver-3"></a>

## createImageReceiver

```TypeScript
function createImageReceiver(options?: ImageReceiverOptions): ImageReceiver | undefined
```

Creates an ImageReceiver instance.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImageReceiver

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ImageReceiverOptions](arkts-image-image-imagereceiveroptions-i.md) | No | Initialization options for the ImageReceiver. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageReceiver](arkts-image-image-imagereceiver-i.md) &#124; undefined | ImageReceiver instance created. If the operation fails, undefined is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7900201](../errorcode-image.md#7900201-invalid-parameter) | Invalid parameter. |

**Examples**

```TypeScript
let options: image.ImageReceiverOptions = {
  size: { width: 480, height: 480 },
  capacity: 3
}
let receiver: image.ImageReceiver | undefined = image.createImageReceiver(options);
```
