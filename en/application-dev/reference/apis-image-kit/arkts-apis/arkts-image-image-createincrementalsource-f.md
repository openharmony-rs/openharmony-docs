# CreateIncrementalSource

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

<a id="createincrementalsource1"></a>

## CreateIncrementalSource

```TypeScript
function CreateIncrementalSource(buf: ArrayBuffer): ImageSource
```

Creates an ImageSource instance in incremental mode based on buffers. Such an instance does not support reading or writing of Exif information.

Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](arkts-image-image-imagesource-i.md#release1) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

The ImageSource instance created in incremental mode supports the following capabilities (applicable to synchronous, callback, and promise modes):

- Obtaining image information: Call [getImageInfo](arkts-image-image-imagesource-i.md#getimageinfo) to obtain image information by index, or call [getImageInfo](arkts-image-image-imagesource-i.md#getimageinfo3) to directly obtain image information.  
- Obtaining an image property: Call [getImageProperty](arkts-image-image-imagesource-i.md#getimageproperty1) to obtain the value of a property with the specified index in an image.  
- Obtaining image properties: Call [getImageProperties](arkts-image-image-imagesource-i.md#getimageproperties) to obtain the values of properties with the given names in an image.  
- Updating incremental data: Call [updateData](arkts-image-image-imagesource-i.md#updatedata).  
- Creating a PixelMap object: Call [createPixelMap](arkts-image-image-imagesource-i.md#createpixelmap1) or [createPixelMap](arkts-image-image-imagesource-i.md#createpixelmap5) to create a PixelMap object based on decoding options; call [createPixelMap](arkts-image-image-imagesource-i.md#createpixelmap3) to create a PixelMap object based on default parameters.  
- Releasing an ImageSource instance: Call [release](arkts-image-image-imagesource-i.md#release1).

**Since:** 9

<!--Device-image-function CreateIncrementalSource(buf: ArrayBuffer): ImageSource--><!--Device-image-function CreateIncrementalSource(buf: ArrayBuffer): ImageSource-End-->

**System capability:** SystemCapability.Multimedia.Image.ImageSource

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buf | ArrayBuffer | Yes | Incremental data. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageSource](arkts-image-image-imagesource-i.md) | ImageSource instance. If the operation fails, undefined is returned. |

**Examples**

```TypeScript
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
      console.info('Succeeded in creating pixelMap');
    }).catch((error: BusinessError) => {
      console.error(`Failed to updateData error code is ${error.code}, message is ${error.message}`);
    })
  }).catch((error: BusinessError) => {
    console.error(`Failed to updateData error code is ${error.code}, message is ${error.message}`);
  })
}
```


<a id="createincrementalsource2"></a>

## CreateIncrementalSource

```TypeScript
function CreateIncrementalSource(buf: ArrayBuffer, options?: SourceOptions): ImageSource
```

Creates an ImageSource instance in incremental mode based on buffers. Such an instance does not support reading or writing of Exif information.

The capabilities supported by the ImageSource instance created by this API are the same as those supported by the instance created by [CreateIncrementalSource(buf: ArrayBuffer): ImageSource](#createincrementalsource1). Images occupy a large amount of memory. When you finish using an ImageSource instance, call [release](arkts-image-image-imagesource-i.md#release1) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 9

<!--Device-image-function CreateIncrementalSource(buf: ArrayBuffer, options?: SourceOptions): ImageSource--><!--Device-image-function CreateIncrementalSource(buf: ArrayBuffer, options?: SourceOptions): ImageSource-End-->

**System capability:** SystemCapability.Multimedia.Image.ImageSource

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buf | ArrayBuffer | Yes | Incremental data. |
| options | [SourceOptions](arkts-image-image-sourceoptions-i.md) | No | Image properties, including the image pixel density, pixel format, and image size. |

**Return value:**

| Type | Description |
| --- | --- |
| [ImageSource](arkts-image-image-imagesource-i.md) | ImageSource instance. If the operation fails, undefined is returned. |

**Examples**

```TypeScript
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
      console.info('Succeeded in creating pixelMap');
    }).catch((error: BusinessError) => {
      console.error(`Failed to updateData error code is ${error.code}, message is ${error.message}`);
    })
  }).catch((error: BusinessError) => {
    console.error(`Failed to updateData error code is ${error.code}, message is ${error.message}`);
  })
}
```
