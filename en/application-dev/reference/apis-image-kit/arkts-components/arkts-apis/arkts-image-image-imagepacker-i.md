# ImagePacker

```TypeScript
interface ImagePacker
```

The **ImagePacker** class provides APIs to compress and encode images.

Before calling any API in ImagePacker, you must use [image.createImagePacker](arkts-image-image-createimagepacker-f.md) to create an ImagePacker instance. During encoding, do not modify or release the ImageSource, PixelMap, or Picture object that is being used as the input. Otherwise, a crash or other undefined behavior may occur.

Images occupy a large amount of memory. When you finish using an ImagePacker instance, call [release](#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

Currently, the following formats are supported: jpeg, webp, png, heic&lt;sup&gt;12+&lt;/sup&gt;, and gif&lt;sup&gt;18+&lt;/sup&gt;. (The supported formats may vary depending on the hardware. You can refer to the **supportedFormats** property of ImagePacker to see which ones are supported.)

**Since:** 6

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## packBinaryImageToTiffData

```TypeScript
packBinaryImageToTiffData(bufferInfo: BinaryBufferInfo, options?: PackingOptionsForTiff): Promise<ArrayBuffer>
```

Compresses or packs an image into a file and uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bufferInfo | [BinaryBufferInfo](arkts-image-image-binarybufferinfo-i.md) | Yes | image buffer info. |
| options | [PackingOptionsForTiff](arkts-image-image-packingoptionsfortiff-i.md) | No | Options for tiff image packing. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | A Promise instance used to return the compressed or packed data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7800202](../errorcode-image.md#7800202-invalid-imagepacker-parameter) | Invalid parameter. Possible causes: 1. Invalid FD; 2. Compression algorithm mismatch. |
| [7800301](../errorcode-image.md#7800301-encoding-failure) | Encode failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { image } from '@kit.ImageKit';

const DOMAIN = 0X00000;
const TAG: string = 'PackBinaryImageToTiffData';

async function PackBinaryImageToTiffData() {
  const width = 100;
  const height = 100;
  const rowBytes = 13;
  const bufferSize = rowBytes * height;
  const data: ArrayBuffer = new ArrayBuffer(bufferSize);

  let bufferInfo: image.BinaryBufferInfo = {
    size: { width: width, height: height },
    data: data,
    bytesPerRow: rowBytes
  };

  let tiffOptions: image.PackingOptionsForTiff = {
    compression: 4 // CCITT G4 compression.
  };

  const imagePackerObj: image.ImagePacker = image.createImagePacker();
  await imagePackerObj.packBinaryImageToTiffData(bufferInfo, tiffOptions)
    .then((data: ArrayBuffer) => {
      hilog.info(DOMAIN, TAG, 'Succeeded in packing binary image to tiff data.');
    }).catch((error: BusinessError) => {
      hilog.error(DOMAIN, TAG, `Failed to pack binary image to tiff data. code ${error.code}, message is ${error.message}`);
    });
}
```

## packBinaryImageToTiffFile

```TypeScript
packBinaryImageToTiffFile(bufferInfo: BinaryBufferInfo, fd: number, options?: PackingOptionsForTiff): Promise<void>
```

Compresses or packs an image into a file and uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bufferInfo | [BinaryBufferInfo](arkts-image-image-binarybufferinfo-i.md) | Yes | image buffer info. |
| fd | number | Yes | ID of a file descriptor<br>The value must be a positive integer. |
| options | [PackingOptionsForTiff](arkts-image-image-packingoptionsfortiff-i.md) | No | Options for tiff image packing. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | A Promise instance used to return the operation result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7800202](../errorcode-image.md#7800202-invalid-imagepacker-parameter) | Invalid parameter. Possible causes: 1. Invalid FD; 2. Compression algorithm mismatch. |
| [7800301](../errorcode-image.md#7800301-encoding-failure) | Encode failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { image } from '@kit.ImageKit';

const DOMAIN = 0X00000;
const TAG: string = 'PackBinaryImageToTiffFile';

async function PackBinaryImageToTiffFile(context: Context) {
  const width = 100;
  const height = 100;
  const rowBytes = 13;
  const bufferSize = rowBytes * height;
  const data: ArrayBuffer = new ArrayBuffer(bufferSize);

  let bufferInfo: image.BinaryBufferInfo = {
    size: { width: width, height: height },
    data: data,
    bytesPerRow: rowBytes
  };

  const filePath: string = context.filesDir + "/output.tiff";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);

  let tiffOptions: image.PackingOptionsForTiff = {
    compression: 4 // CCITT G4 compression.
  };

  const imagePackerObj: image.ImagePacker = image.createImagePacker();
  await imagePackerObj.packBinaryImageToTiffFile(bufferInfo, file.fd, tiffOptions)
    .then(() => {
      hilog.info(DOMAIN, TAG, 'Succeeded in packing binary image to tiff file.');
    }).catch((error: BusinessError) => {
      hilog.error(DOMAIN, TAG, `Failed to pack binary image to tiff file. code ${error.code}, message is ${error.message}`);
    });
  fileIo.closeSync(file);
}
```

## packing

```TypeScript
packing(source: ImageSource, option: PackingOption, callback: AsyncCallback<ArrayBuffer>): void
```

Compresses or re-encodes an image. This API uses an asynchronous callback to return the result.

**Since:** 6

**Deprecated since:** 13

**Substitutes:** [packToData](#packtodata)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [ImageSource](arkts-image-image-imagesource-i.md) | Yes | Image source to compress or re-encode. |
| option | [PackingOption](arkts-image-image-packingoption-i.md) | Yes | Encoding parameters. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ArrayBuffer&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the compressed or encoded image data; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Packing(context : Context) {
  // 'test.jpg' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
  let filePath: string = context.filesDir + "/test.jpg";
  const imageSourceObj: image.ImageSource = image.createImageSource(filePath);
  let packOpts: image.PackingOption = { format: "image/jpeg", quality: 98 };
  const imagePackerObj: image.ImagePacker = image.createImagePacker();
  imagePackerObj.packing(imageSourceObj, packOpts, (err: BusinessError, data: ArrayBuffer) => {
    if (err) {
      console.error(`Failed to pack the image.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in packing the image.');
    }
  })
}
```

<a id="packing-1"></a>

## packing

```TypeScript
packing(source: ImageSource, option: PackingOption): Promise<ArrayBuffer>
```

Compresses or re-encodes an image. This API uses a promise to return the result.

**Since:** 6

**Deprecated since:** 13

**Substitutes:** [packToData](#packtodata)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [ImageSource](arkts-image-image-imagesource-i.md) | Yes | Image source to compress or re-encode. |
| option | [PackingOption](arkts-image-image-packingoption-i.md) | Yes | Encoding parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise used to return the compressed or encoded image data. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Packing(context : Context) {
  // 'test.jpg' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
  let filePath: string = context.filesDir + "/test.jpg";
  const imageSourceObj: image.ImageSource = image.createImageSource(filePath);
  let packOpts: image.PackingOption = { format: "image/jpeg", quality: 98 }
  const imagePackerObj: image.ImagePacker = image.createImagePacker();
  imagePackerObj.packing(imageSourceObj, packOpts)
    .then((data: ArrayBuffer) => {
      console.info('Succeeded in packing the image.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to pack the image.code ${error.code},message is ${error.message}`);
    })
}
```

<a id="packing-2"></a>

## packing

```TypeScript
packing(source: PixelMap, option: PackingOption, callback: AsyncCallback<ArrayBuffer>): void
```

Compresses or re-encodes an image. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> If the message "PixelMap mismatch" is returned, the parameters are abnormal. The possible cause is that the
> PixelMap object is released in advance. You need to check the code and ensure that the PixelMap object is
> released after this API is called.

**Since:** 8

**Deprecated since:** 13

**Substitutes:** [packToData](#packtodata)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [PixelMap](arkts-image-image-pixelmap-i.md) | Yes | PixelMap to compress or re-encode. |
| option | [PackingOption](arkts-image-image-packingoption-i.md) | Yes | Encoding parameters. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ArrayBuffer&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the compressed or encoded image data; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Packing() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to create. The value is calculated as follows: height * width *4.
  let opts: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 4, width: 6 } }
  image.createPixelMap(color, opts).then((pixelMap: image.PixelMap) => {
    let packOpts: image.PackingOption = { format: "image/jpeg", quality: 98 }
    const imagePackerObj: image.ImagePacker = image.createImagePacker();
    imagePackerObj.packing(pixelMap, packOpts, (err: BusinessError, data: ArrayBuffer) => {
      if (err) {
        console.error(`Failed to pack the image.code ${err.code},message is ${err.message}`);
      } else {
        console.info('Succeeded in packing the image.');
      }
    })
  }).catch((error: BusinessError) => {
    console.error(`Failed to create the PixelMap.code ${error.code},message is ${error.message}`);
  })
}
```

<a id="packing-3"></a>

## packing

```TypeScript
packing(source: PixelMap, option: PackingOption): Promise<ArrayBuffer>
```

Compresses or re-encodes an image. This API uses a promise to return the result.

> **NOTE:** 
> 
> If the message "PixelMap mismatch" is returned, the parameters are abnormal. The possible cause is that the
> PixelMap object is released in advance. You need to check the code and ensure that the PixelMap object is
> released after this API is called.

**Since:** 8

**Deprecated since:** 13

**Substitutes:** [packToData](#packtodata)

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [PixelMap](arkts-image-image-pixelmap-i.md) | Yes | PixelMap to compress or re-encode. |
| option | [PackingOption](arkts-image-image-packingoption-i.md) | Yes | Encoding parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise used to return the compressed or encoded image data. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Packing() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to create. The value is calculated as follows: height * width *4.
  let opts: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 4, width: 6 } }
  image.createPixelMap(color, opts).then((pixelMap: image.PixelMap) => {
    let packOpts: image.PackingOption = { format: "image/jpeg", quality: 98 }
    const imagePackerObj: image.ImagePacker = image.createImagePacker();
    imagePackerObj.packing(pixelMap, packOpts)
      .then((data: ArrayBuffer) => {
        console.info('Succeeded in packing the image.');
      }).catch((error: BusinessError) => {
      console.error(`Failed to pack the image.code ${error.code},message is ${error.message}`);
    })
  }).catch((error: BusinessError) => {
    console.error(`Failed to create PixelMap.code ${error.code},message is ${error.message}`);
  })
}
```

<a id="packing-4"></a>

## packing

```TypeScript
packing(picture: Picture, options: PackingOption): Promise<ArrayBuffer>
```

Compresses or re-encodes an image. This API uses a promise to return the result.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| picture | [Picture](arkts-image-image-picture-i.md) | Yes | Picture to compress or re-encode. |
| options | [PackingOption](arkts-image-image-packingoption-i.md) | Yes | Encoding parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise used to return the compressed or encoded image data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [7800301](../errorcode-image.md#7800301-encoding-failure) | Encode failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Packing(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("test.jpg");
  let ops: image.SourceOptions = {
    sourceDensity: 98,
  }
  let imageSource: image.ImageSource = image.createImageSource(rawFile.buffer as ArrayBuffer, ops);
  let commodityPixelMap: image.PixelMap = await imageSource.createPixelMap();
  let pictureObj: image.Picture = image.createPicture(commodityPixelMap);
  const imagePackerObj: image.ImagePacker = image.createImagePacker();
  let funcName = "Packing";
  if (imagePackerObj != null) {
    let opts: image.PackingOption = {
      format: "image/jpeg",
      quality: 98,
      desiredDynamicRange: image.PackingDynamicRange.AUTO,
      needsPackProperties: true};
    await imagePackerObj.packing(pictureObj, opts).then((data: ArrayBuffer) => {
      console.info(funcName, 'Succeeded in packing the image.'+ data);
    }).catch((error: BusinessError) => {
      console.error(funcName, `Failed to pack the image.code ${error.code},message is ${error.message}`);
    });
  }
}
```

## packToData

```TypeScript
packToData(source: ImageSource, options: PackingOption): Promise<ArrayBuffer>
```

Compresses or re-encodes an image. This API uses a promise to return the result.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [ImageSource](arkts-image-image-imagesource-i.md) | Yes | Image source to compress or re-encode. |
| options | [PackingOption](arkts-image-image-packingoption-i.md) | Yes | Encoding parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise used to return the compressed or encoded image data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | If the parameter is invalid. |
| [62980096](../errorcode-image.md#62980096-operation-failed) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980101](../errorcode-image.md#62980101-incorrect-input-image-data) | The image data is abnormal. |
| [62980106](../errorcode-image.md#62980106-too-large-image-data) | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |
| [62980113](../errorcode-image.md#62980113-unknown-image-format) | Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted. |
| [62980119](../errorcode-image.md#62980119-image-encoding-failure) | Failed to encode the image. |
| [62980120](../errorcode-image.md#62980120-failure-in-adding-pixel-mappings) | Add pixelmap out of range. |
| [62980172](../errorcode-image.md#62980172-failed-to-encode-icc) | Failed to encode icc. |
| [62980252](../errorcode-image.md#62980252-failed-to-create-a-surface) | Failed to create surface. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function PackToData(context : Context) {
  // 'test.jpg' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
  let filePath: string = context.filesDir + "/test.jpg";
  const imageSourceObj: image.ImageSource = image.createImageSource(filePath);
  let packOpts: image.PackingOption = { format: "image/jpeg", quality: 98 }
  const imagePackerObj: image.ImagePacker = image.createImagePacker();
  imagePackerObj.packToData(imageSourceObj, packOpts)
    .then((data: ArrayBuffer) => {
      console.info('Succeeded in packing the image.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to pack the image.code ${error.code},message is ${error.message}`);
    })
}
```

<a id="packtodata-1"></a>

## packToData

```TypeScript
packToData(source: PixelMap, options: PackingOption): Promise<ArrayBuffer>
```

Compresses or re-encodes an image. This API uses a promise to return the result.

> **NOTE:** 
> 
> If error code 401 is returned, the parameters are abnormal. The possible cause is that the PixelMap object is
> released in advance. You need to check the code and ensure that the PixelMap object is released after this API
> is called.

**Since:** 13

**Atomic service API:** This API can be used in atomic services since API version 13.

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [PixelMap](arkts-image-image-pixelmap-i.md) | Yes | PixelMap to compress or re-encode. |
| options | [PackingOption](arkts-image-image-packingoption-i.md) | Yes | Encoding parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise used to return the compressed or encoded image data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | If the parameter is invalid. |
| [62980096](../errorcode-image.md#62980096-operation-failed) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980101](../errorcode-image.md#62980101-incorrect-input-image-data) | The image data is abnormal. |
| [62980106](../errorcode-image.md#62980106-too-large-image-data) | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |
| [62980113](../errorcode-image.md#62980113-unknown-image-format) | Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted. |
| [62980119](../errorcode-image.md#62980119-image-encoding-failure) | Failed to encode the image. |
| [62980120](../errorcode-image.md#62980120-failure-in-adding-pixel-mappings) | Add pixelmap out of range. |
| [62980172](../errorcode-image.md#62980172-failed-to-encode-icc) | Failed to encode icc. |
| [62980252](../errorcode-image.md#62980252-failed-to-create-a-surface) | Failed to create surface. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function PackToData() {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to create. The value is calculated as follows: height * width *4.
  let opts: image.InitializationOptions = { editable: true, pixelFormat: 3, size: { height: 4, width: 6 } }
  image.createPixelMap(color, opts).then((pixelMap: image.PixelMap) => {
    let packOpts: image.PackingOption = { format: "image/jpeg", quality: 98 }
    const imagePackerObj: image.ImagePacker = image.createImagePacker();
    imagePackerObj.packToData(pixelMap, packOpts)
      .then((data: ArrayBuffer) => {
        console.info('Succeeded in packing the image.');
      }).catch((error: BusinessError) => {
      console.error(`Failed to pack the image.code ${error.code},message is ${error.message}`);
    })
  }).catch((error: BusinessError) => {
    console.error(`Failed to create PixelMap.code ${error.code},message is ${error.message}`);
  })
}
```

## packToDataFromPixelmapSequence

```TypeScript
packToDataFromPixelmapSequence(pixelmapSequence: Array<PixelMap>, options: PackingOptionsForSequence): Promise<ArrayBuffer>
```

Encodes multiple PixelMap objects into GIF data. This API uses a promise to return the result.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pixelmapSequence | Array&lt;[PixelMap](arkts-image-image-pixelmap-i.md)&gt; | Yes | PixelMaps to encode. |
| options | [PackingOptionsForSequence](arkts-image-image-packingoptionsforsequence-i.md) | Yes | Options for encoding animated images. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise used to return the encoded data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [7800301](../errorcode-image.md#7800301-encoding-failure) | Failed to encode image. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function PackToDataFromPixelmapSequence(context : Context) {
  const resourceMgr = context.resourceManager;
  // 'moving_test.gif' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
  const fileData = await resourceMgr.getRawFileContent('moving_test.gif');
  const color = fileData.buffer as ArrayBuffer;
  let imageSource = image.createImageSource(color);
  let pixelMapList = await imageSource.createPixelMapList();
  let ops: image.PackingOptionsForSequence = {
    frameCount: 3, // Set the number of frames in GIF encoding to 3.
    delayTimeList: [10, 10, 10], // Set the delay time of three frames in GIF encoding to 100 ms, 100 ms, and 100 ms, respectively.
    disposalTypes: [3, 2, 3], // Specify the frame transition modes of the three frames in GIF encoding as 3 (restore to the previous state), 2 (restore to the background color), and 3 (restore to the previous state).
    loopCount: 0 // Set the number of loops in GIF encoding to infinite.
  };
  let packer = image.createImagePacker();
  packer.packToDataFromPixelmapSequence(pixelMapList, ops)
    .then((data: ArrayBuffer) => {
      console.info('Succeeded in packing.');
    }).catch((error: BusinessError) => {
    console.error('Failed to packing.');
  })
}
```

## packToFile

```TypeScript
packToFile(source: ImageSource, fd: number, options: PackingOption, callback: AsyncCallback<void>): void
```

Encodes the image source into a file based on the specified encoding parameters. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [ImageSource](arkts-image-image-imagesource-i.md) | Yes | Image source to encode. |
| fd | number | Yes | File descriptor. |
| options | [PackingOption](arkts-image-image-packingoption-i.md) | Yes | Encoding parameters. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-operation-failed) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980101](../errorcode-image.md#62980101-incorrect-input-image-data) | The image data is abnormal. |
| [62980106](../errorcode-image.md#62980106-too-large-image-data) | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |
| [62980113](../errorcode-image.md#62980113-unknown-image-format) | Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted. |
| [62980115](../errorcode-image.md#62980115-invalid-image-parameter) | Invalid input parameter. |
| [62980119](../errorcode-image.md#62980119-image-encoding-failure) | Failed to encode the image. |
| [62980120](../errorcode-image.md#62980120-failure-in-adding-pixel-mappings) | Add pixelmap out of range. |
| [62980172](../errorcode-image.md#62980172-failed-to-encode-icc) | Failed to encode icc. |
| [62980252](../errorcode-image.md#62980252-failed-to-create-a-surface) | Failed to create surface. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';

async function PackToFile(context : Context) {
  // 'test.png' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
  const path: string = context.filesDir + "/test.png";
  const imageSourceObj: image.ImageSource = image.createImageSource(path);
  let packOpts: image.PackingOption = { format: "image/jpeg", quality: 98 };
  const filePath: string = context.filesDir + "/image_source.jpg";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
  const imagePackerObj: image.ImagePacker = image.createImagePacker();
  imagePackerObj.packToFile(imageSourceObj, file.fd, packOpts, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to pack the image to file.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in packing the image to file.');
    }
  })
}
```

<a id="packtofile-1"></a>

## packToFile

```TypeScript
packToFile(source: ImageSource, fd: number, options: PackingOption): Promise<void>
```

Encodes the image source into a file based on the specified encoding parameters. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [ImageSource](arkts-image-image-imagesource-i.md) | Yes | Image source to encode. |
| fd | number | Yes | File descriptor. |
| options | [PackingOption](arkts-image-image-packingoption-i.md) | Yes | Encoding parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-operation-failed) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980101](../errorcode-image.md#62980101-incorrect-input-image-data) | The image data is abnormal. |
| [62980106](../errorcode-image.md#62980106-too-large-image-data) | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |
| [62980113](../errorcode-image.md#62980113-unknown-image-format) | Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted. |
| [62980115](../errorcode-image.md#62980115-invalid-image-parameter) | Invalid input parameter. |
| [62980119](../errorcode-image.md#62980119-image-encoding-failure) | Failed to encode the image. |
| [62980120](../errorcode-image.md#62980120-failure-in-adding-pixel-mappings) | Add pixelmap out of range. |
| [62980172](../errorcode-image.md#62980172-failed-to-encode-icc) | Failed to encode icc. |
| [62980252](../errorcode-image.md#62980252-failed-to-create-a-surface) | Failed to create surface. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';

async function PackToFile(context : Context) {
  // 'test.png' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
  const path: string = context.filesDir + "/test.png";
  const imageSourceObj: image.ImageSource = image.createImageSource(path);
  let packOpts: image.PackingOption = { format: "image/jpeg", quality: 98 };
  const filePath: string = context.filesDir + "/image_source.jpg";
  let file = fileIo.openSync(filePath, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
  const imagePackerObj: image.ImagePacker = image.createImagePacker();
  imagePackerObj.packToFile(imageSourceObj, file.fd, packOpts).then(() => {
    console.info('Succeeded in packing the image to file.');
  }).catch((error: BusinessError) => { 
    console.error(`Failed to pack the image to file.code ${error.code},message is ${error.message}`);
  })
}
```

<a id="packtofile-2"></a>

## packToFile

```TypeScript
packToFile(source: PixelMap, fd: number, options: PackingOption, callback: AsyncCallback<void>): void
```

Encodes the PixelMap into a file based on the specified encoding parameters. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> If error code 62980115 is returned, the parameters are abnormal. The possible cause is that the PixelMap
> object is released in advance. You need to check the code and ensure that the PixelMap object is released after
> this API is called.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [PixelMap](arkts-image-image-pixelmap-i.md) | Yes | PixelMap to encode. |
| fd | number | Yes | File descriptor. |
| options | [PackingOption](arkts-image-image-packingoption-i.md) | Yes | Encoding parameters. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-operation-failed) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980101](../errorcode-image.md#62980101-incorrect-input-image-data) | The image data is abnormal. |
| [62980106](../errorcode-image.md#62980106-too-large-image-data) | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |
| [62980113](../errorcode-image.md#62980113-unknown-image-format) | Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted. |
| [62980115](../errorcode-image.md#62980115-invalid-image-parameter) | Invalid input parameter. |
| [62980119](../errorcode-image.md#62980119-image-encoding-failure) | Failed to encode the image. |
| [62980120](../errorcode-image.md#62980120-failure-in-adding-pixel-mappings) | Add pixelmap out of range. |
| [62980172](../errorcode-image.md#62980172-failed-to-encode-icc) | Failed to encode icc. |
| [62980252](../errorcode-image.md#62980252-failed-to-create-a-surface) | Failed to create surface. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';

async function PackToFile(context : Context) {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to create. The value is calculated as follows: height * width *4.
  let opts: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 4, width: 6 } }
  const path: string = context.filesDir + "/pixel_map.jpg";
  image.createPixelMap(color, opts).then((pixelmap: image.PixelMap) => {
    let packOpts: image.PackingOption = { format: "image/jpeg", quality: 98 }
    let file = fileIo.openSync(path, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
    const imagePackerObj: image.ImagePacker = image.createImagePacker();
    imagePackerObj.packToFile(pixelmap, file.fd, packOpts, (err: BusinessError) => {
      if (err) {
        console.error(`Failed to pack the image to file.code ${err.code},message is ${err.message}`);
      } else {
        console.info('Succeeded in packing the image to file.');
      }
    })
  })
}
```

<a id="packtofile-3"></a>

## packToFile

```TypeScript
packToFile(source: PixelMap, fd: number, options: PackingOption): Promise<void>
```

Encodes the PixelMap into a file based on the specified encoding parameters. This API uses a promise to return the result.

> **NOTE:** 
> 
> If error code 62980115 is returned, the parameters are abnormal. The possible cause is that the PixelMap
> object is released in advance. You need to check the code and ensure that the PixelMap object is released after
> this API is called.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [PixelMap](arkts-image-image-pixelmap-i.md) | Yes | PixelMap to encode. |
| fd | number | Yes | File descriptor. |
| options | [PackingOption](arkts-image-image-packingoption-i.md) | Yes | Encoding parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [62980096](../errorcode-image.md#62980096-operation-failed) | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory. |
| [62980101](../errorcode-image.md#62980101-incorrect-input-image-data) | The image data is abnormal. |
| [62980106](../errorcode-image.md#62980106-too-large-image-data) | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |
| [62980113](../errorcode-image.md#62980113-unknown-image-format) | Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted. |
| [62980115](../errorcode-image.md#62980115-invalid-image-parameter) | Invalid input parameter. |
| [62980119](../errorcode-image.md#62980119-image-encoding-failure) | Failed to encode the image. |
| [62980120](../errorcode-image.md#62980120-failure-in-adding-pixel-mappings) | Add pixelmap out of range. |
| [62980172](../errorcode-image.md#62980172-failed-to-encode-icc) | Failed to encode icc. |
| [62980252](../errorcode-image.md#62980252-failed-to-create-a-surface) | Failed to create surface. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';

async function PackToFile(context : Context) {
  const color: ArrayBuffer = new ArrayBuffer(96); // 96 is the size of the pixel buffer to create. The value is calculated as follows: height * width *4.
  let opts: image.InitializationOptions = { editable: true, pixelFormat: image.PixelMapFormat.RGBA_8888, size: { height: 4, width: 6 } }
  const path: string = context.filesDir + "/pixel_map.jpg";
  image.createPixelMap(color, opts).then((pixelmap: image.PixelMap) => {
    let packOpts: image.PackingOption = { format: "image/jpeg", quality: 98 }
    let file = fileIo.openSync(path, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
    const imagePackerObj: image.ImagePacker = image.createImagePacker();
    imagePackerObj.packToFile(pixelmap, file.fd, packOpts)
      .then(() => {
        console.info('Succeeded in packing the image to file.');
      }).catch((error: BusinessError) => {
      console.error(`Failed to pack the image to file.code ${error.code},message is ${error.message}`);
    })
  })
}
```

<a id="packtofile-4"></a>

## packToFile

```TypeScript
packToFile(picture: Picture, fd: number, options: PackingOption): Promise<void>
```

Encodes the Picture into a file based on the specified encoding parameters. This API uses a promise to return the result.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| picture | [Picture](arkts-image-image-picture-i.md) | Yes | Picture to encode. |
| fd | number | Yes | File descriptor. |
| options | [PackingOption](arkts-image-image-packingoption-i.md) | Yes | Encoding parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [7800301](../errorcode-image.md#7800301-encoding-failure) | Encode failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';

async function PackToFile(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("test.jpg");
  let ops: image.SourceOptions = {
    sourceDensity: 98,
  }
  let imageSource: image.ImageSource = image.createImageSource(rawFile.buffer as ArrayBuffer, ops);
  let commodityPixelMap: image.PixelMap = await imageSource.createPixelMap();
  let pictureObj: image.Picture = image.createPicture(commodityPixelMap);

  let funcName = "PackToFile";
  const imagePackerObj: image.ImagePacker = image.createImagePacker();
  if (imagePackerObj != null) {
    const filePath: string = context.filesDir + "/test.jpg";
    let file = fileIo.openSync(filePath, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
    let packOpts: image.PackingOption = {
      format: "image/jpeg",
      quality: 98,
      desiredDynamicRange: image.PackingDynamicRange.AUTO,
      needsPackProperties: true};
    await imagePackerObj.packToFile(pictureObj, file.fd, packOpts).then(() => {
      console.info(funcName, 'Succeeded in packing the image to file.');
    }).catch((error: BusinessError) => {
      console.error(funcName, `Failed to pack the image to file.code ${error.code},message is ${error.message}`);
    });
  }
}
```

## packToFileFromPixelmapSequence

```TypeScript
packToFileFromPixelmapSequence(pixelmapSequence: Array<PixelMap>, fd: number, options: PackingOptionsForSequence): Promise<void>
```

Encodes multiple PixelMaps into a GIF file. This API uses a promise to return the result.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pixelmapSequence | Array&lt;[PixelMap](arkts-image-image-pixelmap-i.md)&gt; | Yes | PixelMaps to encode. |
| fd | number | Yes | File descriptor. |
| options | [PackingOptionsForSequence](arkts-image-image-packingoptionsforsequence-i.md) | Yes | Options for encoding animated images. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types;3.Parameter verification failed. |
| [7800301](../errorcode-image.md#7800301-encoding-failure) | Failed to encode image. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';

async function PackToFile(context : Context) {
  const resourceMgr = context.resourceManager;
  // 'moving_test.gif' is only an example. Replace it with the actual one in use. Otherwise, the imageSource instance fails to be created, and subsequent operations cannot be performed.
  const fileData = await resourceMgr.getRawFileContent('moving_test.gif');
  const color = fileData.buffer;
  let imageSource = image.createImageSource(color);
  let pixelMapList = await imageSource.createPixelMapList();
  let path: string = context.cacheDir + '/result.gif';
  let file = fileIo.openSync(path, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
  let ops: image.PackingOptionsForSequence = {
    frameCount: 3, // Set the number of frames in GIF encoding to 3.
    delayTimeList: [10, 10, 10], // Set the delay time of three frames in GIF encoding to 100 ms, 100 ms, and 100 ms, respectively.
    disposalTypes: [3, 2, 3], // Specify the frame transition modes of the three frames in GIF encoding as 3 (restore to the previous state), 2 (restore to the background color), and 3 (restore to the previous state).
    loopCount: 0 // Set the number of loops in GIF encoding to infinite.
  };
  let packer = image.createImagePacker();
  packer.packToFileFromPixelmapSequence(pixelMapList, file.fd, ops)
    .then(() => {
      console.info('Succeeded in packToFileMultiFrames.');
    }).catch((error: BusinessError) => {
    console.error('Failed to packToFileMultiFrames.');
  })
}
```

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Releases this ImagePacker instance. This API uses an asynchronous callback to return the result.

Images occupy a large amount of memory. When you finish using an ImagePacker instance, call this API to free the memory promptly.

Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 6

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Release() {
  const imagePackerObj: image.ImagePacker = image.createImagePacker();
  imagePackerObj.release((err: BusinessError)=>{
    if (err) {
      console.error(`Failed to release image packaging.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in releasing image packaging.');
    }
  })
}
```

<a id="release-1"></a>

## release

```TypeScript
release(): Promise<void>
```

Releases this ImagePacker instance. This API uses a promise to return the result.

Images occupy a large amount of memory. When you finish using an ImagePacker instance, call this API to free the memory promptly.

Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 6

**System capability:** SystemCapability.Multimedia.Image.ImagePacker

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Release() {
  const imagePackerObj: image.ImagePacker = image.createImagePacker();
  imagePackerObj.release().then(() => {
    console.info('Succeeded in releasing image packaging.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release image packaging.code ${error.code},message is ${error.message}`);
  })
}
```

## supportedFormats

```TypeScript
readonly supportedFormats: Array<string>
```

Supported formats for image encoding, including jpeg, webp, png, heic&lt;sup&gt;12+&lt;/sup&gt;, and gif&lt;sup&gt;18+&lt;/sup&gt;. (The supported formats may vary depending on the hardware.)

**Type:** Array&lt;string&gt;

**Since:** 6

**System capability:** SystemCapability.Multimedia.Image.ImagePacker
