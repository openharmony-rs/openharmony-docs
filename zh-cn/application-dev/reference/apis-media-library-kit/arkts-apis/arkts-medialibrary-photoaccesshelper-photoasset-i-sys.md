# PhotoAsset

提供封装文件属性的方法。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

<!--Device-photoAccessHelper-interface PhotoAsset--><!--Device-photoAccessHelper-interface PhotoAsset-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## cancelPhotoRequest

```TypeScript
cancelPhotoRequest(requestId: string): void
```

根据id取消指定的获取媒体缩略图的任务。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-cancelPhotoRequest(requestId: string): void--><!--Device-PhotoAsset-cancelPhotoRequest(requestId: string): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| requestId | string | 是 | 待取消的获取媒体缩略图的任务id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| 14000011 | System inner fail |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { image } from '@kit.ImageKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('cancelPhotoRequestDemo')
    let options: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: new dataSharePredicates.DataSharePredicates()
    }
    let fetchResult = await phAccessHelper.getAssets(options);
    let photoAsset = await fetchResult.getFirstObject();
    let taskId: string = photoAsset.requestPhoto({
      "size": {
        "width": 256,
        "height": 256
      },
      "requestPhotoType": photoAccessHelper.RequestPhotoType.REQUEST_ALL_THUMBNAILS
    }, async (err, pixel: image.PixelMap) => {
      if (err === undefined) {
        console.info("requestSource in, size: " + JSON.stringify((await pixel.getImageInfo()).size))
      } else {
        console.error(`requestSource failed with error: ${err.code}, ${err.message}`);
      }
    })
    console.info('requestSource taskId: ' + taskId)
    photoAsset.cancelPhotoRequest(taskId);
  } catch (err) {
    console.error(`cancelPhotoRequestDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## commitEditedAsset

```TypeScript
commitEditedAsset(editData: string, uri: string, callback: AsyncCallback<void>): void
```

提交编辑数据以及编辑后的图片或视频。使用callback异步回调。 通过uri将编辑后的文件传递给媒体库，uri是编辑后的文件在应用沙箱下的FileUri，可参考 [FileUri](../../apis-core-file-kit/arkts-apis/arkts-file-fileuri.md#ohosfilefileuri)。 > **注意：** > > 新的编辑数据提交后，将覆盖掉原来的编辑数据。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAsset-commitEditedAsset(editData: string, uri: string, callback: AsyncCallback<void>): void--><!--Device-PhotoAsset-commitEditedAsset(editData: string, uri: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editData | string | 是 | 提交的编辑数据。 |
| uri | string | 是 | 提交的编辑后的图片或视频，在应用沙箱下的uri。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | Callback对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail. Possible causes: <br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## commitEditedAsset

```TypeScript
commitEditedAsset(editData: string, uri: string): Promise<void>
```

提交编辑数据以及编辑后的图片或视频。使用Promise异步回调。 通过uri将编辑后的文件传递给媒体库，uri是编辑后的文件在应用沙箱下的FileUri，可参考 [FileUri](../../apis-core-file-kit/arkts-apis/arkts-file-fileuri.md#ohosfilefileuri)。 > **注意：** > > 新的编辑数据提交后，将覆盖掉原来的编辑数据。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAsset-commitEditedAsset(editData: string, uri: string): Promise<void>--><!--Device-PhotoAsset-commitEditedAsset(editData: string, uri: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editData | string | 是 | 提交的编辑数据。 |
| uri | string | 是 | 提交的编辑后的图片或视频，在应用沙箱下的uri。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail. Possible causes: <br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('commitEditedAssetPromiseDemo')
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let editData = '123456';
    let uri = 'file://com.example.temptest/data/storage/el2/base/haps/entry/files/test.jpg';
    await photoAsset.commitEditedAsset(editData, uri);
    console.info('commitEditedAsset is successful');
  } catch (err) {
    console.error(`commitEditedAssetPromiseDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## convertImageFormat

```TypeScript
convertImageFormat(title: string, imageFormat: SupportedImageFormat): Promise<PhotoAsset>
```

复制同一相册（用户创建的相册或应用相册）中的图片，并转换为指定格式。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAsset-convertImageFormat(title: string, imageFormat: SupportedImageFormat): Promise<PhotoAsset>--><!--Device-PhotoAsset-convertImageFormat(title: string, imageFormat: SupportedImageFormat): Promise<PhotoAsset>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| title | string | 是 | 转换后的图片标题。 |
| imageFormat | [SupportedImageFormat](arkts-medialibrary-photoaccesshelper-supportedimageformat-e-sys.md) | 是 | 支持的目标格式类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PhotoAsset&gt; | Promise对象，返回转码后文件的PhotoAsset。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error.It is recommended to retry and check the logs.Possible causes: <br>1. Database corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scene parameters validate failed, possible causes: <br>1. The original file does not exist locally in PhotoAsset; <br>2. The original file format is not within the supported range; <br>3. The original file is a temporary file or is being edited; <br>4. The title is the same with an image in the same album; <br>5. PhotoAsset is a photo in the trash or a hidden photo; <br>6. The title does not meet the parameter specifications. |

## 示例

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('convertImageFormatDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let photoAsset = await fetchResult.getFirstObject();
  try {
    let newPhotoAsset = await photoAsset.convertImageFormat('test', photoAccessHelper.SupportedImageFormat.AVFILE_FORMAT_JPG);
    console.error(`convertImageFormat success.`);
  } catch (err) {
    console.error(`convertImageFormat failed. error: ${err.code}, ${err.message}`);
  }
}
```

## createTemporaryCompatibleDuplicate

```TypeScript
createTemporaryCompatibleDuplicate(): Promise<void>
```

为不支持HEIF/HEIC图片编码格式的第三方应用创建JPEG格式的兼容副本。使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAsset-createTemporaryCompatibleDuplicate(): Promise<void>--><!--Device-PhotoAsset-createTemporaryCompatibleDuplicate(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error.It is recommended to retry and check the logs.Possible causes: <br>1. Database corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scene parameters validate failed, possible causes: <br>1. The original file does not exist locally in PhotoAsset; <br>2. The original file format is not within the supported range; <br>3. The original file is a temporary file or is being edited; |

## 示例

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('createTemporaryCompatibleDuplicatePromiseDemo')
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    await photoAsset.createTemporaryCompatibleDuplicate();
  } catch (err) {
    console.error(`createTemporaryCompatibleDuplicatePromiseDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getAnalysisData

```TypeScript
getAnalysisData(analysisType: AnalysisType): Promise<string>
```

根据智慧分析类型获取指定分析结果数据。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-getAnalysisData(analysisType: AnalysisType): Promise<string>--><!--Device-PhotoAsset-getAnalysisData(analysisType: AnalysisType): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| analysisType | [AnalysisType](arkts-medialibrary-photoaccesshelper-analysistype-e-sys.md) | 是 | Smart analysis type. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Returns analysis info into a json string |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | System inner fail |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('getAnalysisDataDemo')
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: new dataSharePredicates.DataSharePredicates()
    }
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> =
      await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (photoAsset != undefined) {
      let analysisData: string = await photoAsset.getAnalysisData(
        photoAccessHelper.AnalysisType.ANALYSIS_OCR);
      console.info('get ocr result: ' + JSON.stringify(analysisData));
    }
    fetchResult.close();
  } catch (err) {
    console.error(`getAnalysisDataDemofailed with error: ${err.code}, ${err.message}`);
  }
}
```

## getEditData

```TypeScript
getEditData(): Promise<MediaAssetEditData>
```

获得资产编辑数据。使用Promise异步回调。 如果资源未编辑过，则返回的编辑数据的内容为空字符串。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-getEditData(): Promise<MediaAssetEditData>--><!--Device-PhotoAsset-getEditData(): Promise<MediaAssetEditData>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[MediaAssetEditData](arkts-medialibrary-photoaccesshelper-mediaasseteditdata-c-sys.md)&gt; | Promise对象，返回资产编辑数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | System inner fail. Possible causes: <br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('getEditDataDemo')
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let assetEditData: photoAccessHelper.MediaAssetEditData = await photoAsset.getEditData();
    let data: string = assetEditData.data;
    console.info('edit data is ' + data);
  } catch (err) {
    console.error(`getEditDataDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getExif

```TypeScript
getExif(callback: AsyncCallback<string>): void
```

读取jpg格式图片的Exif标签，并返回json格式的字符串。使用callback异步回调。 此接口中获取的Exif标签信息是由 [image](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md#ohosmultimediaimage)模块提供。Exif标签详细信息请参考 [image.PropertyKey](../../apis-image-kit/arkts-apis/arkts-image-image-propertykey-e.md#propertykey)。 > **注意：** > > 此接口返回的是Exif标签组成的json格式的字符串，完整Exif信息由all_exif与 > [PhotoKeys.USER_COMMENT](arkts-medialibrary-photoaccesshelper-photokeys-e.md#photokeys)组成， > [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md#fetchoptions).fetchColumns需要传入这两个字段。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-getExif(callback: AsyncCallback<string>): void--><!--Device-PhotoAsset-getExif(callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | 返回Exif字段组成的json格式的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('getExifDemo');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    predicates.isNotNull('all_exif')
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: ['all_exif', photoAccessHelper.PhotoKeys.USER_COMMENT],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    console.info('getExifDemo photoAsset displayName: ' + JSON.stringify(photoAsset.displayName));
    let userCommentKey = 'UserComment';
    photoAsset.getExif((err, exifMessage) => {
      if (exifMessage !== undefined) {
        let userComment = JSON.stringify(JSON.parse(exifMessage), [userCommentKey]);
        console.info('getExifDemo userComment: ' + JSON.stringify(userComment));
      } else {
        console.error(`getExif failed, error: ${err.code}, ${err.message}`);
      }
    });
    fetchResult.close();
  } catch (err) {
    console.error(`getExifDemoCallback failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getExif

```TypeScript
getExif(): Promise<string>
```

读取jpg格式图片的Exif标签，并返回json格式的字符串。使用Promise异步回调。 此接口中获取的Exif标签信息是由[image](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md#ohosmultimediaimage) 模块提供。Exif标签详细信息请参考 [image.PropertyKey](../../apis-image-kit/arkts-apis/arkts-image-image-propertykey-e.md#propertykey). > **注意：** > > 此接口返回的是Exif标签组成的json格式的字符串，完整Exif信息由all_exif与 > [PhotoKeys.USER_COMMENT](arkts-medialibrary-photoaccesshelper-photokeys-e.md#photokeys)组成， > [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md#fetchoptions).fetchColumns需要传入这两个字段。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-getExif(): Promise<string>--><!--Device-PhotoAsset-getExif(): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | 返回Exif标签组成的json格式的字符串。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('getExifDemo');
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [ 'all_exif',  photoAccessHelper.PhotoKeys.USER_COMMENT],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let exifMessage = await photoAsset.getExif();
    let userCommentKey = 'UserComment';
    let userComment = JSON.stringify(JSON.parse(exifMessage), [userCommentKey]);
    console.info('getExifDemo userComment: ' + JSON.stringify(userComment));
    fetchResult.close();
  } catch (err) {
    console.error(`getExifDemoCallback failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getKeyFrameThumbnail

```TypeScript
getKeyFrameThumbnail(beginFrameTimeMs: long, type: ThumbnailType): Promise<image.PixelMap>
```

获取视频中关键视频帧位置的指定类型缩略图。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-getKeyFrameThumbnail(beginFrameTimeMs: long, type: ThumbnailType): Promise<image.PixelMap>--><!--Device-PhotoAsset-getKeyFrameThumbnail(beginFrameTimeMs: long, type: ThumbnailType): Promise<image.PixelMap>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| beginFrameTimeMs | long | 是 | 获取视频帧的时间位置，单位ms，0：封面帧。 |
| type | [ThumbnailType](arkts-medialibrary-photoaccesshelper-thumbnailtype-e-sys.md) | 是 | 缩略图类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;image.PixelMap&gt; | Promise对象，返回缩略图的PixelMap。若获取不到，默认返回封面帧 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { common }  from '@kit.AbilityKit';
import { dataSharePredicates } from '@kit.ArkData';
import { image } from '@kit.ImageKit';

async function example(context: Context) {
  try{
    console.info('getKeyFrameThumbnail demo');
    let phAccessHelper:photoAccessHelper.PhotoAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    predicates.equalTo(photoAccessHelper.PhotoKeys.PHOTO_TYPE, photoAccessHelper.PhotoType.VIDEO);
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getLastObject();
    let pixelMap: image.PixelMap = await asset.getKeyFrameThumbnail(0, photoAccessHelper.ThumbnailType.LCD);
    console.info('getKeyFrameThumbnail success');
  } catch (error) {
    console.error('getKeyFrameThumbnail failed, error: ' + JSON.stringify(error));
  }
}
```

## getReadOnlyFdWithCached

```TypeScript
getReadOnlyFdWithCached(): Promise<int>
```

打开文件，当从云端流读视频文件时会在图库沙箱进行缓存。

**起始版本：** 26.0.0

**ArkTS模式：** 起始版本为26.0.0。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-getReadOnlyFdWithCached(): Promise<int>--><!--Device-PhotoAsset-getReadOnlyFdWithCached(): Promise<int>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | 返回打开文件的Fd。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800302](../errorcode-medialibrary.md#23800302-打开文件失败) | Failed to open the file. Possible causes: 1. Unable to access cloud images due to network connectivity issues; 2. File system malfunction. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scene parameters validate failed, possible causes: The image and video files corresponding to the photoasset do not exist. |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getReadOnlyFdDemo');
  try {
    // 需要保证设备中存在可读取图片视频文件。
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let assetResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await assetResult.getFirstObject();
    if (photoAsset === undefined) {
      console.error('photoAsset is undefined');
      return;
    }
    let fd: number = await photoAsset.getReadOnlyFdWithCached();
    if (fd !== undefined) {
      console.info('File fd: ' + fd);
      photoAsset.close(fd);
    } else {
      console.error('Failed To Get ReadOnlyFd With Cached fd: ' + fd);
    }
  } catch (err) {
    console.error(`Failed To Get ReadOnly Fd With Cached err: ${err.code}, ${err.message}`);
  }
}
```

## getThumbnailData

```TypeScript
getThumbnailData(type: ThumbnailType): Promise<ArrayBuffer>
```

获取文件缩略图的ArrayBuffer，传入缩略图的类型。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-getThumbnailData(type: ThumbnailType): Promise<ArrayBuffer>--><!--Device-PhotoAsset-getThumbnailData(type: ThumbnailType): Promise<ArrayBuffer>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [ThumbnailType](arkts-medialibrary-photoaccesshelper-thumbnailtype-e-sys.md) | 是 | 缩略图类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise对象，返回缩略图的ArrayBuffer。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## 示例

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getThumbnailDataDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let asset = await fetchResult.getFirstObject();
  console.info('asset displayName = ', asset.displayName);
  asset.getThumbnailData(photoAccessHelper.ThumbnailType.LCD).then((buffer: ArrayBuffer) => {
    console.info('getThumbnailData successful, buffer byteLength = ${buffer.byteLength}');
  }).catch((err: BusinessError) => {
    console.error(`getThumbnailData fail with error: ${err.code}, ${err.message}`);
  });
}
```

## isEdited

```TypeScript
isEdited(callback: AsyncCallback<boolean>): void
```

查询图片或视频资源是否被编辑过。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-isEdited(callback: AsyncCallback<boolean>): void--><!--Device-PhotoAsset-isEdited(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | Callback对象，返回图片或视频资源是否被编辑过。 true为被编辑过，false为没有被编辑过，默认是false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('isEditedCallbackDemo')
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    photoAsset.isEdited((err, isEdited) => {
      if (err === undefined) {
        if (isEdited === true) {
          console.info('Photo is edited');
        } else {
          console.info('Photo is not edited');
        }
      } else {
        console.error(`isEdited failed with error: ${err.code}, ${err.message}`);
      }
    });
  } catch (err) {
    console.error(`isEditedDemoCallback failed with error: ${err.code}, ${err.message}`);
  }
}
```

## isEdited

```TypeScript
isEdited(): Promise<boolean>
```

查询图片或视频资源是否被编辑过。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-isEdited(): Promise<boolean>--><!--Device-PhotoAsset-isEdited(): Promise<boolean>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回图片或视频资源是否被编辑过。 true为被编辑过，false为没有被编辑过，默认是false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('isEditedPromiseDemo')
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let isEdited = await photoAsset.isEdited();
    if (isEdited === true) {
      console.info('Photo is edited');
    } else {
      console.info('Photo is not edited');
    }
  } catch (err) {
    console.error(`isEditedDemoCallback failed with error: ${err.code}, ${err.message}`);
  }
}
```

## open

```TypeScript
open(mode: string, callback: AsyncCallback<number>): void
```

打开当前文件。使用callback异步回调。 该接口返回的文件描述符在使用完毕后需要调用close进行释放。 > **说明：** > > 从API version 10开始支持，从API version 11开始废弃。出于安全考量，不再提供获取正式媒体文件句柄的接口。

**起始版本：** 10

**ArkTS模式：** 起始版本为10。

**废弃版本：** 11

**替代接口：** [open](../../apis-na/arkts-apis/arkts-na-fileio-open-f.md#open)

**需要权限：** ohos.permission.READ_IMAGEVIDEO or ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAsset-open(mode: string, callback: AsyncCallback<number>): void--><!--Device-PhotoAsset-open(mode: string, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | string | 是 | 打开文件方式，分别为：'r'（只读）, 'w'（只写）, 'rw'（读写）。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;number&gt; | 是 | callback返回文件描述符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail. Possible causes: <br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('Open demo');
  let testFileName: string = 'testFile' + Date.now() + '.jpg';
  let photoAsset: photoAccessHelper.PhotoAsset = await phAccessHelper.createAsset(testFileName);
  photoAsset.open('rw', (err, fd) => {
    if (fd !== undefined) {
      console.info('File fd' + fd);
      photoAsset.close(fd);
    } else {
      console.error(`Open file err: ${err.code}, ${err.message}`);
    }
  });
}
```

## open

```TypeScript
open(mode: string): Promise<number>
```

打开当前文件。使用Promise异步回调。 该接口返回的文件描述符在使用完毕后需要调用close进行释放。 > **说明：** > > 从API version 10开始支持，从API version 11开始废弃。出于安全考量，不再提供获取正式媒体文件句柄的接口。

**起始版本：** 10

**ArkTS模式：** 起始版本为10。

**废弃版本：** 11

**替代接口：** [open](../../apis-na/arkts-apis/arkts-na-fileio-open-f.md#open)

**需要权限：** ohos.permission.READ_IMAGEVIDEO or ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAsset-open(mode: string): Promise<number>--><!--Device-PhotoAsset-open(mode: string): Promise<number>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | string | 是 | 打开文件方式，分别为：'r'（只读）, 'w'（只写）, 'rw'（读写）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回文件描述符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail. Possible causes: <br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('Open demo');
  try {
    let testFileName: string = 'testFile' + Date.now() + '.jpg';
    let photoAsset: photoAccessHelper.PhotoAsset = await phAccessHelper.createAsset(testFileName);
    let fd: number = await photoAsset.open('rw');
    if (fd !== undefined) {
      console.info('File fd' + fd);
      photoAsset.close(fd);
    } else {
      console.error('Open file fail');
    }
  } catch (err) {
    console.error(`Open demo err: ${err.code}, ${err.message}`);
  }
}
```

## requestEditData

```TypeScript
requestEditData(callback: AsyncCallback<string>): void
```

获得图片或视频资源的编辑数据。使用callback异步回调。 如果资源未编辑过，则返回一个空字符串。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-requestEditData(callback: AsyncCallback<string>): void--><!--Device-PhotoAsset-requestEditData(callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;string&gt; | 是 | Callback对象，返回图片或视频资源的编辑数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail. Possible causes: <br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('requestEditDataCallbackDemo')
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    photoAsset.requestEditData((err, editdata) => {
      if (err === undefined) {
        console.info('Editdata is ' + editdata);
      } else {
        console.error(`requestEditData failed with error: ${err.code}, ${err.message}`);
      }
    });
  } catch (err) {
    console.error(`requestEditDataCallbackDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## requestEditData

```TypeScript
requestEditData(): Promise<string>
```

获得图片或视频资源的编辑数据。使用Promise异步回调。 如果资源未编辑过，则返回一个空字符串。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-requestEditData(): Promise<string>--><!--Device-PhotoAsset-requestEditData(): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回图片或视频资源的编辑数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail. Possible causes: <br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('requestEditDataPromiseDemo')
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let editdata: string = await photoAsset.requestEditData();
    console.info('Editdata is ' + editdata);
  } catch (err) {
    console.error(`requestEditDataPromiseDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## requestPhoto

```TypeScript
requestPhoto(callback: AsyncCallback<image.PixelMap>): string
```

通过callback的形式，获取资源的快速缩略图和普通缩略图。 快速缩略图尺寸为128*128，普通缩略图尺寸为256*256。应用调用接口后，callback将返回两次缩略图对象，第一次为快速缩略图， 第二次为普通缩略图。

**起始版本：** 11

**ArkTS模式：** 起始版本为11。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-requestPhoto(callback: AsyncCallback<image.PixelMap>): string--><!--Device-PhotoAsset-requestPhoto(callback: AsyncCallback<image.PixelMap>): string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;image.PixelMap&gt; | 是 | Callback对象，返回获取的缩略图，调用2次。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 本次获取任务的id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| 14000011 | System inner fail |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { image } from '@kit.ImageKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('requestPhotoDemo')
    let options: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: new dataSharePredicates.DataSharePredicates()
    }
    let fetchResult = await phAccessHelper.getAssets(options);
    let photoAsset = await fetchResult.getFirstObject();
    let taskId: string = photoAsset.requestPhoto(async (err, pixel: image.PixelMap) => {
      if (err === undefined) {
        console.info("requestSource in, size: " + JSON.stringify((await pixel.getImageInfo()).size))
      } else {
        console.error(`requestSource failed with error: ${err.code}, ${err.message}`);
      }
    })
    console.info('requestSource taskId: ' + taskId)
  } catch (err) {
    console.error(`requestPhotoDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## requestPhoto

```TypeScript
requestPhoto(callback: AsyncCallback<image.PixelMap>): string | null
```

通过callback的形式，获取资源的快速缩略图和普通缩略图。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-requestPhoto(callback: AsyncCallback<image.PixelMap>): string | null--><!--Device-PhotoAsset-requestPhoto(callback: AsyncCallback<image.PixelMap>): string | null-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;image.PixelMap&gt; | 是 | Callback invoked twice to return the quick and quality thumbnails obtained. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns request photo task id. if the operation fails, returns null. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |

## requestPhoto

```TypeScript
requestPhoto(options: RequestPhotoOptions, callback: AsyncCallback<image.PixelMap>): string
```

通过callback的形式，根据传入的选项，获取资源的缩略图。

**起始版本：** 11

**ArkTS模式：** 起始版本为11。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-requestPhoto(options: RequestPhotoOptions, callback: AsyncCallback<image.PixelMap>): string--><!--Device-PhotoAsset-requestPhoto(options: RequestPhotoOptions, callback: AsyncCallback<image.PixelMap>): string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RequestPhotoOptions](arkts-medialibrary-photoaccesshelper-requestphotooptions-i-sys.md) | 是 | 获取资源缩略图的选项。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;image.PixelMap&gt; | 是 | Callback对象，返回获取的缩略图，根据选项的设置可能调用超过1次。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 本次获取任务的id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| 14000011 | System inner fail |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { image } from '@kit.ImageKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('requestPhotoDemo')
    let options: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: new dataSharePredicates.DataSharePredicates()
    }
    let fetchResult = await phAccessHelper.getAssets(options);
    let photoAsset = await fetchResult.getFirstObject();
    let taskId: string = photoAsset.requestPhoto({
      "size": {
        "width": 256,
        "height": 256
      },
      "requestPhotoType": photoAccessHelper.RequestPhotoType.REQUEST_ALL_THUMBNAILS
    }, async (err, pixel: image.PixelMap) => {
      if (err === undefined) {
        console.info("requestSource in, size: " + JSON.stringify((await pixel.getImageInfo()).size))
      } else {
        console.error(`requestSource failed with error: ${err.code}, ${err.message}`);
      }
    })
    console.info('requestSource taskId: ' + taskId)
  } catch (err) {
    console.error(`requestPhotoDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## requestPhoto

```TypeScript
requestPhoto(options: RequestPhotoOptions, callback: AsyncCallback<image.PixelMap>): string | null
```

通过callback的形式，根据传入的选项，获取资源的缩略图。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-requestPhoto(options: RequestPhotoOptions, callback: AsyncCallback<image.PixelMap>): string | null--><!--Device-PhotoAsset-requestPhoto(options: RequestPhotoOptions, callback: AsyncCallback<image.PixelMap>): string | null-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RequestPhotoOptions](arkts-medialibrary-photoaccesshelper-requestphotooptions-i-sys.md) | 是 | Options for obtaining the asset thumbnail. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;image.PixelMap&gt; | 是 | Callback used to return the thumbnails obtained. The callback may be invoked more than once, depending on options. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns request photo task id. if the operation fails, returns null. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |

## requestSource

```TypeScript
requestSource(callback: AsyncCallback<int>): void
```

打开源文件并返回fd（文件描述符）。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-requestSource(callback: AsyncCallback<int>): void--><!--Device-PhotoAsset-requestSource(callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;int&gt; | 是 | Callback对象，返回源文件fd。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail. Possible causes: <br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('requestSourceCallbackDemo')
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    photoAsset.requestSource((err, fd) => {
      if (err === undefined) {
        console.info('Source fd is ' + fd);
      } else {
        console.error(`requestSource failed with error: ${err.code}, ${err.message}`);
      }
    });
  } catch (err) {
    console.error(`requestSourceCallbackDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## requestSource

```TypeScript
requestSource(): Promise<int>
```

打开源文件并返回fd（文件描述符）。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAsset-requestSource(): Promise<int>--><!--Device-PhotoAsset-requestSource(): Promise<int>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，返回源文件fd。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail. Possible causes: <br>1. The database is corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('requestSourcePromiseDemo')
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let fd = await photoAsset.requestSource();
    console.info('Source fd is ' + fd);
  } catch (err) {
    console.error(`requestSourcePromiseDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## revertToOriginal

```TypeScript
revertToOriginal(callback: AsyncCallback<void>): void
```

回退到编辑前的状态。使用callback异步回调。 > **注意：** > > 调用该接口后，编辑数据和编辑后的图片或视频资源都将被删除，无法恢复，请谨慎调用。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAsset-revertToOriginal(callback: AsyncCallback<void>): void--><!--Device-PhotoAsset-revertToOriginal(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | Callback对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

## revertToOriginal

```TypeScript
revertToOriginal(): Promise<void>
```

回退到编辑前的状态。使用Promise异步回调。 > **注意：** > > 调用该接口后，编辑数据和编辑后的图片或视频资源都将被删除，无法恢复，请谨慎调用。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAsset-revertToOriginal(): Promise<void>--><!--Device-PhotoAsset-revertToOriginal(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('revertToOriginalPromiseDemo')
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (photoAsset === undefined) {
      console.error('getHiddenAlbumsViewCallback albums is undefined');
      return;
    }
    photoAsset.revertToOriginal();
    console.info('revertToOriginal is successful');
  } catch (err) {
    console.error(`revertToOriginalPromiseDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## setFavorite

```TypeScript
setFavorite(favoriteState: boolean, callback: AsyncCallback<void>): void
```

将文件设置为收藏文件。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 起始版本为10。

**废弃版本：** 11

**替代接口：** [setFavorite](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md#setfavorite)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAsset-setFavorite(favoriteState: boolean, callback: AsyncCallback<void>): void--><!--Device-PhotoAsset-setFavorite(favoriteState: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| favoriteState | boolean | 是 | 是否设置为收藏文件， true：设置为收藏文件，false：取消收藏。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | callback返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setFavoriteDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let asset = await fetchResult.getFirstObject();
  asset.setFavorite(true, (err) => {
    if (err === undefined) {
      console.info('favorite successfully');
    } else {
      console.error(`favorite failed with error: ${err.code}, ${err.message}`);
    }
  });
}
```

## setFavorite

```TypeScript
setFavorite(favoriteState: boolean): Promise<void>
```

将文件设置为收藏文件。使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** 起始版本为10。

**废弃版本：** 11

**替代接口：** [setFavorite](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md#setfavorite)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAsset-setFavorite(favoriteState: boolean): Promise<void>--><!--Device-PhotoAsset-setFavorite(favoriteState: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| favoriteState | boolean | 是 | 是否设置为收藏文件， true：设置为收藏文件，false：取消收藏。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setFavoriteDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let asset = await fetchResult.getFirstObject();
  if (asset === undefined) {
    console.error('asset is undefined');
    return;
  }
  asset.setFavorite(true).then(() => {
    console.info('setFavorite successfully');
  }).catch((err: BusinessError) => {
    console.error(`setFavorite failed with error: ${err.code}, ${err.message}`);
  });
}
```

## setHidden

```TypeScript
setHidden(hiddenState: boolean, callback: AsyncCallback<void>): void
```

将文件设置为隐私文件。使用callback异步回调。 隐私文件存在隐私相册中，用户通过隐私相册去获取隐私文件后可以通过设置hiddenState为false来从隐私相册中移除。

**起始版本：** 10

**ArkTS模式：** 起始版本为10。

**废弃版本：** 11

**替代接口：** [setHidden](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md#sethidden)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAsset-setHidden(hiddenState: boolean, callback: AsyncCallback<void>): void--><!--Device-PhotoAsset-setHidden(hiddenState: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hiddenState | boolean | 是 | Whether to set a file to hidden state. **true** to hide, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | Callback that returns no value. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setHiddenDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
  let asset = await fetchResult.getFirstObject();
  asset.setHidden(true, (err) => {
    if (err === undefined) {
      console.info('setHidden successfully');
    } else {
      console.error(`setHidden failed with error: ${err.code}, ${err.message}`);
    }
  });
}
```

## setHidden

```TypeScript
setHidden(hiddenState: boolean): Promise<void>
```

将文件设置为隐私文件。使用Promise异步回调。 隐私文件存在隐私相册中，用户通过隐私相册去获取隐私文件后可以通过设置hiddenState为false来从隐私相册中移除。

**起始版本：** 10

**ArkTS模式：** 起始版本为10。

**废弃版本：** 11

**替代接口：** [setHidden](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md#sethidden)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAsset-setHidden(hiddenState: boolean): Promise<void>--><!--Device-PhotoAsset-setHidden(hiddenState: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| hiddenState | boolean | 是 | 是否设置为隐藏文件，true:将文件资产放入隐藏相册;false:从隐藏相册中恢复。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | callback返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  // 示例代码为将文件从隐藏相册中恢复，需要先在隐藏相册预置资源。
  console.info('setHiddenDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let albumList: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.SYSTEM, photoAccessHelper.AlbumSubtype.HIDDEN);
  let album = await albumList.getFirstObject();
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOption);
  let asset = await fetchResult.getFirstObject();
  asset.setHidden(false).then(() => {
    console.info('setHidden successfully');
  }).catch((err: BusinessError) => {
    console.error(`setHidden failed with error: ${err.code}, ${err.message}`);
  });
}
```

## setPending

```TypeScript
setPending(pendingState: boolean, callback: AsyncCallback<void>): void
```

为图片或视频资源设置pending状态。使用callback异步回调。 将文件通过`setPending(true)`设置为pending状态后，只能通过`setPending(false)`解除pending状态。 可以通过`photoAsset.get(photoAccessHelper.PhotoKeys.PENDING)`的方式获取是否为pending状态，pending状态下返回true， 否则返回false。 > **注意：** > > setPending只能在文件的创建期使用，在文件的首次创建流程的close之后，无法通过setPending(true)将文件设置为pending状态。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAsset-setPending(pendingState: boolean, callback: AsyncCallback<void>): void--><!--Device-PhotoAsset-setPending(pendingState: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pendingState | boolean | 是 | 设置的pending状态，true为设置pending状态，false为解除pending状态。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | Callback对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('setPendingCallbackDemo');
    let testFileName: string = 'testFile' + Date.now() + '.jpg';
    let photoAsset = await phAccessHelper.createAsset(testFileName);
    photoAsset.setPending(true, async (err) => {
      if (err !== undefined) {
        console.error(`setPending(true) failed with error: ${err.code}, ${err.message}`);
        return;
      }
      // add asset resource.
      photoAsset.setPending(false, async (err) => {
        if (err !== undefined) {
          console.error(`setPending(false) failed with error: ${err.code}, ${err.message}`);
          return;
        }
      });
    });
  } catch (err) {
    console.error(`setPendingCallbackDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## setPending

```TypeScript
setPending(pendingState: boolean): Promise<void>
```

为图片或视频资源设置pending状态。使用Promise异步回调。 将文件通过`setPending(true)`设置为pending状态后，只能通过`setPending(false)`解除pending状态。 可以通过`photoAsset.get(photoAccessHelper.PhotoKeys.PENDING)`的方式获取是否为pending状态，pending状态下返回true， 否则返回false。 > **注意：** > > setPending只能在文件的创建期使用，在文件的首次创建流程的close之后，无法通过setPending(true)将文件设置为pending状态。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAsset-setPending(pendingState: boolean): Promise<void>--><!--Device-PhotoAsset-setPending(pendingState: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pendingState | boolean | 是 | 设置的pending状态，true为设置pending状态，false为解除pending状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('setPendingPromiseDemo');
    let testFileName: string = 'testFile' + Date.now() + '.jpg';
    let photoAsset = await phAccessHelper.createAsset(testFileName);
    await photoAsset.setPending(true);
    // add asset resource.
    photoAsset.setPending(false);
  } catch (err) {
    console.error(`setPendingPromiseDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## setUserComment

```TypeScript
setUserComment(userComment: string, callback: AsyncCallback<void>): void
```

修改图片或者视频的备注信息。使用callback异步回调。

**起始版本：** 10

**ArkTS模式：** 起始版本为10。

**废弃版本：** 11

**替代接口：** [setUserComment](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md#setusercomment)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAsset-setUserComment(userComment: string, callback: AsyncCallback<void>): void--><!--Device-PhotoAsset-setUserComment(userComment: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userComment | string | 是 | 待修改的图片或视频的备注信息，备注信息最长为420字符。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | callback返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('setUserCommentDemo')
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let userComment = 'test_set_user_comment';
    photoAsset.setUserComment(userComment, (err) => {
      if (err === undefined) {
        console.info('setUserComment successfully');
      } else {
        console.error(`setUserComment failed with error: ${err.code}, ${err.message}`);
      }
    });
  } catch (err) {
    console.error(`setUserCommentDemoCallback failed with error: ${err.code}, ${err.message}`);
  }
}
```

## setUserComment

```TypeScript
setUserComment(userComment: string): Promise<void>
```

修改图片或者视频的备注信息。使用Promise异步回调。

**起始版本：** 10

**ArkTS模式：** 起始版本为10。

**废弃版本：** 11

**替代接口：** [setUserComment](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c-sys.md#setusercomment)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAsset-setUserComment(userComment: string): Promise<void>--><!--Device-PhotoAsset-setUserComment(userComment: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userComment | string | 是 | 待修改的图片或视频的备注信息，备注信息最长为420字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

## 示例

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('setUserCommentDemo')
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    let userComment = 'test_set_user_comment';
    await photoAsset.setUserComment(userComment);
  } catch (err) {
    console.error(`setUserCommentDemoPromise failed with error: ${err.code}, ${err.message}`);
  }
}
```

