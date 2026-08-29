# Metadata

Metadata类，用于存储图像的元数据。目前支持的元数据类型可参考[MetadataType](arkts-image-image-metadatatype-e.md)。

> **说明：**
> 
> - 本Interface首批接口从API version 13开始支持。

**起始版本：** 13

**系统能力：** SystemCapability.Multimedia.Image.Core

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## clone

```TypeScript
clone(): Promise<Metadata>
```

对元数据进行克隆。使用Promise异步回调。

**起始版本：** 13

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Metadata&gt; | Promise对象，成功返回元数据实例。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function Clone(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("exif.jpg"); // 图片包含exif metadata。
  let ops: image.SourceOptions = {
    sourceDensity: 98,
  }
  let imageSource: image.ImageSource = image.createImageSource(rawFile.buffer as ArrayBuffer, ops);
  let commodityPixelMap: image.PixelMap = await imageSource.createPixelMap();
  let pictureObj: image.Picture = image.createPicture(commodityPixelMap);
  let metadataType: image.MetadataType = image.MetadataType.EXIF_METADATA;
  let metaData: image.Metadata | null = await pictureObj.getMetadata(metadataType);
  if (metaData != null) {
    let new_metadata: image.Metadata = await metaData.clone();
    new_metadata.getProperties(["ImageWidth"]).then((data1) => {
      console.info(`Clone new_metadata and get Properties: ${data1}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to clone new_metadata, error : ${err}`);
    });
  } else {
    console.error('Metadata is null.');
  }
}
```

## getAllProperties

```TypeScript
getAllProperties(): Promise<Record<string, string | null>>
```

获取图片中所有元数据的属性和值。使用Promise异步回调。如要查询属性值信息请参考[PropertyKey](arkts-image-image-propertykey-e.md)、[FragmentMapPropertyKey](arkts-image-image-fragmentmappropertykey-e.md)、 [GifPropertyKey](arkts-image-image-gifpropertykey-e.md)和[HeifsPropertyKey](arkts-image-image-heifspropertykey-e.md)。

**起始版本：** 13

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Record &lt;string, string \ | null&gt;&gt; | Promise对象，返回元数据拥有的所有属性的值。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetAllProperties(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("exif.jpg"); // 图片包含exif metadata。
  let ops: image.SourceOptions = {
    sourceDensity: 98,
  }
  let imageSource: image.ImageSource = image.createImageSource(rawFile.buffer as ArrayBuffer, ops);
  let commodityPixelMap: image.PixelMap = await imageSource.createPixelMap();
  let pictureObj: image.Picture = image.createPicture(commodityPixelMap);
  let metadataType: image.MetadataType = image.MetadataType.EXIF_METADATA;
  let metaData: image.Metadata | null = await pictureObj.getMetadata(metadataType);
  if (metaData != null) {
    await metaData.getAllProperties().then((data2) => {
      const count = Object.keys(data2).length;
      console.info('Metadata have ', count, ' properties');
      console.info(`Get metadata all properties: ${data2}`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to get metadata all properties. error.code is ${error.code}, error.message is ${error.message}`);
    });
  } else {
    console.error('Metadata is null.');
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/exif.jpg';  // 图片包含exif metadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function exifMetadataGetAllProperties(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["ImageWidth", "ImageLength"]);
  if (metaData != undefined && metaData.exifMetadata != undefined) {
    await metaData.exifMetadata.getAllProperties().then((data) => {
      const count = Object.keys(data).length;
      console.info(`Succeeded in getting all properties. Count: ${count}, data: ${JSON.stringify(data)}.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to get all properties. Code: ${error.code}, message: ${error.message}.`);
    });
  } else {
    console.error('Metadata is null.');
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/exif.jpg';  // 图片包含exif metadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function makerNoteHuaweiGetAllProperties(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HwMnoteIsXmageSupported", "HwMnoteXmageMode"]);
  if (metaData != undefined && metaData.makerNoteHuaweiMetadata != undefined) {
    await metaData.makerNoteHuaweiMetadata.getAllProperties().then((data) => {
      const count = Object.keys(data).length;
      console.info(`Succeeded in getting all properties. Count: ${count}, data: ${JSON.stringify(data)}.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to get all properties. Code: ${error.code}, message: ${error.message}.`);
    });
  } else {
    console.error('Metadata is null.');
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/heifs.heic';  // 图片包含HeifsMetadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function heifsMetadataGetAllProperties(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HeifsDelayTime"]);
  if (metaData != undefined && metaData.heifsMetadata != undefined) {
    await metaData.heifsMetadata.getAllProperties().then((data) => {
      const count = Object.keys(data).length;
      console.info(`Succeeded in getting all properties. Count: ${count}, data: ${JSON.stringify(data)}.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to get all properties. Code: ${error.code}, message: ${error.message}.`);
    });
  } else {
    console.error('Metadata is null.');
  }
}
```

## getBlob

```TypeScript
getBlob(): Promise<ArrayBuffer>
```

以二进制数据的形式获取元数据。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;ArrayBuffer&gt; | Promise对象，返回元数据的二进制数据。 |

**示例**

```TypeScript
import { fileIo } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/exif.jpg';  // 图片包含exif metadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function GetBlob(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let pictureObj: image.Picture = await imageSource.createPicture();
  let metadataType: image.MetadataType = image.MetadataType.EXIF_METADATA;
  let metaData: image.Metadata | null = await pictureObj.getMetadata(metadataType);
  if (metaData != null) {
    let blob = await metaData.getBlob();
    if (blob != undefined) {
      console.info("Succeeded in getting blob.");
    }
  }
}
```

```TypeScript
import { fileIo } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/exif.jpg';  // 图片包含exif metadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function exifMetadataGetBlob(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["ImageWidth", "ImageLength"]);
  if (metaData != undefined && metaData.exifMetadata != undefined) {
    let blob = await metaData.exifMetadata.getBlob();
    if (blob != undefined) {
      console.info("Succeeded in getting blob.");
    }
  }
}
```

```TypeScript
import { fileIo } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/exif.jpg';  // 图片包含exif metadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function makerNoteHuaweiGetBlob(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HwMnoteIsXmageSupported", "HwMnoteXmageMode"]);
  if (metaData != undefined && metaData.makerNoteHuaweiMetadata != undefined) {
    let blob = await metaData.makerNoteHuaweiMetadata.getBlob();
    if (blob != undefined) {
      console.info("Succeeded in getting blob.");
    }
  }
}
```

```TypeScript
import { fileIo } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/heifs.heic';  // 图片包含HeifsMetadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function heifsMetadataGetBlob(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HeifsDelayTime"]);
  if (metaData != undefined && metaData.heifsMetadata != undefined) {
    let blob = await metaData.heifsMetadata.getBlob();
    if (blob != undefined) {
      console.info("Succeeded in getting blob.");
    }
  }
}
```

## getProperties

```TypeScript
getProperties(key: Array<string>): Promise<Record<string, string | null>>
```

获取图像中属性的值。使用Promise异步回调。如要查询属性值信息请参考[PropertyKey](arkts-image-image-propertykey-e.md)、[FragmentMapPropertyKey](arkts-image-image-fragmentmappropertykey-e.md)、 [GifPropertyKey](arkts-image-image-gifpropertykey-e.md)和[HeifsPropertyKey](arkts-image-image-heifspropertykey-e.md)。

**起始版本：** 13

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | Array &lt;string&gt; | 是 | 要获取其值的属性的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;Record &lt;string, string \ | null&gt;&gt; | Promise对象，返回元数据要获取的属性的值，如获取失败则返回错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [7600202](../errorcode-image.md#7600202-不支持的元数据读写) | Unsupported metadata. Possible causes: 1. Unsupported metadata type. 2. The metadata type does not match the auxiliary picture type. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function GetProperties(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("exif.jpg"); // 图片包含exif metadata。
  let ops: image.SourceOptions = {
    sourceDensity: 98,
  }
  let imageSource: image.ImageSource = image.createImageSource(rawFile.buffer as ArrayBuffer, ops);
  let commodityPixelMap: image.PixelMap = await imageSource.createPixelMap();
  let pictureObj: image.Picture = image.createPicture(commodityPixelMap);
  let metadataType: image.MetadataType = image.MetadataType.EXIF_METADATA;
  let metaData: image.Metadata | null = await pictureObj.getMetadata(metadataType);
  if (metaData != null) {
    await metaData.getProperties(["ImageWidth", "ImageLength"]).then((data2) => {
      console.info('Get properties ',JSON.stringify(data2));
    }).catch((error: BusinessError) => {
      console.error(`Failed to get properties. error.code is ${error.code}, error.message is ${error.message}`);
    });
  } else {
    console.error('Metadata is null.');
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/exif.jpg';  // 图片包含exif metadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function exifMetadataGetProperties(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["ImageWidth", "ImageLength"]);
  if (metaData != undefined && metaData.exifMetadata != undefined) {
    await metaData.exifMetadata.getProperties(["ImageWidth", "ImageLength"]).then((data) => {
      console.info(`Succeeded in getting properties. Data: ${JSON.stringify(data)}.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to get properties. Code: ${error.code}, message: ${error.message}.`);
    });
  } else {
    console.error('Metadata is null.');
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/exif.jpg';  // 图片包含exif metadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function makerNoteHuaweiGetProperties(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HwMnoteIsXmageSupported", "HwMnoteXmageMode"]);
  if (metaData != undefined && metaData.makerNoteHuaweiMetadata != undefined) {
    await metaData.makerNoteHuaweiMetadata.getProperties(["HwMnoteIsXmageSupported", "HwMnoteXmageMode"]).then((data) => {
      console.info(`Succeeded in getting properties. Data: ${JSON.stringify(data)}.`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to get properties. Code: ${error.code}, message: ${error.message}.`);
    });
  } else {
    console.error('Metadata is null.');
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/heifs.heic';  // 图片包含HeifsMetadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function heifsMetadataGetProperties(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HeifsDelayTime"]);
  if (metaData != undefined && metaData.heifsMetadata != undefined) {
    await metaData.heifsMetadata.getProperties(["HeifsDelayTime"]).then((data) => {
      console.info('Succeeded in getting properties. ',JSON.stringify(data));
    }).catch((error: BusinessError) => {
      console.error(`Failed to get properties. error.code is ${error.code}, error.message is ${error.message}`);
    });
  } else {
    console.error('Metadata is null.');
  }
}
```

## setBlob

```TypeScript
setBlob(blob: ArrayBuffer): Promise<void>
```

使用二进制数据替换当前元数据。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blob | ArrayBuffer | 是 | 要替换的二进制数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [7600206](../errorcode-image.md#7600206-无效参数) | Invalid parameter. Possible causes: The blob is empty or has a length of 0. |

**示例**

```TypeScript
import { fileIo } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/exif.jpg';  // 图片包含exif metadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function setBlob(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let pictureObj: image.Picture = await imageSource.createPicture();
  let metadataType: image.MetadataType = image.MetadataType.EXIF_METADATA;
  let metaData: image.Metadata | null = await pictureObj.getMetadata(metadataType);
  if (metaData != null) {
    let blob = await metaData.getBlob();
    if (blob != undefined) {
      console.info("Succeeded in getting blob.");
      metaData.setBlob(blob);
    }
    let new_blob = metaData.getBlob();
    if (new_blob != undefined) {
      console.info("new_blob is not undefined");
    }
  }
}
```

```TypeScript
import { fileIo } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/exif.jpg';  // 图片包含exif metadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function exifMetadataSetBlob(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["ImageWidth", "ImageLength"]);
  if (metaData != undefined && metaData.exifMetadata != undefined) {
    let blob = await metaData.exifMetadata.getBlob();
    if (blob != undefined) {
      console.info("Succeeded in getting blob.");
      metaData.exifMetadata.setBlob(blob);
    }
    let new_blob = metaData.exifMetadata.getBlob();
    if (new_blob != undefined) {
      console.info("new_blob is not undefined");
    }
  }
}
```

```TypeScript
import { fileIo } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/exif.jpg';  // 图片包含exif metadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function makerNoteHuaweiSetBlob(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HwMnoteIsXmageSupported", "HwMnoteXmageMode"]);
  if (metaData != undefined && metaData.makerNoteHuaweiMetadata != undefined) {
    let blob = await metaData.makerNoteHuaweiMetadata.getBlob();
    if (blob != undefined) {
      console.info("Succeeded in getting blob.");
      metaData.makerNoteHuaweiMetadata.setBlob(blob);
    }
    let new_blob = metaData.makerNoteHuaweiMetadata.getBlob();
    if (new_blob != undefined) {
      console.info("new_blob is not undefined");
    }
  }
}
```

```TypeScript
import { fileIo } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/heifs.heic';  // 图片包含HeifsMetadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function heifsMetadataSetBlob(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HeifsDelayTime"]);
  if (metaData != undefined && metaData.heifsMetadata != undefined) {
    let blob = await metaData.heifsMetadata.getBlob();
    if (blob != undefined) {
      console.info("Succeeded in getting blob.");
      metaData.heifsMetadata.setBlob(blob);
    }
    let new_blob = metaData.heifsMetadata.getBlob();
    if (new_blob != undefined) {
      console.info("new_blob is not undefined");
    }
  }
}
```

## setProperties

```TypeScript
setProperties(records: Record<string, string | null>): Promise<void>
```

批量设置图片元数据中的指定属性的值。使用Promise异步回调。如要查询属性值信息请参考[PropertyKey](arkts-image-image-propertykey-e.md)、[FragmentMapPropertyKey](arkts-image-image-fragmentmappropertykey-e.md)、 [GifPropertyKey](arkts-image-image-gifpropertykey-e.md)和[HeifsPropertyKey](arkts-image-image-heifspropertykey-e.md)。

**起始版本：** 13

**系统能力：** SystemCapability.Multimedia.Image.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| records | Record &lt;string, string \ | null&gt; | 是 | 要修改的属性和值的数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;void&gt; | Promise对象，如获取失败则返回错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| [7600202](../errorcode-image.md#7600202-不支持的元数据读写) | Unsupported metadata. Possible causes: 1. Unsupported metadata type. 2. The metadata type does not match the auxiliary picture type. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function SetProperties(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("exif.jpg"); // 图片包含exif metadata。
  let ops: image.SourceOptions = {
    sourceDensity: 98,
  }
  let imageSource: image.ImageSource = image.createImageSource(rawFile.buffer as ArrayBuffer, ops);
  let commodityPixelMap: image.PixelMap = await imageSource.createPixelMap();
  let pictureObj: image.Picture = image.createPicture(commodityPixelMap);
  let metadataType: image.MetadataType = image.MetadataType.EXIF_METADATA;
  let metaData: image.Metadata | null = await pictureObj.getMetadata(metadataType);
  if (metaData != null) {
    let setkey: Record<string, string | null> = {
      "ImageWidth": "200",
      "ImageLength": "300"
    };
    await metaData.setProperties(setkey).then(async () => {
      console.info('Succeeded in setting AuxPictureObj properties.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to set metadata Properties. code is ${error.code}, message is ${error.message}`);
    })
  } else {
    console.error('AuxPictureObj metadata is null. ');
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/exif.jpg';  // 图片包含exif metadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function exifMetadataSetProperties(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["ImageWidth", "ImageLength"]);
  if (metaData != undefined && metaData.exifMetadata != undefined) {
    let setkey: Record<string, string | null> = {
      "ImageWidth": "200",
      "ImageLength": "300"
    };
    await metaData.exifMetadata.setProperties(setkey).then(async () => {
      console.info('Succeeded in setting properties.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to set metadata Properties. code is ${error.code}, message is ${error.message}`);
    })
  } else {
    console.error('metadata is null. ');
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/exif.jpg';  // 图片包含exif metadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function makerNoteHuaweiSetProperties(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HwMnoteIsXmageSupported", "HwMnoteXmageMode"]);
  if (metaData != undefined && metaData.makerNoteHuaweiMetadata != undefined) {
    let setkey: Record<string, string | null> = {
      "HwMnoteIsXmageSupported": "1",
      "HwMnoteXmageMode": "9"
    };
    await metaData.makerNoteHuaweiMetadata.setProperties(setkey).then(async () => {
      console.info('Succeeded in setting properties.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to set metadata Properties. code is ${error.code}, message is ${error.message}`);
    })
  } else {
    console.error('metadata is null. ');
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';

function getFileFd(context: Context): number | undefined {
  const filePath: string = context.cacheDir + '/heifs.heic';  // 图片包含HeifsMetadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  const fd: number = file?.fd;
  return fd;
}

async function heifsMetadataSetProperties(context: Context) {
  let fd = getFileFd(context);
  let imageSource = image.createImageSource(fd);
  let metaData = await imageSource.readImageMetadata(["HeifsDelayTime"]);
  if (metaData != undefined && metaData.heifsMetadata != undefined) {
    let setkey: Record<string, string | null> = {
      "HeifsDelayTime": "200",
    };
    await metaData.heifsMetadata.setProperties(setkey).then(async () => {
      console.info('Succeeded in setting properties.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to set metadata Properties. code is ${error.code}, message is ${error.message}`);
    })
  } else {
    console.error('metadata is null. ');
  }
}
```
