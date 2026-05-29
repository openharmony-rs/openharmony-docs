# Functions
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

> **NOTE**
>
> The initial APIs of this module are supported since API version 6. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { image } from '@kit.ImageKit';
```

## image.createPicture<sup>13+</sup>

createPicture(mainPixelmap : PixelMap): Picture

Creates a Picture object based on a main PixelMap.

Images occupy a large amount of memory. When you finish using a Picture instance, call [release](./arkts-apis-image-Picture.md#release13) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name      | Type               | Mandatory| Description            |
| ------------ | ------------------- | ---- | ---------------- |
| mainPixelmap | [PixelMap](arkts-apis-image-PixelMap.md) | Yes  | Main PixelMap.|

**Return value**

| Type              | Description             |
| ------------------ | ----------------- |
| [Picture](arkts-apis-image-Picture.md) | Picture object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1.Mandatory parameters are left unspecified.2.Incorrect parameter types.3.Parameter verification failed. |

**Example**

```ts
async function CreatePicture(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("test.jpg");
  let ops: image.SourceOptions = {
    sourceDensity: 98,
  }
  let imageSource: image.ImageSource = image.createImageSource(rawFile.buffer as ArrayBuffer, ops);
  let commodityPixelMap: image.PixelMap = await imageSource.createPixelMap();
  let pictureObj: image.Picture = image.createPicture(commodityPixelMap);
  if (pictureObj != null) {
    console.info('Create picture succeeded');
  } else {
    console.error('Create picture failed');
  }
}
```

## image.createPictureFromParcel<sup>13+</sup>

createPictureFromParcel(sequence: rpc.MessageSequence): Picture

Creates a Picture object from a MessageSequence object.

Images occupy a large amount of memory. When you finish using a Picture instance, call [release](./arkts-apis-image-Picture.md#release13) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name  | Type                                                               | Mandatory| Description                                |
| -------- | ------------------------------------------------------------------- | ---- | ------------------------------------ |
| sequence | [rpc.MessageSequence](../apis-ipc-kit/js-apis-rpc.md#messagesequence9) | Yes  | MessageSequence object that stores the Picture information.|

**Return value**

| Type              | Description             |
| ------------------ | ----------------- |
| [Picture](arkts-apis-image-Picture.md) | Picture object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1.Mandatory parameters are left unspecified.2.Incorrect parameter types.3.Parameter verification failed. |
| 62980097 |  IPC error. Possible cause: 1.IPC communication failed. 2. Image upload exception. 3. Decode process exception. 4. Insufficient memory.                                        |

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MySequence implements rpc.Parcelable {
  picture: image.Picture | null = null;
  constructor(conPicture: image.Picture) {
    this.picture = conPicture;
  }
  marshalling(messageSequence: rpc.MessageSequence) {
    if(this.picture != null) {
      this.picture.marshalling(messageSequence);
      console.info('Marshalling success !');
      return true;
    } else {
      console.error('Marshalling failed !');
      return false;
    }
  }
  unmarshalling(messageSequence : rpc.MessageSequence) {
    this.picture = image.createPictureFromParcel(messageSequence);
    this.picture.getMainPixelmap().getImageInfo().then((imageInfo : image.ImageInfo) => {
      console.info(`Unmarshalling to get mainPixelmap information height:${imageInfo.size.height} width:${imageInfo.size.width}`);
    }).catch((error: BusinessError) => {
      console.error(`Unmarshalling failed error.code: ${error.code} ,error.message: ${error.message}`);
    });
    return true;
  }
}

async function Marshalling_UnMarshalling(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("test.jpg");
  let ops: image.SourceOptions = {
    sourceDensity: 98,
  }
  let imageSource: image.ImageSource = image.createImageSource(rawFile.buffer as ArrayBuffer, ops);
  let commodityPixelMap: image.PixelMap = await imageSource.createPixelMap();
  let pictureObj: image.Picture = image.createPicture(commodityPixelMap);
  if (pictureObj != null) {
    let parcelable: MySequence = new MySequence(pictureObj);
    let data: rpc.MessageSequence = rpc.MessageSequence.create();
    // Implement serialization.
    data.writeParcelable(parcelable);
    let ret: MySequence = new MySequence(pictureObj);
    // Implement deserialization.
    data.readParcelable(ret);
  } else {
    console.error('PictureObj is null');
  }
}
```

## image.createPixelMapFromPixels

createPixelMapFromPixels(pixels: ArrayBuffer, param: InitializationOptions): Promise\<PixelMap\>

Creates a PixelMap based on the pixel data and image properties. The passed pixel data is copied and converted into the pixel format specified by [InitializationOptions](arkts-apis-image-i.md#initializationoptions8).pixelFormat to initialize the pixels of the PixelMap. This API returns the result asynchronously through a promise.

> **NOTE**
>
> - This API cannot create PixelMaps of the RGBA_1010102, YCBCR_P010, YCRCB_P010, or ASTC_4x4 format.
> - Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 26.0.0.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name | Type                                            | Mandatory| Description                                                            |
| ------- | ------------------------------------------------ | ---- | ---------------------------------------------------------------- |
| pixels  | ArrayBuffer                                      | Yes  | Buffer for storing the pixel data. It is used to initialize the pixels of the PixelMap.<br>The pixel format in the buffer must be specified by [InitializationOptions](arkts-apis-image-i.md#initializationoptions8).srcPixelFormat. If the pixel format is not specified, the BGRA_8888 format will be used by default.<br>**Note:** Length of the buffer = Width × Height × Number of bytes per pixel|
| param | [InitializationOptions](arkts-apis-image-i.md#initializationoptions8) | Yes  | Image properties, including the dimensions, pixel format, transparency type, scaling mode, and editability.<br>**Note:** If the pixel format is set to ASTC_4x4, the default pixel format defined in this type will be used.|

**Return value**

| Type                            | Description                                                                   |
| -------------------------------- | ----------------------------------------------------------------------- |
| Promise\<[PixelMap](arkts-apis-image-PixelMap.md)\> | Promise used to return the created PixelMap object.                     |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| Error Code| Error Message|
| ------ | --------------------------------------------|
| 7600206 | Invalid parameter. Possible cause: Size of the pixel data buffer does not match InitializationOptions.size. |
| 7600207 | Unsupported pixel format. |
| 7600301 | Failed to allocate memory. Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |
| 7600305 | Failed to create the PixelMap. Possible causes: 1. Failed to perform pixel format conversion. 2. Internal data is corrupted. Please check the logs for detailed information. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function DemoCreatePixelMapFromPixels() {
  const size: image.Size = {
    width: 6,
    height: 4
  };
  const pixels = new ArrayBuffer(size.width * size.height * 4); // 4 indicates the number of bytes per pixel in RGBA format.
  const pixelsArr = new Uint8Array(pixels);
  for (let i = 0; i < pixelsArr.length; i += 4) {
    // In RGBA_8888 format, the following array indexes correspond to the R, G, B, and A channels in sequence.
    pixelsArr[i] = 0xFF;
    pixelsArr[i + 1] = 0x00;
    pixelsArr[i + 2] = 0x00;
    pixelsArr[i + 3] = 0xFF;
  }
  const config: image.InitializationOptions = {
    size,
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the source pixel data in the buffer.
    pixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the new PixelMap.
    editable: true
  };

  image.createPixelMapFromPixels(pixels, config)
    .then((pixelMap: image.PixelMap) => {
      console.info('PixelMap created successfully.');
    }).catch((e: BusinessError) => {
      console.error (`Failed to create the PixelMap. Error code: ${e.code}; Error message: ${e.message}`);
    });
}
```

## image.createPixelMapFromPixelsSync

createPixelMapFromPixelsSync(pixels: ArrayBuffer, param: InitializationOptions): PixelMap

Creates a PixelMap based on the pixel data and image properties. The passed pixel data is copied and converted into the pixel format specified by [InitializationOptions](arkts-apis-image-i.md#initializationoptions8).pixelFormat to initialize the pixels of the PixelMap.

> **NOTE**
>
> - This API cannot create PixelMaps of the RGBA_1010102, YCBCR_P010, YCRCB_P010, or ASTC_4x4 format.
> - Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 26.0.0.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name | Type                                            | Mandatory| Description                                                            |
| ------- | ------------------------------------------------ | ---- | ---------------------------------------------------------------- |
| pixels  | ArrayBuffer                                      | Yes  | Buffer for storing the pixel data. It is used to initialize the pixels of the PixelMap.<br>The pixel format in the buffer must be specified by [InitializationOptions](arkts-apis-image-i.md#initializationoptions8).srcPixelFormat. If the pixel format is not specified, the BGRA_8888 format will be used by default.<br>**Note:** Length of the buffer = Width × Height × Number of bytes per pixel|
| param | [InitializationOptions](arkts-apis-image-i.md#initializationoptions8) | Yes  | Image properties, including the dimensions, pixel format, transparency type, scaling mode, and editability.<br>**Note:** If the pixel format is set to ASTC_4x4, the default pixel format defined in this type will be used.|

**Return value**

| Type                            | Description                                                                   |
| -------------------------------- | ----------------------------------------------------------------------- |
| [PixelMap](arkts-apis-image-PixelMap.md) | Created PixelMap.                                            |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| Error Code| Error Message|
| ------ | --------------------------------------------|
| 7600206 | Invalid parameter. Possible cause: Size of the pixel data buffer does not match InitializationOptions.size. |
| 7600207 | Unsupported pixel format. |
| 7600301 | Failed to allocate memory. Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |
| 7600305 | Failed to create the PixelMap. Possible causes: 1. Failed to perform pixel format conversion. 2. Internal data is corrupted. Please check the logs for detailed information. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function DemoCreatePixelMapFromPixelsSync() {
  const size: image.Size = {
    width: 6,
    height: 4
  };
  const pixels = new ArrayBuffer(size.width * size.height * 4); // 4 indicates the number of bytes per pixel in RGBA format.
  const pixelsArr = new Uint8Array(pixels);
  for (let i = 0; i < pixelsArr.length; i += 4) {
    // In RGBA_8888 format, the following array indexes correspond to the R, G, B, and A channels in sequence.
    pixelsArr[i] = 0xFF;
    pixelsArr[i + 1] = 0x00;
    pixelsArr[i + 2] = 0x00;
    pixelsArr[i + 3] = 0xFF;
  }
  const config: image.InitializationOptions = {
    size,
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the source pixel data in the buffer.
    pixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the new PixelMap.
    editable: true
  };

  try {
    const pixelMap = image.createPixelMapFromPixelsSync(pixels, config);
    console.info('PixelMap created successfully.');
  } catch (e) {
    const error = e as BusinessError;
    console.error (`Failed to create the PixelMap. Error code: ${e.code}; Error message: ${e.message}`);
  }
}
```

## image.createPixelMap<sup>8+</sup>

createPixelMap(colors: ArrayBuffer, options: InitializationOptions): Promise\<PixelMap>

Creates a PixelMap based on the pixel data and image properties. The input pixel data is parsed in BGRA_8888 format by default. This API returns the result asynchronously through a promise.

Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

Since API version 26.0.0, you are advised to use [createPixelMapFromPixels](#imagecreatepixelmapfrompixels) instead for better exception handling.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name | Type                                            | Mandatory| Description                                                            |
| ------- | ------------------------------------------------ | ---- | ---------------------------------------------------------------- |
| colors  | ArrayBuffer                                      | Yes  | Buffer for storing the pixel data. It is used to initialize the pixels of the PixelMap. Before initialization, the pixel format in the buffer must be specified by [InitializationOptions](arkts-apis-image-i.md#initializationoptions8).srcPixelFormat. If the pixel format is not specified, the BGRA_8888 format will be used by default.<br>**NOTE**: The length of the buffer required for storing the pixel data is determined by multiplying the width, height, and the number of bytes per pixel.|
| options | [InitializationOptions](arkts-apis-image-i.md#initializationoptions8) | Yes  | Pixel properties, including the alpha type, size, scale mode, pixel format, and editable.|

**Return value**

| Type                            | Description                                                                   |
| -------------------------------- | ----------------------------------------------------------------------- |
| Promise\<[PixelMap](arkts-apis-image-PixelMap.md)> | Promise used to return the PixelMap object.<br>If the size of the created PixelMap exceeds that of the original image, the PixelMap size of the original image is returned.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to create. The value is calculated as follows: height * width *4.
  let opts: image.InitializationOptions = {
    size: { height: 4, width: 6 },
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the source pixel data in the buffer.
    pixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the new PixelMap.
    editable: true
  };
  image.createPixelMap(color, opts).then((pixelMap: image.PixelMap) => {
    console.info('Succeeded in creating pixelmap.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to create pixelmap. code is ${error.code}, message is ${error.message}`);
  })
}
```

## image.createPixelMap<sup>8+</sup>

createPixelMap(colors: ArrayBuffer, options: InitializationOptions, callback: AsyncCallback\<PixelMap>): void

Creates a PixelMap based on the pixel data and image properties. The input pixel data is parsed in BGRA_8888 format by default. This API uses an asynchronous callback to return the result.

Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

Since API version 26.0.0, you are advised to use [createPixelMapFromPixels](#imagecreatepixelmapfrompixels) instead for better exception handling.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name  | Type                                            | Mandatory| Description                      |
| -------- | ------------------------------------------------ | ---- | -------------------------- |
| colors   | ArrayBuffer                                      | Yes  | Buffer for storing the pixel data. It is used to initialize the pixels of the PixelMap. Before initialization, the pixel format in the buffer must be specified by [InitializationOptions](arkts-apis-image-i.md#initializationoptions8).srcPixelFormat. If the pixel format is not specified, the BGRA_8888 format will be used by default.<br>**NOTE**: The length of the buffer required for storing the pixel data is determined by multiplying the width, height, and the number of bytes per pixel.|
| options  | [InitializationOptions](arkts-apis-image-i.md#initializationoptions8) | Yes  | Pixel properties, including the alpha type, size, scale mode, pixel format, and editable.|
| callback | AsyncCallback\<[PixelMap](arkts-apis-image-PixelMap.md)>           | Yes  | Callback used to return the result. If the operation is successful, **err** is undefined and **data** is the PixelMap object obtained; otherwise, **err** is an error object.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to create. The value is calculated as follows: height * width *4.
  let opts: image.InitializationOptions = {
    size: { height: 4, width: 6 },
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the source pixel data in the buffer.
    pixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the new PixelMap.
    editable: true
  };
  image.createPixelMap(color, opts, (error: BusinessError, pixelMap: image.PixelMap) => {
    if(error) {
      console.error(`Failed to create pixelmap. code is ${error.code}, message is ${error.message}`);
      return;
    } else {
      console.info('Succeeded in creating pixelmap.');
    }
  })
}
```

## image.createPixelMapUsingAllocator<sup>20+</sup>

createPixelMapUsingAllocator(colors: ArrayBuffer, param: InitializationOptions, allocatorType?: AllocatorType): Promise\<PixelMap>

Creates a PixelMap object with the specified properties and memory type. By default, the BGRA_8888 format is used to process data. This API returns the result asynchronously through a promise.

Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name  | Type                                            | Mandatory| Description                      |
| -------- | ------------------------------------------------ | ---- | -------------------------- |
| colors   | ArrayBuffer                                      | Yes  | Buffer for storing the pixel data. It is used to initialize the pixels of the PixelMap. Before initialization, the pixel format in the buffer must be specified by [InitializationOptions](arkts-apis-image-i.md#initializationoptions8).srcPixelFormat.<br>**NOTE**: The length of the buffer required for storing the pixel data is determined by multiplying the width, height, and the number of bytes per pixel.|
| param  | [InitializationOptions](arkts-apis-image-i.md#initializationoptions8) | Yes  | Pixel properties, including the alpha type, size, scale mode, pixel format, and editable.|
| allocatorType  | [AllocatorType](arkts-apis-image-e.md#allocatortype15)          | No  | Memory type for creating the PixelMap. The default memory type is **AllocatorType.AUTO**.<br> 1. **image.AllocatorType.AUTO**: The following formats are not supported for this memory type: UNKNOWN, YCBCR_P010, YCRCB_P010, and ASTC_4x4. For RGBA_1010102, DMA memory is allocated by default. For other formats (RGB_565, RGBA_8888, BGRA_8888, and RGBAF_16), DMA memory is allocated if the dimensions exceed 512*512; otherwise, shared memory is allocated.<br>2. **image.AllocatorType.DMA**: The formats RGBA_1010102, RGB_565, RGBA_8888, BGRA_8888, and RGBAF_16 support DMA memory types. Other formats do not support DMA memory types.<br>3. **image.AllocatorType.SHARED**: The formats UNKNOWN, RGBA_1010102, YCBCR_P010, YCRCB_P010, and ASTC_4x4 do not support shared memory. Other formats support shared memory.|

**Return value**

| Type                            | Description                                                                   |
| -------------------------------- | ----------------------------------------------------------------------- |
| Promise\<[PixelMap](arkts-apis-image-PixelMap.md)> | Promise used to return the PixelMap object.|

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  7600201    | Unsupported operation. |
|  7600301    | Memory alloc failed. |
|  7600302    | Memory copy failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMapUseAllocator() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to create. The value is calculated as follows: height * width *4.
  let opts: image.InitializationOptions = {
    size: { height: 4, width: 6 },
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the source pixel data in the buffer.
    pixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the new PixelMap.
    editable: true
  };
  image.createPixelMapUsingAllocator(color, opts, image.AllocatorType.AUTO).then((pixelMap: image.PixelMap) => {
    console.info('Succeeded in creating pixelmap.');
  }).catch((error: BusinessError) => {
    console.error("Failed to create pixelmap. code is ", error.code);
  })
}
```

## image.createPixelMapFromParcel<sup>11+</sup>

createPixelMapFromParcel(sequence: rpc.MessageSequence): PixelMap

Creates a PixelMap object from a MessageSequence object.

Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name                | Type                                                 | Mandatory| Description                                    |
| ---------------------- | ----------------------------------------------------- | ---- | ---------------------------------------- |
| sequence               | [rpc.MessageSequence](../apis-ipc-kit/js-apis-rpc.md#messagesequence9) | Yes  | MessageSequence object that stores the PixelMap information.     |

**Return value**

| Type                            | Description                 |
| -------------------------------- | --------------------- |
| [PixelMap](arkts-apis-image-PixelMap.md) | PixelMap object. If the operation fails, an error is thrown.|

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 62980096 | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.|
| 62980097 | IPC error. Possible cause: 1.IPC communication failed. 2. Image upload exception. 3. Decode process exception. 4. Insufficient memory.|
| 62980115 | Invalid input parameter.|
| 62980105 | Failed to get the data.|
| 62980177 | Abnormal API environment.|
| 62980178 | Failed to create the PixelMap.|
| 62980179 | Abnormal buffer size.|
| 62980180 | FD mapping failed. Possible cause: 1. Size and address does not match. 2. Memory map in memalloc failed.|
| 62980246 | Failed to read the PixelMap.|

**Example**

```ts
import { rpc } from '@kit.IPCKit';
import { BusinessError } from '@kit.BasicServicesKit';

class MySequence implements rpc.Parcelable {
  pixel_map: image.PixelMap;
  constructor(conPixelmap: image.PixelMap) {
    this.pixel_map = conPixelmap;
  }
  marshalling(messageSequence: rpc.MessageSequence) {
    this.pixel_map.marshalling(messageSequence);
    return true;
  }
  unmarshalling(messageSequence: rpc.MessageSequence) {
    try {
      this.pixel_map = image.createPixelMapFromParcel(messageSequence);
    } catch(e) {
      let error = e as BusinessError;
      console.error(`createPixelMapFromParcel error. code is ${error.code}, message is ${error.message}`);
      return false;
    }
    return true;
  }
}
async function CreatePixelMapFromParcel() {
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
  let pixelMap: image.PixelMap | undefined = undefined;
  await image.createPixelMap(color, opts).then((srcPixelMap: image.PixelMap) => {
    pixelMap = srcPixelMap;
  })
  if (pixelMap != undefined) {
    // Implement serialization.
    let parcelable: MySequence = new MySequence(pixelMap);
    let data: rpc.MessageSequence = rpc.MessageSequence.create();
    data.writeParcelable(parcelable);

    // Implement deserialization to obtain data through the RPC.
    let ret: MySequence = new MySequence(pixelMap);
    data.readParcelable(ret);

    // Obtain the PixelMap object.
    let newPixelmap = ret.pixel_map;
  }
}
```

## image.createPixelMapFromSurface<sup>11+</sup>

createPixelMapFromSurface(surfaceId: string, region: Region): Promise\<PixelMap>

Creates a PixelMap object based on the surface ID and region information. The size of the region is specified by [Region](arkts-apis-image-i.md#region8).size. This API returns the result asynchronously through a promise.

Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

> **NOTE**
> For foldable devices, during switching between folded and unfolded states, the API call may fail because of the built-in rotation angle of the surface. You need to adjust the width and height to match the rotation angle. You are advised to use [image.createPixelMapFromSurface](#imagecreatepixelmapfromsurface15).

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name                | Type                | Mandatory| Description                                    |
| ---------------------- | -------------       | ---- | ---------------------------------------- |
| surfaceId              | string              | Yes  | Surface ID, which can be obtained through the preview component, for example, [XComponent](../apis-arkui/arkui-ts/ts-basic-components-xcomponent.md).|
| region                 | [Region](arkts-apis-image-i.md#region8)  | Yes  | Area of the image to capture. Capture must start from the top-left corner of the screen, so **x** and **y** in **Region** must be **0**, and **Width** and **height** in **Region.size** must be within the range [1, preview stream width] and [1, preview stream height], respectively. To capture any area, first use [image.createPixelMapFromSurface](#imagecreatepixelmapfromsurface15) to obtain the full screen, and then use [crop](arkts-apis-image-PixelMap.md#crop9) to capture the desired area.|

**Return value**

| Type                            | Description                 |
| -------------------------------- | --------------------- |
| Promise\<[PixelMap](arkts-apis-image-PixelMap.md)> | Promise used to return the PixelMap object.|

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 62980115 | If the image parameter invalid.|
| 62980105 | Failed to get the data.|
| 62980178 | Failed to create the PixelMap.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMapFromSurface(surfaceId: string) {
  let region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  image.createPixelMapFromSurface(surfaceId, region).then(() => {
    console.info('Succeeded in creating pixelmap from Surface');
  }).catch((error: BusinessError) => {
    console.error(`Failed to create pixelmap. code is ${error.code}, message is ${error.message}`);
  });
} 
```

## image.createPixelMapFromSurfaceSync<sup>12+</sup>

createPixelMapFromSurfaceSync(surfaceId: string, region: Region): PixelMap

Creates a PixelMap object based on the surface ID and region information. This API returns the result synchronously. The size of the region is specified by [Region](arkts-apis-image-i.md#region8).size.

Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

> **NOTE**
> For foldable devices, during switching between folded and unfolded states, the API call may fail because of the built-in rotation angle of the surface. You need to adjust the width and height to match the rotation angle. In such cases, [image.createPixelMapFromSurfaceSync](#imagecreatepixelmapfromsurfacesync15) is recommended.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name                | Type                | Mandatory| Description                                    |
| ---------------------- | -------------       | ---- | ---------------------------------------- |
| surfaceId              | string              | Yes  | Surface ID, which can be obtained through the preview component, for example, [XComponent](../apis-arkui/arkui-ts/ts-basic-components-xcomponent.md).|
| region                 | [Region](arkts-apis-image-i.md#region8)  | Yes  | Area of the image to capture. Capture must start from the top-left corner of the screen, so **x** and **y** in **Region** must be **0**, and **Width** and **height** in **Region.size** must be within the range [1, preview stream width] and [1, preview stream height], respectively. To capture any area, first use [image.createPixelMapFromSurfaceSync](#imagecreatepixelmapfromsurfacesync15) to obtain the full screen, and then use [cropSync](arkts-apis-image-PixelMap.md#cropsync12) to capture the desired area.|

**Return value**

| Type                            | Description                 |
| -------------------------------- | --------------------- |
| [PixelMap](arkts-apis-image-PixelMap.md) | PixelMap object. If the operation fails, an error is thrown.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed.|
| 62980105 | Failed to get the data.|
| 62980178 | Failed to create the PixelMap.|

**Example**

```ts
async function Demo(surfaceId: string) {
  let region: image.Region = { x: 0, y: 0, size: { height: 100, width: 100 } };
  let pixelMap: image.PixelMap = image.createPixelMapFromSurfaceSync(surfaceId, region);
  return pixelMap;
}
```

## image.createPixelMapFromSurface<sup>15+</sup>

createPixelMapFromSurface(surfaceId: string): Promise\<PixelMap>

Creates a PixelMap object from a surface ID. This API returns the result asynchronously through a promise.

Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name                | Type                | Mandatory| Description                                    |
| ---------------------- | -------------       | ---- | ---------------------------------------- |
| surfaceId              | string              | Yes  | Surface ID, which can be obtained through the preview component, for example, [XComponent](../apis-arkui/arkui-ts/ts-basic-components-xcomponent.md).|

**Return value**

| Type                            | Description                 |
| -------------------------------- | --------------------- |
| Promise\<[PixelMap](arkts-apis-image-PixelMap.md)> | Promise used to return the PixelMap object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed|
| 62980105 | Failed to get the data|
| 62980178 | Failed to create the PixelMap|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMapFromSurface(surfaceId: string) {
  image.createPixelMapFromSurface(surfaceId).then(() => {
    console.info('Succeeded in creating pixelmap from Surface');
  }).catch((error: BusinessError) => {
    console.error(`Failed to create pixelmap. code is ${error.code}, message is ${error.message}`);
  });
} 
```

## image.createPixelMapFromSurfaceSync<sup>15+</sup>

createPixelMapFromSurfaceSync(surfaceId: string): PixelMap

Creates a PixelMap object from a surface ID. This API returns the result synchronously.

Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name                | Type                | Mandatory| Description                                    |
| ---------------------- | -------------       | ---- | ---------------------------------------- |
| surfaceId              | string              | Yes  | Surface ID, which can be obtained through the preview component, for example, [XComponent](../apis-arkui/arkui-ts/ts-basic-components-xcomponent.md).|

**Return value**

| Type                            | Description                 |
| -------------------------------- | --------------------- |
| [PixelMap](arkts-apis-image-PixelMap.md) | PixelMap object. If the operation fails, an error is thrown.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed|
| 62980105 | Failed to get the data|
| 62980178 | Failed to create the PixelMap|

**Example**

```ts
async function CreatePixelMapFromSurfaceSync(surfaceId: string) {
  let pixelMap : image.PixelMap = image.createPixelMapFromSurfaceSync(surfaceId);
  return pixelMap;
}
```

## image.createPixelMapFromSurfaceWithTransformation<sup>23+</sup>

createPixelMapFromSurfaceWithTransformation(surfaceId: string, transformEnabled: boolean): Promise\<PixelMap\>

Creates a PixelMap object for previewing a stream based on a surface ID. The surface may carry rotation or flipping information. This API returns the result asynchronously through a promise.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name                | Type          | Mandatory| Description                                    |
| ---------------------- | ------------- | ---- | ---------------------------------------- |
| surfaceId              | string        | Yes  | Surface ID, which can be obtained through the preview component, for example, [XComponent](../apis-arkui/arkui-ts/ts-basic-components-xcomponent.md).|
| transformEnabled       | boolean       | Yes  | Whether to perform inverse transformation on the surface that carries transformation information to eliminate the rotation or flipping effect of the PixelMap. If the surface does not carry transformation information, this parameter does not take effect.<br>If this parameter is set to **true**, the inverse transformation is performed. The transform angle matches the angle carried by the surface but in the opposite direction, and the output PixelMap has no rotation or flipping effect.<br>If this parameter is set to **false**, no inverse transformation is performed. The output PixelMap has the rotation or flipping effect based on the transformation information in the surface.|

**Return value**

| Type                            | Description                 |
| -------------------------------- | --------------------- |
| Promise\<[PixelMap](arkts-apis-image-PixelMap.md)\> | Promise used to return the PixelMap object.|

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 7600104 | Failed to get the data from Surface. |
| 7600201 | Unsupported operation, e.g. on cross-platform. |
| 7600206 | Invalid parameter. |
| 7600305 | Failed to create the PixelMap. |

**Example**

```ts
function DemoCreatePixelMapFromSurfaceWithTransformation(surfaceId: string, transformEnabled: boolean) {
  image.createPixelMapFromSurfaceWithTransformation(surfaceId, transformEnabled).then((pixelMap: image.PixelMap) => {
    console.info('PixelMap created successfully.');
  }).catch((e: Error) => {
    console.error(`Failed to create PixelMap. Code: ${e}`);
  });
}
```

## image.createPixelMapFromSurfaceWithTransformationSync<sup>23+</sup>

createPixelMapFromSurfaceWithTransformationSync(surfaceId: string, transformEnabled: boolean): PixelMap

Creates a PixelMap object for previewing a stream based on a surface ID. The surface may carry rotation or flipping information. This API returns the PixelMap object synchronously.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name                | Type          | Mandatory| Description                                    |
| ---------------------- | ------------- | ---- | ---------------------------------------- |
| surfaceId              | string        | Yes  | Surface ID, which can be obtained through the preview component, for example, [XComponent](../apis-arkui/arkui-ts/ts-basic-components-xcomponent.md).|
| transformEnabled       | boolean       | Yes  | Whether to perform inverse transformation on the surface that carries transformation information to eliminate the rotation or flipping effect of the PixelMap. If the surface does not carry transformation information, this parameter does not take effect.<br>If this parameter is set to **true**, the inverse transformation is performed. The transform angle matches the angle carried by the surface but in the opposite direction, and the output PixelMap has no rotation or flipping effect.<br>If this parameter is set to **false**, no inverse transformation is performed. The output PixelMap has the rotation or flipping effect based on the transformation information in the surface.|

**Return value**

| Type                            | Description                 |
| -------------------------------- | --------------------- |
| [PixelMap](arkts-apis-image-PixelMap.md) | If the operation is successful, a PixelMap is returned synchronously. If the operation fails, an error is thrown.|

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 7600104 | Failed to get the data from Surface. |
| 7600201 | Unsupported operation, e.g. on cross-platform. |
| 7600206 | Invalid parameter. |
| 7600305 | Failed to create the PixelMap. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function DemoCreatePixelMapFromSurfaceWithTransformationSync(surfaceId: string, transformEnabled: boolean) {
  try {
    const pixelMap: image.PixelMap = image.createPixelMapFromSurfaceWithTransformationSync(surfaceId, transformEnabled);
    console.info('PixelMap created successfully.');
  } catch (e) {
    const error = e as BusinessError;
    console.error(`Failed to create PixelMap. Code: ${error.code}, message: ${error.message}`);
  }
}
```

## image.createPixelMapSync<sup>12+</sup>

createPixelMapSync(colors: ArrayBuffer, options: InitializationOptions): PixelMap

Creates a PixelMap based on the pixel data and image properties. The input pixel data is parsed in BGRA_8888 format by default. This API returns the result synchronously.

Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

Since API version 26.0.0, you are advised to use [createPixelMapFromPixelsSync](#imagecreatepixelmapfrompixelssync) instead for better exception handling.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name | Type                                            | Mandatory| Description                                                            |
| ------- | ------------------------------------------------ | ---- | ---------------------------------------------------------------- |
| colors  | ArrayBuffer                                      | Yes  | Buffer for storing the pixel data. It is used to initialize the pixels of the PixelMap. Before initialization, the pixel format in the buffer must be specified by [InitializationOptions](arkts-apis-image-i.md#initializationoptions8).srcPixelFormat. If the pixel format is not specified, the BGRA_8888 format will be used by default.<br>**NOTE**: The length of the buffer required for storing the pixel data is determined by multiplying the width, height, and the number of bytes per pixel.|
| options | [InitializationOptions](arkts-apis-image-i.md#initializationoptions8) | Yes  | Pixel properties, including the alpha type, size, scale mode, pixel format, and editable.|

**Return value**

| Type                            | Description                 |
| -------------------------------- | --------------------- |
| [PixelMap](arkts-apis-image-PixelMap.md) | PixelMap object. If the operation fails, an error is thrown.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed|

**Example**

```ts
function CreatePixelMapSync() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to create. The value is calculated as follows: height * width *4.
  let opts: image.InitializationOptions = {
    size: { height: 4, width: 6 },
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the source pixel data in the buffer.
    pixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the new PixelMap.
    editable: true
  };
  let pixelMap : image.PixelMap = image.createPixelMapSync(color, opts);
  return pixelMap;
}
```

## image.createEmptyPixelMap

createEmptyPixelMap(param: InitializationOptions): PixelMap

Creates an empty PixelMap based on image properties.

> **NOTE**
>
> - This API cannot create PixelMaps of the ASTC_4x4 format.
> - Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Widget capability**: This API can be used in ArkTS widgets since API version 26.0.0.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name | Type                                            | Mandatory| Description                                                            |
| ------- | ------------------------------------------------ | ---- | ---------------------------------------------------------------- |
| param | [InitializationOptions](arkts-apis-image-i.md#initializationoptions8) | Yes  | Image properties, including the dimensions, pixel format, transparency type, scaling mode, and editability.<br>**Note:** If the pixel format is set to ASTC_4x4, the default pixel format defined in this type will be used.|

**Return value**

| Type                            | Description                                                                   |
| -------------------------------- | ----------------------------------------------------------------------- |
| [PixelMap](arkts-apis-image-PixelMap.md) | Promise used to return the created empty PixelMap.                                        |

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| Error Code| Error Message|
| ------ | --------------------------------------------|
| 7600206 | Invalid parameter. |
| 7600301 | Failed to allocate memory. Possible causes: 1. The resulting PixelMap size is too large. 2. The system is out of memory. |
| 7600305 | Failed to create the PixelMap. Possible cause: Internal data is corrupted. Please check the logs for detailed information. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function DemoCreateEmptyPixelMap() {
  const config: image.InitializationOptions = {
    size: { width: 6, height: 4 },
    pixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the new PixelMap.
    editable: true
  };

  try {
    const pixelMap = image.createEmptyPixelMap(config);
    console.info('Empty PixelMap created successfully.');
  } catch (e) {
    const error = e as BusinessError;
    console.error (`Failed to create the empty PixelMap. Error code: ${e.code}; Error message: ${e.message}`);
  }
}
```

## image.createPixelMapSync<sup>12+</sup>

createPixelMapSync(options: InitializationOptions): PixelMap

Creates an empty PixelMap based on image properties. This API returns the result synchronously.

Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

Since API version 26.0.0, you are advised to use [createEmptyPixelMap](#imagecreateemptypixelmap) instead for better exception handling.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name | Type                                            | Mandatory| Description                                                            |
| ------- | ------------------------------------------------ | ---- | ---------------------------------------------------------------- |
| options | [InitializationOptions](arkts-apis-image-i.md#initializationoptions8) | Yes  | Pixel properties, including the alpha type, size, scale mode, pixel format, and editable.|

**Return value**
| Type                            | Description                 |
| -------------------------------- | --------------------- |
| [PixelMap](arkts-apis-image-PixelMap.md) | PixelMap object. If the operation fails, an error is thrown.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401    | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed|

**Example**

```ts
function CreatePixelMapSync() {
  let opts: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 4, width: 6 } }
  let pixelMap : image.PixelMap = image.createPixelMapSync(opts);
  return pixelMap;
}
```

## image.createPixelMapUsingAllocatorSync<sup>20+</sup>

createPixelMapUsingAllocatorSync(colors: ArrayBuffer, param: InitializationOptions, allocatorType?: AllocatorType): PixelMap

Creates a PixelMap based on the pixel data and image properties. You can specify the memory type. This API returns the result synchronously.

Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name | Type                                            | Mandatory| Description                                                            |
| ------- | ------------------------------------------------ | ---- | ---------------------------------------------------------------- |
| colors  | ArrayBuffer                                      | Yes  | Buffer for storing the pixel data. It is used to initialize the pixels of the PixelMap. Before initialization, the pixel format in the buffer must be specified by [InitializationOptions](arkts-apis-image-i.md#initializationoptions8).srcPixelFormat.<br>**NOTE**: The length of the buffer required for storing the pixel data is determined by multiplying the width, height, and the number of bytes per pixel.|
| param | [InitializationOptions](arkts-apis-image-i.md#initializationoptions8) | Yes  | Pixel properties, including the alpha type, size, scale mode, pixel format, and editable.|
| allocatorType  | [AllocatorType](arkts-apis-image-e.md#allocatortype15)          | No  | Memory type for creating the PixelMap. The default memory type is **AllocatorType.AUTO**.<br> 1. **image.AllocatorType.AUTO**: The following formats are not supported for this memory type: UNKNOWN, YCBCR_P010, YCRCB_P010, and ASTC_4x4. For RGBA_1010102, DMA memory is allocated by default. For other formats (RGB_565, RGBA_8888, BGRA_8888, and RGBAF_16), DMA memory is allocated if the dimensions exceed 512*512; otherwise, shared memory is allocated.<br>2. **image.AllocatorType.DMA**: The formats RGBA_1010102, RGB_565, RGBA_8888, BGRA_8888, and RGBAF_16 support DMA memory types. Other formats do not support DMA memory types.<br>3. **image.AllocatorType.SHARED**: The formats UNKNOWN, RGBA_1010102, YCBCR_P010, YCRCB_P010, and ASTC_4x4 do not support shared memory. Other formats support shared memory.|

**Return value**

| Type                            | Description                 |
| -------------------------------- | --------------------- |
| [PixelMap](arkts-apis-image-PixelMap.md) | PixelMap object. If the operation fails, an error is thrown.|

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  7600201    | Unsupported operation. |
|  7600301    | Memory alloc failed. |
|  7600302    | Memory copy failed. |

**Example**

```ts
function CreatePixelMapSync() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to create. The value is calculated as follows: height * width *4.
  let opts: image.InitializationOptions = {
    size: { height: 4, width: 6 },
    srcPixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the source pixel data in the buffer.
    pixelFormat: image.PixelMapFormat.RGBA_8888, // Pixel format of the new PixelMap.
    editable: true
  };
  let pixelMap : image.PixelMap = image.createPixelMapUsingAllocatorSync(color, opts, image.AllocatorType.AUTO);
  return pixelMap;
}
```

## image.createPixelMapUsingAllocatorSync<sup>20+</sup>

createPixelMapUsingAllocatorSync(param: InitializationOptions, allocatorType?: AllocatorType): PixelMap

Creates an empty PixelMap based on the image properties. You can specify the memory type. This API returns the PixelMap object synchronously.

Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name | Type                                            | Mandatory| Description                                                            |
| ------- | ------------------------------------------------ | ---- | ---------------------------------------------------------------- |
| param | [InitializationOptions](arkts-apis-image-i.md#initializationoptions8) | Yes  | Pixel properties, including the alpha type, size, scale mode, pixel format, and editable.|
| allocatorType  | [AllocatorType](arkts-apis-image-e.md#allocatortype15)          | No  | Memory type for creating the PixelMap. The default memory type is **AllocatorType.AUTO**.<br> 1. **image.AllocatorType.AUTO**: The following formats are not supported for this memory type: UNKNOWN and ASTC_4x4. For RGBA_1010102, YCBCR_P010, and YCRCB_P010, DMA memory is allocated by default. For other formats (RGB_565, RGBA_8888, BGRA_8888, and RGBAF_16), DMA memory is allocated if the dimensions exceed 512*512; otherwise, shared memory is allocated.<br>2. **image.AllocatorType.DMA**: The formats RGB_565, RGBA_8888, BGRA_8888, RGBAF_16, RGBA_1010102, YCBCR_P010, and YCRCB_P010 support DMA memory type. Other formats do not support DMA memory type.<br>3. **image.AllocatorType.SHARED**: The formats UNKNOWN, RGBA_1010102, YCBCR_P010, YCRCB_P010, and ASTC_4x4 do not support shared memory. Other formats support shared memory.|

**Return value**

| Type                            | Description                 |
| -------------------------------- | --------------------- |
| [PixelMap](arkts-apis-image-PixelMap.md) | PixelMap object. If the operation fails, an error is thrown.|

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  7600201    | Unsupported operation.|
|  7600301    | Memory alloc failed. |

**Example**

```ts
function CreatePixelMapSync() {
  let opts: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 4, width: 6 } }
  let pixelMap : image.PixelMap = image.createPixelMapUsingAllocatorSync(opts, image.AllocatorType.AUTO);
  return pixelMap;
}
```

## image.createPremultipliedPixelMap<sup>12+</sup>

createPremultipliedPixelMap(src: PixelMap, dst: PixelMap, callback: AsyncCallback\<void>): void

Converts a non-premultiplied alpha of a PixelMap to a premultiplied one and stores the converted data to a target PixelMap. This API uses an asynchronous callback to return the result.

Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name  | Type                                            | Mandatory| Description                      |
| -------- | ------------------------------------------------ | ---- | -------------------------- |
| src | [PixelMap](arkts-apis-image-PixelMap.md) | Yes  | Source PixelMap object.|
| dst | [PixelMap](arkts-apis-image-PixelMap.md) | Yes  | Target PixelMap object.|
|callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401          | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed|
|  62980103     | The image data is not supported |
|  62980246      | Failed to read the pixelMap |
|  62980248     | Pixelmap not allow modify |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePremultipliedPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(16); // 16 is the size of the pixel buffer to create. The value is calculated as follows: height * width * 4.
  let bufferArr = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i += 4) {
    bufferArr[i] = 255;
    bufferArr[i+1] = 255;
    bufferArr[i+2] = 122;
    bufferArr[i+3] = 122;
  }
  let optsForUnpre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 } , alphaType: image.AlphaType.UNPREMUL}
  let srcPixelmap = image.createPixelMapSync(color, optsForUnpre);
  let optsForPre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 } , alphaType: image.AlphaType.PREMUL}
  let dstPixelMap = image.createPixelMapSync(optsForPre);
  image.createPremultipliedPixelMap(srcPixelmap, dstPixelMap, (error: BusinessError) => {
    if(error) {
      console.error(`Failed to convert pixelmap, error code is ${error}`);
      return;
    } else {
      console.info('Succeeded in converting pixelmap.');
    }
  })
}
```

## image.createPremultipliedPixelMap<sup>12+</sup>

createPremultipliedPixelMap(src: PixelMap, dst: PixelMap): Promise\<void>

Converts a non-premultiplied alpha of a PixelMap to a premultiplied one and stores the converted data to a target PixelMap. This API returns the result asynchronously through a promise.

Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name  | Type                                            | Mandatory| Description                      |
| -------- | ------------------------------------------------ | ---- | -------------------------- |
| src | [PixelMap](arkts-apis-image-PixelMap.md) | Yes  | Source PixelMap object.|
| dst | [PixelMap](arkts-apis-image-PixelMap.md) | Yes  | Target PixelMap object.|

**Return value**

| Type                            | Description                                                                   |
| -------------------------------- | ----------------------------------------------------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401          | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed|
|  62980103     | The image data is not supported |
|  62980246      | Failed to read the pixelMap |
|  62980248     | Pixelmap not allow modify |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePremultipliedPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(16); // 16 is the size of the pixel buffer to create. The value is calculated as follows: height * width * 4.
  let bufferArr = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i += 4) {
    bufferArr[i] = 255;
    bufferArr[i+1] = 255;
    bufferArr[i+2] = 122;
    bufferArr[i+3] = 122;
  }
  let optsForUnpre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 } , alphaType: image.AlphaType.UNPREMUL}
  let srcPixelmap = image.createPixelMapSync(color, optsForUnpre);
  let optsForPre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 } , alphaType: image.AlphaType.PREMUL}
  let dstPixelMap = image.createPixelMapSync(optsForPre);
  image.createPremultipliedPixelMap(srcPixelmap, dstPixelMap).then(() => {
    console.info('Succeeded in converting pixelmap.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to convert pixelmap, error code is ${error}`);
  })
}
```

## image.createUnpremultipliedPixelMap<sup>12+</sup>

createUnpremultipliedPixelMap(src: PixelMap, dst: PixelMap, callback: AsyncCallback\<void>): void

Converts a premultiplied alpha of a PixelMap to a non-premultiplied one and stores the converted data to a target PixelMap. This API uses an asynchronous callback to return the result.

Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name  | Type                                            | Mandatory| Description                      |
| -------- | ------------------------------------------------ | ---- | -------------------------- |
| src | [PixelMap](arkts-apis-image-PixelMap.md) | Yes  | Source PixelMap object.|
| dst | [PixelMap](arkts-apis-image-PixelMap.md) | Yes  | Target PixelMap object.|
|callback | AsyncCallback\<void> | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401          | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed|
|  62980103     | The image data is not supported |
|  62980246      | Failed to read the pixelMap |
|  62980248     | Pixelmap not allow modify |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreateUnpremultipliedPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(16); // 16 is the size of the pixel buffer to create. The value is calculated as follows: height * width * 4.
  let bufferArr = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i += 4) {
    bufferArr[i] = 255;
    bufferArr[i+1] = 255;
    bufferArr[i+2] = 122;
    bufferArr[i+3] = 122;
  }
  let optsForPre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 } , alphaType: image.AlphaType.PREMUL}
  let srcPixelmap = image.createPixelMapSync(color, optsForPre);
  let optsForUnpre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 } , alphaType: image.AlphaType.UNPREMUL}
  let dstPixelMap = image.createPixelMapSync(optsForUnpre);
  image.createUnpremultipliedPixelMap(srcPixelmap, dstPixelMap, (error: BusinessError) => {
    if(error) {
      console.error(`Failed to convert pixelmap, error code is ${error}`);
      return;
    } else {
      console.info('Succeeded in converting pixelmap.');
    }
  })
}
```

## image.createUnpremultipliedPixelMap<sup>12+</sup>

createUnpremultipliedPixelMap(src: PixelMap, dst: PixelMap): Promise\<void>

Converts a premultiplied alpha of a PixelMap to a non-premultiplied one and stores the converted data to a target PixelMap. This API returns the result asynchronously through a promise.

Images occupy a large amount of memory. When you finish using a PixelMap instance, call [release](./arkts-apis-image-PixelMap.md#release7) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name | Type                                            | Mandatory| Description                                                            |
| ------- | ------------------------------------------------ | ---- | ---------------------------------------------------------------- |
| src | [PixelMap](arkts-apis-image-PixelMap.md) | Yes  | Source PixelMap object.|
| dst | [PixelMap](arkts-apis-image-PixelMap.md) | Yes  | Target PixelMap object.|

**Return value**

| Type                            | Description                                                                   |
| -------------------------------- | ----------------------------------------------------------------------- |
| Promise\<void> |  Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
|  401          | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed.|
|  62980103    | The image data is not supported. |
|  62980246    | Failed to read the pixelMap. |
|  62980248    | Pixelmap not allow modify. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreateUnpremultipliedPixelMap() {
  const color: ArrayBuffer = new ArrayBuffer(16); // 16 is the size of the pixel buffer to create. The value is calculated as follows: height * width * 4.
  let bufferArr = new Uint8Array(color);
  for (let i = 0; i < bufferArr.length; i += 4) {
    bufferArr[i] = 255;
    bufferArr[i+1] = 255;
    bufferArr[i+2] = 122;
    bufferArr[i+3] = 122;
  }
  let optsForPre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 } , alphaType: image.AlphaType.PREMUL}
  let srcPixelmap = image.createPixelMapSync(color, optsForPre);
  let optsForUnpre: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 2, width: 2 } , alphaType: image.AlphaType.UNPREMUL}
  let dstPixelMap = image.createPixelMapSync(optsForUnpre);
  image.createUnpremultipliedPixelMap(srcPixelmap, dstPixelMap).then(() => {
    console.info('Succeeded in converting pixelmap.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to convert pixelmap, error code is ${error}`);
  })
}
```

## image.createImageSource

createImageSource(uri: string): ImageSource

Creates an ImageSource instance based on a given URI.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](./arkts-apis-image-ImageSource.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name| Type  | Mandatory| Description                              |
| ------ | ------ | ---- | ---------------------------------- |
| uri    | string | Yes  | Image path. Currently, only the application sandbox path is supported.<br>Currently, the following formats are supported: JPEG, PNG, GIF, BMP, WebP, DNG, HEIC<sup>12+</sup>, WBMP<sup>23+</sup>, HEIFS<sup>23+</sup>, TIFF<sup>23+</sup>, [SVG<sup>10+</sup>](#svg-tags), and ICO<sup>11+</sup>. Since API version 26.0.0, the AVIF and AVIS formats are supported.<br>Decoding support for certain formats depends on the specific device hardware. You are advised to use the [image.getImageSourceSupportedFormats](arkts-apis-image-f.md#imagegetimagesourcesupportedformats20) API before calling this API to dynamically query the decoding capabilities of the current device.|

**Return value**

| Type                       | Description                                        |
| --------------------------- | -------------------------------------------- |
| [ImageSource](arkts-apis-image-ImageSource.md) | ImageSource instance. If the operation fails, undefined is returned.|

**Example**
```ts
async function CreateImageSource(context : Context) {
  // 'test.jpg' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
  const path: string = context.filesDir + "/test.jpg";
  const imageSourceObj: image.ImageSource = image.createImageSource(path);
}
```

## image.createImageSource<sup>9+</sup>

createImageSource(uri: string, options: SourceOptions): ImageSource

Creates an ImageSource instance based on a given URI.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](./arkts-apis-image-ImageSource.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name | Type                           | Mandatory| Description                               |
| ------- | ------------------------------- | ---- | ----------------------------------- |
| uri     | string                          | Yes  | Image path. Currently, only the application sandbox path is supported.<br>Currently, the following formats are supported: JPEG, PNG, GIF, BMP, WebP, DNG, HEIC<sup>12+</sup>, WBMP<sup>23+</sup>, HEIFS<sup>23+</sup>, TIFF<sup>23+</sup>, [SVG<sup>10+</sup>](#svg-tags), and ICO<sup>11+</sup>. Since API version 26.0.0, the AVIF and AVIS formats are supported.<br>Decoding support for certain formats depends on the specific device hardware. You are advised to use the [image.getImageSourceSupportedFormats](arkts-apis-image-f.md#imagegetimagesourcesupportedformats20) API before calling this API to dynamically query the decoding capabilities of the current device.|
| options | [SourceOptions](arkts-apis-image-i.md#sourceoptions9) | Yes  | Image properties, including the image pixel density, pixel format, and image size.|

**Return value**

| Type                       | Description                                        |
| --------------------------- | -------------------------------------------- |
| [ImageSource](arkts-apis-image-ImageSource.md) | ImageSource instance. If the operation fails, undefined is returned.|

**Example**

```ts
async function CreateImageSource(context : Context) {
  let sourceOptions: image.SourceOptions = { sourceDensity: 120 };
  // 'test.png' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
  const path: string = context.filesDir + "/test.png";
  let imageSourceObj: image.ImageSource = image.createImageSource(path, sourceOptions);
}
```

## image.createImageSource<sup>7+</sup>

createImageSource(fd: number): ImageSource

Creates an ImageSource instance based on a given file descriptor.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](./arkts-apis-image-ImageSource.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name| Type  | Mandatory| Description         |
| ------ | ------ | ---- | ------------- |
| fd     | number | Yes  | File descriptor.|

**Return value**

| Type                       | Description                                        |
| --------------------------- | -------------------------------------------- |
| [ImageSource](arkts-apis-image-ImageSource.md) | ImageSource instance. If the operation fails, undefined is returned.|

**Example**

```ts
import { fileIo } from '@kit.CoreFileKit';

async function CreateImageSource(context : Context) {
  // 'test.jpg' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
  let filePath: string = context.filesDir + "/test.jpg";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
  const imageSourceObj: image.ImageSource = image.createImageSource(file.fd);
}
```

## image.createImageSource<sup>9+</sup>

createImageSource(fd: number, options: SourceOptions): ImageSource

Creates an ImageSource instance based on a given file descriptor.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](./arkts-apis-image-ImageSource.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name | Type                           | Mandatory| Description                               |
| ------- | ------------------------------- | ---- | ----------------------------------- |
| fd      | number                          | Yes  | File descriptor.                     |
| options | [SourceOptions](arkts-apis-image-i.md#sourceoptions9) | Yes  | Image properties, including the image pixel density, pixel format, and image size.|

**Return value**

| Type                       | Description                                        |
| --------------------------- | -------------------------------------------- |
| [ImageSource](arkts-apis-image-ImageSource.md) | ImageSource instance. If the operation fails, undefined is returned.|

**Example**

```ts
import { fileIo } from '@kit.CoreFileKit';

async function CreateImageSource(context : Context) {
  let sourceOptions: image.SourceOptions = { sourceDensity: 120 };
  // 'test.jpg' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
  const filePath: string = context.filesDir + "/test.jpg";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
  const imageSourceObj: image.ImageSource = image.createImageSource(file.fd, sourceOptions);
}
```

## image.createImageSource<sup>9+</sup>

createImageSource(buf: ArrayBuffer): ImageSource

Creates an ImageSource instance based on buffers. The data passed by **buf** must be undecoded. Do not pass the pixel buffer data such as RBGA and YUV. If you want to create a PixelMap based on the pixel buffer data, call [image.createPixelMapSync](./arkts-apis-image-f.md#imagecreatepixelmapsync12).

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](./arkts-apis-image-ImageSource.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name| Type       | Mandatory| Description            |
| ------ | ----------- | ---- | ---------------- |
| buf    | ArrayBuffer | Yes  | Array of image buffers.|

**Return value**

| Type                       | Description                                        |
| --------------------------- | -------------------------------------------- |
| [ImageSource](arkts-apis-image-ImageSource.md) | ImageSource instance. If the operation fails, undefined is returned.|

**Example**

```ts
async function CreateImageSource() {
  const buf: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to create. The value is calculated as follows: height * width *4.
  const imageSourceObj: image.ImageSource = image.createImageSource(buf);
}
```

## image.createImageSource<sup>9+</sup>

createImageSource(buf: ArrayBuffer, options: SourceOptions): ImageSource

Creates an ImageSource instance based on buffers. The data passed by **buf** must be undecoded. Do not pass the pixel buffer data such as RBGA and YUV. If you want to create a PixelMap based on the pixel buffer data, call [image.createPixelMapSync](./arkts-apis-image-f.md#imagecreatepixelmapsync12).

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](./arkts-apis-image-ImageSource.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name| Type                            | Mandatory| Description                                |
| ------ | -------------------------------- | ---- | ------------------------------------ |
| buf    | ArrayBuffer                      | Yes  | Array of image buffers.                    |
| options | [SourceOptions](arkts-apis-image-i.md#sourceoptions9) | Yes  | Image properties, including the image pixel density, pixel format, and image size.|

**Return value**

| Type                       | Description                                        |
| --------------------------- | -------------------------------------------- |
| [ImageSource](arkts-apis-image-ImageSource.md) | ImageSource instance. If the operation fails, undefined is returned.|

**Example**

```ts
async function CreateImageSource() {
  const data: ArrayBuffer = new ArrayBuffer(112);
  let sourceOptions: image.SourceOptions = { sourceDensity: 120 };
  const imageSourceObj: image.ImageSource = image.createImageSource(data, sourceOptions);
}
```

## image.createImageSource<sup>11+</sup>

createImageSource(rawfile: resourceManager.RawFileDescriptor, options?: SourceOptions): ImageSource

Creates an ImageSource instance based on the raw file descriptor of an image resource file.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](./arkts-apis-image-ImageSource.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name| Type                            | Mandatory| Description                                |
| ------ | -------------------------------- | ---- | ------------------------------------ |
| rawfile | [resourceManager.RawFileDescriptor](../apis-localization-kit/js-apis-resource-manager.md#rawfiledescriptor9) | Yes| Raw file descriptor of the image resource file.|
| options | [SourceOptions](arkts-apis-image-i.md#sourceoptions9) | No| Image properties, including the image pixel density, pixel format, and image size.|

**Return value**

| Type                       | Description                                        |
| --------------------------- | -------------------------------------------- |
| [ImageSource](arkts-apis-image-ImageSource.md) | ImageSource instance. If the operation fails, undefined is returned.|

**Example**

```ts
import { resourceManager } from '@kit.LocalizationKit';
import { BusinessError } from '@kit.BasicServicesKit';
  
async function CreateImageSource(context : Context) {
  // Obtain a resource manager.
  const resourceMgr: resourceManager.ResourceManager = context.resourceManager;
  // 'test.jpg' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
  resourceMgr.getRawFd('test.jpg').then((rawFileDescriptor: resourceManager.RawFileDescriptor) => {
    const imageSourceObj: image.ImageSource = image.createImageSource(rawFileDescriptor);
  }).catch((error: BusinessError) => {
    console.error(`Failed to get RawFileDescriptor.code is ${error.code}, message is ${error.message}`);
  })
}
```

## image.CreateIncrementalSource<sup>9+</sup>

CreateIncrementalSource(buf: ArrayBuffer): ImageSource

Creates an ImageSource instance in incremental mode based on buffers. Such an instance does not support reading or writing of Exif information.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](./arkts-apis-image-ImageSource.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

The ImageSource instance created in incremental mode supports the following capabilities (applicable to synchronous, callback, and promise modes):

- Obtaining image information: Call [getImageInfo](arkts-apis-image-ImageSource.md#getimageinfo) to obtain image information by index, or call [getImageInfo](arkts-apis-image-ImageSource.md#getimageinfo-1) to directly obtain image information.
- Obtaining an image property: Call [getImageProperty](arkts-apis-image-ImageSource.md#getimageproperty11) to obtain the value of a property with the specified index in an image.
- Obtaining image properties: Call [getImageProperties](arkts-apis-image-ImageSource.md#getimageproperties12) to obtain the values of properties with the given names in an image.
- Updating incremental data: Call [updateData](arkts-apis-image-ImageSource.md#updatedata9).
- Creating a PixelMap object: Call [createPixelMap](arkts-apis-image-ImageSource.md#createpixelmap7) or [createPixelMap](arkts-apis-image-ImageSource.md#createpixelmap7-2) to create a PixelMap object based on decoding options; call [createPixelMap](arkts-apis-image-ImageSource.md#createpixelmap7-1) to create a PixelMap object based on default parameters.
- Releasing an ImageSource instance: Call [release](arkts-apis-image-ImageSource.md#release).

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name | Type       | Mandatory| Description     |
| ------- | ------------| ---- | ----------|
| buf     | ArrayBuffer | Yes  | Incremental data.|

**Return value**

| Type                       | Description                             |
| --------------------------- | --------------------------------- |
| [ImageSource](arkts-apis-image-ImageSource.md) | ImageSource instance. If the operation fails, undefined is returned.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreateIncrementalImageSource(context : Context) {
  let imageArray = context.resourceManager.getMediaContentSync($r('app.media.startIcon').id); // Obtain the image resource.
  // 'app.media.startIcon' is only an example. Replace it with the actual one in use. Otherwise, the imageArray instance fails to be created, and subsequent operations cannot be performed.
  let splitBuff1 = imageArray.slice(0, imageArray.byteLength / 2);  // Image slice.
  let splitBuff2 = imageArray.slice(imageArray.byteLength / 2);
  const imageSourceIncrementalSApi: image.ImageSource = image.CreateIncrementalSource(new ArrayBuffer(imageArray.byteLength));
  imageSourceIncrementalSApi.updateData(splitBuff1, false, 0, splitBuff1.byteLength).then(() => {
    imageSourceIncrementalSApi.updateData(splitBuff2, true, 0, splitBuff2.byteLength).then(() => {
      let pixelMap = imageSourceIncrementalSApi.createPixelMapSync();
      let imageInfo = pixelMap.getImageInfoSync();
      console.info('Succeeded in creating pixelMap');
    }).catch((error : BusinessError) => {
      console.error(`Failed to updateData error code is ${error.code}, message is ${error.message}`);
    })
  }).catch((error : BusinessError) => {
    console.error(`Failed to updateData error code is ${error.code}, message is ${error.message}`);
  })
}
```

## image.CreateIncrementalSource<sup>9+</sup>

CreateIncrementalSource(buf: ArrayBuffer, options?: SourceOptions): ImageSource

Creates an ImageSource instance in incremental mode based on buffers. Such an instance does not support reading or writing of Exif information.

The capabilities supported by the ImageSource instance created by this API are the same as those supported by the instance created by [CreateIncrementalSource(buf: ArrayBuffer): ImageSource](#imagecreateincrementalsource9).

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](./arkts-apis-image-ImageSource.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Parameters**

| Name | Type                           | Mandatory| Description                                |
| ------- | ------------------------------- | ---- | ------------------------------------ |
| buf     | ArrayBuffer                     | Yes  | Incremental data.                          |
| options | [SourceOptions](arkts-apis-image-i.md#sourceoptions9) | No  | Image properties, including the image pixel density, pixel format, and image size.|

**Return value**

| Type                       | Description                             |
| --------------------------- | --------------------------------- |
| [ImageSource](arkts-apis-image-ImageSource.md) | ImageSource instance. If the operation fails, undefined is returned.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreateIncrementalImageSource(context : Context) {
  let imageArray = context.resourceManager.getMediaContentSync($r('app.media.startIcon').id); // Obtain the image resource.
  // 'app.media.startIcon' is only an example. Replace it with the actual one in use. Otherwise, the imageArray instance fails to be created, and subsequent operations cannot be performed.
  let splitBuff1 = imageArray.slice(0, imageArray.byteLength / 2);  // Image slice.
  let splitBuff2 = imageArray.slice(imageArray.byteLength / 2);
  let sourceOptions: image.SourceOptions = { sourceDensity: 120};

  const imageSourceIncrementalSApi: image.ImageSource = image.CreateIncrementalSource(new ArrayBuffer(imageArray.byteLength), sourceOptions);
  imageSourceIncrementalSApi.updateData(splitBuff1, false, 0, splitBuff1.byteLength).then(() => {
    imageSourceIncrementalSApi.updateData(splitBuff2, true, 0, splitBuff2.byteLength).then(() => {
      let pixelMap = imageSourceIncrementalSApi.createPixelMapSync();
      let imageInfo = pixelMap.getImageInfoSync();
      console.info('Succeeded in creating pixelMap');
    }).catch((error : BusinessError) => {
      console.error(`Failed to updateData error code is ${error.code}, message is ${error.message}`);
    })
  }).catch((error : BusinessError) => {
    console.error(`Failed to updateData error code is ${error.code}, message is ${error.message}`);
  })
}
```

## image.getImageSourceSupportedFormats<sup>20+</sup>

getImageSourceSupportedFormats(): string[]

Obtains the supported decoding formats, represented by MIME types.

**System capability**: SystemCapability.Multimedia.Image.ImageSource

**Return value**

| Type    | Description                                      |
| -------- | ------------------------------------------ |
| string[] | List of supported decoding formats (MIME types).|

**Example**

```ts
async function GetImageSourceSupportedFormats() {
    let formats = image.getImageSourceSupportedFormats();
    console.info('formats:', formats);
}

async function IsSupportedTiffFormat() {
    let formats = image.getImageSourceSupportedFormats();
    return formats.includes("image/tiff");
}

```

## image.createImagePacker

createImagePacker(): ImagePacker

Creates an ImagePacker instance.

Images occupy a large amount of memory. When you finish using an ImagePacker instance, call [release](./arkts-apis-image-ImagePacker.md#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Multimedia.Image.ImagePacker

**Return value**

| Type                       | Description                 |
| --------------------------- | --------------------- |
| [ImagePacker](arkts-apis-image-ImagePacker.md) | ImagePacker instance created.|

**Example**

```ts
async function CreateImagePacker() {
  const imagePackerObj: image.ImagePacker = image.createImagePacker();
}
```

## image.getImagePackerSupportedFormats<sup>20+</sup>

getImagePackerSupportedFormats(): string[]

Obtains the supported encoding formats, represented by MIME types.

**System capability**: SystemCapability.Multimedia.Image.ImagePacker

**Return value**

| Type    | Description                                      |
| -------- | ------------------------------------------ |
| string[] | List of supported encoding formats (MIME types).|

**Example**

```ts
async function GetImagePackerSupportedFormats() {
    let formats = image.getImagePackerSupportedFormats();
    console.info('formats:', formats);
}
```

## image.createAuxiliaryPicture<sup>13+</sup>

createAuxiliaryPicture(buffer: ArrayBuffer, size: Size, type: AuxiliaryPictureType): AuxiliaryPicture

Creates an AuxiliaryPicture instance based on the ArrayBuffer image data, auxiliary picture size, and auxiliary picture type. This API accepts only continuous pixel data in BGRA format and will create an auxiliary picture in RGBA format.

Images occupy a large amount of memory. When you finish using an AuxiliaryPicture instance, call [release](./arkts-apis-image-AuxiliaryPicture.md#release13) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name| Type                                           | Mandatory| Description                        |
| ------ | ----------------------------------------------- | ---- | ---------------------------- |
| buffer | ArrayBuffer                                     | Yes  | Image data stored in the buffer. |
| size   | [Size](arkts-apis-image-i.md#size)                                   | Yes  | Size of the auxiliary picture, in px.   |
| type   | [AuxiliaryPictureType](arkts-apis-image-e.md#auxiliarypicturetype13) | Yes  | Type of the auxiliary picture.                |

**Return value**

| Type                                   | Description                                      |
| --------------------------------------- | ------------------------------------------ |
| [AuxiliaryPicture](arkts-apis-image-AuxiliaryPicture.md) | AuxiliaryPicture instance.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes:1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |

**Example**

```ts
async function CreateAuxiliaryPicture(context: Context) {
  let funcName = "CreateAuxiliaryPicture";
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("hdr.jpg"); // An HDR-compatible image is required.
  let auxBuffer: ArrayBuffer = rawFile.buffer as ArrayBuffer;
  let auxSize: Size = {
    height: 180,
    width: 240
  };
  let auxType: image.AuxiliaryPictureType = image.AuxiliaryPictureType.GAINMAP;
  let auxPictureObj: image.AuxiliaryPicture | null = image.createAuxiliaryPicture(auxBuffer, auxSize, auxType);
  if(auxPictureObj != null) {
    let type: image.AuxiliaryPictureType = auxPictureObj.getType();
    console.info(funcName, `CreateAuxiliaryPicture succeeded this.Aux_picture.type ${type}`);
  } else {
    console.error(funcName, 'CreateAuxiliaryPicture failed');
  }
}
```

## image.createAuxiliaryPictureUsingAllocator<sup>24+</sup>

createAuxiliaryPictureUsingAllocator(auxiliaryPictureInfo: AuxiliaryPictureInfo, allocatorType?: AllocatorType, pixels?: ArrayBuffer): AuxiliaryPicture

Creates an auxiliary picture object based on the auxiliary picture information and pixel data using the specified memory type.

> **NOTE**
>
> - When processing **AuxiliaryPicture** returned by this API, the space occupied by each row of pixels in memory must be taken into account.
> - The created auxiliary picture is initialized using the input pixels.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.Core

**Parameters**

| Name|              Type            | Mandatory| Description                        |
| ------ | ----------------------------------------------- | ---- | ---------------------------- |
| auxiliaryPictureInfo | [AuxiliaryPictureInfo](arkts-apis-image-i.md#auxiliarypictureinfo13) | Yes| Auxiliary picture information.<br>- The pixel format of the input ArrayBuffer and the actual pixel format of the created auxiliary picture must be consistent with that specified in **auxiliaryPictureInfo**.<br>- If **AuxiliaryPictureType** is **GAINMAP**, **AllocatorType** can only be set to **AUTO** or **DMA**.<br>- If **SHARE_MEMORY** is passed, error code 7600205 is returned. |
| allocatorType | [AllocatorType](arkts-apis-image-e.md#allocatortype15) | No| Memory type for image decoding. **DMA** is used if **AUTO** or the default value is passed. |
| pixels | ArrayBuffer | No| Image data stored in the buffer.<br>If **ArrayBuffer** is not provided, a blank auxiliary picture is created by default. |

**Return value**

| Type                                   | Description                                      |
| --------------------------------------- | ------------------------------------------ |
| [AuxiliaryPicture](arkts-apis-image-AuxiliaryPicture.md) | AuxiliaryPicture instance.|

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID| Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 7600205  | Unsupported allocator type,e.g., use shared memory to create a gainmap as only DMA supported hdr metadata. |
| 7600206  | Invalid parameter, size.height or size.width is less than or equal to 0. |
| 7600301  | Alloc memory failed. |

**Example**

```ts
import { image } from '@kit.ImageKit';

function CreateAuxiliaryPictureUsingAllocator(info: image.AuxiliaryPictureInfo,  allocatorType?: image.AllocatorType, pixels?: ArrayBuffer ) {
  let res : image.AuxiliaryPicture;
  try {
    res = image.createAuxiliaryPictureUsingAllocator(info, allocatorType, pixels);
  } catch (error) {
    console.error(`Failed to create auxiliary picture using allocator=${allocatorType} and pixels=${pixels?.byteLength}.`);
  }
}
```

## image.createImageReceiver<sup>11+</sup>

createImageReceiver(size: Size, format: ImageFormat, capacity: number): ImageReceiver

Creates an ImageReceiver instance by specifying the image size, format, and capacity. The ImageReceiver object acts as the receiver and consumer of images. Its parameter properties do not actually affect the received images. The configuration of image properties should be done on the sending side (the producer), such as when creating a camera preview stream with [createPreviewOutput](../apis-camera-kit/arkts-apis-camera-CameraManager.md#createpreviewoutput).

Images occupy a large amount of memory. When you finish using an ImageReceiver instance, call [release](./arkts-apis-image-ImageReceiver.md#release9) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Parameters**

| Name  | Type  | Mandatory| Description                  |
| -------- | ------ | ---- | ---------------------- |
| size    | [Size](arkts-apis-image-i.md#size)  | Yes  | Default size of the image. This parameter does not affect the size of the received image. The actual returned size is determined by the producer, for example, the camera.      |
| format   | [ImageFormat](arkts-apis-image-e.md#imageformat9) | Yes  | Image format, which is a constant of [ImageFormat](arkts-apis-image-e.md#imageformat9). (Currently, only **ImageFormat:JPEG** is supported. The format actually returned is determined by the producer, for example, camera.)            |
| capacity | number | Yes  | Maximum number of images that can be accessed at the same time. This parameter is used only as an expected value. The actual capacity is determined by the device hardware.|

**Return value**

| Type                            | Description                                   |
| -------------------------------- | --------------------------------------- |
| [ImageReceiver](arkts-apis-image-ImageReceiver.md) | ImageReceiver instance.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401| Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;   |

**Example**

```ts
let size: image.Size = {
  height: 8192,
  width: 8192
}
let receiver: image.ImageReceiver = image.createImageReceiver(size, image.ImageFormat.JPEG, 8);
```

## image.createImageReceiver<sup>23+</sup>

createImageReceiver(options?: ImageReceiverOptions): ImageReceiver | undefined

Creates an ImageReceiver instance using ImageReceiverOptions. The ImageReceiver object acts as the receiver and consumer of images. Its properties do not actually affect the received images. The configuration of image properties should be done on the sending side (the producer), such as when creating a camera preview stream with [createPreviewOutput](../apis-camera-kit/arkts-apis-camera-CameraManager.md#createpreviewoutput).

Images occupy a large amount of memory. When you finish using an ImageReceiver instance, call [release](./arkts-apis-image-ImageReceiver.md#release9) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Parameters**

| Name  | Type  | Mandatory| Description                  |
| -------- | ------ | ---- | ---------------------- |
| options  | [ImageReceiverOptions](arkts-apis-image-i.md#imagereceiveroptions23)  | No  | Options for creating an ImageReceiver object, including the default image size and the maximum number of images that can be accessed concurrently.<br>If **options** is not passed, the default size is 1920 × 1080, in pixels, indicating that the expected image width is 1920 pixels and height is 1080 pixels.<br>If **options** is not passed, the default value of **capacity** is 3, indicating that the expected maximum number of concurrent images pending read is three.      |

**Return value**

| Type                            | Description                                   |
| -------------------------------- | --------------------------------------- |
| [ImageReceiver](arkts-apis-image-ImageReceiver.md) \| undefined | If the operation is successful, the ImageReceiver object is returned. Otherwise, **undefined** is returned.|

**Error codes**

For details about the error codes, see [Image Error Codes](errorcode-image.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 7900201| Invalid parameter.   |

**Example**

```ts
let options: image.ImageReceiverOptions = {
  size: { width: 480, height: 480 },
  capacity: 3
}
let receiver: image.ImageReceiver | undefined = image.createImageReceiver(options);
```

## image.createImageCreator<sup>11+</sup>

createImageCreator(size: Size, format: ImageFormat, capacity: number): ImageCreator

Creates an ImageCreator instance by specifying the image size, format, and capacity.

Images occupy a large amount of memory. When you finish using an ImageCreator instance, call [release](./arkts-apis-image-ImageCreator.md#release9) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**System capability**: SystemCapability.Multimedia.Image.ImageCreator

**Parameters**

| Name  | Type  | Mandatory| Description                  |
| -------- | ------ | ---- | ---------------------- |
| size    | [Size](arkts-apis-image-i.md#size)  | Yes  | Default size of the image.      |
| format   | [ImageFormat](arkts-apis-image-e.md#imageformat9) | Yes  | Image format, for example, YCBCR_422_SP or JPEG.            |
| capacity | number | Yes  | Maximum number of images that can be accessed at the same time. This parameter is used only as an expected value. The actual capacity is determined by the device hardware.|

**Return value**

| Type                          | Description                                   |
| ------------------------------ | --------------------------------------- |
| [ImageCreator](arkts-apis-image-ImageCreator.md) | ImageCreator instance.|


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401| Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;          |

**Example**

```ts
let size: image.Size = {
  height: 8192,
  width: 8192
}
let creator: image.ImageCreator = image.createImageCreator(size, image.ImageFormat.JPEG, 8);
```

## image.createImageReceiver<sup>(deprecated)</sup>

createImageReceiver(width: number, height: number, format: number, capacity: number): ImageReceiver

Creates an ImageReceiver instance by specifying the image width, height, format, and capacity. The ImageReceiver object acts as the receiver and consumer of images. Its parameter properties do not actually affect the received images. The configuration of image properties should be done on the sending side (the producer), such as when creating a camera preview stream with [createPreviewOutput](../apis-camera-kit/arkts-apis-camera-CameraManager.md#createpreviewoutput).

Images occupy a large amount of memory. When you finish using an ImageReceiver instance, call [release](./arkts-apis-image-ImageReceiver.md#release9) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

> **NOTE**
>
> This API is supported since API version 9 and is deprecated since API version 11. You are advised to use [createImageReceiver](#imagecreateimagereceiver11) instead.

**System capability**: SystemCapability.Multimedia.Image.ImageReceiver

**Parameters**

| Name  | Type  | Mandatory| Description                  |
| -------- | ------ | ---- | ---------------------- |
| width    | number | Yes  | Default image width, in px. This parameter does not affect the width of the received image. The actual width is determined by the producer, for example, the camera.      |
| height   | number | Yes  | Default image height, in px. This parameter does not affect the height of the received image. The actual height is determined by the producer, for example, the camera.      |
| format   | number | Yes  | Image format, which is a constant of [ImageFormat](arkts-apis-image-e.md#imageformat9). (Currently, only **ImageFormat:JPEG** is supported. The format actually returned is determined by the producer, for example, camera.) |
| capacity | number | Yes  | Maximum number of images that can be accessed at the same time. This parameter is used only as an expected value. The actual capacity is determined by the device hardware.|

**Return value**

| Type                            | Description                                   |
| -------------------------------- | --------------------------------------- |
| [ImageReceiver](arkts-apis-image-ImageReceiver.md) | ImageReceiver instance.|

**Example**

```ts
let receiver: image.ImageReceiver = image.createImageReceiver(8192, 8192, image.ImageFormat.JPEG, 8);
```

## image.createImageCreator<sup>(deprecated)</sup>

createImageCreator(width: number, height: number, format: number, capacity: number): ImageCreator

Creates an ImageCreator instance by specifying the image width, height, format, and capacity.

Images occupy a large amount of memory. When you finish using an ImageCreator instance, call [release](./arkts-apis-image-ImageCreator.md#release9) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

> **NOTE**
>
> This API is supported since API version 9 and is deprecated since API version 11. You are advised to use [createImageCreator](#imagecreateimagecreator11) instead.

**System capability**: SystemCapability.Multimedia.Image.ImageCreator

**Parameters**

| Name  | Type  | Mandatory| Description                  |
| -------- | ------ | ---- | ---------------------- |
| width    | number | Yes  | Default image width, in px.      |
| height   | number | Yes  | Default image height, in px.      |
| format   | number | Yes  | Image format, for example, YCBCR_422_SP or JPEG.            |
| capacity | number | Yes  | Maximum number of images that can be accessed at the same time. This parameter is used only as an expected value. The actual capacity is determined by the device hardware.|

**Return value**

| Type                          | Description                                   |
| ------------------------------ | --------------------------------------- |
| [ImageCreator](arkts-apis-image-ImageCreator.md) | ImageCreator instance.|

**Example**

```ts
let creator: image.ImageCreator = image.createImageCreator(8192, 8192, image.ImageFormat.JPEG, 8);
```

## SVG Tags

The SVG tags are supported since API version 10. The used version is (SVG) 1.1, and the width and height of the SVG tag must be set. An XML declaration can be added to an SVG file and start with **<?xml**. The following tags are supported:

- a
- circle
- clipPath
- defs
- ellipse
- feBlend
- feColorMatrix
- feComposite
- feDiffuseLighting
- feDisplacementMap
- feDistantLight
- feFlood
- feGaussianBlur
- feImage
- feMorphology
- feOffset
- fePointLight
- feSpecularLighting
- feSpotLight
- feTurbulence
- filter
- g
- image
- line
- linearGradient
- mask
- path
- pattern
- polygon
- polyline
- radialGradient
- rect
- stop
- svg
- text
- textPath
- tspan
- use
