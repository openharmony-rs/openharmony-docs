# Interface (AuxiliaryPicture)
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

AuxiliaryPicture类，用于读取或写入图像的辅助图数据以及获取图像的辅助图信息。目前支持的辅助图类型可参考[AuxiliaryPictureType](arkts-apis-image-e.md#auxiliarypicturetype13)。

在调用AuxiliaryPicture的方法前，需要通过[image.createAuxiliaryPicture](arkts-apis-image-f.md#imagecreateauxiliarypicture13)或Picture的[getAuxiliaryPicture](./arkts-apis-image-Picture.md#getauxiliarypicture13)创建一个AuxiliaryPicture实例。

由于图片占用内存较大，所以当AuxiliaryPicture对象使用完成后，应主动调用[release](#release13)方法及时释放对象。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该对象。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本Interface首批接口从API version 13开始支持。

## 导入模块

```ts
import { image } from '@kit.ImageKit';
```

## writePixelsFromBuffer<sup>13+</sup>

writePixelsFromBuffer(data: ArrayBuffer): Promise\<void>

读取ArrayBuffer中的辅助图片数据，并将数据写入AuxiliaryPicture对象。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Image.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型        | 必填 | 说明             |
| ------ | ----------- | ---- | ---------------- |
| data   | ArrayBuffer | 是   | 辅助图像素数据。 |

**返回值：**

| 类型           | 说明                                   |
| -------------- | -------------------------------------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |

**示例:**

ArkTS-Dyn示例：
```ts
async function WritePixelsFromBuffer(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("hdr.jpg"); // 需要支持hdr的图片。
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
    console.info('Write pixels from buffer success.');
  } else {
    console.error('AuxPictureObj is null.');
  }
}
```

ArkTS-Sta示例：
```ts
function WritePixelsFromBufferFunc(auxPicture: image.AuxiliaryPicture): void {
  try {
    let auxBuffer: ArrayBuffer = await auxPicture.readPixelsToBuffer();
    await auxPicture.writePixelsFromBuffer(auxBuffer);
    console.info(0x00000, 'writePixelsFromBufferFunc', 'writePixelsFromBuffer success!');
  } catch (err) {
    console.error(0x00000, 'writePixelsFromBufferFunc', 'writePixelsFromBufferFunc failed: ' + err);
  }
}
```

## readPixelsToBuffer<sup>13+</sup>

ArkTS-Dyn: readPixelsToBuffer(): Promise\<ArrayBuffer>

ArkTS-Sta: readPixelsToBuffer(): Promise\<ArrayBuffer | undefined>

读取图像像素映射数据并将数据写入ArrayBuffer。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Image.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                  | 说明                              |
| --------------------- | --------------------------------- |
| ArkTS-Dyn: Promise\<ArrayBuffer> <br>ArkTS-Sta: Promise\<ArrayBuffer \| undefined> | Promise对象。返回辅助图像素数据。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function ReadPixelsToBuffer(context: Context) {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("hdr.jpg"); // 需要支持hdr的图片。
  let ops: image.SourceOptions = {
    sourceDensity: 98,
  }
  let imageSource: image.ImageSource = image.createImageSource(rawFile.buffer as ArrayBuffer, ops);
  let commodityPixelMap: image.PixelMap = await imageSource.createPixelMap();
  let pictureObj: image.Picture = image.createPicture(commodityPixelMap);
  let auxPictureObj: image.AuxiliaryPicture | null = pictureObj.getAuxiliaryPicture(image.AuxiliaryPictureType.GAINMAP);
  if(auxPictureObj != null) {
    await auxPictureObj.readPixelsToBuffer().then((pixelsBuffer: ArrayBuffer) => {
      console.info('Read pixels to buffer success.' );
    }).catch((error: BusinessError) => {
      console.error(`Read pixels to buffer failed error.code: ${error.code}, error.message: ${error.message}`);
    });
  } else {
    console.error('AuxPictureObj is null.');
  }
}
```

ArkTS-Sta示例：
```ts
function ReadPixelsToBufferFunc(auxPicture: image.AuxiliaryPicture): void {
  try {
    let auxBuffer = await auxPicture.readPixelsToBuffer();
    console.info(0x00000, 'ReadPixelsToBufferFunc', 'readPixelsToBuffer success!');
  } catch (err) {
    console.error(0x00000, 'ReadPixelsToBufferFunc', 'ReadPixelsToBufferFunc failed: ' + err);
  }
}
```

## getType<sup>13+</sup>

ArkTS-Dyn: getType(): AuxiliaryPictureType

ArkTS-Sta: getType(): AuxiliaryPictureType | undefined

获取辅助图的类型。

**系统能力：** SystemCapability.Multimedia.Image.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                            | 说明                         |
| ----------------------------------------------- | ---------------------------- |
|  ArkTS-Dyn: [AuxiliaryPictureType](arkts-apis-image-e.md#auxiliarypicturetype13) <br>ArkTS-Sta: [AuxiliaryPictureType](arkts-apis-image-e.md#auxiliarypicturetype13) \| undefined | 操作成功，返回辅助图的类型。 |

**示例：**

ArkTS-Dyn示例：
```ts
async function GetAuxiliaryPictureType(auxPictureObj : image.AuxiliaryPicture) {
  if (auxPictureObj != null) {
    let type: image.AuxiliaryPictureType = auxPictureObj.getType();
    console.info('Success get auxiliary picture type ' +  JSON.stringify(type));
  } else {
    console.error('Failed get auxiliary picture type ');
  }
}
```

ArkTS-Sta示例：
```ts
function GetTypeFunc(auxPicture: image.AuxiliaryPicture): void {
  try {
    let type = auxPicture.getType();
    console.info(0x00000, 'GetTypeFunc', 'getType success! Auxiliary Type: ' + type);
  } catch (err) {
    console.error(0x00000, 'GetTypeFunc', 'GetTypeFunc failed: ' + err);
  }
}
```

## setMetadata<sup>13+</sup>

setMetadata(metadataType: MetadataType, metadata: Metadata): Promise\<void>

设置辅助图元数据。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Image.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名       | 类型                            | 必填 | 说明                                 |
| ------------ | ------------------------------- | ---- | ------------------------------------ |
| metadataType | [MetadataType](arkts-apis-image-e.md#metadatatype13) | 是   | 元数据的类型，用于设置对应的元数据。 |
| metadata     | [Metadata](arkts-apis-image-Metadata.md)         | 是   | 元数据对象。                         |

**返回值：**

| 类型           | 说明                                   |
| -------------- | -------------------------------------- |
| Promise\<void> | Promise对象，无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |
| 7600202  | Unsupported metadata. Possible causes: 1. Unsupported metadata type. 2. The metadata type does not match the auxiliary picture type. |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function SetAuxPictureObjMetadata(exifContext: Context, auxPictureObj: image.AuxiliaryPicture) {
  const exifResourceMgr = exifContext.resourceManager;
  const exifRawFile = await exifResourceMgr.getRawFileContent("exif.jpg");// 图片包含exif metadata。
  let exifOps: image.SourceOptions = {
    sourceDensity: 98,
  }
  let exifImageSource: image.ImageSource = image.createImageSource(exifRawFile.buffer as ArrayBuffer, exifOps);
  let exifCommodityPixelMap: image.PixelMap = await exifImageSource.createPixelMap();
  let exifPictureObj: image.Picture = image.createPicture(exifCommodityPixelMap);
  if (exifPictureObj != null) {
    console.info('Create picture succeeded');
  } else {
    console.error('Create picture failed');
  }

  if (auxPictureObj != null) {
    let metadataType: image.MetadataType = image.MetadataType.EXIF_METADATA;
    let exifMetaData: image.Metadata = await exifPictureObj.getMetadata(metadataType);
    auxPictureObj.setMetadata(metadataType, exifMetaData).then(() => {
      console.info('Set metadata success');
    }).catch((error: BusinessError) => {
      console.error(`Set metadata failed.error.code: ${error.code}, error.message: ${error.message}`);
    });
  } else {
    console.error('AuxPictureObjMetaData is null');
  }
}
```

ArkTS-Sta示例：
```ts
import { common } from '@kit.AbilityKit';

function SetMetadataFunc(auxPicture: image.AuxiliaryPicture, context: common.UIAbilityContext): void {
  const resourceMgr = context.resourceManager;
  const rawFile = await resourceMgr.getRawFileContent("hdr_exif_image.jpg");
  let opts: image.SourceOptions = { sourceDensity: 98 };
  try {
    let imageSource: image.ImageSource = image.createImageSource(rawFile.buffer as ArrayBuffer, opts);
    let pixelMap: image.PixelMap = await imageSource.createPixelMap(); // 解码图片获取PixelMap。
    let picture: image.Picture = image.createPicture(pixelMap); // 创建Picture对象以获取元数据。
    let metadataType: image.MetadataType = image.MetadataType.EXIF_METADATA;
    let metadata: image.Metadata | null = await picture.getMetadata(metadataType); // 从Picture获取EXIF元数据。
    if (metadata != null) {
       auxPicture.setMetadata(metadataType, metadata); // 将元数据设置到辅助图对象。
       console.info(0x00000, 'SetMetadataFunc', 'setMetadata success!');
    }
  } catch (err) {
    console.error(0x00000, 'SetMetadataFunc', 'SetMetadataFunc failed: ' + err);
  }
}
```

## getMetadata<sup>13+</sup>

getMetadata(metadataType: MetadataType): Promise\<Metadata>

getMetadata(metadataType: MetadataType): Promise\<Metadata | undefined>

从辅助图中获取元数据。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Image.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名       | 类型                            | 必填 | 说明                                   |
| ------------ | ------------------------------- | ---- | -------------------------------------- |
| metadataType | [MetadataType](arkts-apis-image-e.md#metadatatype13) | 是   | 元数据类型，用于获取对应类型的元数据。 |

**返回值：**

| 类型                             | 说明             |
| -------------------------------- | ---------------- |
| Promise<[Metadata](arkts-apis-image-Metadata.md)> | Promise对象，返回元数据的Promise对象。 |
| Promise<[Metadata](arkts-apis-image-Metadata.md) \| undefined> | 返回元数据对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. **ArkTS模式**: 该错误码仅适用于ArkTS-Dyn|
| 7600202  | Unsupported metadata. Possible causes: 1. Unsupported metadata type. 2. The metadata type does not match the auxiliary picture type. |

**示例：**

ArkTS-Dyn示例：
```ts
async function GetAuxPictureObjMetadata(auxPictureObj: image.AuxiliaryPicture) {
  if (auxPictureObj != null) {
    let metadataType: image.MetadataType = image.MetadataType.EXIF_METADATA;
    let auxPictureObjMetaData: image.Metadata | null = await auxPictureObj.getMetadata(metadataType);
    if (auxPictureObjMetaData != null) {
      console.info('Get AuxPictureObj Metadata success' );
    } else {
      console.error('Get AuxPictureObj Metadata failed');
    }
  } else {
    console.error('Get AuxPictureObj is null.');
  }
}
```

ArkTS-Sta示例：
```ts
function GetMetadataFunc(auxPicture: image.AuxiliaryPicture): void {
  try {
    let metadataType: image.MetadataType = image.MetadataType.EXIF_METADATA;
    let metadata = await auxPicture.getMetadata(metadataType);
    if (metadata != null) {
      console.info(0x00000, 'GetMetadataFunc', 'getMetadata success!');
    }
  } catch (err) {
    console.error(0x00000, 'GetMetadataFunc', 'GetMetadataFunc failed: ' + err);
  }
}
```

## getAuxiliaryPictureInfo<sup>13+</sup>

ArkTS-Dyn: getAuxiliaryPictureInfo(): AuxiliaryPictureInfo

ArkTS-Sta: getAuxiliaryPictureInfo(): AuxiliaryPictureInfo | undefined

获取有关此辅助图的图像信息。

**系统能力：** SystemCapability.Multimedia.Image.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                                            | 说明                              |
| ----------------------------------------------- | --------------------------------- |
| ArkTS-Dyn: [AuxiliaryPictureInfo](arkts-apis-image-i.md#auxiliarypictureinfo13) <br>ArkTS-Sta: [AuxiliaryPictureInfo](arkts-apis-image-i.md#auxiliarypictureinfo13) \| undefined | 返回辅助图图像信息。 |

**示例：**

ArkTS-Dyn示例：
```ts
async function GetAuxiliaryPictureInfo(auxPictureObj: image.AuxiliaryPicture) {
  if(auxPictureObj != null) {
    let auxinfo: image.AuxiliaryPictureInfo = auxPictureObj.getAuxiliaryPictureInfo();
    console.info('GetAuxiliaryPictureInfo Type: ' + auxinfo.auxiliaryPictureType +
      ' height: ' + auxinfo.size.height + ' width: ' + auxinfo.size.width +
      ' rowStride: ' +  auxinfo.rowStride +  ' pixelFormat: ' + auxinfo.pixelFormat +
      ' colorSpace: ' +  auxinfo.colorSpace);
  } else {
    console.error('Get auxiliary picture information failed');
  }
}
```

ArkTS-Sta示例：
```ts
function GetAuxiliaryPictureInfoFunc(auxPicture: image.AuxiliaryPicture): void {
  try {
    let auxInfo = auxPicture.getAuxiliaryPictureInfo();
    console.info(0x00000, 'GetAuxiliaryPictureInfoFunc',
      'getAuxiliaryPictureInfo Type: ' + auxInfo.auxiliaryPictureType +
      ' height: ' + auxInfo.size.height + ' width: ' + auxInfo.size.width + ' rowStride: ' + auxInfo.rowStride +
      ' pixelFormat: ' + auxInfo.pixelFormat + ' colorSpace: ' + auxInfo.colorSpace);
  } catch (err) {
    console.error(0x00000, 'GetAuxiliaryPictureInfoFunc', 'GetAuxiliaryPictureInfoFunc failed: ' + err);
  }
}
```

## setAuxiliaryPictureInfo<sup>13+</sup>

setAuxiliaryPictureInfo(info: AuxiliaryPictureInfo): void

设置辅助图的图像信息。

**系统能力：** SystemCapability.Multimedia.Image.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                            | 必填 | 说明               |
| ------ | ----------------------------------------------- | ---- | ------------------ |
| info   | [AuxiliaryPictureInfo](arkts-apis-image-i.md#auxiliarypictureinfo13) | 是   | 辅助图的图像信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)。

| 错误码ID | 错误信息                                                     |
| -------- | :----------------------------------------------------------- |
| 401      | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified. 2.Incorrect parameter types. 3.Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：
```ts
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

ArkTS-Sta示例：
```ts
import { colorSpaceManager } from '@kit.ArkGraphics2D';

function SetAuxiliaryPictureInfoFunc(auxPicture: image.AuxiliaryPicture): void {
  try {
    let colorSpaceName: colorSpaceManager.ColorSpace = colorSpaceManager.ColorSpace.SRGB;
    let info: image.AuxiliaryPictureInfo = {
      auxiliaryPictureType: image.AuxiliaryPictureType.GAINMAP,
      size: {height: 100, width: 200},
      pixelFormat: image.PixelMapFormat.RGBA_8888,
      rowStride: 0,
      colorSpace: colorSpaceManager.create(colorSpaceName),
    };
    auxPicture.setAuxiliaryPictureInfo(info);
    console.info(0x00000, 'SetAuxiliaryPictureInfoFunc', 'SetAuxiliaryPictureInfoFunc success!');
  } catch (err) {
    console.error(0x00000, 'SetAuxiliaryPictureInfoFunc', 'SetAuxiliaryPictureInfoFunc failed: ' + err);
  }
}
```

## release<sup>13+</sup>

release():void

释放辅助图对象，无返回值。

由于图片占用内存较大，所以当AuxiliaryPicture对象使用完成后，应主动调用该方法，及时释放内存。

释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**系统能力：** SystemCapability.Multimedia.Image.Core

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 23

**示例：**

ArkTS-Dyn示例：
```ts
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

ArkTS-Sta示例：
```ts
import { common } from '@kit.AbilityKit';
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
if (context != undefined) {
  let auxPicture: image.AuxiliaryPicture | null = GetAuxiliaryPicture(context)
  if (auxPicture != null) {
    auxPicture.release();
  } else {
    console.error(0x00000, 'GetAuxiliaryPicture', 'auxPicture is null!');
  }
}
```