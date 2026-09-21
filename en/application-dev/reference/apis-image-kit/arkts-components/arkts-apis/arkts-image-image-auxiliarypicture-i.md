# AuxiliaryPicture

```TypeScript
interface AuxiliaryPicture
```

The **AuxiliaryPicture** class is used to read or write auxiliary picture data of an image and obtain auxiliary picture information of an image. The supported types of auxiliary pictures can be found in [AuxiliaryPictureType](arkts-image-image-auxiliarypicturetype-e.md).

Before calling any API in AuxiliaryPicture, you must create an AuxiliaryPicture instance using [image.createAuxiliaryPicture](arkts-image-image-createauxiliarypicture-f.md) or [getAuxiliaryPicture](arkts-image-image-picture-i.md#getauxiliarypicture) in Picture.

Images occupy a large amount of memory. When you finish using an AuxiliaryPicture instance, call [release](#release) to free the memory promptly. Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { image } from '@kit.ImageKit';
```

## getAuxiliaryPictureInfo

```TypeScript
getAuxiliaryPictureInfo(): AuxiliaryPictureInfo
```

Obtains the auxiliary picture information.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| [AuxiliaryPictureInfo](arkts-image-image-auxiliarypictureinfo-i.md) | Auxiliary picture information. |

**Examples**

```TypeScript
async function GetAuxiliaryPictureInfo(auxPictureObj: image.AuxiliaryPicture) {
  if(auxPictureObj != null) {
    let auxinfo: image.AuxiliaryPictureInfo = auxPictureObj.getAuxiliaryPictureInfo();
    console.info('GetAuxiliaryPictureInfo Type: ' + auxinfo.auxiliaryPictureType +
      ' height: ' + auxinfo.size.height + ' width: ' + auxinfo.size.width +
      ' rowStride: ' +  auxinfo.rowStride +  ' pixelFormat: ' + auxinfo.pixelFormat +
      ' colorSpace: ' +  auxinfo.colorSpace);
  } else {
    console.error('Failed to get auxiliary picture information.');
  }
}
```

## getMetadata

```TypeScript
getMetadata(metadataType: MetadataType): Promise<Metadata>
```

Obtains the metadata of this auxiliary picture. This API uses a promise to return the result.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| metadataType | [MetadataType](arkts-image-image-metadatatype-e.md) | Yes | Metadata type, which is used to obtain metadata of the corresponding type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Metadata](arkts-image-image-metadata-i.md)&gt; | Promise that returns the metadata. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [7600202](../errorcode-image.md#7600202-unsupported-metadata-readwrite-operation) | Unsupported metadata. Possible causes: 1. Unsupported metadata type. 2. The metadata type does not match the auxiliary picture type. |

**Examples**

```TypeScript
async function GetAuxPictureObjMetadata(auxPictureObj: image.AuxiliaryPicture) {
  if (auxPictureObj != null) {
    let metadataType: image.MetadataType = image.MetadataType.EXIF_METADATA;
    let auxPictureObjMetaData: image.Metadata | null = await auxPictureObj.getMetadata(metadataType);
    if (auxPictureObjMetaData != null) {
      console.info('Succeeded in getting AuxPictureObj Metadata.' );
    } else {
      console.error('Failed to get AuxPictureObj Metadata.');
    }
  } else {
    console.error('Get AuxPictureObj is null.');
  }
}
```

## getType

```TypeScript
getType(): AuxiliaryPictureType
```

Obtains the type of this auxiliary picture.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| [AuxiliaryPictureType](arkts-image-image-auxiliarypicturetype-e.md) | Type of the auxiliary picture. |

**Examples**

```TypeScript
async function GetAuxiliaryPictureType(auxPictureObj : image.AuxiliaryPicture) {
  if (auxPictureObj != null) {
    let type: image.AuxiliaryPictureType = auxPictureObj.getType();
    console.info('Succeeded in getting auxiliary picture type ' +  JSON.stringify(type));
  } else {
    console.error('Failed to get auxiliary picture type.');
  }
}
```

## readPixelsToBuffer

```TypeScript
readPixelsToBuffer(): Promise<ArrayBuffer>
```

Reads pixels of this auxiliary picture and writes the data to an ArrayBuffer. This API uses a promise to return the result.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise used to return the pixels of the auxiliary picture. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function ReadPixelsToBuffer(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("hdr.jpg"); // An HDR-compatible image is required.
  let ops: image.SourceOptions = {
    sourceDensity: 98,
  }
  let imageSource: image.ImageSource = image.createImageSource(rawFile.buffer as ArrayBuffer, ops);
  let commodityPixelMap: image.PixelMap = await imageSource.createPixelMap();
  let pictureObj: image.Picture = image.createPicture(commodityPixelMap);
  let auxPictureObj: image.AuxiliaryPicture | null = pictureObj.getAuxiliaryPicture(image.AuxiliaryPictureType.GAINMAP);
  if(auxPictureObj != null) {
    await auxPictureObj.readPixelsToBuffer().then((pixelsBuffer: ArrayBuffer) => {
      console.info('Succeeded in reading pixels to buffer success.' );
    }).catch((error: BusinessError) => {
      console.error(`Failed to read pixels to buffer. error.code: ${error.code}, error.message: ${error.message}`);
    });
  } else {
    console.error('AuxPictureObj is null.');
  }
}
```

## release

```TypeScript
release():void
```

Releases this AuxiliaryPicture object. No value is returned.

Images occupy a large amount of memory. When you finish using an AuxiliaryPicture instance, call this API to free the memory promptly.

Before releasing the instance, ensure that all asynchronous operations associated with the instance have finished and the instance is no longer needed.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Examples**

```TypeScript
async function Release(auxPictureObj: image.AuxiliaryPicture) {
  let funcName = "Release";
  if (auxPictureObj != null) {
    auxPictureObj.release();
    if (auxPictureObj.getType() == null) {
      console.info(funcName, 'Success !');
    } else {
      console.error(funcName, 'Failed !');
    }
  } else {
    console.error('PictureObj is null');
  }
}
```

## setAuxiliaryPictureInfo

```TypeScript
setAuxiliaryPictureInfo(info: AuxiliaryPictureInfo): void
```

Sets the auxiliary picture information.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [AuxiliaryPictureInfo](arkts-image-image-auxiliarypictureinfo-i.md) | Yes | Auxiliary picture information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |

**Examples**

```TypeScript
import { colorSpaceManager } from '@kit.ArkGraphics2D';

async function SetAuxiliaryPictureInfo(auxPictureObj: image.AuxiliaryPicture) {
  if(auxPictureObj != null) {
    let colorSpaceName = colorSpaceManager.ColorSpace.SRGB;
    let info: image.AuxiliaryPictureInfo = {
      auxiliaryPictureType: image.AuxiliaryPictureType.GAINMAP,
      size: {height: 100, width: 200},
      pixelFormat: image.PixelMapFormat.RGBA_8888,
      rowStride: 0,
      colorSpace: colorSpaceManager.create(colorSpaceName),
    };
    auxPictureObj.setAuxiliaryPictureInfo(info);
  }
}
```

## setMetadata

```TypeScript
setMetadata(metadataType: MetadataType, metadata: Metadata): Promise<void>
```

Sets the metadata for this auxiliary picture. This API uses a promise to return the result.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| metadataType | [MetadataType](arkts-image-image-metadatatype-e.md) | Yes | Metadata type, which is used to set the corresponding metadata. |
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

async function SetAuxPictureObjMetadata(exifContext: Context, auxPictureObj: image.AuxiliaryPicture) {
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

  if (auxPictureObj != null) {
    let metadataType: image.MetadataType = image.MetadataType.EXIF_METADATA;
    let exifMetaData: image.Metadata = await exifPictureObj.getMetadata(metadataType);
    auxPictureObj.setMetadata(metadataType, exifMetaData).then(() => {
      console.info('Succeeded in setting metadata.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to set metadata. error.code: ${error.code}, error.message: ${error.message}`);
    });
  } else {
    console.error('AuxPictureObjMetaData is null');
  }
}
```

## writePixelsFromBuffer

```TypeScript
writePixelsFromBuffer(data: ArrayBuffer): Promise<void>
```

Reads pixels from an ArrayBuffer and writes the data to this AuxiliaryPicture object. This API uses a promise to return the result.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Image.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | ArrayBuffer | Yes | Pixels of the auxiliary picture. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |

**Examples**

```TypeScript
async function WritePixelsFromBuffer(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("hdr.jpg"); // An HDR-compatible image is required.
  let ops: image.SourceOptions = {
    sourceDensity: 98,
  }
  let imageSource: image.ImageSource = image.createImageSource(rawFile.buffer as ArrayBuffer, ops);
  let commodityPixelMap: image.PixelMap = await imageSource.createPixelMap();
  let pictureObj: image.Picture = image.createPicture(commodityPixelMap);
  let auxPictureObj: image.AuxiliaryPicture | null = pictureObj.getAuxiliaryPicture(image.AuxiliaryPictureType.GAINMAP);
  if(auxPictureObj != null) {
    let auxBuffer: ArrayBuffer = await auxPictureObj.readPixelsToBuffer();
    await auxPictureObj.writePixelsFromBuffer(auxBuffer);
    console.info('Succeeded in writing pixels from buffer.');
  } else {
    console.error('AuxPictureObj is null.');
  }
}
```
