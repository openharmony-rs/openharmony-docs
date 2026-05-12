# Interface (ImageSource)
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

ImageSource类，用于获取图片相关信息。

在调用ImageSource的方法前，需要先通过[image.createImageSource](arkts-apis-image-f.md#imagecreateimagesource)构建一个ImageSource实例。

ImageSource的所有方法均不支持并发调用。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用[release](#release)方法及时释放内存。释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { image } from '@kit.ImageKit';
```

## 属性

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 23

| 名称             | 类型           | 只读 | 可选 | 说明                                                         |
| ---------------- | -------------- | ---- | ---- | ------------------------------------------------------------ |
| supportedFormats | Array\<string> | 是   | 否   | 支持的图片格式。<br>包括：PNG、JPEG、BMP、GIF、WebP、DNG、HEIC<sup>12+</sup>、WBMP<sup>23+</sup>、HEIFS<sup>23+</sup>、TIFF<sup>23+</sup>。从API版本26.0.0开始，增加支持AVIF、AVIS格式。<br>部分格式的解码能力依赖于具体的设备硬件，建议在调用前使用[image.getImageSourceSupportedFormats](arkts-apis-image-f.md#imagegetimagesourcesupportedformats20)接口，动态查询当前设备上的解码能力。 |

## getImageInfo

ArkTS-Dyn: getImageInfo(index: number, callback: AsyncCallback\<ImageInfo>): void

ArkTS-Sta: getImageInfo(index: int, callback: AsyncCallback\<ImageInfo | undefined>): void

获取指定序号的图片信息。使用callback异步回调。

**卡片能力（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                                        | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| index    |  ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 创建ImageSource时的序号。默认值为0，表示第一张图片。当取值为N时，表示第N+1张图片。单帧图片场景中index取值只能为0，动图等多帧图片场景中index的取值范围为：[0, (帧数-1)]。|
| callback |  ArkTS-Dyn: AsyncCallback<[ImageInfo](arkts-apis-image-i.md#imageinfo)> <br>ArkTS-Sta: AsyncCallback<[ImageInfo](arkts-apis-image-i.md#imageinfo) \| undefined> | 是   | 回调函数。当获取图片信息成功，err为undefined，data为获取到的图片信息；否则为错误对象。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

imageSourceApi.getImageInfo(0, (error: BusinessError, imageInfo: image.ImageInfo) => {
  if (error) {
    console.error(`Failed to obtain the image information.code is ${error.code}, message is ${error.message}`);
  } else {
    console.info('Succeeded in obtaining the image information.');
  }
})
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

function GetImageInfoFunc(imageSource: image.ImageSource): void {
  try {
    imageSource.getImageInfo(0, (err: BusinessError | null, imageInfo: image.ImageInfo | undefined) => {
      if (err) {
        console.error(0x00000, 'GetImageInfoFunc', 'getImageInfo failed: ' + err);
      } else {
        console.info(0x00000, 'GetImageInfoFunc', 'getImageInfo success!');
      }
    });
  } catch (err) {
    console.error(0x00000, 'GetImageInfoFunc', 'GetImageInfoFunc failed: ' + err);
  }
}
```

## getImageInfo

ArkTS-Dyn: getImageInfo(callback: AsyncCallback\<ImageInfo>): void

ArkTS-Sta: getImageInfo(callback: AsyncCallback\<ImageInfo | undefined>): void

获取图片信息。使用callback异步回调。

**卡片能力（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                   | 必填 | 说明                                     |
| -------- | -------------------------------------- | ---- | ---------------------------------------- |
| callback | ArkTS-Dyn: AsyncCallback<[ImageInfo](arkts-apis-image-i.md#imageinfo)> <br>ArkTS-Sta: AsyncCallback<[ImageInfo](arkts-apis-image-i.md#imageinfo) \| undefined> | 是   | 回调函数。当获取图片信息成功，err为undefined，data为获取到的图片信息；否则为错误对象。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageInfo(imageSourceObj : image.ImageSource) {
  imageSourceObj.getImageInfo(0, (error: BusinessError, imageInfo: image.ImageInfo) => {
    if (error) {
      console.error(`Failed to obtain the image information.code is ${error.code}, message is ${error.message}`);
    } else {
      console.info('Succeeded in obtaining the image information.');
    }
  })
}
```

ArkTS-Sta示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function GetImageInfoFunc(imageSource: image.ImageSource): void {
  try {
    imageSource.getImageInfo((err: BusinessError | null, imageInfo: image.ImageInfo | undefined) => {
      if (err) {
        console.error(0x00000, 'GetImageInfoFunc', 'getImageInfo failed: ' + err);
      } else {
        console.info(0x00000, 'GetImageInfoFunc', 'getImageInfo success!');
      }
    });
  } catch (err) {
    console.error(0x00000, 'GetImageInfoFunc', 'GetImageInfoFunc failed: ' + err);
  }
}
```

## getImageInfo

ArkTS-Dyn: getImageInfo(index?: number): Promise\<ImageInfo>

ArkTS-Sta: getImageInfo(index?: int): Promise\<ImageInfo | undefined>

获取图片信息。使用Promise异步回调。

**卡片能力（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名| 类型   | 必填 | 说明                                  |
| ----- | ------ | ---- | ------------------------------------- |
| index | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否   | 创建ImageSource时的序号。默认值为0，表示第一张图片。当取值为N时，表示第N+1张图片。单帧图片场景中index的取值只能为0，动图等多帧图片场景中index的取值范围为：[0, (帧数-1)]。 |

**返回值：**

| 类型                             | 说明                   |
| -------------------------------- | ---------------------- |
| ArkTS-Dyn: Promise<[ImageInfo](arkts-apis-image-i.md#imageinfo)> <br>ArkTS-Sta: Promise<[ImageInfo](arkts-apis-image-i.md#imageinfo) \| undefined> | Promise对象，返回获取到的图片信息。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageInfo(imageSourceObj : image.ImageSource) {
  imageSourceObj.getImageInfo((err: BusinessError, imageInfo: image.ImageInfo) => {
    if (err) {
      console.error(`Failed to obtain the image information.code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('Succeeded in obtaining the image information.');
    }
  })
}
```

ArkTS-Sta示例：
```ts
async function GetImageInfoFunc(imageSource: image.ImageSource): void {
  try {
    let imageInfo = await imageSource.getImageInfo(0);
    console.info(0x00000, 'GetImageInfoFunc', 'getImageInfo success!');
  } catch (err) {
    console.error(0x00000, 'GetImageInfoFunc', 'GetImageInfoFunc failed: ' + err);
  }
}
```

## getImageInfoSync<sup>12+</sup>

ArkTS-Dyn: getImageInfoSync(index?: number): ImageInfo

ArkTS-Sta: getImageInfoSync(index?: int): ImageInfo | undefined

获取指定序号的图片信息，使用同步形式返回图片信息。

> **说明：**
>
> 该方法为同步方法，调用时会阻塞当前线程，不建议在主线程中调用，否则可能导致应用卡顿、掉帧或响应延迟。具体场景参考[耗时任务并发场景简介](../../arkts-utils/time-consuming-task-overview.md)。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名| 类型   | 必填 | 说明                                  |
| ----- | ------ | ---- | ------------------------------------- |
| index | ArkTS-Dyn: number<br>ArkTS-Sta: int | 否   | 创建ImageSource时的序号。默认值为0，表示第一张图片。当取值为N时，表示第N+1张图片。单帧图片场景中index取值只能为0，动图等多帧图片场景中index的取值范围为：[0, (帧数-1)]。|

**返回值：**

| 类型                             | 说明                   |
| -------------------------------- | ---------------------- |
| ArkTS-Dyn: [ImageInfo](arkts-apis-image-i.md#imageinfo) <br>ArkTS-Sta: [ImageInfo](arkts-apis-image-i.md#imageinfo) \| undefined | 同步返回获取到的图片信息。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageInfo(imageSourceObj : image.ImageSource) {
  imageSourceObj.getImageInfo(0)
    .then((imageInfo: image.ImageInfo) => {
      console.info('Succeeded in obtaining the image information.');
    }).catch((error: BusinessError) => {
      console.error(`Failed to obtain the image information.code is ${error.code}, message is ${error.message}`);
    })
}
```

ArkTS-Sta示例：
```ts
function GetImageInfoSyncFunc(imageSource: image.ImageSource) {
  try {
    let imageInfo = imageSource.getImageInfoSync(0);
    console.info(0x00000, 'GetImageInfoSyncFunc', 'getImageInfoSync success!');
  } catch (err) {
    console.error(0x00000, 'GetImageInfoSyncFunc', 'GetImageInfoSyncFunc failed: ' + err);
  }
}
```

## getImageProperty<sup>11+</sup>

getImageProperty(key:PropertyKey, options?: ImagePropertyOptions): Promise\<string>

获取图片中给定索引处图像的指定属性键的值。使用Promise异步回调。

该接口仅支持JPEG、PNG、HEIF<sup>12+</sup>、WEBP<sup>23+</sup>和DNG<sup>23+</sup>（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                                 | 必填 | 说明                                 |
| ------- | ---------------------------------------------------- | ---- | ------------------------------------ |
| key     | [PropertyKey](arkts-apis-image-e.md#propertykey7)                                               | 是   | 图片属性名。                         |
| options | [ImagePropertyOptions](arkts-apis-image-i.md#imagepropertyoptions11) | 否   | 图片属性，包括图片序号与默认属性值。 |

**返回值：**

| 类型             | 说明                                                              |
| ---------------- | ----------------------------------------------------------------- |
| Promise\<string> | Promise对象，返回图片属性值，如获取失败则返回属性默认值。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401  | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed;              |
| 62980096 | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.             |
| 62980103 | The image data is not supported.         |
| 62980110 | The image source data is incorrect.      |
| 62980111 | The image source data is incomplete. |
| 62980112 | The image format does not match.       |
| 62980113| Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted.            |
| 62980115 | Invalid image parameter.      |
| 62980118 | Failed to create the image plugin.   |
| 62980122 | Failed to decode the image header.   |
| 62980123| The image does not support EXIF decoding. |
| 62980135| The EXIF value is invalid.             |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageProperty(imageSourceObj : image.ImageSource) {
  let options: image.ImagePropertyOptions = { index: 0, defaultValue: '9999' }
  imageSourceObj.getImageProperty(image.PropertyKey.BITS_PER_SAMPLE, options)
    .then((data: string) => {
      console.info('Succeeded in getting the value of the specified attribute key of the image.');
    }).catch((error: BusinessError) => {
    console.error(`Failed to get the value of the specified attribute key of the image, error.code ${error.code}, error.message ${error.message}`);
  })
}
```

ArkTS-Sta示例：
```ts
async function GetImagePropertyFunc(imageSource: image.ImageSource): void {
  let opts: image.ImagePropertyOptions = { index: 0, defaultValue: '9999' };
  try {
    let property: string = await imageSource.getImageProperty(image.PropertyKey.BITS_PER_SAMPLE, opts);
    console.info(0x00000, 'GetImagePropertyFunc', 'getImageProperty success!');
  } catch (err) {
    console.error(0x00000, 'GetImagePropertyFunc', 'GetImagePropertyFunc failed: ' + err);
  }
}
```

## getImageProperties<sup>12+</sup>

ArkTS-Dyn: getImageProperties(key: Array\<PropertyKey>): Promise<Record<PropertyKey, string|null>>

ArkTS-Sta: getImageProperties(key: Array\<PropertyKey>): Promise<Record<string, string|null>>

批量获取图片中的指定属性键的值。使用Promise异步回调。

该接口仅支持JPEG、PNG、HEIF、WEBP<sup>23+</sup>和DNG<sup>23+</sup>（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                                 | 必填 | 说明                                 |
| ------- | ---------------------------------------------------- | ---- | ------------------------------------ |
| key     | Array\<[PropertyKey](arkts-apis-image-e.md#propertykey7)>                                 | 是   | 图片属性名的数组。                         |

**返回值：**

| 类型             | 说明                                                              |
| ---------------- | ----------------------------------------------------------------- |
| ArkTS-Dyn: Promise\<Record<[PropertyKey](arkts-apis-image-e.md#propertykey7), string \| null>> <br>ArkTS-Sta: Promise\<Record<string, string \| null>>  | Promise对象，返回图片属性值，如获取失败则返回null。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401  | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed; <br> **ArkTS模式：** 该错误码仅适用于ArkTS-Dyn。 |
| 62980096| The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.             |
| 62980110| The image source data is incorrect.            |
| 62980113| Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted.            |
| 62980116| Failed to decode the image.            |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageProperties(imageSourceObj : image.ImageSource) {
  let key = [image.PropertyKey.IMAGE_WIDTH, image.PropertyKey.IMAGE_LENGTH];
  imageSourceObj.getImageProperties(key).then((data) => {
    console.info(JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(JSON.stringify(err));
  });
}
```

ArkTS-Sta示例：
```ts
async function GetImagePropertiesFunc(imageSource: image.ImageSource): void {
  let key = [image.PropertyKey.IMAGE_WIDTH, image.PropertyKey.IMAGE_LENGTH];
  try {
    let properties = await imageSource.getImageProperties(key);
    console.info(0x00000, 'GetImagePropertiesFunc', 'getImageProperty success!');
  } catch (err) {
    console.error(0x00000, 'GetImagePropertiesFunc', 'GetImagePropertiesFunc failed: ' + err);
  }
}
```

## getImagePropertySync<sup>20+</sup>

ArkTS-Dyn: getImagePropertySync(key: PropertyKey): string

ArkTS-Sta: getImagePropertySync(key: PropertyKey): string | undefined

获取图片Exif指定属性键的值，使用同步形式返回结果。

>**说明：**
>
> - 该方法仅支持JPEG、PNG、HEIF、WEBP<sup>23+</sup>和DNG<sup>23+</sup>（不同硬件设备支持情况不同）文件，且需要包含Exif信息。
>
> - Exif信息是图片的元数据，包含拍摄时间、相机型号、光圈、焦距、ISO等。
>
>- 该方法为同步方法，调用时会阻塞当前线程，不建议在主线程中调用，否则可能导致应用卡顿、掉帧或响应延迟。具体场景参考[耗时任务并发场景简介](../../arkts-utils/time-consuming-task-overview.md)。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                                 | 必填 | 说明                                 |
| ------- | ---------------------------------------------------- | ---- | ------------------------------------ |
| key     | [PropertyKey](arkts-apis-image-e.md#propertykey7)                                               | 是   | 图片属性名。                         |

**返回值：**

| 类型             | 说明                                                              |
| ---------------- | ----------------------------------------------------------------- |
| ArkTS-Dyn: string<br>ArkTS-Sta: string \| undefined| 返回图片EXIF中指定属性键的值（如获取失败则返回属性默认值），各个数据值作用请参考[PropertyKey](arkts-apis-image-e.md#propertykey7)。 |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。
| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 7700101  | Bad source. e.g.,1. Image has invalid width or height. 2. Image source incomplete. 3. Read image data failed. 4. Codec create failed.|
| 7700102 | Unsupported MIME type.|
| 7700202 | Unsupported metadata. For example, key is not supported.|

**示例：**

ArkTS-Dyn示例：
```ts
function GetImagePropertySync(context : Context) {
  let resourceMgr = context.resourceManager;
  if (resourceMgr == null) {
    return;
  }
  let fd = resourceMgr.getRawFdSync("example.jpg");

  const imageSourceObj = image.createImageSource(fd);
  console.info("getImagePropertySync");
  let bits_per_sample = imageSourceObj.getImagePropertySync(image.PropertyKey.BITS_PER_SAMPLE);
  console.info("bits_per_sample : " + bits_per_sample);
}
```

ArkTS-Sta示例：
```ts
const imageSourceApi = image.createImageSource(fd);
console.info("getImagePropertySync");
if (imageSourceApi) {
  let bits_per_sample = imageSourceApi.getImagePropertySync(image.PropertyKey.BITS_PER_SAMPLE);
  console.info("bits_per_sample : " + bits_per_sample);
}
```

## modifyImageProperty<sup>11+</sup>

modifyImageProperty(key: PropertyKey, value: string): Promise\<void>

通过指定的键修改图片属性的值。使用Promise异步回调。

该接口仅支持JPEG、PNG、HEIF<sup>12+</sup>和WEBP<sup>23+</sup>（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

> **说明：**
>
> 调用modifyImageProperty修改属性会改变属性字节长度，使用buffer创建的ImageSource调用modifyImageProperty会导致buffer内容覆盖，目前buffer创建的ImageSource不支持调用此接口，请改用fd或path创建的ImageSource。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型   | 必填 | 说明         |
| ------- | ------ | ---- | ------------ |
| key     | [PropertyKey](arkts-apis-image-e.md#propertykey7)   | 是   | 图片属性名。 |
| value   | string | 是   | 属性值。     |

**返回值：**

| 类型           | 说明                        |
| -------------- | --------------------------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401  | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;    |
| 62980123| The image does not support EXIF decoding.             |
| 62980133| The EXIF data is out of range.             |
| 62980135| The EXIF value is invalid.             |
| 62980146| The EXIF data failed to be written to the file.        |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function ModifyImageProperty(imageSourceObj : image.ImageSource) {
  imageSourceObj.modifyImageProperty(image.PropertyKey.IMAGE_WIDTH, "120").then(() => {
    imageSourceObj.getImageProperty(image.PropertyKey.IMAGE_WIDTH).then((width: string) => {
      console.info(`ImageWidth is :${width}`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to get the Image Width, error.code ${error.code}, error.message ${error.message}`);
    })
  }).catch((error: BusinessError) => {
    console.error(`Failed to modify the Image Width, error.code ${error.code}, error.message ${error.message}`);
  })
}
```

ArkTS-Sta示例：
```ts
async function ModifyImagePropertyFunc(imageSource: image.ImageSource): void {
  let opts: image.ImagePropertyOptions = { index: 0, defaultValue: '9999' };
  try {
    await imageSource.modifyImageProperty(image.PropertyKey.IMAGE_WIDTH, "120");
    let property: string = await imageSource.getImageProperty(image.PropertyKey.IMAGE_WIDTH);
    console.info(0x00000, 'ModifyImagePropertyFunc', 'modifyImageProperty success!');
    console.info(0x00000, 'ModifyImagePropertyFunc', 'image width is: ' + property);
  } catch (err) {
    console.error(0x00000, 'ModifyImagePropertyFunc', 'ModifyImagePropertyFunc failed: ' + err);
  }
}
```

## modifyImageProperties<sup>12+</sup>

ArkTS-Dyn: modifyImageProperties(records: Record<PropertyKey, string|null>): Promise\<void>

ArkTS-Sta: modifyImageProperties(records: Record<string, string|null>): Promise\<void>

批量通过指定的键修改图片属性的值。使用Promise异步回调。

该接口仅支持JPEG、PNG、HEIF和WEBP<sup>23+</sup>（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

> **说明：**
>
> 调用modifyImageProperties修改属性会改变属性字节长度，使用buffer创建的ImageSource调用modifyImageProperties会导致buffer内容覆盖，目前buffer创建的ImageSource不支持调用此接口，请改用fd或path创建的ImageSource。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型   | 必填 | 说明         |
| ------- | ------ | ---- | ------------ |
| records     | ArkTS-Dyn: Record<[PropertyKey](arkts-apis-image-e.md#propertykey7), string \| null>  <br>ArkTS-Sta: Record<string, string \| null>  | 是   | 包含图片属性名和属性值的数组。 |

**返回值：**

| 类型           | 说明                        |
| -------------- | --------------------------- |
| Promise\<void> |  Promise对象。无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401| Parameter error.Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types; 3.Parameter verification failed. <br> **ArkTS模式：** 该错误码仅适用于ArkTS-Dyn。   |
| 62980123| The image does not support EXIF decoding.             |
| 62980135| The EXIF value is invalid.             |
| 62980146| The EXIF data failed to be written to the file.             |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function ModifyImageProperties(imageSourceObj : image.ImageSource) {
  let keyValues: Record<PropertyKey, string|null> = {
    [image.PropertyKey.IMAGE_WIDTH] : "1024",
    [image.PropertyKey.IMAGE_LENGTH] : "1024"
  };
  let checkKey = [image.PropertyKey.IMAGE_WIDTH, image.PropertyKey.IMAGE_LENGTH];
  imageSourceObj.modifyImageProperties(keyValues).then(() => {
    imageSourceObj.getImageProperties(checkKey).then((data) => {
      console.info(`Image Width and Image Height:${data}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to modify the Image Width and Image Height, error.code ${err.code}, error.message ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to modify the Image Width and Image Height, error.code ${err.code}, error.message ${err.message}`);
  });
}
```

ArkTS-Sta示例：
```ts
async function ModifyImagePropertiesFunc(imageSource: image.ImageSource): void {
  let keyValues: Record<image.PropertyKey, string | null> = {};
  keyValues[image.PropertyKey.IMAGE_WIDTH] = "1024";
  keyValues[image.PropertyKey.IMAGE_LENGTH] = "1024";
  try {
    await imageSource.modifyImageProperties(keyValues);
    console.info(0x00000, 'ModifyImagePropertiesFunc', 'modifyImageProperties success!');
  } catch (err) {
    console.error(0x00000, 'ModifyImagePropertiesFunc', 'ModifyImagePropertiesFunc failed: ' + err);
  }
}
```

## modifyImagePropertiesEnhanced<sup>22+</sup>

modifyImagePropertiesEnhanced(records: Record\<string, string | null\>): Promise\<void\>

批量修改图片属性。使用Promise异步回调。

> **说明：**
>
> - 调用该接口修改属性会改变属性字节长度，建议通过传入文件描述符来创建[image.createImageSource](arkts-apis-image-f.md#imagecreateimagesource7)实例或通过传入的uri创建[image.createImageSource](arkts-apis-image-f.md#imagecreateimagesource)实例。
> - 该方法在内存中完成批量数据修改后会一次性写入文件，相比[modifyImageProperties](#modifyimageproperties12)更高效。
> - 支持修改JPEG、PNG、HEIF和WEBP文件类型的图片属性，图片需要包含Exif信息。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 22

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型   | 必填 | 说明         |
| ------- | ------ | ---- | ------------ |
| records | Record\<string, string \| null>|是| 包含图片属性名和属性值的键值对集合。|

**返回值：**

| 类型           | 说明                        |
| -------------- | --------------------------- |
| Promise\<void> | Promise对象，无返回结果。|

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 7700102 | Unsupported MIME type.             |
| 7700202 | Unsupported metadata. For example, the property key is not supported, or the property value is invalid.             |
| 7700304 | Failed to write image properties to the file.             |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function ModifyImagePropertiesEnhanced(imageSourceObj : image.ImageSource) {
  let keyValues: Record<string, string|null> = {
    "ImageWidth" : "1024",
    "ImageLength" : "1024"
  };
  let checkKey = [image.PropertyKey.IMAGE_WIDTH, image.PropertyKey.IMAGE_LENGTH];
  imageSourceObj.modifyImagePropertiesEnhanced(keyValues).then(() => {
    imageSourceObj.getImageProperties(checkKey).then((data) => {
      console.info(`Image Width and Image Height:${data}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to modify the Image Width and Image Height, error.code ${err.code}, error.message ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to modify the Image Width and Image Height, error.code ${err.code}, error.message ${err.message}`);
  });
}
```

ArkTS-Sta示例：
```ts
async function ModifyImagePropertiesEnhanced(imageSourceObj: image.ImageSource) {
  const keyValues: Record<string, string | null> = {};
  keyValues[image.PropertyKey.IMAGE_WIDTH] = "1024";
  keyValues[image.PropertyKey.IMAGE_LENGTH] = "1024";

  const checkKey = [image.PropertyKey.IMAGE_WIDTH, image.PropertyKey.IMAGE_LENGTH];

  try {
    await imageSourceObj.modifyImagePropertiesEnhanced(keyValues);
    const data = await imageSourceObj.getImageProperties(checkKey);
    console.info(`Image Width and Image Height:${data}`);
  } catch (err) {
    console.error(`Failed to modify the Image Width and Image Height, error.code ${err.code}, error.message ${err.message}`);
  }
}
```

## readImageMetadata<sup>23+</sup>

ArkTS-Dyn: readImageMetadata(propertyKeys?: string[], index?: number): Promise\<ImageMetadata>

ArkTS-Sta: readImageMetadata(propertyKeys?: string[], index?: int): Promise\<ImageMetadata>

读取图像源的元数据，使用propertyKeys指定元数据字段。使用Promise异步回调。

该接口仅支持JPEG、PNG、HEIF、WebP、DNG、GIF、TIFF、HEIFS、JFIF和AVIS（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

> **说明：**
>
> 读取DNG格式图片时，该接口对部分propertyKeys有特殊处理。以下字段的字符串取值请参考[PropertyKey](arkts-apis-image-e.md#propertykey7)中的值：
> - NewSubfileType、ImageWidth、ImageLength、DefaultCropSize、Orientation、Compression、PhotometricInterpretation、PlanarConfiguration、RowsPerStrip、StripOffsets、StripByteCounts、SamplesPerPixel、BitsPerSample、YCbCrCoefficients、YCbCrSubSampling、YCbCrPositioning、ReferenceBlackWhite、XResolution、YResolution、ResolutionUnit字段：返回主图相关的字段值。
> - ImageUniqueID字段：根据规范进行校验，不符合规范时会返回空字符串。
> - ExifVersion、FlashpixVersion、ColorSpace字段：当图片中不存在该标签时，返回错误码。
> - DNGVersion字段：当版本号小于1.0.0.0时，统一返回1.0.0.0。
> - GPSVersionID字段：当没有有效的GPS数据时，会清除GPS版本号并返回0。
> - GPSAltitudeRef字段：当未设置GPSAltitude时，会设置为0xFFFFFFFF。
> - ISOSpeedRatings字段：当该标签值为0或65535时，会优先使用推荐曝光指数，若不存在则依次使用标准输出灵敏度、ISO速度、曝光指数。
> - 从API version 24开始，支持读取DNG元数据。要查询的属性的具体信息请参考[DngPropertyKey](arkts-apis-image-e.md#dngpropertykey24)。
> - 从API version 24开始，支持读取HEIFS元数据。要查询的属性的具体信息请参考[HeifsPropertyKey](arkts-apis-image-e.md#heifspropertykey23)。
> - 从API版本26.0.0开始，支持读取PNG元数据。要查询的属性的具体信息请参考[PngPropertyKey](arkts-apis-image-e.md#pngpropertykey)。
> - 从API版本26.0.0开始，支持读取JFIF元数据。要查询的属性的具体信息请参考[JfifPropertyKey](arkts-apis-image-e.md#jfifpropertykey)。
> - 从API版本26.0.0开始，支持读取TIFF元数据。要查询的属性的具体信息请参考[TiffPropertyKey](arkts-apis-image-e.md#tiffpropertykey)。
> - 从API版本26.0.0开始，支持读取GIF元数据。要查询的属性的具体信息请参考[GifPropertyKey](arkts-apis-image-e.md#gifpropertykey20)。
> - 从API版本26.0.0开始，支持读取JPEG、PNG、GIF、DNG、TIFF格式图片的XMP元数据。XMP元数据的操作方法可以参考[XMPMetadata](arkts-apis-image-XMPMetadata.md)。
> - 从API版本26.0.0开始，支持读取AVIS元数据。要查询的属性的具体信息请参考[AvisPropertyKey](arkts-apis-image-e.md#avispropertykey)。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名       | 类型     | 必填 | 说明                      |
| ------------ | -------- | ---- | ------------------------- |
| propertyKeys | string[] | 否   | 图片属性名的数组。若未指定propertyKeys，则返回所有支持的元数据。        |
| index        | ArkTS-Dyn: number<br>ArkTS-Sta: int   | 否   | 感兴趣的索引，默认值为0。 |

**返回值：**

| 类型                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Promise\<[ImageMetadata](arkts-apis-image-i.md#imagemetadata23)> | Promise对象，返回ImageMetadata对象，其中含有图片属性名对应的metadata对象，通过ImageMetadata中的metadata对象可以获取图片属性值。 |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息               |
| -------- | ---------------------- |
| 7700102  | Unsupported MIME type. |
| 7700202  | Unsupported metadata.  |
| 7700204  | Invalid parameter. Possible causes: 1. The index is negative. 2. The index is greater than or equal to the number of frames in the image.  |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function ReadImageMetadata(imageSourceObj : image.ImageSource) {
  let propertyKeys = ["ImageWidth", "HwMnoteIsXmageSupported"];
  await imageSourceObj.readImageMetadata(propertyKeys).then((metaData: image.ImageMetadata) => {
    if (metaData != undefined && metaData.exifMetadata != undefined &&
      metaData.makerNoteHuaweiMetadata != undefined) {
      console.info("ImageWidth: " + metaData.exifMetadata.imageWidth +
        " HwMnoteIsXmageSupported: " + metaData.makerNoteHuaweiMetadata.isXmageSupported);
    }
  }).catch((error: BusinessError) => {
    console.error(`ReadImageMetadata failed error.code is ${error.code}, error.message is ${error.message}`);
  })
}
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

function getFileFd(context: common.UIAbilityContext): int | undefined {
  const filePath: string = context.cacheDir + '/exif.jpg';  // 图片包含exif metadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  let fd = file.fd;
  return fd;
}

async function exifMetadataGetProperties(context: common.UIAbilityContext) {
  let fd = getFileFd(context);
  if (fd == undefined) {
    return;
  }
  let imageSource = image.createImageSource(fd);
  if (imageSource == null) {
    return;
  }
  let metaData = await imageSource.readImageMetadata(["ImageWidth", "ImageLength"]);
  if (metaData != undefined && metaData.exifMetadata != undefined) {
    console.info('readImageMetadata: ',JSON.stringify(metaData));
  } else {
    console.error('Metadata is null.');
  }
  fileIo.closeSync(fd);
}
```

## writeImageMetadata<sup>23+</sup>

writeImageMetadata(imageMetadata: ImageMetadata): Promise\<void>

批量修改图片属性。使用Promise异步回调。

> **说明：**
>
> - 调用该接口修改属性会改变属性字节长度，建议通过传入文件描述符来创建[image.createImageSource](arkts-apis-image-f.md#imagecreateimagesource7)实例或通过传入的uri创建[image.createImageSource](arkts-apis-image-f.md#imagecreateimagesource)实例。
> - 该方法在内存中完成批量数据修改后会一次性写入文件，相比[modifyImageProperties](#modifyimageproperties12)更高效。
> - 支持修改JPEG、PNG和HEIF文件类型的图片属性，图片需要包含Exif信息。修改属性前，先通过supportedFormats属性查询设备是否支持HEIF格式的Exif读写。
> - 从API版本26.0.0开始，支持修改JPEG、PNG、GIF格式图片的XMP元数据。XMP元数据的操作方法可以参考[XMPMetadata](arkts-apis-image-XMPMetadata.md)。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 23

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名        | 类型                                                   | 必填 | 说明             |
| ------------- | ------------------------------------------------------ | ---- | ---------------- |
| imageMetadata | [ImageMetadata](arkts-apis-image-i.md#imagemetadata23) | 是   | 图像的元数据集。若imageMetadata中的属性值都为空，则清空所有Exif元数据。 |

**返回值：**

| 类型           | 说明                      |
| -------------- | ------------------------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息               |
| -------- | ---------------------- |
| 7700102  | Unsupported MIME type. |
| 7700202  | Unsupported metadata.  |
| 7700204  | Invalid parameter. Possible causes: The imageSource object is released.  |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function WriteImageMetadata(imageSourceObj : image.ImageSource) {
  let propertyKeys = ["ImageWidth", "HwMnoteIsXmageSupported"];
  let metaData = await imageSourceObj.readImageMetadata(propertyKeys);
  if (metaData != undefined && metaData.exifMetadata != undefined) {
    metaData.exifMetadata.imageLength = 3072;
  }
  await imageSourceObj.writeImageMetadata(metaData).then(() => {
    console.info(`write image metadata success.`);
  }).catch((error: BusinessError) => {
    console.error(`writeImageMetadata failed error.code is ${error.code}, error.message is ${error.message}`);
  });
}
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

function getFileFd(context: common.UIAbilityContext): int | undefined {
  const filePath: string = context.cacheDir + '/exif.jpg';  // 图片包含exif metadata。
  const file: fileIo.File = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
  let fd = file.fd;
  return fd;
}

async function exifMetadataGetProperties(context: common.UIAbilityContext) {
  let fd = getFileFd(context);
  if (fd == undefined) {
    return;
  }
  let imageSource = image.createImageSource(fd);
  if (imageSource == null) {
    return;
  }
  let metaData = await imageSource.readImageMetadata(["ImageWidth", "ImageLength"]);
  if (metaData != undefined && metaData.exifMetadata != undefined) {
    console.info('readImageMetadata: ',JSON.stringify(metaData));
    await imageSource.writeImageMetadata(metaData);
  } else {
    console.error('Metadata is null.');
  }
  fileIo.closeSync(fd);
}
```

## readImageMetadataByType<sup>24+</sup>

ArkTS-Dyn: readImageMetadataByType(metadataTypes?: MetadataType[], index?: number): Promise\<ImageMetadata>

ArkTS-Sta: readImageMetadataByType(metadataTypes?: MetadataType[], index?: int): Promise\<ImageMetadata>

读取图像源的元数据，使用metadataTypes指定元数据类型。若未指定metadataTypes，则返回所有支持的元数据。使用Promise异步回调。

该接口仅支持JPEG、PNG、HEIF、WebP、DNG、GIF、TIFF、HEIFS、JFIF和AVIS（不同硬件设备支持情况不同）文件。

> **说明：**
>
> - EXIF_METADATA元数据类型适用于JPEG、PNG、HEIF、WEBP和DNG格式图片。
> - HEIFS_METADATA元数据类型适用于HEIFS格式图片。
> - 当传入的MetadataType与图片格式无法匹配时，返回错误码7700102。
> - 从API version 24开始，支持读取DNG元数据。要查询的属性的具体信息请参考[DngPropertyKey](arkts-apis-image-e.md#dngpropertykey24)。
> - 从API version 24开始，支持读取HEIFS元数据。要查询的属性的具体信息请参考[HeifsPropertyKey](arkts-apis-image-e.md#heifspropertykey23)。
> - 从API版本26.0.0开始，支持读取PNG元数据。要查询的属性的具体信息请参考[PngPropertyKey](arkts-apis-image-e.md#pngpropertykey)。
> - 从API版本26.0.0开始，支持读取JFIF元数据。要查询的属性的具体信息请参考[JfifPropertyKey](arkts-apis-image-e.md#jfifpropertykey)。
> - 从API版本26.0.0开始，支持读取TIFF元数据。要查询的属性的具体信息请参考[TiffPropertyKey](arkts-apis-image-e.md#tiffpropertykey)。
> - 从API版本26.0.0开始，支持读取GIF元数据。要查询的属性的具体信息请参考[GifPropertyKey](arkts-apis-image-e.md#gifpropertykey20)。
> - 从API版本26.0.0开始，支持读取JPEG、PNG、GIF、DNG、TIFF格式图片的XMP元数据。XMP元数据的操作方法可以参考[XMPMetadata](arkts-apis-image-XMPMetadata.md)。
> - 从API版本26.0.0开始，支持读取AVIS元数据。要查询的属性的具体信息请参考[AvisPropertyKey](arkts-apis-image-e.md#avispropertykey)。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名        | 类型            | 必填 | 说明                      |
| ------------- | -------------- | ---- | ------------------------- |
| metadataTypes | [MetadataType](arkts-apis-image-e.md#metadatatype13)[] | 否   | 元数据类型的数组。当该参数缺省时，获取全部支持的元数据。 |
| index         | ArkTS-Dyn: number<br>ArkTS-Sta: int         | 否   | 图片帧序号，表示获取指定帧的元数据。默认值为0。<br>- 单帧图片场景中index取值只能为0。<br>- 动图等多帧图片场景中index的取值范围为[0, 帧数-1]。 |

**返回值：**

| 类型                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Promise\<[ImageMetadata](arkts-apis-image-i.md#imagemetadata23)> | Promise对象。返回的ImageMetadata对象中含有对应的metadata对象，通过ImageMetadata中的metadata对象可以获取图片属性值。 |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息               |
| -------- | ---------------------- |
| 7700102  | Unsupported MIME type. |
| 7700202  | Unsupported metadata.  |
| 7700204  | Invalid parameter. Possible causes: 1.The index is negative.2. The index is greater than or equal to the number of frames in the image. |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function ReadImageMetadataByType(imageSource : image.ImageSource, type: image.MetadataType) {
  let types: image.MetadataType[] = [type];
  await imageSource.readImageMetadataByType(types, 0).then((metaData: image.ImageMetadata) => {
    if (metaData != undefined && metaData.exifMetadata != undefined) {
      console.info("ImageWidth: " + metaData.exifMetadata.imageWidth);
    }
  }).catch((error: BusinessError) => {
    console.error(`ReadImageMetadataByType failed error.code is ${error.code}, error.message is ${error.message}`);
  })
}
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function ReadImageMetadataByType(imageSource : image.ImageSource, type: image.MetadataType) {
  try {
    let types: image.MetadataType[] = [type];
    let metaData: image.ImageMetadata = await imageSource.readImageMetadataByType(types, 0);
    if (metaData && metaData.exifMetadata) {
      let width = metaData.exifMetadata?.imageWidth;
      console.info(`ImageWidth: ${width}`);
    }
  } catch (err) {
    console.error(`ReadImageMetadataByType failed error.code is ${err.code}, error.message is ${err.message}`);
  }
}
```

## createImageRawData<sup>24+</sup>

createImageRawData(): Promise\<ImageRawData>

获取图片原始数据。使用Promise异步回调。目前仅支持获取DNG图片类型的原始数据。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 24

**ArkTS-Sta起始版本：** 24

**返回值：**

| 类型           | 说明                      |
| -------------- | ------------------------- |
| Promise\<[ImageRawData](arkts-apis-image-i.md#imagerawdata24)> | Promise对象，返回ImageRawData对象，其中含有数据缓冲区和像素位数。 |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息               |
| -------- | ---------------------- |
| 7700101  | Bad source.  |
| 7700102  | Unsupported MIME type. |

**示例：**
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function createImageRawData(imageSourceObj: image.ImageSource) {
  await imageSourceObj.createImageRawData().then((data: image.ImageRawData) => {
    console.info(`createImageRawData success. length: ${data.buffer.byteLength}, bitPerPixel:${data.bitsPerPixel}`);
    if (data.bitsPerPixel == 16) {
      let array: Uint16Array = new Uint16Array();
      let value: string = "";
      array = new Uint16Array(data.buffer);
      for (let i = 0; i < array.length && i < 10; i++) {
        value += array[i] + ', ';
      }
      console.info(`get dng rawdata is:${value}.`);
    }
  }).catch((error: BusinessError) => {
    console.error(`createImageRawData failed error.code is ${error.code}, error.message is ${error.message}`);
  });
}
```

## updateData<sup>9+</sup>

ArkTS-Dyn: updateData(buf: ArrayBuffer, isFinished: boolean, offset: number, length: number): Promise\<void>

ArkTS-Sta: updateData(buf: ArrayBuffer, isFinished: boolean, offset: int, length: int): Promise\<void>

更新增量数据。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型        | 必填 | 说明         |
| ---------- | ----------- | ---- | ------------ |
| buf        | ArrayBuffer         | 是   | 存放增量数据的buffer。           |
| isFinished | boolean             | 是   | true表示数据更新完成，当前buffer内存放最后一段数据；false表示数据还未更新完成，需要继续更新。|
| offset     | ArkTS-Dyn: number<br/>ArkTS-Sta: int                | 是   | 即当前buffer中的数据首地址，相对于整个图片文件首地址的偏移量。单位：字节。             |
| length     | ArkTS-Dyn: number<br/>ArkTS-Sta: int                | 是   | 当前buffer的长度。单位：字节。            |

**返回值：**

| 类型           | 说明                       |
| -------------- | -------------------------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。|

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

const array: ArrayBuffer = new ArrayBuffer(100);
imageSourceApi.updateData(array, false, 0, 10).then(() => {
  console.info('Succeeded in updating data.');
}).catch((err: BusinessError) => {
  console.error(`Failed to update data.code is ${err.code},message is ${err.message}`);
})
```

ArkTS-Sta示例：
```ts
async function UpdateDataFunc(imageSource: image.ImageSource): void {
  const array: ArrayBuffer = new ArrayBuffer(100);
  try {
    await imageSource.updateData(array, false, 0, 10);
    console.info(0x00000, 'UpdateDataFunc', 'updateData success!');
  } catch (err) {
    console.error(0x00000, 'UpdateDataFunc', 'UpdateDataFunc failed: ' + err);
  }
}
```


## updateData<sup>9+</sup>

ArkTS-Dyn: updateData(buf: ArrayBuffer, isFinished: boolean, offset: number, length: number, callback: AsyncCallback\<void>): void

ArkTS-Sta: updateData(buf: ArrayBuffer, isFinished: boolean, offset: int, length: int, callback: AsyncCallback\<void>): void

更新增量数据。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                | 必填 | 说明                 |
| ---------- | ------------------- | ---- | -------------------- |
| buf        | ArrayBuffer         | 是   | 存放增量数据的buffer。           |
| isFinished | boolean             | 是   | true表示数据更新完成，当前buffer内存放最后一段数据；false表示数据还未更新完成，需要继续更新。|
| offset     | ArkTS-Dyn: number<br/>ArkTS-Sta: int                 | 是   | 即当前buffer中的数据首地址，相对于整个图片文件首地址的偏移量。单位：字节。             |
| length     | ArkTS-Dyn: number<br/>ArkTS-Sta: int                 | 是   | 当前buffer的长度。单位：字节。            |
| callback   | AsyncCallback\<void> | 是   |  回调函数，当更新增量数据成功，err为undefined，否则为错误对象。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

const array: ArrayBuffer = new ArrayBuffer(100);
imageSourceApi.updateData(array, false, 0, 10, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to update data.code is ${err.code},message is ${err.message}`);
  } else {
    console.info('Succeeded in updating data.');
  }
})
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

function UpdateDataFunc(imageSource: image.ImageSource): void {
  const array: ArrayBuffer = new ArrayBuffer(100);
  try {
    imageSource.updateData(array, false, 0, 10, (err: BusinessError | null) => {
      if (err) {
        console.error(0x00000, 'UpdateDataFunc', 'updateData failed: ' + err);
      } else {
        console.info(0x00000, 'UpdateDataFunc', 'updateData success!');
      }
    });
    console.info(0x00000, 'UpdateDataFunc', 'updateData success!');
  } catch (err) {
    console.error(0x00000, 'UpdateDataFunc', 'UpdateDataFunc failed: ' + err);
  }
}
```

## createPicture<sup>13+</sup>

ArkTS-Dyn: createPicture(options?: DecodingOptionsForPicture): Promise\<Picture>

ArkTS-Sta: createPicture(options?: DecodingOptionsForPicture): Promise\<Picture | undefined>

通过图片解码参数创建Picture对象。使用Promise异步回调。

由于图片占用内存较大，所以当Picture对象使用完成后，应主动调用[release](./arkts-apis-image-Picture.md#release13)方法，及时释放内存。

释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 13

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                                   | 必填 | 说明       |
| ------- | ------------------------------------------------------ | ---- | ---------- |
| options | [DecodingOptionsForPicture](arkts-apis-image-i.md#decodingoptionsforpicture13) | 否   | 解码参数。 |

**返回值：**

| 类型                         | 说明                       |
| ---------------------------- | -------------------------- |
| ArkTS-Dyn: Promise\<[Picture](arkts-apis-image-Picture.md)> | Promise对象，返回Picture。 |
| ArkTS-Sta: Promise\<[Picture](arkts-apis-image-Picture.md) \| undefined> | Promise对象，返回Picture。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified.2.Incorrect parameter types; 3.Parameter verification failed.  |
| 7700203  | Unsupported options, For example, unsupported desiredPixelFormat causes a failure in converting an image into the desired pixel format. |
| 7700301  | Decode failed. |

**示例：**

ArkTS-Dyn示例：
```ts
async function CreatePicture() {
  let options: image.DecodingOptionsForPicture = {
    desiredAuxiliaryPictures: [image.AuxiliaryPictureType.GAINMAP] // GAINMAP为需要解码的辅助图类型。 
  };
  let pictureObj: image.Picture = await imageSourceApi.createPicture(options);
  if (pictureObj != null) {
    console.info('Create picture succeeded');
  } else {
    console.error('Create picture failed');
  }
}
```

ArkTS-Sta示例：
```ts
async function CreatePictureFunc(imageSource: image.ImageSource): void {
  let opts: image.DecodingOptionsForPicture = { desiredAuxiliaryPictures: [image.AuxiliaryPictureType.GAINMAP] };
  try {
    let picture = await imageSource.createPicture(opts);
    console.info(0x00000, 'CreatePictureFunc', 'createPicture success!');
  } catch (err) {
    console.error(0x00000, 'CreatePictureFunc', 'CreatePictureFunc failed: ' + err);
  }
}
```

## createPictureAtIndex<sup>20+</sup>

ArkTS-Dyn: createPictureAtIndex(index: number): Promise\<Picture>

ArkTS-Sta: createPictureAtIndex(index: int): Promise<Picture | undefined>

通过指定序号的图片创建Picture对象。使用Promise异步回调。

> **说明：**
>
> - 支持GIF和HEIF<sup>23+</sup>图像序列格式。从API版本26.0.0开始，增加支持AVIS格式。
> - 由于图片占用内存较大，所以当Picture对象使用完成后，应主动调用[release](./arkts-apis-image-Picture.md#release13)方法，及时释放内存。
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                                              |
| ------ | ------ | ---- | ------------------------------------------------ |
| index  | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 解码图片序号。图片序号有效的取值范围为：[0, (帧数-1)]。 |

**返回值：**

| 类型                         | 说明                         |
| ---------------------------- | ---------------------------- |
|  ArkTS-Dyn: Promise\<[Picture](arkts-apis-image-Picture.md)> <br> ArkTS-Sta: Promise\<[Picture](arkts-apis-image-Picture.md) \| undefined> | Promise对象，返回Picture。 |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息                                                      |
| -------- | ------------------------------------------------------------ |
| 7700101  | Bad source. |
| 7700102  | Unsupported MIME type. |
| 7700103  | Image too large. |
| 7700203  | Unsupported options. For example, index is invalid. |
| 7700301  | Decoding failed. |

**示例：**

ArkTS-Dyn示例：
```ts
async function CreatePictures() {
  let frameCount: number = await imageSourceApi.getFrameCount();
  for (let index = 0; index < frameCount; index++) {
    try {
      let pictureObj: image.Picture = await imageSourceApi.createPictureAtIndex(index);
      console.info('Create picture succeeded for frame: ' + index);
    } catch (e) {
      console.error('Create picture failed for frame: ' + index);
    }
  }
}
```

ArkTS-Sta示例：
```ts
async function CreatePictures(imageSourceApi: image.ImageSource) {
  let frameCount: number = await imageSourceApi.getFrameCount();
  for (let index = 0; index < frameCount; index++) {
    try {
      let pictureObj: image.Picture | undefined = await imageSourceApi.createPictureAtIndex(index);
      if (pictureObj) {
        console.info('Create picture succeeded for frame: ' + index);
      }
    } catch (e) {
      console.error('Create picture failed for frame: ' + index);
    }
  }
}
```

## createPixelMap<sup>7+</sup>

ArkTS-Dyn: createPixelMap(options?: DecodingOptions): Promise\<PixelMap>

ArkTS-Sta: createPixelMap(options?: DecodingOptions): Promise\<PixelMap | undefined>

通过图片解码参数创建PixelMap对象。使用Promise异步回调。

从API version 15开始，推荐使用[createPixelMapUsingAllocator](#createpixelmapusingallocator15)，该接口可以指定输出pixelMap的内存类型[AllocatorType](arkts-apis-image-e.md#allocatortype15)，详情请参考[图片解码内存优化(ArkTS)](../../media/image/image-allocator-type.md)。

> **说明：**
>
> - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](./arkts-apis-image-PixelMap.md#release7)方法，及时释放内存。
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**卡片能力（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                                 | 必填 | 说明       |
| ------- | ------------------------------------ | ---- | ---------- |
| options | [DecodingOptions](arkts-apis-image-i.md#decodingoptions7) | 否   | 解码参数。 |

**返回值：**

| 类型                             | 说明                  |
| -------------------------------- | --------------------- |
| ArkTS-Dyn: Promise\<[PixelMap](arkts-apis-image-PixelMap.md)> <br>ArkTS-Sta: Promise\<[PixelMap](arkts-apis-image-PixelMap.md) \| undefined> | Promise对象，返回PixelMap。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

imageSourceApi.createPixelMap().then((pixelMap: image.PixelMap) => {
  console.info('Succeeded in creating pixelMap object through image decoding parameters.');
}).catch((error: BusinessError) => {
  console.error('Failed to create pixelMap object through image decoding parameters.');
})
```

ArkTS-Sta示例：
```ts
async function CreatePixelMapFunc(imageSource: image.ImageSource): void {
  try {
    let pixelMap = await imageSource.createPixelMap();
    console.info(0x00000, 'CreatePixelMapFunc', 'createPixelMap success!');
  } catch (err) {
    console.error(0x00000, 'CreatePixelMapFunc', 'CreatePixelMapFunc failed: ' + err);
  }
}
```

## createPixelMap<sup>7+</sup>

ArkTS-Dyn: createPixelMap(callback: AsyncCallback\<PixelMap>): void

ArkTS-Sta: createPixelMap(callback: AsyncCallback\<PixelMap | undefined>): void

通过默认参数创建PixelMap对象。使用callback异步回调。

从API version 15开始，推荐使用[createPixelMapUsingAllocator](#createpixelmapusingallocator15)，该接口可以指定输出pixelMap的内存类型[AllocatorType](arkts-apis-image-e.md#allocatortype15)，详情请参考[图片解码内存优化(ArkTS)](../../media/image/image-allocator-type.md)。

> **说明：**
>
> - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](./arkts-apis-image-PixelMap.md#release7)方法，及时释放内存。
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**卡片能力（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                                  | 必填 | 说明                       |
| -------- | ------------------------------------- | ---- | -------------------------- |
| callback | ArkTS-Dyn: AsyncCallback<[PixelMap](arkts-apis-image-PixelMap.md)>  <br>ArkTS-Sta: AsyncCallback<[PixelMap](arkts-apis-image-PixelMap.md) \| undefined>| 是   | 回调函数，当创建PixelMap对象成功，err为undefined，data为获取到的PixelMap对象；否则为错误对象。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

imageSourceApi.createPixelMap((err: BusinessError, pixelMap: image.PixelMap) => {
  if (err) {
    console.error(`Failed to create pixelMap.code is ${err.code},message is ${err.message}`);
  } else {
    console.info('Succeeded in creating pixelMap object.');
  }
})
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

function CreatePixelMapCallbackFunc(imageSource: image.ImageSource): void {
  try {
    imageSource.createPixelMap((err: BusinessError | null, pixelMap: image.PixelMap | undefined) => {
      if (err) {
        console.error(0x00000, 'CreatePixelMapCallbackFunc', 'createPixelMap failed: ' + err);
      } else {
        console.info(0x00000, 'CreatePixelMapCallbackFunc', 'createPixelMap success!');
      }
    });
  } catch (err) {
    console.error(0x00000, 'CreatePixelMapCallbackFunc', 'CreatePixelMapCallbackFunc failed: ' + err);
  }
}
```

## createPixelMap<sup>7+</sup>

ArkTS-Dyn: createPixelMap(callback: AsyncCallback\<PixelMap>): void

ArkTS-Sta: createPixelMap(callback: AsyncCallback\<PixelMap | undefined>): void

通过图片解码参数创建PixelMap对象。使用callback异步回调。

从API version 15开始，推荐使用[createPixelMapUsingAllocator](#createpixelmapusingallocator15)，该接口可以指定输出pixelMap的内存类型[AllocatorType](arkts-apis-image-e.md#allocatortype15)，详情请参考[图片解码内存优化(ArkTS)](../../media/image/image-allocator-type.md)。

> **说明：**
>
> - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](./arkts-apis-image-PixelMap.md#release7)方法，及时释放内存。
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**卡片能力（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                                  | 必填 | 说明                       |
| -------- | ------------------------------------- | ---- | -------------------------- |
| callback | ArkTS-Dyn: AsyncCallback<[PixelMap](arkts-apis-image-PixelMap.md)>  <br>ArkTS-Sta: AsyncCallback<[PixelMap](arkts-apis-image-PixelMap.md) \| undefined>| 是   | 回调函数，当创建PixelMap对象成功，err为undefined，data为获取到的PixelMap对象；否则为错误对象。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

imageSourceApi.createPixelMap((err: BusinessError, pixelMap: image.PixelMap) => {
  if (err) {
    console.error(`Failed to create pixelMap.code is ${err.code},message is ${err.message}`);
  } else {
    console.info('Succeeded in creating pixelMap object.');
  }
})
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

function CreatePixelMapFunc(imageSource: image.ImageSource): void {
  try {
    await imageSource.createPixelMap((err: BusinessError | null, pixelMap: image.PixelMap | undefined) => {
      if (err) {
        console.error(0x00000, 'CreatePixelMapFunc', 'createPixelMap failed: ' + err);
      } else {
        console.info(0x00000, 'CreatePixelMapFunc', 'createPixelMap success!');
      }
    });
  } catch (err) {
    console.error(0x00000, 'CreatePixelMapFunc', 'CreatePixelMapFunc failed: ' + err);
  }
}
```

## createPixelMap<sup>7+</sup>

ArkTS-Dyn: createPixelMap(options: DecodingOptions, callback: AsyncCallback\<PixelMap>): void

ArkTS-Sta: createPixelMap(options: DecodingOptions, callback: AsyncCallback\<PixelMap | undefined>): void

通过图片解码参数创建PixelMap对象。

从API version 15开始，推荐使用[createPixelMapUsingAllocator](#createpixelmapusingallocator15)，该接口可以指定输出pixelMap的内存类型[AllocatorType](arkts-apis-image-e.md#allocatortype15)，详情请参考[申请图片解码内存(ArkTS)](../../media/image/image-allocator-type.md)。


**卡片能力（仅ArkTS-Dyn）：** 从API version 12开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 7

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                  | 必填 | 说明                       |
| -------- | ------------------------------------- | ---- | -------------------------- |
| options  | [DecodingOptions](arkts-apis-image-i.md#decodingoptions7)  | 是   | 解码参数。                 |
| callback | ArkTS-Dyn: AsyncCallback<[PixelMap](arkts-apis-image-PixelMap.md)> <br>ArkTS-Sta: AsyncCallback<[PixelMap](arkts-apis-image-PixelMap.md) \| undefined>  | 是   | 回调函数，当创建PixelMap对象成功，err为undefined，data为获取到的PixelMap对象；否则为错误对象。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let decodingOptions: image.DecodingOptions = {
  sampleSize: 1,
  editable: true,
  desiredSize: { width: 1, height: 2 },
  rotate: 10,
  desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
  desiredRegion: { size: { width: 1, height: 2 }, x: 0, y: 0 },
  // 若解码接口同时传入了desiredSize参数与desiredRegion参数，需进一步传入cropAndScaleStrategy参数指定缩放与裁剪的先后顺序，推荐设置CROP_FIRST。
  cropAndScaleStrategy: image.CropAndScaleStrategy.CROP_FIRST,
  index: 0
};
imageSourceApi.createPixelMap(decodingOptions, (err: BusinessError, pixelMap: image.PixelMap) => {
  if (err) {
    console.error(`Failed to create pixelMap.code is ${err.code},message is ${err.message}`);
  } else {
    console.info('Succeeded in creating pixelMap object.');
  }
})
```

ArkTS-Sta示例：
```ts
function CreatePixelMapFunc(imageSource: image.ImageSource): void {
  let decodingOpts: image.DecodingOptions = {
    sampleSize: 1,
    editable: true,
    desiredSize: { width: 1, height: 2 },
    rotate: 10,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    desiredRegion: { size: { width: 1, height: 2 }, x: 0, y: 0 },
    // 若解码接口同时传入了desiredSize参数与desiredRegion参数，需进一步传入cropAndScaleStrategy参数指定缩放与裁剪的先后顺序，推荐设置CROP_FIRST。
    cropAndScaleStrategy: image.CropAndScaleStrategy.CROP_FIRST,
    index: 0
  };
  try {
    imageSource.createPixelMap(decodingOpts, (err: BusinessError | null, pixelMap: image.PixelMap | undefined) => {
      if (err) {
        console.error(0x00000, 'CreatePixelMapFunc', 'createPixelMap failed: ' + err);
      } else {
        console.info(0x00000, 'CreatePixelMapFunc', 'createPixelMap success!');
      }
    });
  } catch (err) {
    console.error(0x00000, 'CreatePixelMapFunc', 'CreatePixelMapFunc failed: ' + err);
  }
}
```

## createPixelMapSync<sup>12+</sup>

ArkTS-Dyn: createPixelMapSync(options?: DecodingOptions): PixelMap

ArkTS-Sta: createPixelMapSync(options?: DecodingOptions): PixelMap | undefined

通过图片解码参数同步创建PixelMap对象。

由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](./arkts-apis-image-PixelMap.md#release7)方法，及时释放内存。

释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

从API version 15开始，推荐使用[createPixelMapUsingAllocatorSync](#createpixelmapusingallocatorsync15)，该接口可以指定输出pixelMap的内存类型[AllocatorType](arkts-apis-image-e.md#allocatortype15)，详情请参考[图片解码内存优化(ArkTS)](../../media/image/image-allocator-type.md)。

> **说明：**
>
> 该方法为同步方法，调用时会阻塞当前线程，不建议在主线程中调用，否则可能导致应用卡顿、掉帧或响应延迟。具体场景参考[耗时任务并发场景简介](../../arkts-utils/time-consuming-task-overview.md)。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                  | 必填 | 说明                       |
| -------- | ------------------------------------- | ---- | -------------------------- |
| options  | [DecodingOptions](arkts-apis-image-i.md#decodingoptions7)  | 否   | 解码参数。 |

**返回值：**

| 类型                             | 说明                  |
| -------------------------------- | --------------------- |
| ArkTS-Dyn: [PixelMap](arkts-apis-image-PixelMap.md) <br>ArkTS-Sta: [PixelMap](arkts-apis-image-PixelMap.md) \| undefined | 用于同步返回创建结果。 |

**示例：**

ArkTS-Dyn示例：
```ts
function CreatePixelMapSync(context : Context) {
  // 此处'test.jpg'仅作示例，请开发者自行替换，否则imageSource创建失败会导致后续无法正常执行。
  let filePath: string = context.filesDir + "/test.jpg";
  let imageSource = image.createImageSource(filePath);
  let decodingOptions: image.DecodingOptions = {
    sampleSize: 1,
    editable: true,
    desiredSize: { width: 1, height: 2 },
    rotate: 10,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    desiredRegion: { size: { width: 1, height: 2 }, x: 0, y: 0 },
    // 若解码接口同时传入了desiredSize参数与desiredRegion参数，需进一步传入cropAndScaleStrategy参数指定缩放与裁剪的先后顺序，推荐设置CROP_FIRST。
    cropAndScaleStrategy: image.CropAndScaleStrategy.CROP_FIRST,
    index: 0
  };
  let pixelmap = imageSource.createPixelMapSync(decodingOptions);
  if (pixelmap != undefined) {
    console.info('Succeeded in creating pixelMap object.');
  } else {
    console.error('Failed to create pixelMap.');
  }
}
```

ArkTS-Sta示例：
```ts
function CreatePixelMapSyncFunc(imageSource: image.ImageSource): void {
  try {
    let pixelMap = imageSource.createPixelMapSync();
    console.info(0x00000, 'CreatePixelMapSyncFunc', 'createPixelMapSync success!');
  } catch (err) {
    console.error(0x00000, 'CreatePixelMapSyncFunc', 'CreatePixelMapSyncFunc failed: ' + err);
  }
}
```

## createPixelMapList<sup>10+</sup>

createPixelMapList(options?: DecodingOptions): Promise<Array\<PixelMap>>

通过图片解码参数创建PixelMap数组。使用Promise异步回调。

针对动态图（如Gif、Webp），该接口会返回每帧图片数据；针对静态图，该接口会返回唯一的一帧图片数据。

> **说明：**
>
> - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](./arkts-apis-image-PixelMap.md#release7)方法，及时释放内存。
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。
> - 此接口会一次性解码全部帧，当帧数过多或单帧图像过大时，会占用较大内存，造成系统内存紧张，此种情况推荐使用Image组件显示动图，Image组件采用逐帧解码，占用内存比此接口少。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                  | 必填 | 说明                       |
| -------- | ------------------------------------- | ---- | -------------------------- |
| options  | [DecodingOptions](arkts-apis-image-i.md#decodingoptions7)  | 否   | 解码参数。 |

**返回值：**

| 类型                             | 说明                  |
| -------------------------------- | --------------------- |
| Promise\<Array\<[PixelMap](arkts-apis-image-PixelMap.md)>> | 异步返回PixelMap数组。 |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 62980096| The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.              |
| 62980099 | The shared memory data is abnormal. |
| 62980101 | The image data is abnormal. |
| 62980103| The image data is not supported.             |
| 62980106 | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |
| 62980109 | Failed to crop the image. |
| 62980111| The image source data is incomplete.           |
| 62980115 | Invalid image parameter. |
| 62980116 | Failed to decode the image. |
| 62980118| Failed to create the image plugin.             |
| 62980137 | Invalid media operation. |
| 62980173 | The DMA memory does not exist. |
| 62980174 | The DMA memory data is abnormal. |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMapList(imageSourceObj : image.ImageSource) {
  let decodeOpts: image.DecodingOptions = {
    sampleSize: 1,
    editable: true,
    desiredSize: { width: 198, height: 202 },
    rotate: 0,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    index: 0,
  };
  imageSourceObj.createPixelMapList(decodeOpts).then((pixelMapList: Array<image.PixelMap>) => {
    console.info('Succeeded in creating pixelMapList object.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to create pixelMapList object, error code is ${err}`);
  })
}
```

ArkTS-Sta示例：
```ts
async function CreatePixelMapListFunc(imageSource: image.ImageSource): void {
  let decodeOpts: image.DecodingOptions = {
  sampleSize: 1,
  editable: true,
  desiredSize: { width: 198, height: 202 },
  rotate: 0,
  desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
  index: 0,
};
  try {
    let pixelMapList: Array<image.PixelMap> = await imageSource.createPixelMapList(decodeOpts);
    console.info(0x00000, 'CreatePixelMapListFunc', 'createPixelMapList success!');
  } catch (err) {
    console.error(0x00000, 'CreatePixelMapListFunc', 'CreatePixelMapListFunc failed: ' + err);
  }
}
```

## createPixelMapList<sup>10+</sup>

createPixelMapList(callback: AsyncCallback<Array\<PixelMap>>): void

通过默认参数创建PixelMap数组。使用callback异步回调。

针对动态图（如Gif、Webp），该接口会返回每帧图片数据；针对静态图，该接口会返回唯一的一帧图片数据。

> **说明：**
>
> - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](./arkts-apis-image-PixelMap.md#release7)方法，及时释放内存。
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。
> - 此接口会一次性解码全部帧，当帧数过多或单帧图像过大时，会占用较大内存，造成系统内存紧张，此种情况推荐使用Image组件显示动图，Image组件采用逐帧解码，占用内存比此接口少。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名     | 类型                                  | 必填 | 说明                       |
| -------- | ------------------------------------- | ---- | -------------------------- |
| callback | AsyncCallback<Array<[PixelMap](arkts-apis-image-PixelMap.md)>> | 是   | 回调函数，当创建PixelMap对象数组成功，err为undefined，data为获取到的PixelMap对象数组；否则为错误对象。  |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 62980096 | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.             |
| 62980099 | The shared memory data is abnormal.  |
| 62980101 | The image data is abnormal.          |
| 62980103 | The image data is not supported.         |
| 62980106 | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |
| 62980109 | Failed to crop the image.            |
| 62980111 | The image source data is incomplete. |
| 62980115 | Invalid image parameter.      |
| 62980116 | Failed to decode the image.         |
| 62980118 | Failed to create the image plugin.   |
| 62980137 | Invalid media operation.     |
| 62980173 | The DMA memory does not exist.        |
| 62980174 | The DMA memory data is abnormal.    |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMapList(imageSourceObj : image.ImageSource) {
  imageSourceObj.createPixelMapList((err: BusinessError, pixelMapList: Array<image.PixelMap>) => {
    if (err) {
      console.error(`Failed to create pixelMapList object, error code is ${err}`);
    } else {
      console.info('Succeeded in creating pixelMapList object.');
    }
  })
}
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

function CreatePixelMapListFunc(imageSource: image.ImageSource): void {
  try {
    imageSource.createPixelMapList((err: BusinessError | null, pixelMapList: Array<image.PixelMap> | undefined) => {
      if (err) {
        console.error(0x00000, 'CreatePixelMapListFunc', 'createPixelMapList failed: ' + err);
      } else {
        console.info(0x00000, 'CreatePixelMapListFunc', 'createPixelMapList success!');
      }
    });
  } catch (err) {
    console.error(0x00000, 'CreatePixelMapListFunc', 'CreatePixelMapListFunc failed: ' + err);
  }
}
```

## createPixelMapList<sup>10+</sup>

createPixelMapList(options: DecodingOptions, callback: AsyncCallback<Array\<PixelMap>>): void

通过图片解码参数创建PixelMap数组。使用callback异步回调。

针对动态图（如Gif、Webp），该接口会返回每帧图片数据；针对静态图，该接口会返回唯一的一帧图片数据。

> **说明：**
>
> - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](./arkts-apis-image-PixelMap.md#release7)方法，及时释放内存。
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。
> - 此接口会一次性解码全部帧，当帧数过多或单帧图像过大时，会占用较大内存，造成系统内存紧张，此种情况推荐使用Image组件显示动图，Image组件采用逐帧解码，占用内存比此接口少。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                 | 必填 | 说明                               |
| -------- | -------------------- | ---- | ---------------------------------- |
| options | [DecodingOptions](arkts-apis-image-i.md#decodingoptions7) | 是 | 解码参数。 |
| callback | AsyncCallback<Array<[PixelMap](arkts-apis-image-PixelMap.md)>> | 是   | 回调函数，当创建PixelMap对象数组成功，err为undefined，data为获取到的PixelMap对象数组；否则为错误对象。  |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 62980096 | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.            |
| 62980099 | The shared memory data is abnormal.  |
| 62980101 | The image data is abnormal.         |
| 62980103 | The image data is not supported.        |
| 62980106 | The image data is too large. This status code is thrown when an error occurs during the process of checking size. |
| 62980109 | Failed to crop the image.           |
| 62980111 | The image source data is incomplete. |
| 62980115 | Invalid image parameter.      |
| 62980116 | Failed to decode the image.         |
| 62980118 | Failed to create the image plugin.  |
| 62980137 | Invalid media operation.      |
| 62980173 | The DMA memory does not exist.         |
| 62980174 | The DMA memory data is abnormal.     |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function CreatePixelMapList(imageSourceObj : image.ImageSource) {
  let decodeOpts: image.DecodingOptions = {
    sampleSize: 1,
    editable: true,
    desiredSize: { width: 198, height: 202 },
    rotate: 0,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    index: 0,
  };
  imageSourceObj.createPixelMapList(decodeOpts, (err: BusinessError, pixelMapList: Array<image.PixelMap>) => {
    if (err) {
      console.error(`Failed to create pixelMapList object, error code is ${err}`);
    } else {
      console.info('Succeeded in creating pixelMapList object.');
    }
  })
}
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

function CreatePixelMapListFunc(imageSource: image.ImageSource): void {
  let decodeOpts: image.DecodingOptions = {
    sampleSize: 1,
    editable: true,
    desiredSize: { width: 198, height: 202 },
    rotate: 0,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    index: 0,
  };
  try {
    imageSource.createPixelMapList(decodeOpts, (err: BusinessError | null, pixelMapList: Array<image.PixelMap> | undefined) => {
      if (err) {
        console.error(0x00000, 'CreatePixelMapListFunc', 'createPixelMapList failed: ' + err);
      } else {
        console.info(0x00000, 'CreatePixelMapListFunc', 'createPixelMapList success!');
      }
    });
  } catch (err) {
    console.error(0x00000, 'CreatePixelMapListFunc', 'CreatePixelMapListFunc failed: ' + err);
  }
}
```

## createPixelMapUsingAllocator<sup>15+</sup>

ArkTS-Dyn: createPixelMapUsingAllocator(options?: DecodingOptions, allocatorType?: AllocatorType): Promise\<PixelMap>

ArkTS-Sta: createPixelMapUsingAllocator(options?: DecodingOptions, allocatorType?: AllocatorType): Promise\<PixelMap | undefined>

使用指定的分配器根据图像解码参数异步创建PixelMap对象。使用Promise异步回调。接口使用详情请参考[图片解码内存优化(ArkTS)](../../media/image/image-allocator-type.md)。

> **说明：**
>
> - 该方法为非线程安全的方法，不支持在同一个ImageSource实例上并发调用。
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](./arkts-apis-image-PixelMap.md#release7)方法，及时释放内存。
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名        | 类型                                 | 必填 | 说明                     |
| ------------- | ------------------------------------ | ---- | ------------------------ |
| options        | [DecodingOptions](arkts-apis-image-i.md#decodingoptions7) | 否   | 解码参数。 |
| allocatorType | [AllocatorType](arkts-apis-image-e.md#allocatortype15)   | 否   | 用于图像解码的内存类型。默认值为AllocatorType.AUTO。 |

**返回值：**

| 类型                             | 说明                        |
| -------------------------------- | --------------------------- |
| ArkTS-Dyn: Promise\<[PixelMap](arkts-apis-image-PixelMap.md)>  | Promise对象，返回PixelMap。 |
| ArkTS-Sta: Promise\<[PixelMap](arkts-apis-image-PixelMap.md) \| undefined> | Promise对象，返回PixelMap。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types;3.Parameter verification failed. |
| 7700101  | Bad source. e.g.,1. Image has invalid width or height. 2. Image source incomplete. 3. Read image data failed. 4. Codec create failed. |
| 7700102  | Unsupported mimetype.                                        |
| 7700103  | Image too large.  This status code is thrown when an error occurs during the process of checking size. |
| 7700201  | Unsupported allocator type, e.g., use share memory to decode a HDR image as only DMA supported hdr metadata. |
| 7700203  | Unsupported options, e.g., cannot convert image into desired pixel format. |
| 7700301  | Failed to decode image.                                      |
| 7700302  | Failed to allocate memory.                                   |

**示例：**

ArkTS-Dyn示例：
```ts
async function CreatePixelMapUsingAllocator(context : Context) {
  // 此处'test.jpg'仅作示例，请开发者自行替换，否则imageSource创建失败会导致后续无法正常执行。
  let filePath: string = context.filesDir + "/test.jpg";
  let imageSource = image.createImageSource(filePath);
  let decodingOptions: image.DecodingOptions = {
    editable: true,
    desiredSize: { width: 3072, height: 4096 },
    rotate: 10,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    desiredRegion: { size: { width: 3072, height: 4096 }, x: 0, y: 0 },
    // 若解码接口同时传入了desiredSize参数与desiredRegion参数，需进一步传入cropAndScaleStrategy参数指定缩放与裁剪的先后顺序，推荐设置CROP_FIRST。
    cropAndScaleStrategy: image.CropAndScaleStrategy.CROP_FIRST,
    index: 0
  };
  let pixelmap = imageSource.createPixelMapUsingAllocator(decodingOptions, image.AllocatorType.AUTO);
  if (pixelmap != undefined) {
    console.info('Succeeded in creating pixelMap object.');
  } else {
    console.error('Failed to create pixelMap.');
  }
}
```

ArkTS-Sta示例：
```ts
async function CreatePixelMapUsingAllocatorFunc(imageSource: image.ImageSource): void {
   let decodeOpts: image.DecodingOptions = {
    sampleSize: 1,
    editable: true,
    desiredSize: { width: 198, height: 202 },
    rotate: 0,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    index: 0,
  };
  try {
    let pixelMap = await imageSource.createPixelMapUsingAllocator(decodeOpts, image.AllocatorType.AUTO);
    console.info(0x00000, 'CreatePixelMapUsingAllocatorFunc', 'createPixelMapUsingAllocator success!');
  } catch (err) {
    console.error(0x00000, 'CreatePixelMapUsingAllocatorFunc', 'CreatePixelMapUsingAllocatorFunc failed: ' + err);
  }
}
```

## createPixelMapUsingAllocatorSync<sup>15+</sup>

ArkTS-Dyn: createPixelMapUsingAllocatorSync(options?: DecodingOptions, allocatorType?: AllocatorType): PixelMap

ArkTS-Sta: createPixelMapUsingAllocatorSync(options?: DecodingOptions, allocatorType?: AllocatorType): PixelMap | undefined

根据指定的分配器同步创建一个基于图像解码参数的PixelMap对象。接口使用详情请参考[图片解码内存优化(ArkTS)](../../media/image/image-allocator-type.md)。

由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](./arkts-apis-image-PixelMap.md#release7)方法，及时释放内存。

释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

> **说明：**
>
> 该方法为同步方法，调用时会阻塞当前线程，不建议在主线程中调用，否则可能导致应用卡顿、掉帧或响应延迟。具体场景参考[耗时任务并发场景简介](../../arkts-utils/time-consuming-task-overview.md)。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名        | 类型                                 | 必填 | 说明                     |
| ------------- | ------------------------------------ | ---- | ------------------------ |
| options        | [DecodingOptions](arkts-apis-image-i.md#decodingoptions7) | 否   | 解码参数。 |
| allocatorType | [AllocatorType](arkts-apis-image-e.md#allocatortype15)   | 否   | 用于图像解码的内存类型。默认值为AllocatorType.AUTO。 |

**返回值：**

| 类型                   | 说明                   |
| ---------------------- | ---------------------- |
| ArkTS-Dyn: [PixelMap](arkts-apis-image-PixelMap.md)  | 用于同步返回创建结果。 |
| ArkTS-Sta: [PixelMap](arkts-apis-image-PixelMap.md) \| undefined | 用于同步返回创建结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码说明文档](../errorcode-universal.md)和[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error.Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types;3.Parameter verification failed. |
| 7700101  | Bad source. e.g.,1. Image has invalid width or height. 2. Image source incomplete. 3. Read image data failed. 4. Codec create failed. |
| 7700102  | Unsupported mimetype.                                        |
| 7700103  | Image too large.  This status code is thrown when an error occurs during the process of checking size. |
| 7700201  | Unsupported allocator type, e.g., use share memory to decode a HDR image as only DMA supported hdr metadata. |
| 7700203  | Unsupported options, e.g., cannot convert image into desired pixel format. |
| 7700301  | Failed to decode image.                                      |
| 7700302  | Failed to allocate memory.                                   |

**示例：**

ArkTS-Dyn示例：
```ts
async function CreatePixelMapUsingAllocator(context : Context) {
  // 此处'test.jpg'仅作示例，请开发者自行替换，否则imageSource创建失败会导致后续无法正常执行。
  let filePath: string = context.filesDir + "/test.jpg";
  let imageSource = image.createImageSource(filePath);
  let decodingOptions: image.DecodingOptions = {
    editable: true,
    desiredSize: { width: 3072, height: 4096 },
    rotate: 10,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    desiredRegion: { size: { width: 3072, height: 4096 }, x: 0, y: 0 },
    // 若解码接口同时传入了desiredSize参数与desiredRegion参数，需进一步传入cropAndScaleStrategy参数指定缩放与裁剪的先后顺序，推荐设置CROP_FIRST。
    cropAndScaleStrategy: image.CropAndScaleStrategy.CROP_FIRST,
    index: 0
  };
  let pixelmap = imageSource.createPixelMapUsingAllocatorSync(decodingOptions, image.AllocatorType.AUTO);
  if (pixelmap != undefined) {
    console.info('Succeeded in creating pixelMap object.');
  } else {
    console.error('Failed to create pixelMap.');
  }
}
```

ArtTS-Sta示例:
```ts
function CreatePixelMapUsingAllocatorSyncFunc(imageSource: image.ImageSource): void {
   let decodeOpts: image.DecodingOptions = {
    sampleSize: 1,
    editable: true,
    desiredSize: { width: 198, height: 202 },
    rotate: 0,
    desiredPixelFormat: image.PixelMapFormat.RGBA_8888,
    index: 0,
  };
  try {
    let pixelMap = imageSource.createPixelMapUsingAllocatorSync(decodeOpts, image.AllocatorType.AUTO);
    console.info(0x00000, 'CreatePixelMapUsingAllocatorSyncFunc', 'createPixelMapUsingAllocatorSync success!');
  } catch (err) {
    console.error(0x00000, 'CreatePixelMapUsingAllocatorSyncFunc', 'CreatePixelMapUsingAllocatorSyncFunc failed: ' + err);
  }
}
```

## createThumbnail

createThumbnail(options?: DecodingOptionsForThumbnail): Promise\<PixelMap \| undefined>

通过图片解码参数创建缩略图PixelMap对象。使用Promise异步回调。

当前支持对JPEG和HEIF格式的图片创建缩略图PixelMap对象。

优先解码图片文件中包含的缩略图。若图片文件中没有缩略图，则对原图进行解码。

> **说明：**
>
> - 不支持在同一个ImageSource实例上并发调用。
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](./arkts-apis-image-PixelMap.md#release7)方法，及时释放内存。
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名  | 类型                                                         | 必填 | 说明       |
| ------- | ------------------------------------------------------------ | ---- | ---------- |
| options | [DecodingOptionsForThumbnail](arkts-apis-image-i.md#decodingoptionsforthumbnail) | 否   | 解码参数，控制是否生成缩略图以及生成缩略图的目标尺寸。<br>默认表现：<br>- 当图像有缩略图时，解码原始缩略图，返回的PixelMap对象的宽和高与原缩略图保持一致。<br>- 当原图文件无缩略图时，对原图进行解码后，根据解码参数options下采样生成缩略图，生成后的缩略图PixelMap对象宽和高都限制在512像素以内。 |

**返回值：**

| 类型                                                         | 说明                        |
| ------------------------------------------------------------ | --------------------------- |
| Promise\<[PixelMap](arkts-apis-image-PixelMap.md) \| undefined> | Promise对象，返回PixelMap。 |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息                                       |
| -------- | ---------------------------------------------- |
| 7700102  | Unsupported mimetype.                          |
| 7700103  | Image too large.                               |
| 7700204  | Invalid parameter, e.g, invalid generate size. |
| 7700301  | Decode failed.                                 |
| 7700303  | Image does not carry thumbnail data.           |
| 7700305  | Thumbnail generation failed.                   |

**示例：**

ArkTS-Dyn示例：
```ts
async function CreateThumbnail(imageSource: image.ImageSource): Promise<image.PixelMap | undefined> {
  try {
    if (!imageSource) {
      console.error('CreateThumbnail: imageSource is null or undefined');
      return undefined;
    }
    const imageInfo = await imageSource.getImageInfo();
    const supportedMimeTypes = ['image/jpeg', 'image/heif', 'image/heic'];
    if (!supportedMimeTypes.includes(imageInfo.mimeType)) {
      console.error(`CreateThumbnail: Unsupported MIME type: ${imageInfo.mimeType}`);
      return undefined;
    }

    const decodingOptions: image.DecodingOptionsForThumbnail = {
      generateThumbnailIfAbsent: true,
      maxGeneratedPixelDimension: 200,
    };

    const pixelmap = await imageSource.createThumbnail(decodingOptions);
    if (pixelmap) {
      console.info('Succeeded in creating thumbnail pixelMap object.');
      return pixelmap;
    } else {
      console.error('Failed to create thumbnail pixelMap.');
      return undefined;
    }
  } catch (error) {
    console.error('CreateThumbnail error:', JSON.stringify(error));
    return undefined;
  }
}
```

ArkTS-Sta示例：
```ts
async function CreateThumbnailFunc(imageSource: image.ImageSource): Promise<image.PixelMap | undefined> {
  try {
    let imageInfo = await imageSource.getImageInfo();
    if (!imageInfo) {
      console.error('CreateThumbnail: imageInfo is undefined');
      return undefined;
    }
    let supportedMimeTypes = ['image/jpeg', 'image/heif', 'image/heic'];
    if (!supportedMimeTypes.includes(imageInfo.mimeType)) {
      console.error(`CreateThumbnail: Unsupported MIME type: ${imageInfo.mimeType}`);
      return undefined;
    }

    let decodingOptions: image.DecodingOptionsForThumbnail = {
      generateThumbnailIfAbsent: true,
      maxGeneratedPixelDimension: 200,
    };

    let pixelmap = await imageSource.createThumbnail(decodingOptions);
    if (pixelmap) {
      console.info('Succeeded in creating thumbnail pixelMap object.');
      return pixelmap;
    } else {
      console.error('Failed to create thumbnail pixelMap.');
      return undefined;
    }
  } catch (err) {
    console.error('CreateThumbnailFunc failed: ' + err);
    return undefined;
  }
}
```

## createThumbnailSync

createThumbnailSync(options?: DecodingOptionsForThumbnail): PixelMap \| undefined

通过图片解码参数同步创建缩略图。返回创建结果对应的[PixelMap](arkts-apis-image-PixelMap.md)对象。

当前支持对JPEG和HEIF格式的图片创建缩略图PixelMap对象。

优先解码图片文件中包含的缩略图。若图片文件中没有缩略图，则对原图进行解码。

> **说明：**
>
> - 由于图片占用内存较大，所以当PixelMap对象使用完成后，应主动调用[release](./arkts-apis-image-PixelMap.md#release7)方法，及时释放内存。
> - 释放时应确保该对象的所有异步方法均执行完成，且后续不再使用该对象。
> - 该方法为同步方法，调用时会阻塞当前线程，不建议在主线程中调用，否则可能导致应用卡顿、掉帧或响应延迟。具体场景参考[耗时任务并发场景简介](../../arkts-utils/time-consuming-task-overview.md)。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名  | 类型                                                         | 必填 | 说明       |
| ------- | ------------------------------------------------------------ | ---- | ---------- |
| options | [DecodingOptionsForThumbnail](arkts-apis-image-i.md#decodingoptionsforthumbnail) | 否   | 解码参数，控制是否生成缩略图以及生成缩略图的目标尺寸。<br>默认表现：<br>- 当图像有缩略图时，解码原始缩略图，返回的PixelMap对象的宽和高与原缩略图保持一致。<br>- 当原图文件无缩略图时，对原图进行解码后，根据解码参数options下采样生成缩略图，生成后的缩略图PixelMap对象宽和高都限制在512像素以内。 |

**返回值：**

| 类型                                                  | 说明                   |
| ----------------------------------------------------- | ---------------------- |
| [PixelMap](arkts-apis-image-PixelMap.md) \| undefined | 用于同步返回创建结果。 |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息                                       |
| -------- | ---------------------------------------------- |
| 7700102  | Unsupported mimetype.                          |
| 7700103  | Image too large.                               |
| 7700204  | Invalid parameter, e.g, invalid generate size. |
| 7700301  | Decode failed.                                 |
| 7700303  | Image does not carry thumbnail data.           |
| 7700305  | Thumbnail generation failed.                   |

**示例：**

ArkTS-Dyn示例：
```ts
async function CreateThumbnailSync(imageSource: image.ImageSource): Promise<image.PixelMap | undefined> {
  try {
    if (!imageSource) {
      console.error('CreateThumbnailSync: imageSource is null or undefined');
      return undefined;
    }
    const imageInfo = await imageSource.getImageInfo();
    const supportedMimeTypes = ['image/jpeg', 'image/heif', 'image/heic'];
    if (!supportedMimeTypes.includes(imageInfo.mimeType)) {
      console.error(`CreateThumbnailSync: Unsupported MIME type: ${imageInfo.mimeType}`);
      return undefined;
    }

    const decodingOptionsForThumbnail: image.DecodingOptionsForThumbnail = {
      generateThumbnailIfAbsent: true,
      maxGeneratedPixelDimension: 200,
    };

    const pixelmap = imageSource.createThumbnailSync(decodingOptionsForThumbnail);

    if (pixelmap) {
      console.info('Succeeded in creating thumbnail pixelMap object.');
      return pixelmap;
    } else {
      console.error('Failed to create thumbnail pixelMap.');
      return undefined;
    }
  } catch (error) {
    console.error('CreateThumbnailSync error:', JSON.stringify(error));
    return undefined;
  }
}
```

ArkTS-Sta示例：
```ts
async function CreateThumbnailSyncFunc(imageSource: image.ImageSource): Promise<image.PixelMap | undefined> {
  try {
    let imageInfo = await imageSource.getImageInfo();
    if (!imageInfo) {
      console.error('CreateThumbnailSync: imageInfo is undefined');
      return undefined;
    }
    let supportedMimeTypes = ['image/jpeg', 'image/heif', 'image/heic'];
    if (!supportedMimeTypes.includes(imageInfo.mimeType)) {
      console.error(`CreateThumbnailSync: Unsupported MIME type: ${imageInfo.mimeType}`);
      return undefined;
    }

    let decodingOptions: image.DecodingOptionsForThumbnail = {
      generateThumbnailIfAbsent: true,
      maxGeneratedPixelDimension: 200,
    };

    let pixelmap = imageSource.createThumbnailSync(decodingOptions);
    if (pixelmap) {
      console.info('Succeeded in creating thumbnail pixelMap object.');
      return pixelmap;
    } else {
      console.error('Failed to create thumbnail pixelMap.');
      return undefined;
    }
  } catch (err) {
    console.error('CreateThumbnailSync error:', JSON.stringify(err));
    return undefined;
  }
}
```

## getDelayTimeList<sup>10+</sup>

ArkTS-Dyn: getDelayTimeList(callback: AsyncCallback<Array\<number>>): void

ArkTS-Sta: getDelayTimeList(callback: AsyncCallback<Array\<int>>): void

获取图像延迟时间数组。使用callback异步回调。此接口仅用于gif图片和webp图片。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                 | 必填 | 说明                               |
| -------- | -------------------- | ---- | ---------------------------------- |
| callback | ArkTS-Dyn: AsyncCallback<Array\<number>><br/>ArkTS-Sta: AsyncCallback<Array\<int>> | 是   | 回调函数，当获取图像延迟时间数组成功，err为undefined，data为获取到的图像延时时间数组；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 62980096| The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.              |
| 62980110| The image source data is incorrect.             |
| 62980111| The image source data is incomplete.            |
| 62980115 | Invalid image parameter. |
| 62980116| Failed to decode the image. |
| 62980118| Failed to create the image plugin. |
| 62980122| Failed to decode the image header. |
| 62980149 | Invalid MIME type for the image source. |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetDelayTimeList(imageSourceObj : image.ImageSource) {
  imageSourceObj.getDelayTimeList((err: BusinessError, delayTimes: Array<number>) => {
    if (err) {
      console.error(`Failed to get delayTimes object.code is ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in getting delayTimes object.');
    }
  })
}
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

function GetDelayTimeListFunc(imageSource: image.ImageSource): void {
  try {
    imageSource.getDelayTimeList((err: BusinessError | null, delayTimeList: Array<int> | undefined) => {
      if (err) {
        console.error(0x00000, 'GetDelayTimeListFunc', 'getDelayTimeList failed: ' + err);
      } else {
        console.info(0x00000, 'GetDelayTimeListFunc', 'getDelayTimeList success!');
      }
    });
  } catch (err) {
    console.error(0x00000, 'GetDelayTimeListFunc', 'GetDelayTimeListFunc failed: ' + err);
  }
}
```

## getDelayTimeList<sup>10+</sup>

ArkTS-Dyn: getDelayTimeList(): Promise<Array\<number>>

ArkTS-Sta: getDelayTimeList(): Promise<Array\<int>>

获取图像延迟时间数组。使用Promise异步回调。此接口仅用于gif图片和webp图片。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型           | 说明                        |
| -------------- | --------------------------- |
| ArkTS-Dyn: Promise<Array\<number>><br/>ArkTS-Sta: Promise<Array\<int>> | Promise对象，返回延迟时间数组。 |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 62980096 | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.             |
| 62980110 | The image source data is incorrect.      |
| 62980111 | The image source data is incomplete. |
| 62980115 | Invalid image parameter.      |
| 62980116 | Failed to decode the image.          |
| 62980118 | Failed to create the image plugin.  |
| 62980122 | Failed to decode the image header.   |
| 62980149 | Invalid MIME type for the image source.      |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetDelayTimeList(imageSourceObj : image.ImageSource) {
  imageSourceObj.getDelayTimeList().then((delayTimes: Array<number>) => {
    console.info('Succeeded in getting delayTimes object.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to get delayTimes object.code is ${err.code},message is ${err.message}`);
  })
}
```

ArkTS-Sta示例：
```ts
async function GetDelayTimeListFunc(imageSource: image.ImageSource): void {
  try {
    let delayTimes: Array<int> = await imageSource.getDelayTimeList();
    console.info(0x00000, 'GetDelayTimeListFunc', 'getDelayTimeList success!');
  } catch (err) {
    console.error(0x00000, 'GetDelayTimeListFunc', 'GetDelayTimeListFunc failed: ' + err);
  }
}
```

## getFrameCount<sup>10+</sup>

ArkTS-Dyn: getFrameCount(callback: AsyncCallback\<number>): void

ArkTS-Sta: getFrameCount(callback: AsyncCallback\<int>): void

获取图像帧数。使用callback异步回调。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                 | 必填 | 说明                               |
| -------- | -------------------- | ---- | ---------------------------------- |
| callback | ArkTS-Dyn: AsyncCallback\<number><br/>ArkTS-Sta: AsyncCallback\<int> | 是   | 回调函数，当获取图像帧数成功，err为undefined，data为获取到的图像帧数；否则为错误对象。 |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 62980096| The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.             |
| 62980111| The image source data is incomplete. |
| 62980112| The image format does not match. |
| 62980113| Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted.            |
| 62980115| Invalid image parameter. |
| 62980116| Failed to decode the image. |
| 62980118| Failed to create the image plugin. |
| 62980122| Failed to decode the image header. |
| 62980137| Invalid media operation. |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetFrameCount(imageSourceObj : image.ImageSource) {
  imageSourceObj.getFrameCount((err: BusinessError, frameCount: number) => {
    if (err) {
      console.error(`Failed to get frame count.code is ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in getting frame count.');
    }
  })
}
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

function GetFrameCountFunc(imageSource: image.ImageSource): void {
  try {
    imageSource.getFrameCount((err: BusinessError | null, frameCount: int | undefined) => {
      if (err) {
        console.error(0x00000, 'GetFrameCountFunc', 'getFrameCount failed: ' + err);
      } else {
        console.info(0x00000, 'GetFrameCountFunc', 'getFrameCount success!');
      }
    });
  } catch (err) {
    console.error(0x00000, 'GetFrameCountFunc', 'GetFrameCountFunc failed: ' + err);
  }
}
```

## getFrameCount<sup>10+</sup>

ArkTS-Dyn: getFrameCount(): Promise\<number>

ArkTS-Sta: getFrameCount(): Promise\<int>

获取图像帧数。使用Promise异步回调。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型           | 说明                        |
| -------------- | --------------------------- |
| ArkTS-Dyn: Promise\<number><br/>ArkTS-Sta: Promise\<int> | Promise对象，返回图像帧数。 |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 62980096 | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.             |
| 62980111 | The image source data is incomplete. |
| 62980112 | The image format does not match.        |
| 62980113| Unknown image format. The image data provided is not in a recognized or supported format, or it may be corrupted.            |
| 62980115 | Invalid image parameter.      |
| 62980116 | Failed to decode the image.          |
| 62980118 | Failed to create the image plugin.   |
| 62980122 | Failed to decode the image header.  |
| 62980137 | Invalid media operation.      |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetFrameCount(imageSourceObj : image.ImageSource) {
  imageSourceObj.getFrameCount().then((frameCount: number) => {
    console.info('Succeeded in getting frame count.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to get frame count.code is ${err.code},message is ${err.message}`);
  })
}
```

ArkTS-Sta示例：
```ts
async function GetFrameCountFunc(imageSource: image.ImageSource): void {
  try {
    let frameCount: int = await imageSource.getFrameCount();
    console.info(0x00000, 'GetFrameCountFunc', 'getFrameCount success!');
  } catch (err) {
    console.error(0x00000, 'GetFrameCountFunc', 'GetFrameCountFunc failed: ' + err);
  }
}
```

## getDisposalTypeList<sup>12+</sup>

ArkTS-Dyn: getDisposalTypeList(): Promise\<Array\<number>>

ArkTS-Sta: getDisposalTypeList(): Promise\<Array\<int>>

获取图像帧过渡模式数组。使用Promise异步回调。此接口仅用于gif图片。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型           | 说明                        |
| -------------- | --------------------------- |
| ArkTS-Dyn: Promise\<Array\<number>><br/>ArkTS-Sta: Promise\<Array\<int>> | Promise对象，返回帧过渡模式数组。 |

**错误码：**

以下错误码的详细介绍请参见[Image错误码](errorcode-image.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 62980096 | The operation failed. Possible cause: 1.Image upload exception. 2. Decoding process exception. 3. Insufficient memory.      |
| 62980101 | The image data is abnormal. |
| 62980137 | Invalid media operation.        |
| 62980149 | Invalid MIME type for the image source.      |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetDisposalTypeList(imageSourceObj : image.ImageSource) {
  imageSourceObj.getDisposalTypeList().then((disposalTypes: Array<number>) => {
    console.info('Succeeded in getting disposalTypes object.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to get disposalTypes object.code ${err.code},message is ${err.message}`);
  })
}
```

ArkTS-Sta示例：
```ts
async function GetDisposalTypeListFunc(imageSource: image.ImageSource): void {
  try {
    let disposalTypes: Array<int> = await imageSource.getDisposalTypeList();
    console.info(0x00000, 'GetDisposalTypeListFunc', 'getDisposalTypeList success!');
  } catch (err) {
    console.error(0x00000, 'GetDisposalTypeListFunc', 'GetDisposalTypeListFunc failed: ' + err);
  }
}
```

## release

release(callback: AsyncCallback\<void>): void

释放ImageSource实例。使用callback异步回调。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用该方法，及时释放内存。

释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                 | 必填 | 说明                               |
| -------- | -------------------- | ---- | ---------------------------------- |
| callback | AsyncCallback\<void> | 是   | 回调函数，当资源释放成功，err为undefined，否则为错误对象。  |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(imageSourceObj : image.ImageSource) {
  imageSourceObj.release((err: BusinessError) => {
    if (err) {
      console.error(`Failed to release the image source instance.code ${err.code},message is ${err.message}`);
    } else {
      console.info('Succeeded in releasing the image source instance.');
    }
  })
}
```

ArkTS-Sta示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

function ReleaseFunc(imageSource: image.ImageSource): void {
  try {
    imageSource.release((err: BusinessError | null) => {
      if (err) {
        console.error(0x00000, 'ReleaseFunc', 'release failed: ' + err);
      } else {
        console.info(0x00000, 'ReleaseFunc', 'release success!');
      }
    });
  } catch (err) {
    console.error(0x00000, 'ReleaseFunc', 'ReleaseFunc failed: ' + err);
  }
}
```

## release

release(): Promise\<void>

释放ImageSource实例。使用Promise异步回调。

由于图片占用内存较大，所以当ImageSource实例使用完成后，应主动调用该方法，及时释放内存。

释放时应确保该实例的所有异步方法均执行完成，且后续不再使用该实例。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 6

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型           | 说明                        |
| -------------- | --------------------------- |
| Promise\<void> |  Promise对象。无返回结果的Promise对象。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function Release(imageSourceObj : image.ImageSource) {
  imageSourceObj.release().then(() => {
    console.info('Succeeded in releasing the image source instance.');
  }).catch((error: BusinessError) => {
    console.error(`Failed to release the image source instance.code ${error.code},message is ${error.message}`);
  })
}
```

ArkTS-Sta示例：
```ts
async function ReleaseFunc(imageSource: image.ImageSource): void {
  try {
    await imageSource.release();
    console.info(0x00000, 'ReleaseFunc', 'release success!');
  } catch (err) {
    console.error(0x00000, 'ReleaseFunc', 'ReleaseFunc failed: ' + err);
  }
}
```

## getImageProperty<sup>(deprecated)</sup>

getImageProperty(key: string, options?: GetImagePropertyOptions): Promise\<string>

获取图片中给定索引处图像的指定属性键的值。用Promise异步回调。

该接口仅支持JPEG、PNG、HEIF<sup>12+</sup>和WEBP<sup>23+</sup>（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

> **说明：**
>
> 从API version 7 开始支持，从API version 11废弃，建议使用[getImageProperty](#getimageproperty11)代替。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 7

**参数：**

| 参数名  | 类型                                                 | 必填 | 说明                                 |
| ------- | ---------------------------------------------------- | ---- | ------------------------------------ |
| key     | string                                               | 是   | 图片属性名。                         |
| options | [GetImagePropertyOptions](arkts-apis-image-i.md#getimagepropertyoptionsdeprecated) | 否   | 图片属性，包括图片序号与默认属性值。 |

**返回值：**

| 类型             | 说明                                                              |
| ---------------- | ----------------------------------------------------------------- |
| Promise\<string> | Promise对象，返回图片属性值，如获取失败则返回属性默认值。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageProperty(imageSourceObj : image.ImageSource) {
  imageSourceObj.getImageProperty("BitsPerSample")
    .then((data: string) => {
      console.info('Succeeded in getting the value of the specified attribute key of the image.');
    }).catch((error: BusinessError) => {
    console.error(`Failed to get the value of the specified attribute key of the image, error.code ${error.code}, error.message ${error.message}`);
  })
}
```

## getImageProperty<sup>(deprecated)</sup>

getImageProperty(key: string, callback: AsyncCallback\<string>): void

获取图片中给定索引处图像的指定属性键的值。使用callback异步回调。

该接口仅支持JPEG、PNG、HEIF<sup>12+</sup>和WEBP<sup>23+</sup>（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

> **说明：**
>
> 从API version 7 开始支持，从API version 11废弃，建议使用[getImageProperty](#getimageproperty11)代替。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 7

**参数：**

| 参数名   | 类型                   | 必填 | 说明                                                         |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| key      | string                 | 是   | 图片属性名。                                                 |
| callback | AsyncCallback\<string> | 是   | 回调函数，当获取图片属性值成功，err为undefined，data为获取到的图片属性值；否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageProperty(imageSourceObj : image.ImageSource) {
  imageSourceObj.getImageProperty("BitsPerSample", (error: BusinessError, data: string) => {
    if (error) {
      console.error('Failed to get the value of the specified attribute key of the image.');
    } else {
      console.info('Succeeded in getting the value of the specified attribute key of the image.');
    }
  })
}
```

## getImageProperty<sup>(deprecated)</sup>

getImageProperty(key:string, options: GetImagePropertyOptions, callback: AsyncCallback\<string>): void

获取图片指定属性键的值。使用callback异步回调。

该接口仅支持JPEG、PNG、HEIF<sup>12+</sup>和WEBP<sup>23+</sup>（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

> **说明：**
>
> 从API version 7 开始支持，从API version 11废弃，建议使用[getImageProperty](#getimageproperty11)代替。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 7

**参数：**

| 参数名   | 类型                                                 | 必填 | 说明                                                          |
| -------- | ---------------------------------------------------- | ---- | ------------------------------------------------------------- |
| key      | string                                               | 是   | 图片属性名。                                                  |
| options  | [GetImagePropertyOptions](arkts-apis-image-i.md#getimagepropertyoptionsdeprecated) | 是   | 图片属性，包括图片序号与默认属性值。                          |
| callback | AsyncCallback\<string>                               | 是   | 回调函数，当获取图片属性值成功，err为undefined，data为获取到的图片属性值；否则为错误对象。|

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function GetImageProperty(imageSourceObj : image.ImageSource) {
  let property: image.GetImagePropertyOptions = { index: 0, defaultValue: '9999' }
  imageSourceObj.getImageProperty("BitsPerSample", property, (error: BusinessError, data: string) => {
    if (error) {
      console.error('Failed to get the value of the specified attribute key of the image.');
    } else {
      console.info('Succeeded in getting the value of the specified attribute key of the image.');
    }
  })
}
```

## modifyImageProperty<sup>(deprecated)</sup>

modifyImageProperty(key: string, value: string): Promise\<void>

通过指定的键修改图片属性的值。使用Promise异步回调。

该接口仅支持JPEG、PNG、HEIF<sup>12+</sup>和WEBP<sup>23+</sup>（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

> **说明：**
>
> - 调用modifyImageProperty修改属性会改变属性字节长度，使用buffer创建的ImageSource调用modifyImageProperty会导致buffer内容覆盖，目前buffer创建的ImageSource不支持调用此接口，请改用fd或path创建的ImageSource。
>
> - 从API version 9开始支持，从API version 11废弃，建议使用[modifyImageProperty](#modifyimageproperty11)代替。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名  | 类型   | 必填 | 说明         |
| ------- | ------ | ---- | ------------ |
| key     | string | 是   | 图片属性名。 |
| value   | string | 是   | 属性值。     |

**返回值：**

| 类型           | 说明                        |
| -------------- | --------------------------- |
| Promise\<void> |  Promise对象。无返回结果的Promise对象。|

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function ModifyImageProperty(imageSourceObj : image.ImageSource) {
  imageSourceObj.modifyImageProperty("ImageWidth", "120").then(() => {
    imageSourceObj.getImageProperty("ImageWidth").then((width: string) => {
      console.info(`ImageWidth is :${width}`);
    }).catch((error: BusinessError) => {
      console.error(`Failed to get the Image Width, error.code ${error.code}, error.message ${error.message}`);
    })
  }).catch((error: BusinessError) => {
    console.error(`Failed to modify the Image Width, error.code ${error.code}, error.message ${error.message}`);
  })
}
```

## modifyImageProperty<sup>(deprecated)</sup>

modifyImageProperty(key: string, value: string, callback: AsyncCallback\<void>): void

通过指定的键修改图片属性的值。使用callback异步回调。

仅支持JPEG、PNG、HEIF<sup>12+</sup>和WEBP<sup>23+</sup>（不同硬件设备支持情况不同）文件，且需要包含Exif信息。

> **说明：**
>
> - 调用modifyImageProperty修改属性会改变属性字节长度，使用buffer创建的ImageSource调用modifyImageProperty会导致buffer内容覆盖，目前buffer创建的ImageSource不支持调用此接口，请改用fd或path创建的ImageSource。
>
> - 从API version 9开始支持，从API version 11废弃，建议使用[modifyImageProperty](#modifyimageproperty11)代替。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**ArkTS-Dyn起始版本：** 9

**参数：**

| 参数名   | 类型                | 必填 | 说明                           |
| -------- | ------------------- | ---- | ------------------------------ |
| key      | string              | 是   | 图片属性名。                   |
| value    | string              | 是   | 属性值。                       |
| callback | AsyncCallback\<void> | 是   | 回调函数，当修改图片属性值成功，err为undefined，否则为错误对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

async function ModifyImageProperty(imageSourceObj : image.ImageSource) {
  imageSourceObj.modifyImageProperty("ImageWidth", "120", (err: BusinessError) => {
    if (err) {
      console.error(`Failed to modify the Image Width.code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('Succeeded in modifying the Image Width.');
    }
  })
}
```