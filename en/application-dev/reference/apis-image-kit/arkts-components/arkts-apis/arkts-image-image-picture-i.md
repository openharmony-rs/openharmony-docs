# Picture

```TypeScript
interface Picture
```

An image that contains special information can be decoded into a picture object, which generally contains the main picture, auxiliary picture, and metadata. The main picture contains most information about the image and is mainly used to render the image. The auxiliary picture is used to store data related to but different from the main picture, revealing more comprehensive details. The metadata is generally used to store information about the image file. The picture object class is used to read or write picture objects. Before calling any API in Picture, you must use [image.createPicture](arkts-image-image-createpicture-f.md) to create a Picture object.

Images occupy a large amount of memory. When you finish using a Picture instance, call [release](#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## getAuxiliaryPicture

```TypeScript
getAuxiliaryPicture(type: AuxiliaryPictureType): AuxiliaryPicture | null
```

Obtains an auxiliary picture by type.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [AuxiliaryPictureType](arkts-image-image-auxiliarypicturetype-e.md) | Yes | Type of the auxiliary picture. |

**Return value:**

| Type | Description |
| --- | --- |
| [AuxiliaryPicture](arkts-image-image-auxiliarypicture-i.md) &#124; null | AuxiliaryPicture object. If there is no AuxiliaryPicture object, null is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |

**Examples**

```TypeScript
async function GetAuxiliaryPicture(pictureObj : image.Picture) {
  if (pictureObj != null) {
    let type: image.AuxiliaryPictureType = image.AuxiliaryPictureType.GAINMAP;
    let auxPictureObj: image.AuxiliaryPicture | null = pictureObj.getAuxiliaryPicture(type);
  }
}
```

## getGainmapPixelmap

```TypeScript
getGainmapPixelmap(): PixelMap | null
```

Obtains the PixelMap object of the gain map.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) &#124; null | PixelMap object obtained. If there is no PixelMap object, null is returned. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetGainmapPixelmap(pictureObj : image.Picture) {
  let funcName = "getGainmapPixelmap";
  if (pictureObj != null) { // A gain map is contained.
    let gainPixelmap: image.PixelMap | null = pictureObj.getGainmapPixelmap();
    if (gainPixelmap != null) {
      gainPixelmap.getImageInfo().then((imageInfo: image.ImageInfo) => {
        if (imageInfo != null) {
          console.info(`Succeeded in getting gainmap PixelMap information. Height: ${imageInfo.size.height}, width: ${imageInfo.size.width}.`);
        } else {
          console.error('Gainmap PixelMap is null.');
        }
      }).catch((error: BusinessError) => {
        console.error(funcName, `Failed to get gainmap PixelMap information. Code: ${error.code}, message: ${error.message}.`);
      });
    } else {
      console.info('Gainmap PixelMap is null.');
    }
  } else {
    console.error('Picture object is null.');
  }
}
```

## getHdrComposedPixelmap

```TypeScript
getHdrComposedPixelmap(): Promise<PixelMap>
```

Generates a High Dynamic Range (HDR) image and obtains its PixelMap object. This API uses a promise to return the result.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-image-pixelmap-i.md)&gt; | Promise used to return the PixelMap object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600901](../errorcode-image.md#7600901-unknown-error) | Inner unknown error. Please check the logs for detailed information. |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation. e.g.,1. The picture does not has a gainmap. 2. MainPixelMap's allocator type is not DMA. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetHdrComposedPixelmap(pictureObj : image.Picture) {
  let funcName = "getHdrComposedPixelmap";
  if (pictureObj != null) { // An HDR image is contained.
    let hdrComposedPixelmap: image.PixelMap = await pictureObj.getHdrComposedPixelmap();
    if (hdrComposedPixelmap != null) {
      hdrComposedPixelmap.getImageInfo().then((imageInfo: image.ImageInfo) => {
        if (imageInfo != null) {
          console.info(`Succeeded in getting HDR composed PixelMap information. Height: ${imageInfo.size.height}, width: ${imageInfo.size.width}.`);
        }
      }).catch((error: BusinessError) => {
        console.error(funcName, `Failed to get HDR composed PixelMap information. Code: ${error.code}, message: ${error.message}.`);
      });
    }
  } else {
    console.error('Picture object is null.');
  }
}
```

## getHdrComposedPixelmapWithOptions

```TypeScript
getHdrComposedPixelmapWithOptions(options?: HdrComposeOptions): Promise<PixelMap | undefined>
```

Composites an HDR image and returns PixelMap of the image. Composition options (such as PixelMapFormat) can be passed. This API uses a promise to return the result.

The Picture object that calls this API must contain the main picture, gain map, and metadata.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [HdrComposeOptions](arkts-image-image-hdrcomposeoptions-i.md) | No | Options for HDR composition. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PixelMap](arkts-image-image-pixelmap-i.md) &#124; undefined&gt; | Promise, which returns the PixelMap object or **undefined**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation. |

**Examples**

```TypeScript
// EntryAbility.ets
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function GetHdrComposedPixelmapWithOptions(picture : image.Picture) {
  if (picture == null) {
    console.error('Picture is null.');
    return;
  }

  let opt: image.HdrComposeOptions = {
    desiredPixelFormat: image.PixelMapFormat.RGBA_1010102
  };
  let hdrComposedPixelmap: image.PixelMap | undefined = await picture.getHdrComposedPixelmapWithOptions(opt);
  if (hdrComposedPixelmap == null || hdrComposedPixelmap == undefined) {
    console.error(`Failed to get an HDR composed PixelMap with options.`);
    return;
  }

  hdrComposedPixelmap.getImageInfo().then((imageInfo: image.ImageInfo) => {
    if (imageInfo !== null) {
      console.info(`Succeeded in getting HDR composed PixelMap information with options. Height: ${imageInfo.size.height}, width: ${imageInfo.size.width}.`);
    }
  }).catch((error: BusinessError) => {
    console.error(`Failed to get HDR composed PixelMap information with options. Code: ${error.code}, message: ${error.message}.`);
  });
}
```

## getMainPixelmap

```TypeScript
getMainPixelmap(): PixelMap
```

Obtains the PixelMap object of the main picture. This API returns the result synchronously.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| [PixelMap](arkts-image-image-pixelmap-i.md) | PixelMap object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetMainPixelmap(pictureObj : image.Picture) {
  let funcName = "getMainPixelmap";
  if (pictureObj != null) {
    let mainPixelmap: image.PixelMap = pictureObj.getMainPixelmap();
    if (mainPixelmap != null) {
      mainPixelmap.getImageInfo().then((imageInfo: image.ImageInfo) => {
        if (imageInfo != null) {
          console.info(`Succeeded in getting main PixelMap information. Height: ${imageInfo.size.height}, width: ${imageInfo.size.width}.`);
        }
      }).catch((error: BusinessError) => {
        console.error(funcName, `Failed to get main PixelMap information. Code: ${error.code}, message: ${error.message}.`);
      });
    }
  } else {
    console.error('Picture object is null.');
  }
}
```

## getMetadata

```TypeScript
getMetadata(metadataType: MetadataType): Promise<Metadata>
```

Obtains the metadata of this Picture object. This API uses a promise to return the result.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| metadataType | [MetadataType](arkts-image-image-metadatatype-e.md) | Yes | Metadata type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Metadata](arkts-image-image-metadata-i.md)&gt; | Promise used to return the metadata. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [7600202](../errorcode-image.md#7600202-unsupported-metadata-readwrite-operation) | Unsupported metadata. Possible causes: 1. Unsupported metadata type. 2. The metadata type does not match the auxiliary picture type. |

**Examples**

```TypeScript
async function GetPictureObjMetadataProperties(pictureObj : image.Picture) {
  if (pictureObj != null) {
    let metadataType: image.MetadataType = image.MetadataType.EXIF_METADATA;
    let pictureObjMetaData: image.Metadata = await pictureObj.getMetadata(metadataType);
    if (pictureObjMetaData != null) {
      console.info('Succeeded in getting picture metadata.');
    } else {
      console.error('Failed to get picture metadata.');
    }
  } else {
    console.error(" pictureObj is null");
  }
}
```

## hdrComposeToMainPixelmap

```TypeScript
hdrComposeToMainPixelmap(): Promise<void>
```

Invokes the VPE algorithm to compose the main pixelmap and gainmap. The composed result will replace the main pixelmap of the current picture object.

The Picture object that calls this API must contain the main pixelmap, gain map.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7600201](../errorcode-image.md#7600201-unsupported-operation) | Unsupported operation. e.g.,1. The picture does not have a gainmap. 2. pixelMap's allocator type is not DMA. |

**Examples**

```TypeScript
// EntryAbility.ets
import { image } from '@kit.ImageKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function HdrComposeToMainPixelmap(picture : image.Picture) {
  if (picture == null) {
    console.error('picture is null');
    return;
  }
  try {
    await picture.hdrComposeToMainPixelmap();
  } catch(error) {
    console.error(`Failed to do HdrComposeToMainPixelmap. error.code: ${error.code} ,error.message: ${error.message}`);
  }
}
```

## marshalling

```TypeScript
marshalling(sequence: rpc.MessageSequence): void
```

Marshals this Picture object and writes it to a MessageSequence object.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sequence | [rpc.MessageSequence](../../apis-ipc-kit/arkts-apis/arkts-ipc-rpc-messagesequence-c.md) | Yes | MessageSequence object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [62980097](../errorcode-image.md#62980097-pixelmap-serialization-failed) | IPC error. Possible cause: 1.IPC communication failed. 2. Image upload exception. 3. Decode process exception. 4. Insufficient memory. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { rpc } from '@kit.IPCKit';

class MySequence implements rpc.Parcelable {
  picture: image.Picture | null = null;
  constructor(conPicture: image.Picture) {
    this.picture = conPicture;
  }
  marshalling(messageSequence: rpc.MessageSequence) {
    if(this.picture != null) {
      this.picture.marshalling(messageSequence);
      console.info('Succeeded in marshalling a picture.');
      return true;
    } else {
      console.error('Failed to marshall a picture.');
      return false;
    }
  }
  unmarshalling(messageSequence : rpc.MessageSequence) {
    this.picture = image.createPictureFromParcel(messageSequence);
    this.picture.getMainPixelmap().getImageInfo().then((imageInfo : image.ImageInfo) => {
      console.info(`Succeeded in unmarshalling a picture and getting main PixelMap information. Height: ${imageInfo.size.height}, width: ${imageInfo.size.width}.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to unmarshall a picture. Code: ${error.code}, message: ${error.message}.`);
    });
    return true;
  }
}

async function Marshalling_UnMarshalling(pictureObj : image.Picture) {
  if (pictureObj != null) {
    let parcelable: MySequence = new MySequence(pictureObj);
    let data: rpc.MessageSequence = rpc.MessageSequence.create();
    // Implement serialization.
    data.writeParcelable(parcelable);
    let ret: MySequence = new MySequence(pictureObj);
    // Implement deserialization.
    data.readParcelable(ret);
  } else {
    console.error('Picture object is null.');
  }
}
```

## release

```TypeScript
release(): void
```

Releases this Picture object.

Images occupy a large amount of memory. When you finish using a Picture instance, call this API to free the memory promptly.

Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Examples**

```TypeScript
async function Release(pictureObj : image.Picture) {
  let funcName = "Release";
  if (pictureObj != null) {
    pictureObj.release();
    if (pictureObj.getMainPixelmap() == null) {
      console.info(funcName, 'Succeeded in releasing a picture.');
    } else {
      console.error(funcName, 'Failed to release a picture.');
    }
  } else {
    console.error('Picture object is null.');
  }
}
```

## setAuxiliaryPicture

```TypeScript
setAuxiliaryPicture(type: AuxiliaryPictureType, auxiliaryPicture: AuxiliaryPicture): void
```

Sets an auxiliary picture.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [AuxiliaryPictureType](arkts-image-image-auxiliarypicturetype-e.md) | Yes | Type of the auxiliary picture. |
| auxiliaryPicture | [AuxiliaryPicture](arkts-image-image-auxiliarypicture-i.md) | Yes | AuxiliaryPicture object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |

**Examples**

```TypeScript
async function SetAuxiliaryPicture(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("hdr.jpg"); // An HDR-compatible image is required.
  let ops: image.SourceOptions = {
    sourceDensity: 98,
  }
  let imageSource: image.ImageSource = image.createImageSource(rawFile.buffer as ArrayBuffer, ops);
  let pixelMap: image.PixelMap = await imageSource.createPixelMap();
  let pictureObj: image.Picture = image.createPicture(pixelMap);
  if (pictureObj != null) {
    console.info('Succeeded in creating picture.');
  } else {
    console.error('Failed to create picture.');
  }

  if (pictureObj != null) {
    let type: image.AuxiliaryPictureType = image.AuxiliaryPictureType.GAINMAP;
    let auxPictureObj: image.AuxiliaryPicture | null = pictureObj.getAuxiliaryPicture(type);
    if (auxPictureObj != null) {
      pictureObj.setAuxiliaryPicture(type, auxPictureObj);
    }
  }
}
```

## setMainPixelmap

```TypeScript
setMainPixelmap(pixelmap: PixelMap): void
```

Sets the PixelMap object of the picture.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pixelmap | [PixelMap](arkts-image-image-pixelmap-i.md) | Yes | PixelMap object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [7700204](../errorcode-image.md#7700204-invalid-parameter) | Parameter error. The pixelmap object is null or has been released. |

## setMetadata

```TypeScript
setMetadata(metadataType: MetadataType, metadata: Metadata): Promise<void>
```

Sets the metadata for this Picture object. This API uses a promise to return the result.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| metadataType | [MetadataType](arkts-image-image-metadatatype-e.md) | Yes | Metadata type. |
| metadata | [Metadata](arkts-image-image-metadata-i.md) | Yes | Metadata object. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [7600202](../errorcode-image.md#7600202-unsupported-metadata-readwrite-operation) | Unsupported metadata. Possible causes: 1. Unsupported metadata type. 2. The metadata type does not match the auxiliary picture type. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function SetPictureObjMetadata(exifContext: Context) {
  const exifResourceMgr = exifContext.resourceManager;
  const exifRawFile = await exifResourceMgr.getRawFileContent("exif.jpg"); // An image containing Exif metadata is required.
  let exifOps: image.SourceOptions = {
    sourceDensity: 98,
  }
  let exifImageSource: image.ImageSource = image.createImageSource(exifRawFile.buffer as ArrayBuffer, exifOps);
  let exifCommodityPixelMap: image.PixelMap = await exifImageSource.createPixelMap();
  let exifPictureObj: image.Picture = image.createPicture(exifCommodityPixelMap);
  if (exifPictureObj != null) {
    console.info('Succeeded in creating picture.');
  } else {
    console.error('Failed to create picture.');
  }

  if (exifPictureObj != null) {
    let metadataType: image.MetadataType = image.MetadataType.EXIF_METADATA;
    let exifMetaData: image.Metadata = await exifPictureObj.getMetadata(metadataType);
    exifPictureObj.setMetadata(metadataType, exifMetaData).then(() => {
      console.info('Succeeded in setting metadata.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to set metadata. error.code: ${error.code} ,error.message: ${error.message}`);
    });
  } else {
    console.error('exifPictureObj is null');
  }
}
```
