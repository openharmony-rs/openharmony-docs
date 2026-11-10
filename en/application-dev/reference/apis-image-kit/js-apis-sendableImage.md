# @ohos.multimedia.sendableImage (Image Processing Based on Sendable Objects)
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=cc99e5187aa152bc96569f8b87fca412b6552a60 translatedAt=2026-11-10T08:16:19.484Z pushedAt=2026-11-10T11:58:27.583Z nl=1 -->

The module provides APIs for image processing based on the [Sendable](../../arkts-utils/arkts-sendable.md) object. You can use the APIs to create a PixelMap object with specified properties or read pixels of an image (or even in a region of an image).

> **NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { sendableImage } from '@kit.ImageKit';
```

## sendableImage.createPixelMap

createPixelMap(colors: ArrayBuffer, options: image.InitializationOptions): Promise\<PixelMap>

Creates a PixelMap based on pixel data and image properties. The input pixel data is copied and converted to the pixel format specified by [InitializationOptions](arkts-apis-image-i.md#initializationoptions8).pixelFormat, which is used to initialize the pixels of the PixelMap. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> - This API does not support creating a PixelMap in the following pixel formats: RGBA_1010102, YCBCR_P010, YCRCB_P010, and ASTC_4x4.
> - Because an image occupies a large amount of memory, call [release](#release) to free the memory in a timely manner after the PixelMap object is no longer used. Before releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will not be used again.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name | Type                                            | Mandatory| Description                                                            |
| ------- | ------------------------------------------------ | ---- | ---------------------------------------------------------------- |
| colors  | ArrayBuffer                                      | Yes   | Buffer of the image pixel data, used to initialize the pixels of the PixelMap. The pixel data in the buffer must be tightly packed and must not contain memory alignment padding bytes.<br>The pixel format of the buffer must be specified by [InitializationOptions](arkts-apis-image-i.md#initializationoptions8).srcPixelFormat. Otherwise, the default pixel format of the buffer is BGRA_8888.<br>**Note:** The buffer length is: image width * image height * bytes per pixel. |
| options | [image.InitializationOptions](arkts-apis-image-i.md#initializationoptions8) | Yes   | Initialization attributes for creating the image, including the size, pixel format, alpha type, scale mode, and whether the image is editable.<br>**Note:** If the pixel format is specified as ASTC_4x4, the default RGBA_8888 format is used. |

**Return value**

| Type                            | Description                                                                   |
| -------------------------------- | ----------------------------------------------------------------------- |
| Promise\<[PixelMap](#pixelmap)> | Promise object used to return the created PixelMap.<br>If the size of the created PixelMap exceeds the image size that the source pixel data can represent, a PixelMap created based on the image size that the source pixel data can represent is returned.|

**Example**

```ts
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to be created, calculated as: width * height * 4.
  let opts: image.InitializationOptions = {
    size: { height: 4, width: 6 },
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the source pixel data in the buffer.
    pixelFormat: image.PixelMapFormat.BGRA_8888, // Pixel format of the newly created PixelMap.
    editable: true
  };
  sendableImage.createPixelMap(color, opts).then((pixelMap: sendableImage.PixelMap) => {
    console.info('Succeeded in creating the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## sendableImage.createPixelMapSync

createPixelMapSync(colors: ArrayBuffer, options: image.InitializationOptions): PixelMap

Creates a PixelMap based on the pixel data and image properties. The input pixel data is copied and converted to the pixel format specified by [InitializationOptions](arkts-apis-image-i.md#initializationoptions8).pixelFormat, and is used to initialize the pixels of the PixelMap. The result is returned synchronously.

> **NOTE**
>
> - This API does not support creating a PixelMap in the following pixel formats: RGBA_1010102, YCBCR_P010, YCRCB_P010, and ASTC_4x4.
> - Because an image occupies a large amount of memory, call [release](#release) to free the memory in a timely manner after the PixelMap object is no longer used. Before releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will no longer be used.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name                | Type                                                 | Mandatory| Description                                    |
| ---------------------- | ----------------------------------------------------- | ---- | ---------------------------------------- |
| colors  | ArrayBuffer                                      | Yes   | Buffer of the image pixel data, used to initialize the pixels of the PixelMap. The pixel data in the buffer must be tightly packed and must not contain memory alignment padding bytes.<br>The pixel format of the buffer must be specified by [InitializationOptions](arkts-apis-image-i.md#initializationoptions8).srcPixelFormat. Otherwise, the default pixel format of the buffer is BGRA_8888.<br>**Note:** The buffer length is: image width * image height * bytes per pixel. |
| options | [image.InitializationOptions](arkts-apis-image-i.md#initializationoptions8) | Yes   | Initialization attributes for creating the image, including the size, pixel format, alpha type, scale mode, and editability.<br>**Note:** If the pixel format is specified as ASTC_4x4, the default RGBA_8888 format is used. |

**Return value**
| Type                            | Description                 |
| -------------------------------- | --------------------- |
| [PixelMap](#pixelmap) | Returns the created PixelMap object. Throws an exception if the API call fails. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed.|

**Example**

```ts
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapSync() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to be created. The value is width * height * 4.
  let opts: image.InitializationOptions = {
    size: { height: 4, width: 6 },
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the source pixel data in the buffer.
    pixelFormat: image.PixelMapFormat.BGRA_8888, // Pixel format of the newly created PixelMap.
    editable: true
  };
  try {
    let pixelMap: sendableImage.PixelMap = sendableImage.createPixelMapSync(color, opts);
    if (pixelMap == undefined) {
      console.error(`Failed to create the PixelMap.`);
      return;
    }
    console.info('Succeeded in creating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## sendableImage.createPixelMapFromParcel

createPixelMapFromParcel(sequence: rpc.MessageSequence): PixelMap

Deserializes and obtains a PixelMap from a MessageSequence.

> **NOTE**
>
> Because an image occupies a large amount of memory, call [release](#release) to free the memory in a timely manner after the PixelMap object is no longer used. Before releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will no longer be used.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name                | Type                | Mandatory| Description                                    |
| ---------------------- | -------------       | ---- | ---------------------------------------- |
| sequence               | [rpc.MessageSequence](../apis-ipc-kit/js-apis-rpc.md#messagesequence9) | Yes   | MessageSequence that stores the serialized data of the PixelMap.      |

**Return value**

| Type                            | Description                 |
| -------------------------------- | --------------------- |
| [PixelMap](#pixelmap) | Returns the created PixelMap object. Throws an exception if the API call fails. |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 62980096 | Operation failed. |
| 62980097 | IPC error. |
| 62980115 | Invalid input parameter. |
| 62980105 | Failed to get the data. |
| 62980177 | Abnormal API environment. |
| 62980178 | Failed to create the PixelMap. |
| 62980179 | Abnormal buffer size. |
| 62980180 | FD mapping failed. |
| 62980246 | Failed to read the PixelMap. |

**Example**

```ts
// EntryAbility.ets
import { image } from '@kit.ImageKit';
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MySequence implements rpc.Parcelable {
  pixelMap: sendableImage.PixelMap;
  constructor(pixelMap: sendableImage.PixelMap) {
    this.pixelMap = pixelMap;
  }
  marshalling(messageSequence: rpc.MessageSequence) {
    this.pixelMap.marshalling(messageSequence);
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence) {
    try {
      this.pixelMap = sendableImage.createPixelMapFromParcel(messageSequence);
    } catch (e) {
      const err = e as BusinessError;
      console.error(`Failed to create the PixelMap from parcel. Code: ${err.code}, message: ${err.message}`);
      return false;
    }
    return true;
  }
}

async function createPixelMapFromParcel() {
  const color: ArrayBuffer = new ArrayBuffer(96);
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = 0x80;
  }
  let opts: image.InitializationOptions = {
    editable: true,
    pixelFormat: image.PixelMapFormat.BGRA_8888,
    size: { height: 4, width: 6 },
    alphaType: image.AlphaType.UNPREMUL
  };
  const pixelMap: sendableImage.PixelMap | undefined = await sendableImage.createPixelMap(color, opts);
  if (pixelMap != undefined) {
    // Serialize.
    let parcelable: MySequence = new MySequence(pixelMap);
    let data: rpc.MessageSequence = rpc.MessageSequence.create();
    data.writeParcelable(parcelable);

    // Deserialize the RPC to obtain the data.
    let seq: MySequence = new MySequence(pixelMap);
    data.readParcelable(seq);

    // Obtain the PixelMap.
    let newPixelMap = seq.pixelMap;
    if (newPixelMap != undefined) {
      console.info('Succeeded in getting the PixelMap.');
    }
  }
}
```

## sendableImage.createPixelMapFromSurface

createPixelMapFromSurface(surfaceId: string, region: image.Region): Promise\<PixelMap>

Creates a PixelMap object based on the surface ID and region information. The size of the region is specified by [Region](arkts-apis-image-i.md#region8).size. Uses a promise to return the result asynchronously.

> **NOTE**
>
> - On a foldable device, when the fold state changes, the API may fail to create the object because the surface carries a rotation angle. Adjust the width and height passed in based on the rotation angle of the surface. For example, swap the width and height when the rotation angle is 90° or 270°.
> - Because an image occupies a large amount of memory, call [release](#release) to free the memory in a timely manner after the PixelMap object is no longer used. Before releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will not be used again.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name | Type                                            | Mandatory| Description                                                            |
| ------- | ------------------------------------------------ | ---- | ---------------------------------------------------------------- |
| surfaceId              | string              | Yes   | ID of the corresponding surface, which can be obtained through a preview component, for example, the [XComponent](../apis-arkui/arkui-ts/ts-basic-components-xcomponent.md) component. |
| region                 | [image.Region](arkts-apis-image-i.md#region8)  | Yes   | Region of the frame to crop. Only cropping part or all of the frame starting from the upper left corner is supported, that is, x and y in Region must be 0, and the value ranges of width and height in Region.size are [1, preview stream width] and [1, preview stream height], respectively. To crop an arbitrary region, obtain the entire frame first and then use [crop](#crop) to crop the desired region. |

**Return value**
| Type                            | Description                 |
| -------------------------------- | --------------------- |
| Promise\<[PixelMap](#pixelmap)> | Promise used to return the created PixelMap object. An exception is thrown if the API call fails. |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 62980115 | If the image parameter invalid. |
| 62980105 | Failed to get the data. |
| 62980178 | Failed to create the PixelMap. |

**Example**

```ts
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function createPixelMapFromSurface(surfaceId: string) {
  let region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  sendableImage.createPixelMapFromSurface(surfaceId, region).then((pixelMap: sendableImage.PixelMap) => {
    console.info('Succeeded in creating the PixelMap from Surface.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create the PixelMap from Surface. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## sendableImage.convertFromPixelMap

convertFromPixelMap(pixelmap: image.PixelMap): PixelMap

Creates a PixelMap object under **sendableImage** from a PixelMap object under **image**. This API returns the result synchronously. The APIs of the PixelMap object under **image** cannot be called anymore.

> **NOTE**
>
> Because an image occupies a large amount of memory, call [release](#release) to free the memory in a timely manner after the PixelMap object is no longer used. Before releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will not be used again.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name | Type                                            | Mandatory| Description                                                            |
| ------- | ------------------------------------------------ | ---- | ---------------------------------------------------------------- |
| pixelmap | [image.PixelMap](arkts-apis-image-PixelMap.md) | Yes | Non-Sendable PixelMap under image. |

**Return value**
| Type                            | Description                 |
| -------------------------------- | --------------------- |
| [PixelMap](#pixelmap) | Synchronously returns a Sendable PixelMap object on success, and throws an exception on failure. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | If the image parameter invalid. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed.|
| 62980104 | Failed to initialize the internal object.|

**Example**

```ts
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function convertFromPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to be created, with the value of width * height * 4.
  const opts: image.InitializationOptions = { editable: true, pixelFormat: 3, size: { height: 4, width: 6 } };
  let pixelMap: image.PixelMap = image.createPixelMapSync(color, opts);
  try {
    let sendablePixelMap: sendableImage.PixelMap = sendableImage.convertFromPixelMap(pixelMap);
    console.info('Succeeded in converting the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to convert the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## sendableImage.convertToPixelMap

convertToPixelMap(pixelmap: PixelMap): image.PixelMap

Creates a PixelMap object under **image** from a PixelMap object under **sendableImage**. This API returns the result synchronously. The APIs of the PixelMap object under **sendableImage** cannot be called anymore.

> **NOTE**
>
> Because an image occupies a large amount of memory, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory in a timely manner after the PixelMap object is no longer used. Before releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will not be used again.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name | Type                                            | Mandatory| Description                                                            |
| ------- | ------------------------------------------------ | ---- | ---------------------------------------------------------------- |
| pixelmap | [PixelMap](#pixelmap) | Yes  | PixelMap object under **sendableImage**.|

**Return value**
| Type                            | Description                 |
| -------------------------------- | --------------------- |
| [image.PixelMap](arkts-apis-image-PixelMap.md) | Synchronously returns a non-Sendable PixelMap object under image on success, and throws an exception on failure. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | If the image parameter invalid. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed.|
| 62980104 | Failed to initialize the internal object.|

**Example**

```ts
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function convertToPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to be created, calculated as width * height * 4.
  const opts: image.InitializationOptions = { editable: true, pixelFormat: 3, size: { height: 4, width: 6 } };
  let sendablePixelMap: sendableImage.PixelMap = sendableImage.createPixelMapSync(color, opts);
  try {
    let pixelMap: image.PixelMap = sendableImage.convertToPixelMap(sendablePixelMap);
    console.info('Succeeded in converting the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to convert the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## ISendable
type ISendable = lang.ISendable

**ISendable** is the parent type of all sendable types except null and undefined. It does not have any necessary methods or properties.

**System capability**: SystemCapability.Multimedia.Image.Core

| Type               | Description                    |
| ------------------ | ------------------------ |
| [lang.ISendable](../apis-arkts/js-apis-arkts-lang.md#isendable)  | Parent type of all sendable types.               |

## PixelMap

Provides image pixel operations for reading or writing image data and obtaining image information. It also supports image transformation (scaling, translation, rotation, flipping, and cropping), setting opacity, extracting the alpha channel, and setting the color space. It is applicable to scenarios that require pixel-level data operations, such as image processing, image editing, and image display. Before calling the PixelMap APIs, create a PixelMap object by passing in pixel data through [sendableImage.createPixelMap](#sendableimagecreatepixelmap). Currently, the maximum serialization size of a PixelMap is 128 MiB. If the size exceeds this limit, rendering fails. The size of a PixelMap is calculated as follows: width \* height \* bytes per pixel (for details, see [PixelMapFormat](arkts-apis-image-e.md#pixelmapformat7)).

The PixelMap in sendableImage supports the Sendable attribute and can be shared across worker threads. The PixelMap in sendableImage can be converted to and from the PixelMap in image by using [sendableImage.convertToPixelMap](#sendableimageconverttopixelmap). After the conversion, none of the methods of the original object can be called; otherwise, error 501 is reported, indicating that the API cannot be called. When processing a PixelMap across threads, consider the multi-thread race condition.

An image usually occupies a large amount of memory. After a PixelMap object is no longer used, call [release](#release) to free the memory in a timely manner. Before releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will no longer be used.

### Properties

**System capability**: SystemCapability.Multimedia.Image.Core

| Name             | Type   | Read-Only| Optional| Description                      |
| -----------------| ------- | ---- | ---- | -------------------------- |
| isEditable        | boolean | Yes   | No   | Whether the image pixel is editable. The value **true** means editable, and **false** means not editable. When the value is **false**, the image rendering and transmission performance is better.<br>**Atomic service API:** Starting from API version 12, this API is supported in atomic services. |
| isStrideAlignment | boolean | Yes   | No   | Whether the row data of the image is memory-aligned. The value **true** means memory-aligned, with blank padding bytes at the end of each row to meet the alignment requirement (if the data itself already meets the alignment requirement, there are no padding bytes); the value **false** means not memory-aligned, with each row of data tightly arranged and no blank padding bytes at the end. |

### readPixelsToBuffer

readPixelsToBuffer(dst: ArrayBuffer): Promise\<void>

Reads the pixel data of the entire PixelMap and stores it in the buffer according to the pixel format of the PixelMap. This API uses a promise to return the result asynchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name| Type       | Mandatory| Description                                                                                                 |
| ------ | ----------- | ---- | ----------------------------------------------------------------------------------------------------- |
| dst    | ArrayBuffer | Yes   | Destination buffer. The obtained pixel data is copied to this buffer. The pixel format in the buffer is the same as that of the PixelMap, excluding memory alignment padding bytes. The buffer size is obtained by calling [getPixelBytesNumber](#getpixelbytesnumber). |

**Return value**

| Type          | Description                                           |
| -------------- | ----------------------------------------------- |
| Promise\<void> | Promise that returns no value. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsToBuffer(pixelMap: sendableImage.PixelMap) {
  const readBuffer: ArrayBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  pixelMap.readPixelsToBuffer(readBuffer).then(() => {
    console.info('Succeeded in reading image pixel data.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to read image pixel data. Code: ${err.code}, message: ${err.message}`);
  });
}
```

### readPixelsToBufferSync

readPixelsToBufferSync(dst: ArrayBuffer): void

Reads the pixel data of the entire PixelMap and stores it in the buffer according to the pixel format of the PixelMap. This API returns the result synchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name  | Type                | Mandatory| Description                                                                                                 |
| -------- | -------------------- | ---- | ----------------------------------------------------------------------------------------------------- |
| dst      | ArrayBuffer          | Yes   | Target buffer. The obtained pixel data is copied to this buffer. The pixel format in the buffer is the same as that of the PixelMap, without memory alignment padding bytes. The buffer size is obtained by calling the [getPixelBytesNumber](#getpixelbytesnumber) API. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
|  501    | Resource Unavailable. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsToBufferSync(pixelMap: sendableImage.PixelMap) {
  const readBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  try {
    pixelMap.readPixelsToBufferSync(readBuffer);
    console.info('Succeeded in reading image pixel data.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to read image pixel data. Code: ${err.code}, message: ${err.message}`);
  }
}
```

### readPixels

readPixels(area: image.PositionArea): Promise\<void>

Reads the pixel data in the specified region of the PixelMap and stores it in the buffer. If the pixel format of the PixelMap is a YUV type, the data is stored in the buffer according to the pixel format of the PixelMap; otherwise, it is stored in the buffer in the BGRA_8888 format. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> The buffer size required by PositionArea can be calculated by using the following formulas.
>
> - Formula for the RGBA region: number of pixels in the read region (Region.size {width * height}) * 4 (1x R component + 1x G component + 1x B component + 1x A component)
> - Formula for the YUV region: number of pixels in the read region (Region.size {width * height}) * 1.5 (1x Y component + 0.25x U component + 0.25x V component)

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name| Type                          | Mandatory| Description                    |
| ------ | ------------------------------ | ---- | ------------------------ |
| area   | [image.PositionArea](arkts-apis-image-i.md#positionarea7) | Yes   | Region data to read.<br>The region is specified by [PositionArea](arkts-apis-image-i.md#positionarea7).region, and the obtained pixel data is copied to the [PositionArea](arkts-apis-image-i.md#positionarea7).pixels buffer. If the pixel format of the PixelMap is of the YUV type, the obtained pixel data format is the same as that of the PixelMap; otherwise, it is converted to the BGRA_8888 format. |

**Return value**

| Type          | Description                                               |
| :------------- | :-------------------------------------------------- |
| Promise\<void> | Promise that returns no value. |

**Example**

```ts
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsRGBA(pixelMap: sendableImage.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8), // 8 is the size of the pixel buffer to create, calculated as width * height * 4.
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  pixelMap.readPixels(area).then(() => {
    console.info('Succeeded in reading the image data in the area from the specified area.');
    console.info('BGRA data: ', new Uint8Array(area.pixels));
  }).catch((err: BusinessError) => {
    console.error(`Failed to read the image data from the specified area. Code: ${err.code}, message: ${err.message}`);
  });
}

function readPixelsYUV(pixelMap: sendableImage.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(6),  // 6 is the size of the pixel buffer to create, calculated as width * height * 1.5.
    offset: 0,
    stride: 8,
    region: { size: { height: 2, width: 2 }, x: 0, y: 0 }
  };
  pixelMap.readPixels(area).then(() => {
    console.info('Succeeded in reading the image data in the area from the specified area.');
    console.info('YUV data: ', new Uint8Array(area.pixels));
  }).catch((err: BusinessError) => {
    console.error(`Failed to read the image data from the specified area. Code: ${err.code}, message: ${err.message}`);
  });
}
```

### readPixelsSync

readPixelsSync(area: image.PositionArea): void

Reads the pixel data in the specified region of the PixelMap and stores it in the buffer. If the pixel format of the PixelMap is a YUV type, the data is stored in the buffer according to the pixel format of the PixelMap; otherwise, it is stored in the buffer in the BGRA_8888 format. This API returns the result synchronously.

> **NOTE**
>
> The buffer size required by PositionArea can be calculated by using the following formulas.
>
> - Formula for the RGBA region: number of pixels in the read region (Region.size {width * height}) * 4 (1x R component + 1x G component + 1x B component + 1x A component)
> - Formula for the YUV region: number of pixels in the read region (Region.size {width * height}) * 1.5 (1x Y component + 0.25x U component + 0.25x V component)

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name| Type                          | Mandatory| Description                    |
| ------ | ------------------------------ | ---- | ------------------------ |
| area   | [image.PositionArea](arkts-apis-image-i.md#positionarea7) | Yes   | Read region data.<br>The region is specified by [PositionArea](arkts-apis-image-i.md#positionarea7).region, and the obtained pixel data is copied to the [PositionArea](arkts-apis-image-i.md#positionarea7).pixels buffer. If the pixel format of the PixelMap is of the YUV type, the obtained pixel data format is the same as that of the PixelMap; otherwise, it is converted to the BGRA_8888 format. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
|  501    | Resource Unavailable. |

**Example**

```ts
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function readPixelsSync(pixelMap: sendableImage.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8),
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  try {
    pixelMap.readPixelsSync(area);
    console.info('Succeeded in reading the image data from the specified area.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to read the image data from the specified area. Code: ${err.code}, message: ${err.message}`);
  }
}
```

### writePixels

writePixels(area: image.PositionArea): Promise\<void>

Writes the pixel data in the buffer to the specified region of the PixelMap. If the pixel format of the PixelMap is YUV, the data in the buffer is parsed according to the pixel format of the PixelMap; otherwise, it is parsed in the BGRA_8888 format. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> The buffer size required by PositionArea can be calculated using the following formulas.
>
> - RGBA region: number of pixels in the write region (Region.size {width * height}) * 4 (1x R component + 1x G component + 1x B component + 1x A component)
> - YUV region: number of pixels in the write region (Region.size {width * height}) * 1.5 (1x Y component + 0.25x U component + 0.25x V component)

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name| Type                          | Mandatory| Description                |
| ------ | ------------------------------ | ---- | -------------------- |
| area   | [image.PositionArea](arkts-apis-image-i.md#positionarea7) | Yes   | Region data to write.<br>The region is specified by [PositionArea](arkts-apis-image-i.md#positionarea7).region, and the pixel data in the [PositionArea](arkts-apis-image-i.md#positionarea7).pixels buffer is written to this region of the PixelMap. If the pixel format of the PixelMap is of the YUV type, the pixel data format in the buffer must be the same as that of the PixelMap; otherwise, it must be BGRA_8888. |

**Return value**

| Type          | Description                                               |
| :------------- | :-------------------------------------------------- |
| Promise\<void> | Promise that returns no value. |

**Example**

```ts
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function writePixelsRGBA(pixelMap: sendableImage.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8), // 8 is the size of the pixel buffer to be created, which is width * height * 4.
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  let bufferArr: Uint8Array = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  pixelMap.writePixels(area).then(() => {
    console.info('Succeeded in writing pixels into the specified area.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to write pixels into the specified area. Code: ${err.code}, message: ${err.message}`);
  });
}

function writePixelsYUV(pixelMap: sendableImage.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(6), // 6 is the size of the pixel buffer to be created, which is width * height * 1.5.
    offset: 0,
    stride: 8, // When PixelMap is in YUV format, the writePixels function does not use this variable.
    region: { size: { height: 2, width: 2 }, x: 0, y: 0 }
  };
  let bufferArr: Uint8Array = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  pixelMap.writePixels(area).then(() => {
    console.info('Succeeded in writing pixels into the specified area.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to write pixels into the specified area. Code: ${err.code}, message: ${err.message}`);
  });
}
```

### writePixelsSync

writePixelsSync(area: image.PositionArea): void

Writes the pixel data in the buffer to the specified region of the PixelMap. If the pixel format of the PixelMap is YUV, the data in the buffer is parsed according to the pixel format of the PixelMap; otherwise, it is parsed in the BGRA_8888 format. The result is returned synchronously.

> **NOTE**
>
> The buffer size required by PositionArea can be calculated using the following formulas.
>
> - RGBA region: number of pixels in the write region (Region.size {width * height}) * 4 (1x R component + 1x G component + 1x B component + 1x A component)
> - YUV region: number of pixels in the write region (Region.size {width * height}) * 1.5 (1x Y component + 0.25x U component + 0.25x V component)

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name| Type                          | Mandatory| Description                |
| ------ | ------------------------------ | ---- | -------------------- |
| area   | [image.PositionArea](arkts-apis-image-i.md#positionarea7) | Yes   | Region data to write.<br>The region is specified by [PositionArea](arkts-apis-image-i.md#positionarea7).region, and the pixel data in the [PositionArea](arkts-apis-image-i.md#positionarea7).pixels buffer is written to this region of the PixelMap. If the pixel format of the PixelMap is of the YUV type, the pixel data format in the buffer must be the same as that of the PixelMap; otherwise, it must be BGRA_8888. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
|  501    | Resource Unavailable. |

**Example**

```ts
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function writePixelsSync(pixelMap: sendableImage.PixelMap) {
  const area: image.PositionArea = {
    pixels: new ArrayBuffer(8),
    offset: 0,
    stride: 8,
    region: { size: { height: 1, width: 2 }, x: 0, y: 0 }
  };
  let bufferArr: Uint8Array = new Uint8Array(area.pixels);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  try {
    pixelMap.writePixelsSync(area);
    console.info('Succeeded in writing pixels into the specified area.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to write pixels into the specified area. Code: ${err.code}, message: ${err.message}`);
  }
}
```

### writeBufferToPixels

writeBufferToPixels(src: ArrayBuffer): Promise\<void>

Writes the pixel data in the buffer to the entire PixelMap. This API uses a promise to return the result asynchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name| Type       | Mandatory| Description          |
| ------ | ----------- | ---- | -------------- |
| src    | ArrayBuffer | Yes   | Source data buffer. The image pixel data in this buffer will be written to the PixelMap. The pixel data in the buffer must be the pixel data of the entire PixelMap, and the pixel format must be the same as that of the PixelMap, without memory alignment padding bytes. The buffer size can be obtained through [getPixelBytesNumber](#getpixelbytesnumber). |

**Return value**

| Type          | Description                                           |
| -------------- | ----------------------------------------------- |
| Promise\<void> | Promise used to return the result. If the operation fails, an error message is returned.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function writeBufferToPixels(pixelMap: sendableImage.PixelMap) {
  const color: ArrayBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  pixelMap.writeBufferToPixels(color).then(() => {
    console.info('Succeeded in writing data from the buffer to the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to write data from the buffer to the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

### writeBufferToPixelsSync

writeBufferToPixelsSync(src: ArrayBuffer): void

Writes the pixel data in the buffer to the entire PixelMap. The result is returned synchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name| Type       | Mandatory| Description          |
| ------ | ----------- | ---- | -------------- |
| src    | ArrayBuffer | Yes   | Source data buffer. The image pixel data in this buffer will be written to the PixelMap. The pixel data in the buffer must be the pixel data of the entire PixelMap, and the pixel format must be the same as that of the PixelMap, without memory alignment padding bytes. The buffer size can be obtained through [getPixelBytesNumber](#getpixelbytesnumber). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
|  501    | Resource Unavailable. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function writeBufferToPixelsSync(pixelMap: sendableImage.PixelMap) {
  const color: ArrayBuffer = new ArrayBuffer(pixelMap.getPixelBytesNumber());
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = i + 1;
  }
  try {
    pixelMap.writeBufferToPixelsSync(color);
    console.info('Succeeded in writing data from the buffer to the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to write data from the buffer to the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

### getImageInfo

getImageInfo(): Promise\<image.ImageInfo>

Obtains the image information. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Return value**

| Type                             | Description                                                       |
| --------------------------------- | ----------------------------------------------------------- |
| Promise\<[image.ImageInfo](arkts-apis-image-i.md#imageinfo)> | Promise object used to return the image pixel information. |

**Example**

```ts
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function getImageInfo(pixelMap: sendableImage.PixelMap) {
  pixelMap.getImageInfo().then((imageInfo: image.ImageInfo) => {
    console.info(`Succeeded in obtaining information of the PixelMap with size ${imageInfo.size} and pixel format ${imageInfo.pixelFormat}.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to obtain information of the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

### getImageInfoSync

getImageInfoSync(): image.ImageInfo

Obtains the image pixel information. The result is returned synchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Return value**

| Type                             | Description                                                       |
| --------------------------------- | ----------------------------------------------------------- |
| [image.ImageInfo](arkts-apis-image-i.md#imageinfo)           | Image information.                                               |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  501    | Resource Unavailable. |

**Example**

```ts
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function getImageInfoSync(pixelMap: sendableImage.PixelMap) {
  try {
    let imageInfo: image.ImageInfo = pixelMap.getImageInfoSync();
    console.info(`Succeeded in obtaining information of the PixelMap with size ${imageInfo.size} and pixel format ${imageInfo.pixelFormat}.`);
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to obtain information of the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

### getBytesNumberPerRow

getBytesNumberPerRow(): number

Obtains the number of bytes per row of the image.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Return value**

| Type  | Description                |
| ------ | -------------------- |
| number | Number of bytes per row of image pixels. Unit: bytes (Byte). |

**Example**

```ts
function getBytesNumberPerRow(pixelMap: sendableImage.PixelMap) {
  let rowBytes: number = pixelMap.getBytesNumberPerRow();
}
```

### getPixelBytesNumber

getPixelBytesNumber(): number

Obtains the total number of bytes occupied by all image pixels, excluding memory alignment padding bytes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Return value**

| Type  | Description                |
| ------ | -------------------- |
| number | Total number of bytes of the image pixel. Unit: bytes (Byte). |

**Example**

```ts
function getPixelBytesNumber(pixelMap: sendableImage.PixelMap) {
  let pixelBytesNumber: number = pixelMap.getPixelBytesNumber();
}
```

### getDensity

getDensity(): number

Obtains the pixel density of the image.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Return value**

| Type  | Description           |
| ------ | --------------- |
| number | Pixel density of the image, in ppi (pixels per inch). |

**Example**

```ts
function getDensity(pixelMap: sendableImage.PixelMap) {
  let density: number = pixelMap.getDensity();
}
```

### opacity

opacity(rate: number): Promise\<void>

Sets the opacity of the PixelMap. The specified opacity value is applied to all pixels, regardless of the opacity of the original image. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> Setting the opacity is not supported for images in YUV format.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name| Type  | Mandatory| Description                       |
| ------ | ------ | ---- | --------------------------- |
| rate   | number | Yes   | Opacity value, ranging from (0.0, 1.0]. 1.0 indicates fully opaque, and the closer the value is to 0.0, the higher the transparency. |

**Return value**

| Type          | Description                                           |
| -------------- | ----------------------------------------------- |
| Promise\<void> | Promise that returns no value. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function opacity(pixelMap: sendableImage.PixelMap) {
  const rate: number = 0.5;
  pixelMap.opacity(rate).then(() => {
    console.info('Succeeded in setting opacity.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set opacity. Code: ${err.code}, message: ${err.message}`);
  });
}
```

### opacitySync

opacitySync(rate: number): void

Sets the opacity of the PixelMap. The specified opacity value is applied to all pixels, regardless of the opacity of the original image. This API returns the result synchronously.

> **NOTE**
>
> Setting the opacity is not supported for images in YUV format.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name  | Type                | Mandatory| Description                          |
| -------- | -------------------- | ---- | ------------------------------ |
| rate     | number               | Yes   | Opacity value, ranging from (0.0, 1.0]. 1.0 indicates full opacity, and the closer the value is to 0.0, the higher the transparency. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
|  501    | Resource Unavailable. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function opacitySync(pixelMap: sendableImage.PixelMap) {
  const rate: number = 0.5;
  try {
    pixelMap.opacitySync(rate);
    console.info('Succeeded in setting opacity.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to set opacity. Code: ${err.code}, message: ${err.message}`);
  }
}
```

### createAlphaPixelmap

createAlphaPixelmap(): Promise\<PixelMap>

Generates a PixelMap in ALPHA_8 format that contains only the alpha channel information based on the alpha channel information. The generated PixelMap is not editable and can be used for shadow effects. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> - This API is not supported for the YUV format.
> - If the format of the original PixelMap is ALPHA_F16, the newly generated PixelMap retains the ALPHA_F16 format.
> - Since the image occupies a large amount of memory, call [release](#release) to free the memory in a timely manner after the PixelMap object is no longer used. When releasing the object, ensure that all asynchronous methods of the object have been executed and the object will no longer be used.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Return value**

| Type                            | Description                       |
| -------------------------------- | --------------------------- |
| Promise\<[PixelMap](#pixelmap)> | Promise object that returns a PixelMap in ALPHA_8 format containing only alpha channel information. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function createAlphaPixelmap(pixelMap: sendableImage.PixelMap) {
  pixelMap.createAlphaPixelmap().then((alphaPixelMap: sendableImage.PixelMap) => {
    console.info('Succeeded in creating alpha PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create alpha PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

### createAlphaPixelmapSync

createAlphaPixelmapSync(): PixelMap

Generates a PixelMap in ALPHA_8 format that contains only the alpha channel information based on the alpha channel information. The generated PixelMap is not editable and can be used for shadow effects. This API returns the result synchronously.

> **NOTE**
>
> - This API is not supported for the YUV format.
> - If the format of the original PixelMap is ALPHA_F16, the newly generated PixelMap retains the ALPHA_F16 format.
> - Since an image occupies a large amount of memory, call [release](#release) to free the memory in a timely manner after the PixelMap object is no longer used. Before releasing the object, ensure that all asynchronous methods of the object have been executed and that the object will no longer be used.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Return value**

| Type                            | Description                 |
| -------------------------------- | --------------------- |
| [PixelMap](#pixelmap) | Synchronously returns a PixelMap object in ALPHA_8 format that contains only alpha channel information on success, and throws an exception on failure. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | Parameter error. Possible causes: 1.Parameter verification failed. |
|  501    | Resource Unavailable. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function createAlphaPixelmapSync(pixelMap: sendableImage.PixelMap) {
  try {
    let alphaPixelMap: sendableImage.PixelMap = pixelMap.createAlphaPixelmapSync();
    if (alphaPixelMap == undefined) {
      console.error(`Failed to create alpha PixelMap.`);
      return;
    }
    console.info('Succeeded in creating alpha PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to create alpha PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

### scale

scale(x: number, y: number): Promise\<void>

Scales the image based on the given width and height scaling factors. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> The scaling factor = the image size after scaling / the image size before scaling.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name| Type  | Mandatory| Description                           |
| ------ | ------ | ---- | ------------------------------- |
| x      | number | Yes   | Scaling factor of the width.<br>The value cannot be 0. A positive value is recommended; otherwise, a flip effect occurs. |
| y      | number | Yes   | Scaling factor of the height.<br>The value cannot be 0. A positive value is recommended; otherwise, a flip effect occurs. |

**Return value**

| Type          | Description                       |
| -------------- | --------------------------- |
| Promise\<void> | Promise that returns no value. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function scale(pixelMap: sendableImage.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.0;
  pixelMap.scale(scaleX, scaleY).then(() => {
    console.info('Succeeded in scaling the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to scale the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

### scaleSync

scaleSync(x: number, y: number): void

Scales the image based on the given width and height scaling factors. This API returns the result synchronously.

> **NOTE**
>
> The scaling factor = the image size after scaling / the image size before scaling.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name| Type  | Mandatory| Description                           |
| ------ | ------ | ---- | ------------------------------- |
| x      | number | Yes   | Scaling factor of the width.<br>The value cannot be 0. A positive value is recommended; otherwise, a flip effect occurs. |
| y      | number | Yes   | Scaling factor of the height.<br>The value cannot be 0. A positive value is recommended; otherwise, a flip effect occurs. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
|  501    | Resource Unavailable. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function scaleSync(pixelMap: sendableImage.PixelMap) {
  const scaleX: number = 2.0;
  const scaleY: number = 1.0;
  try {
    pixelMap.scaleSync(scaleX, scaleY);
    console.info('Succeeded in scaling the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to scale the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

### translate

translate(x: number, y: number): Promise\<void>

Translates this PixelMap based on given coordinates. This API uses a promise to return the result.

> **NOTE**
>
> The size of the translated image becomes: width = original width + x, height = original height + y.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name| Type  | Mandatory| Description       |
| ------ | ------ | ---- | ----------- |
| x      | number | Yes   | Horizontal translation distance. A positive value moves the image to the right, and a negative value moves it to the left. The value range is (-image width, +∞). Unit: pixels (px).<br>When the value is negative, the translation effect is equivalent to cropping x columns of pixels from the left side of the image. |
| y      | number | Yes   | Vertical translation distance. A positive value moves the image downward, and a negative value moves it upward. The value range is (-image height, +∞). Unit: pixels (px).<br>When the value is negative, the translation effect is equivalent to cropping y rows of pixels from the top of the image. |

**Return value**

| Type          | Description                       |
| -------------- | --------------------------- |
| Promise\<void> | Promise that returns no value. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function translate(pixelMap: sendableImage.PixelMap) {
  const translateX: number = 50.0;
  const translateY: number = 10.0;
  pixelMap.translate(translateX, translateY).then(() => {
    console.info('Succeeded in translating the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to translate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

### translateSync

translateSync(x: number, y: number): void

Translates the image based on the given coordinates. This API returns the result synchronously.

> **NOTE**
>
> After the translation, the image size changes to: width = original width + x, height = original height + y.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name  | Type                | Mandatory| Description                           |
| -------- | -------------------- | ---- | ------------------------------- |
| x      | number | Yes   | Horizontal translation distance. A positive value moves the image to the right, and a negative value moves it to the left. The value range is (-image width, +∞). Unit: pixels (px).<br>When the value is negative, the translation is equivalent to cropping x columns of pixels from the left side of the image. |
| y      | number | Yes   | Vertical translation distance. A positive value moves the image downward, and a negative value moves it upward. The value range is (-image height, +∞). Unit: pixels (px).<br>When the value is negative, the translation is equivalent to cropping y rows of pixels from the top of the image. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
|  501    | Resource Unavailable. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function translateSync(pixelMap: sendableImage.PixelMap) {
  const translateX: number = 50.0;
  const translateY: number = 10.0;
  try {
    pixelMap.translateSync(translateX, translateY);
    console.info('Succeeded in translating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to translate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

### rotate

rotate(angle: number): Promise\<void>

Rotates this PixelMap based on a given angle. This API uses a promise to return the result.

> **NOTE**
>
> - The YUV format supports only rotation angles that are multiples of 90°.
> - The rotation angle ranges from 0 to 360 degrees. If the angle is out of this range, it is automatically corrected based on a full circle of 360°. For example, -100° has the same effect as 260°.
> - If the rotation angle is not a multiple of 90, the image size changes after rotation.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name| Type  | Mandatory| Description                         |
| ------ | ------ | ---- | ----------------------------- |
| angle  | number | Yes   | Rotation angle of the image. A positive value indicates clockwise rotation, and a negative value indicates counterclockwise rotation. Unit: degree (°). |

**Return value**

| Type          | Description                       |
| -------------- | --------------------------- |
| Promise\<void> | Promise that returns no value. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function rotate(pixelMap: sendableImage.PixelMap) {
  const angle: number = 90.0;
  pixelMap.rotate(angle).then(() => {
    console.info('Succeeded in rotating the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to rotate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

### rotateSync

rotateSync(angle: number): void

Rotates this PixelMap based on a given angle. This API returns the result synchronously.

> **NOTE**
>
> - The YUV format supports only rotation angles that are multiples of 90°.
> - The rotation angle ranges from 0 to 360 degrees. If the angle is out of this range, it is automatically corrected based on a full circle of 360°. For example, -100° has the same effect as 260°.
> - If the rotation angle is not a multiple of 90, the image size changes after rotation.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name  | Type                | Mandatory| Description                         |
| -------- | -------------------- | ---- | ----------------------------- |
| angle    | number               | Yes   | Rotation angle of the image. Positive values indicate clockwise rotation, and negative values indicate counterclockwise rotation. Unit: degrees (°). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
|  501    | Resource Unavailable. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function rotateSync(pixelMap: sendableImage.PixelMap) {
  const angle: number = 90.0;
  try {
    pixelMap.rotateSync(angle);
    console.info('Succeeded in rotating the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to rotate the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

### flip

flip(horizontal: boolean, vertical: boolean): Promise\<void>

Flips this PixelMap based on the given horizontal or vertical flip conditions. This API uses a promise to return the result asynchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name    | Type   | Mandatory| Description     |
| ---------- | ------- | ---- | --------- |
| horizontal | boolean              | Yes  | Whether to flip the image horizontally. The value **true** means to flip the image horizontally, and **false** means the opposite.           |
| vertical   | boolean              | Yes  | Whether to flip the image vertically. The value **true** means to flip the image vertically, and **false** means the opposite.           |

**Return value**

| Type          | Description                       |
| -------------- | --------------------------- |
| Promise\<void> | Promise that returns no value. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function flip(pixelMap: sendableImage.PixelMap) {
  const horizontal: boolean = true;
  const vertical: boolean = false;
  pixelMap.flip(horizontal, vertical).then(() => {
    console.info('Succeeded in flipping the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to flip the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

### flipSync

flipSync(horizontal: boolean, vertical: boolean): void

Flips this PixelMap based on the given horizontal or vertical flip conditions. This API returns the result synchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name    | Type                | Mandatory| Description                         |
| ---------- | -------------------- | ---- | ----------------------------- |
| horizontal | boolean              | Yes  | Whether to flip the image horizontally. The value **true** means to flip the image horizontally, and **false** means the opposite.           |
| vertical   | boolean              | Yes  | Whether to flip the image vertically. The value **true** means to flip the image vertically, and **false** means the opposite.           |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
|  501    | Resource Unavailable. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function flipSync(pixelMap: sendableImage.PixelMap) {
  const horizontal: boolean = true;
  const vertical: boolean = false;
  try {
    pixelMap.flipSync(horizontal, vertical);
    console.info('Succeeded in flipping the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to flip the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

### crop

crop(region: image.Region): Promise\<void>

Crops this PixelMap based on the given region. This API uses a promise to return the result asynchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name| Type              | Mandatory| Description       |
| ------ | ------------------ | ---- | ----------- |
| region | [image.Region](arkts-apis-image-i.md#region8) | Yes | Region to crop, including the start coordinates, width, and height. The value range cannot exceed the image width and height. Unit: pixels (px). |

**Return value**

| Type          | Description                       |
| -------------- | --------------------------- |
| Promise\<void> | Promise that returns no value. |

**Example**

```ts
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function crop(pixelMap: sendableImage.PixelMap) {
  const region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  pixelMap.crop(region).then(() => {
    console.info('Succeeded in cropping the PixelMap.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to crop the PixelMap. Code: ${err.code}, message: ${err.message}`);
  });
}
```

### cropSync

cropSync(region: image.Region): void

Crops the image based on the specified region. This API returns the result synchronously.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name  | Type                | Mandatory| Description                         |
| -------- | -------------------- | ---- | ----------------------------- |
| region   | [image.Region](arkts-apis-image-i.md#region8)   | Yes   | Region to crop, including the start coordinates, width, and height. The value range cannot exceed the image width and height. Unit: pixels (px). |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
|  501    | Resource Unavailable. |

**Example**

```ts
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

function cropSync(pixelMap: sendableImage.PixelMap) {
  const region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  try {
    pixelMap.cropSync(region);
    console.info('Succeeded in cropping the PixelMap.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to crop the PixelMap. Code: ${err.code}, message: ${err.message}`);
  }
}
```

### getColorSpace

getColorSpace(): colorSpaceManager.ColorSpaceManager

Obtains the color space of the image.

**System capability**: SystemCapability.Multimedia.Image.Core

**Return value**

| Type                               | Description            |
| ----------------------------------- | ---------------- |
| [colorSpaceManager.ColorSpaceManager](../apis-arkgraphics2d/js-apis-colorSpaceManager.md#colorspacemanager) | Image color space information. If the image does not contain color space information, an exception is thrown. |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 62980101| If the image data abnormal.            |
| 62980103| If the image data unsupport.             |
| 62980115| If the image parameter invalid.            |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getColorSpace(pixelMap: sendableImage.PixelMap) {
  try {
    const csm = pixelMap.getColorSpace();
    console.info(`Succeeded in getting color space: ${csm.getColorSpaceName()}.`);
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to get color space. Code: ${err.code}, message: ${err.message}`);
  }
}
```

### setColorSpace

setColorSpace(colorSpace: colorSpaceManager.ColorSpaceManager): void

Sets the color space of the image. To convert the pixel colors of the image to another color space at the same time, use [applyColorSpace](#applycolorspace).

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name    | Type                               | Mandatory| Description           |
| ---------- | ----------------------------------- | ---- | --------------- |
| colorSpace | [colorSpaceManager.ColorSpaceManager](../apis-arkgraphics2d/js-apis-colorSpaceManager.md#colorspacemanager) | Yes | Color space information of the image. |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 62980111| If the operation invalid.        |
| 62980115| If the image parameter invalid.             |

**Example**

```ts
import { colorSpaceManager } from '@kit.ArkGraphics2D';
import { BusinessError } from '@kit.BasicServicesKit';

function setColorSpace(pixelMap: sendableImage.PixelMap) {
  const colorSpaceName = colorSpaceManager.ColorSpace.SRGB;
  const csm: colorSpaceManager.ColorSpaceManager = colorSpaceManager.create(colorSpaceName);
  try {
    pixelMap.setColorSpace(csm);
    console.info('Succeeded in setting color space.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`Failed to set color space. Code: ${err.code}, message: ${err.message}`);
  }
}
```

### applyColorSpace

applyColorSpace(targetColorSpace: colorSpaceManager.ColorSpaceManager): Promise\<void>

Converts the pixel colors of the image to the target color space. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> This API only performs mathematical conversion between color spaces and does not include tone mapping from HDR to SDR. When the source image uses an HDR color space (with the transfer function HLG or PQ, such as BT2020_HLG, BT2020_PQ, P3_HLG, or P3_PQ) and the target is an SDR color space (with the transfer function sRGB gamma, such as SRGB, DISPLAY_P3, DCI_P3, or ADOBE_RGB_1998), calling this API directly causes the image to appear overly bright, washed out, and lose highlight details.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name| Type              | Mandatory| Description       |
| ------ | ------------------ | ---- | ----------- |
| targetColorSpace | [colorSpaceManager.ColorSpaceManager](../apis-arkgraphics2d/js-apis-colorSpaceManager.md#colorspacemanager) | Yes  | Target color space. SRGB, DCI_P3, DISPLAY_P3, and ADOBE_RGB_1998 are supported.|

**Return value**

| Type          | Description                       |
| -------------- | --------------------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | ------------------------------------------|
| 401     | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| 62980104| Failed to initialize the internal object. |
| 62980108| Failed to convert the color space.       |
| 62980115| Invalid image parameter.            |

**Example**

```ts
import { colorSpaceManager } from '@kit.ArkGraphics2D';
import { BusinessError } from '@kit.BasicServicesKit';

function applyColorSpace(pixelMap: sendableImage.PixelMap) {
  const colorSpaceName = colorSpaceManager.ColorSpace.SRGB;
  const targetColorSpace: colorSpaceManager.ColorSpaceManager = colorSpaceManager.create(colorSpaceName);
  pixelMap.applyColorSpace(targetColorSpace).then(() => {
    console.info('Succeeded in applying color space.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to apply color space. Code: ${err.code}, message: ${err.message}`);
  });
}
```

### marshalling

marshalling(sequence: rpc.MessageSequence): void

Marshals this PixelMap object and writes it to a MessageSequence object.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name                | Type                                                 | Mandatory| Description                                    |
| ---------------------- | ------------------------------------------------------ | ---- | ---------------------------------------- |
| sequence               | [rpc.MessageSequence](../apis-ipc-kit/js-apis-rpc.md#messagesequence9)  | Yes  | MessageSequence object.                |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 62980115 | Invalid image parameter.              |
| 62980097 | IPC error.             |

**Example**

```ts
// EntryAbility.ets
import { image } from '@kit.ImageKit';
import { rpc } from '@kit.IPCKit';

class MySequence implements rpc.Parcelable {
  pixelMap: sendableImage.PixelMap;
  constructor(pixelMap: sendableImage.PixelMap) {
    this.pixelMap = pixelMap;
  }
  marshalling(messageSequence: rpc.MessageSequence) {
    this.pixelMap.marshalling(messageSequence);
    console.info('Marshalled the PixelMap.');
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence) {
    sendableImage.createPixelMap(new ArrayBuffer(96), {size: { height: 4, width: 6 }}).then((pixelParcel: sendableImage.PixelMap) => {
      pixelParcel.unmarshalling(messageSequence).then(async (pixelMap: sendableImage.PixelMap) => {
        this.pixelMap = pixelMap;
        pixelMap.getImageInfo().then((imageInfo: image.ImageInfo) => {
          console.info(`Unmarshalled information: height = ${imageInfo.size.height}, width = ${imageInfo.size.width}.`);
        });
      });
    });
    return true;
  }
}

async function marshal() {
  const color: ArrayBuffer = new ArrayBuffer(96);
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = 0x80;
  }
  let opts: image.InitializationOptions = {
    editable: true,
    pixelFormat: image.PixelMapFormat.BGRA_8888,
    size: { height: 4, width: 6 },
    alphaType: image.AlphaType.UNPREMUL
  }
  let pixelMap: sendableImage.PixelMap | undefined = await sendableImage.createPixelMap(color, opts);
  if (pixelMap != undefined) {
    // Implement serialization.
    let parcelable: MySequence = new MySequence(pixelMap);
    let data: rpc.MessageSequence = rpc.MessageSequence.create();
    data.writeParcelable(parcelable);

    // Implement deserialization to obtain data through the RPC.
    let seq: MySequence = new MySequence(pixelMap);
    data.readParcelable(seq);
  }
}
```

### unmarshalling

unmarshalling(sequence: rpc.MessageSequence): Promise\<PixelMap>

Deserializes a PixelMap from a MessageSequence. This API uses a promise to return the result asynchronously.

> **NOTE**
>
> To deserialize and create a PixelMap synchronously, use [createPixelMapFromParcel](#sendableimagecreatepixelmapfromparcel).

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name                | Type                                                 | Mandatory| Description                                    |
| ---------------------- | ----------------------------------------------------- | ---- | ---------------------------------------- |
| sequence               | [rpc.MessageSequence](../apis-ipc-kit/js-apis-rpc.md#messagesequence9) | Yes  | MessageSequence object that stores the PixelMap information.     |

**Return value**

| Type                            | Description                 |
| -------------------------------- | --------------------- |
| Promise\<[PixelMap](#pixelmap)> | Promise that returns the deserialized PixelMap. |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 62980115 | Invalid image parameter.              |
| 62980097 | IPC error.              |
| 62980096 | The operation failed.         |

**Example**

```ts
// EntryAbility.ets
import { image } from '@kit.ImageKit';
import { rpc } from '@kit.IPCKit';

class MySequence implements rpc.Parcelable {
  pixelMap: sendableImage.PixelMap;
  constructor(pixelMap: sendableImage.PixelMap) {
    this.pixelMap = pixelMap;
  }
  marshalling(messageSequence: rpc.MessageSequence) {
    this.pixelMap.marshalling(messageSequence);
    console.info('Marshalled the PixelMap.');
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence) {
    sendableImage.createPixelMap(new ArrayBuffer(96), {size: { height: 4, width: 6 }}).then((pixelParcel: sendableImage.PixelMap) => {
      pixelParcel.unmarshalling(messageSequence).then(async (pixelMap: sendableImage.PixelMap) => {
        this.pixelMap = pixelMap;
        pixelMap.getImageInfo().then((imageInfo: image.ImageInfo) => {
          console.info(`Unmarshalled information: height = ${imageInfo.size.height}, width = ${imageInfo.size.width}.`);
        });
      });
    });
    return true;
  }
}

async function unmarshal() {
  const color: ArrayBuffer = new ArrayBuffer(96);
  let bufferArr: Uint8Array = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i++) {
    bufferArr[i] = 0x80;
  }
  let opts: image.InitializationOptions = {
    editable: true,
    pixelFormat: image.PixelMapFormat.BGRA_8888,
    size: { height: 4, width: 6 },
    alphaType: image.AlphaType.UNPREMUL
  }
  let pixelMap: sendableImage.PixelMap | undefined = await sendableImage.createPixelMap(color, opts);
  if (pixelMap != undefined) {
    // Implement serialization.
    let parcelable: MySequence = new MySequence(pixelMap);
    let data: rpc.MessageSequence = rpc.MessageSequence.create();
    data.writeParcelable(parcelable);

    // Implement deserialization to obtain data through the RPC.
    let seq: MySequence = new MySequence(pixelMap);
    data.readParcelable(seq);
  }
}
```

### release

release():Promise\<void>

Releases the PixelMap object. After the object is released, any method call that accesses its internal data will fail. This API uses a promise to return the result asynchronously.

Images occupy a large amount of memory. When you finish using a PixelMap instance, call this API to free the memory promptly.

Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

> **NOTE**
>
> Releasing means that the ArkTS object releases the management right of the associated native object. The memory occupied by the native object is reclaimed only when all ArkTS objects that manage the native object are released.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

**Return value**

| Type          | Description                           |
| -------------- | ------------------------------- |
| Promise\<void> | Promise that returns no value. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function release(pixelMap: sendableImage.PixelMap) {
  pixelMap.release().then(() => {
    console.info('Succeeded in releasing the PixelMap object.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to release the PixelMap object. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## Size

Describes the size of an image.

It inherits from [lang.ISendable](../../arkts-utils/arkts-sendable.md#isendable).

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name  | Type  | Read-Only| Optional| Description          |
| ------ | ------ | ---- | ---- | -------------- |
| height | number | No  | No  | Height of the output image, in px.|
| width  | number | No  | No  | Width of the output image, in px.|

## Region

Describes the region information.

It inherits from [lang.ISendable](../../arkts-utils/arkts-sendable.md#isendable).

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.Core

| Name| Type         | Read-Only| Optional| Description        |
| ---- | ------------- | ---- | ---- | ------------ |
| size | [Size](#size) | No  | No  | Region size.  |
| x    | number        | No  | No  | X coordinate, in px.|
| y    | number        | No  | No  | Y coordinate, in px.|

## sendableImage.createImageSource

createImageSource(uri: string): ImageSource

Creates an ImageSource instance based on a given URI.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](#release-1) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name| Type  | Mandatory| Description                              |
| ------ | ------ | ---- | ---------------------------------- |
| uri    | string | Yes  | Image path. Currently, only the application sandbox path is supported.<br>The following formats are supported: .jpg, .png, .gif, .bmp, .webp, .dng [SVG](arkts-apis-image-f.md#svg-tags), and ico.|

**Return value**

| Type                       | Description                                        |
| --------------------------- | -------------------------------------------- |
| [ImageSource](#imagesource) | ImageSource instance. If the operation fails, undefined is returned.|

**Example**

```ts
import { sendableImage } from '@kit.ImageKit';

async function CreateImageSource(context : Context) {
  const path: string = context.cacheDir + "/test.jpg";
  const sendableImageSourceObj: sendableImage.ImageSource = sendableImage.createImageSource(path);
}
```

## sendableImage.createImageSource

createImageSource(fd: number): ImageSource

Creates an ImageSource instance based on a given file descriptor.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](#release-1) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name| Type  | Mandatory| Description         |
| ------ | ------ | ---- | ------------- |
| fd     | number | Yes  | File descriptor.|

**Return value**

| Type                       | Description                                        |
| --------------------------- | -------------------------------------------- |
| [ImageSource](#imagesource) | ImageSource instance. If the operation fails, undefined is returned.|

**Example**

```ts
import { sendableImage } from '@kit.ImageKit';
import { fileIo } from '@kit.CoreFileKit';

async function CreateImageSource(context : Context) {
  const path: string = context.cacheDir + "/test.jpg";
  let file = fileIo.openSync(path, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
  const sendableImageSourceObj: sendableImage.ImageSource = sendableImage.createImageSource(file.fd);
}
```

## sendableImage.createImageSource

createImageSource(buf: ArrayBuffer): ImageSource

Creates an ImageSource instance from a buffer. The buf data is undecoded data. Do not pass pixel buffer data such as RGBA or YUV. To create a PixelMap from pixel buffer data, call APIs such as [sendableImage.createPixelMap](#sendableimagecreatepixelmap).

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](#release-1) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name| Type       | Mandatory| Description            |
| ------ | ----------- | ---- | ---------------- |
| buf    | ArrayBuffer | Yes  | Array of image buffers.|

**Return value**

| Type                       | Description                                        |
| --------------------------- | -------------------------------------------- |
| [ImageSource](#imagesource) | ImageSource instance. If the operation fails, undefined is returned.|

**Example**

```ts
import { sendableImage } from '@kit.ImageKit';

async function CreateImageSource() {
  const buf: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to create. The value is calculated as follows: height * width *4.
  const sendableImageSourceObj: sendableImage.ImageSource = sendableImage.createImageSource(buf);
}
```

## sendableImage.createImageReceiver

createImageReceiver(size: image.Size, format: image.ImageFormat, capacity: number): ImageReceiver

Creates an ImageReceiver instance based on the specified image size, format, and capacity.

Images occupy a large amount of memory. When you finish using an ImageReceiver instance, call [release](#release-3) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Parameters**

| Name  | Type  | Mandatory| Description                  |
| -------- | ------ | ---- | ---------------------- |
| size    | [image.Size](./arkts-apis-image-i.md#size)  | Yes  | Default size of the image.      |
| format   | [image.ImageFormat](./arkts-apis-image-e.md#imageformat9) | Yes  | Image format, which is a constant of **image.ImageFormat**. (Currently, only **ImageFormat:JPEG** is supported.)            |
| capacity | number | Yes  | Maximum number of images that can be accessed at the same time. This parameter is used only as an expected value. The actual capacity is determined by the device hardware.|

**Return value**

| Type                            | Description                                   |
| -------------------------------- | --------------------------------------- |
| [ImageReceiver](#imagereceiver) | ImageReceiver instance.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    |  The parameter check failed. |

**Example**

```ts
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

## ImageSource

Provides APIs to obtain image information. Before calling any API in ImageSource, you must use [sendableImage.createImageSource](#sendableimagecreateimagesource) to create an ImageSource instance.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](#release-1) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

### createPixelMap

createPixelMap(options?: image.DecodingOptions): Promise\<PixelMap>

Creates a PixelMap object based on decoding options. This API uses a promise to return the result.

Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name | Type                                | Mandatory| Description      |
| ------- | ------------------------------------ | ---- | ---------- |
| options | [image.DecodingOptions](./arkts-apis-image-i.md#decodingoptions7) | No  | Decoding options.|

**Return value**

| Type                            | Description                 |
| -------------------------------- | --------------------- |
| Promise\<[PixelMap](#pixelmap)> | Promise used to return the PixelMap object.|

**Example**

```ts
import { sendableImage } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMap(context : Context) {
  const path: string = context.cacheDir + "/test.jpg";
  const sendableImageSourceObj: sendableImage.ImageSource = sendableImage.createImageSource(path);
  sendableImageSourceObj.createPixelMap().then((pixelMap: sendableImage.PixelMap) => {
    console.info('Succeeded in creating pixelMap object through image decoding parameters.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to create pixelMap object through image decoding parameters. code ${error.code}, message is ${error.message}`);
  })
}
```

### release

release(): Promise\<void>

Releases this ImageSource instance. This API uses a promise to return the result.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call this API to free the memory promptly.

Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Return value**

| Type          | Description                       |
| -------------- | --------------------------- |
| Promise\<void> | Promise used to return the result.|

**Example**

```ts
import { sendableImage } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(context : Context) {
  const path: string = context.cacheDir + "/test.jpg";
  const sendableImageSourceObj: sendableImage.ImageSource = sendableImage.createImageSource(path);
  sendableImageSourceObj.release().then(() => {
    console.info('Succeeded in releasing the image source instance.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release the image source instance. code ${error.code}, message is ${error.message}`);
  })
}
```

## Image

Provides APIs for basic image operations, including obtaining image information and reading and writing image data. An Image instance is returned when [readNextImage](#readnextimage) and [readLatestImage](#readlatestimage) are called. This class inherits from [ISendable](../../arkts-utils/arkts-sendable.md#isendable).

Images occupy a large amount of memory. When you finish using an Image instance, call [release](#release-2) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

### Properties

**System capability**: SystemCapability.Multimedia.Image.Core

| Name    | Type              | Read-Only| Optional| Description                                              |
| -------- | ------------------ | ---- | ---- | -------------------------------------------------- |
| clipRect | [Region](#region) | No  | No  | Image area to be cropped.                                |
| size     | [Size](#size)      | Yes  | No  | Image size.<br>If the Image object stores camera preview stream data (YUV image data), the width and height in **size** reflect the dimensions of the YUV image.<br>If the Image object stores camera capture stream data (JPEG image data), given that it is an encoded file, the width in **size** is the size of the JPEG file, while the height is set to **1**.<br>The type of data stored in the Image object depends on whether the application passes the surface ID in the receiver to a previewOutput or captureOutput object of the camera.<br>For details about the best practices of camera preview and photo capture, see [Dual-Channel Preview (ArkTS)](../../media/camera/camera-dual-channel-preview.md) and [Photo Capture Sample (ArkTS)](../../media/camera/camera-shooting-case.md).|
| format   | number             | Yes  | No  | Image format. For details, see [OH_NativeBuffer_Format](../apis-arkgraphics2d/capi-buffer-common-h.md#oh_nativebuffer_format).|
| timestamp| number         | Yes     | No  | Image timestamp. Timestamps, measured in nanoseconds, are usually monotonically increasing. The specific meaning and baseline of these timestamps are determined by the image producer, which is the camera in the camera preview and photo scenarios. As a result, images from different producers may carry timestamps with distinct meanings and baselines, making direct comparison between them infeasible. To obtain the generation time of a photo, you can use [getImageProperty](arkts-apis-image-ImageSource.md#getimageproperty11) to read the related Exif information.|

### getComponent

getComponent(componentType: image.ComponentType): Promise\<image.Component>

Obtains the component buffer from the Image instance based on the color component type. This API uses a promise to return the result. The thread that runs **getComponent** is insecure.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name       | Type                            | Mandatory| Description            |
| ------------- | -------------------------------- | ---- | ---------------- |
| componentType | [image.ComponentType](./arkts-apis-image-e.md#componenttype9) | Yes  | Color component type of the image.|

**Return value**

| Type                             | Description                             |
| --------------------------------- | --------------------------------- |
| Promise<[image.Component](./arkts-apis-image-i.md#component9)> | Promise used to return the component buffer.|

**Example**

```ts
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

### release

release(): Promise\<void>

Releases this Image instance. This API uses a promise to return the result.

The corresponding resources must be released before another image arrives.

Images occupy a large amount of memory. When you finish using an Image instance, call this API to free the memory promptly.

Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.Core

**Return value**

| Type          | Description                 |
| -------------- | --------------------- |
| Promise\<void> | Promise used to return the result.|

**Example**

```ts
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

## ImageReceiver

Image receiver class. You can use it to obtain the surface ID of a component, read the latest image and the next image, and release **ImageReceiver** instances.

Before calling any APIs in ImageReceiver, you must create an ImageReceiver instance.

### Properties

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

| Name    | Type                        | Read-Only| Optional| Description              |
| -------- | ---------------------------- | ---- | ---- | ------------------ |
| size     | [image.Size](./arkts-apis-image-i.md#size)                | Yes  | No  | Image size.        |
| capacity | number                       | Yes  | No  | Maximum number of images that can be accessed at the same time. This parameter is used only as an expected value. The actual capacity is determined by the device hardware.|
| format   | [image.ImageFormat](./arkts-apis-image-e.md#imageformat9) | Yes  | No  | Image format.        |

### getReceivingSurfaceId

getReceivingSurfaceId(): Promise\<string>

Obtains a surface ID for the camera or other components. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Return value**

| Type            | Description                |
| ---------------- | -------------------- |
| Promise\<string> | Asynchronously returns the surface ID.|

**Example**

```ts
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

### readLatestImage

readLatestImage(): Promise\<Image>

Reads the latest image from the ImageReceiver instance. This API uses a promise to return the result.

> **NOTE**
>
> This API must be called after the [on](#on) callback is triggered to receive data properly. After the [Image](#image) object returned by this API is used, call [release](#release-2) to release it. Only after the release can new data be received.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Return value**

| Type                     | Description              |
| ------------------------- | ------------------ |
| Promise<[Image](#image)> | Promise used to return the latest image.|

**Example**

```ts
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

### readNextImage

readNextImage(): Promise\<Image>

Reads the next image from the ImageReceiver instance. This API uses a promise to return the result.

> **NOTE**
>
> This API must be called after the [on](#on) callback is triggered to receive data properly. After the [Image](#image) object returned by this API is used, call [release](#release-2) to release it. Only after the release can new data be received.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Return value**

| Type                     | Description                |
| ------------------------- | -------------------- |
| Promise<[Image](#image)> | Promise used to return the next image.|

**Example**

```ts
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

### on

on(type: 'imageArrival', callback: AsyncCallback\<void>): void

Listens for image arrival events. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Parameters**

| Name  | Type                | Mandatory| Description                                                  |
| -------- | -------------------- | ---- | ------------------------------------------------------ |
| type     | string               | Yes  | Type of event to listen for. The value is fixed at **'imageArrival'**, which is triggered when an image is received.|
| callback | AsyncCallback\<void> | Yes  | Callback invoked for the event.                                      |

**Example**

```ts
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

### release

release(): Promise\<void>

Releases this ImageReceiver instance. This API uses a promise to return the result.

Images occupy a large amount of memory. When you finish using an ImageReceiver instance, call this API to free the memory promptly.

Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Return value**

| Type          | Description              |
| -------------- | ------------------ |
| Promise\<void> | Promise used to return the result.|

**Example**

```ts
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
