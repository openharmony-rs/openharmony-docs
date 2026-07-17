# CreateIncrementalSource

## 导入模块

```TypeScript
import { image } from '@kit.ImageKit';
```

## CreateIncrementalSource

```TypeScript
function CreateIncrementalSource(buf: ArrayBuffer): ImageSource
```

通过缓冲区以增量的方式创建ImageSource实例，IncrementalSource不支持读写Exif信息。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

以增量方式创建的ImageSource实例，仅支持使用以下功能，同步、异步callback、异步Promise均支持。

- 获取图片信息：指定序号-[getImageInfo](arkts-image-image-imagesource-i.md#getimageinfo-1)、直接获取-[getImageInfo](arkts-image-image-imagesource-i.md#getimageinfo-3)  
- 获取图片中给定索引处图像的指定属性键的值：[getImageProperty](arkts-image-image-imagesource-i.md#getimageproperty-1)  
- 批量获取图片中的指定属性键的值：[getImageProperties](image.ImageSource.getImageProperties(key: Array<PropertyKey>))  
- 更新增量数据：[updateData](arkts-image-image-imagesource-i.md#updatedata-1)  
- 创建PixelMap对象：通过图片解码参数创建-[createPixelMap](arkts-image-image-createpixelmap-f.md#createpixelmap-1)、通过默认参数创建-[createPixelMap](arkts-image-image-createpixelmap-f.md#createpixelmap-1) 、通过图片解码参数-[createPixelMap](arkts-image-image-createpixelmap-f.md#createpixelmap-1)  
- 释放ImageSource实例：[release](arkts-image-image-imagesource-i.md#release-1)

**起始版本：** 9

<!--Device-image-function CreateIncrementalSource(buf: ArrayBuffer): ImageSource--><!--Device-image-function CreateIncrementalSource(buf: ArrayBuffer): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 增量数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageSource](arkts-image-sendableimage-imagesource-i.md) | 返回ImageSource，失败时返回undefined。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function CreateIncrementalImageSource(context : Context) {
  let imageArray = context.resourceManager.getMediaContentSync($r('app.media.startIcon').id); // 获取图像资源。
  // 此处'app.media.startIcon'仅作示例，请开发者自行替换，否则imageArray创建失败会导致后续无法正常执行。
  let splitBuff1 = imageArray.slice(0, imageArray.byteLength / 2);  // 分片。
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


## CreateIncrementalSource

```TypeScript
function CreateIncrementalSource(buf: ArrayBuffer, options?: SourceOptions): ImageSource
```

通过缓冲区以增量的方式创建ImageSource实例，IncrementalSource不支持读写Exif信息。

此接口支持的功能与[CreateIncrementalSource(buf: ArrayBuffer): ImageSource](arkts-image-image-createincrementalsource-f.md#createincrementalsource-1)所生成的实例支持的功能相同。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](arkts-image-image-imagesource-i.md#release-1)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**起始版本：** 9

<!--Device-image-function CreateIncrementalSource(buf: ArrayBuffer, options?: SourceOptions): ImageSource--><!--Device-image-function CreateIncrementalSource(buf: ArrayBuffer, options?: SourceOptions): ImageSource-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| buf | [ArrayBuffer](../../apis-arkts/arkts-apis/arkts-arkts-collections-arraybuffer-c.md) | 是 | 增量数据。 |
| options | [SourceOptions](arkts-image-image-sourceoptions-i.md) | 否 | 图片属性，包括图片像素密度、像素格式和图片尺寸。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ImageSource](arkts-image-sendableimage-imagesource-i.md) | 返回ImageSource，失败时返回undefined。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function CreateIncrementalImageSource(context : Context) {
  let imageArray = context.resourceManager.getMediaContentSync($r('app.media.startIcon').id); // 获取图像资源。
  // 此处'app.media.startIcon'仅作示例，请开发者自行替换，否则imageArray创建失败会导致后续无法正常执行。
  let splitBuff1 = imageArray.slice(0, imageArray.byteLength / 2);  // 分片。
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

