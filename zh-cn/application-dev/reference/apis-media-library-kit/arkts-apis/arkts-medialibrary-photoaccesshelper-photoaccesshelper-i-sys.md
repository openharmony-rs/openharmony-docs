# PhotoAccessHelper

提供访问照片和相册的功能。

**起始版本：** 23

<!--Device-photoAccessHelper-interface PhotoAccessHelper--><!--Device-photoAccessHelper-interface PhotoAccessHelper-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## acquireDebugDatabase

```TypeScript
acquireDebugDatabase(betaIssueId: string, betaScenario: string): Promise<Map<string, string>>
```

Start medialibrary database backup and wait for returning with backup infomation which only works on beta device.

**起始版本：** 23

<!--Device-PhotoAccessHelper-acquireDebugDatabase(betaIssueId: string, betaScenario: string): Promise<Map<string, string>>--><!--Device-PhotoAccessHelper-acquireDebugDatabase(betaIssueId: string, betaScenario: string): Promise<Map<string, string>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| betaIssueId | string | 是 | The beta issue id. |
| betaScenario | string | 是 | The beta scenario. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Map&lt;string, string&gt;&gt; | The returning with backup information, which includes FILE_FD, FILE_NAME and FILE_SIZE. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800201](../errorcode-medialibrary.md#23800201-不支持的操作类型) | Unsupported operation type, this api only works on beta device. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. The betaIssueId parameter is invalid, such as null, undefined or empty string. <br>2. The betaScenario parameter is invalid, such as null, undefined or empty string. <br>3. The same betaIssueId task is processing. |

## batchGetPhotoAssetParams

```TypeScript
batchGetPhotoAssetParams(assets: PhotoAsset[], members: string[]): PhotoAssetParams
```

批量获取传入的PhotoAsset对象数组中指定属性的值。

**起始版本：** 23

<!--Device-PhotoAccessHelper-batchGetPhotoAssetParams(assets: PhotoAsset[], members: string[]): PhotoAssetParams--><!--Device-PhotoAccessHelper-batchGetPhotoAssetParams(assets: PhotoAsset[], members: string[]): PhotoAssetParams-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | PhotoAsset[] | 是 | 需要批量获取属性的文件数组。 |
| members | string[] | 是 | 需要批量获取的属性数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PhotoAssetParams](arkts-medialibrary-photoaccesshelper-photoassetparams-t.md) | 文件属性名称及其值的Record类型数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800104](../errorcode-medialibrary.md#23800104-传入参数校验不通过) | The provided member must be a property name of PhotoKey. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. <br>Possible causes: The attribute to be queried does not exist in assets. |

**示例**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { photoAccessHelper} from '@kit.MediaLibraryKit';

async function example(context: Context) {
  console.info('batchGetPhotoAssetParams');
  type PhotoAsset = photoAccessHelper.PhotoAsset;
  let phAccessHelper: photoAccessHelper.PhotoAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
  const FETCH_COLUMNS: string[] = [
    photoAccessHelper.PhotoKeys.SIZE,
    photoAccessHelper.PhotoKeys.DATE_ADDED,
    photoAccessHelper.PhotoKeys.DATE_MODIFIED,
    photoAccessHelper.PhotoKeys.PHOTO_TYPE,
    photoAccessHelper.PhotoKeys.TITLE,
    photoAccessHelper.PhotoKeys.DATE_MODIFIED_MS,
    photoAccessHelper.PhotoKeys.DURATION,
    photoAccessHelper.PhotoKeys.WIDTH,
    photoAccessHelper.PhotoKeys.HEIGHT,
    photoAccessHelper.PhotoKeys.DATE_TRASHED_MS,
    photoAccessHelper.PhotoKeys.POSITION,
    photoAccessHelper.PhotoKeys.DATE_TAKEN,
    'owner_album_id',
    'thumbnail_ready',
    'data',
  ];
  const keyToGet: string[] = [
    photoAccessHelper.PhotoKeys.URI,
    photoAccessHelper.PhotoKeys.DISPLAY_NAME,
    photoAccessHelper.PhotoKeys.DATE_ADDED,
    photoAccessHelper.PhotoKeys.SIZE,
    photoAccessHelper.PhotoKeys.DURATION,
    photoAccessHelper.PhotoKeys.WIDTH,
    photoAccessHelper.PhotoKeys.HEIGHT,
    'data',
    photoAccessHelper.PhotoKeys.THUMBNAIL_READY,];
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: FETCH_COLUMNS,
    predicates: predicates
  };
  let albumPredicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let albumFetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: albumPredicates
  }
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.
  getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, albumFetchOptions);
  let album: photoAccessHelper.Album = await fetchResult.getFirstObject();
  let photoAssetsFetchResult: photoAccessHelper.FetchResult<PhotoAsset> = await album.getAssets(fetchOptions);
  let photoAssets: PhotoAsset[] = await photoAssetsFetchResult.getAllObjects();
  const batchParamOfPhotoAssets: photoAccessHelper.PhotoAssetParams =
   phAccessHelper.batchGetPhotoAssetParams(photoAssets, keyToGet);
  console.info(`batchGetPhotoAssetParams success, the length is ${batchParamOfPhotoAssets.length}`);
}
```

## canPerformDeepOptimizeSpace

```TypeScript
canPerformDeepOptimizeSpace(): Promise<boolean>
```

查询当前系统是否可以执行深度优化存储空间功能。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-canPerformDeepOptimizeSpace(): Promise<boolean>--><!--Device-PhotoAccessHelper-canPerformDeepOptimizeSpace(): Promise<boolean>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。**true**表示可以调用 [startDeepOptimizeSpace()]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let canPerform: boolean = await phAccessHelper.canPerformDeepOptimizeSpace();
    console.info(`canPerformDeepOptimizeSpace result: ${canPerform}`);
  } catch (err) {
    console.error(`canPerformDeepOptimizeSpace failed with error: ${err.code}, ${err.message}`);
  }
}
```

## cancelAnalysisTool

```TypeScript
cancelAnalysisTool(config: ToolCancelConfig): Promise<void>
```

取消执行智能分析工具。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.CONTROL_IMAGEVIDEO_ANALYSIS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-cancelAnalysisTool(config: ToolCancelConfig): Promise<void>--><!--Device-PhotoAccessHelper-cancelAnalysisTool(config: ToolCancelConfig): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ToolCancelConfig](arkts-medialibrary-photoaccesshelper-toolcancelconfig-i-sys.md) | 是 | 取消工具配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不会返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. Possible causes: <br>1. IPC timeout; <br>2. System exception. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. Invalid task id. <br>2. The length of **param** in **ToolCancelConfig** exceeds 16KB. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('cancelAnalysisToolDemo');
  let config: photoAccessHelper.ToolCancelConfig = {
    taskId: '123456',
    param: '{"key":"value"}'
  };

  try {
    await phAccessHelper.cancelAnalysisTool(config);
    console.info('do cancelAnalysisTool successfully');
  } catch (err) {
    console.error('failed to do cancelAnalysisTool');
  }
}
```

## cancelPhotoUriPermission

```TypeScript
cancelPhotoUriPermission(tokenId: long, uri: string, photoPermissionType: PhotoPermissionType): Promise<int>
```

取消应用对uri的访问权限。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-cancelPhotoUriPermission(tokenId: long, uri: string, photoPermissionType: PhotoPermissionType): Promise<int>--><!--Device-PhotoAccessHelper-cancelPhotoUriPermission(tokenId: long, uri: string, photoPermissionType: PhotoPermissionType): Promise<int>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenId | long | 是 | 应用标识，将取消tokenId标识应用对媒体资源的访问权限。 |
| uri | string | 是 | 媒体资源的uri，取消应用对uri表示的资源的访问权限。 |
| photoPermissionType | [PhotoPermissionType](arkts-medialibrary-photoaccesshelper-photopermissiontype-e-sys.md) | 是 | 权限类型，取消应用对媒体资源的访问权限为photoPermissionType。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，0:取消成功。-1:取消失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument. Possible causes: <br>1. Incorrect uri format; <br>2. The value of photoPermissionType or hideSensitiveType is out of range. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('cancelPhotoUriPermissionDemo');

  try {
    let tokenId = 502334412;
    let result = await phAccessHelper.cancelPhotoUriPermission(tokenId,
        'file://media/Photo/11/IMG_datetime_0001/displayName.jpg',
        photoAccessHelper.PhotoPermissionType.TEMPORARY_READ_IMAGEVIDEO);

    console.info('cancelPhotoUriPermission success, result=' + result);
  } catch (err) {
    console.error('cancelPhotoUriPermission failed, error=' + err);
  }
}
```

## cloneAssetsByPath

```TypeScript
cloneAssetsByPath(assets: string[], target: Album, option?: BatchOperationOptions): Promise<string[]>
```

将文件管理中的资产复制到目标相册中。使用Promise异步回调。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-cloneAssetsByPath(assets: string[], target: Album, option?: BatchOperationOptions): Promise<string[]>--><!--Device-PhotoAccessHelper-cloneAssetsByPath(assets: string[], target: Album, option?: BatchOperationOptions): Promise<string[]>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | string[] | 是 | 文管公共目录的图片 |
| target | Album | 是 | 相册 |
| option | [BatchOperationOptions](arkts-medialibrary-photoaccesshelper-batchoperationoptions-i-sys.md) | 否 | 批量操作选项 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string[]&gt; | Returns successed assets URI. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. Asset to be cloned has been delete or hidden; <br>2. Asset to be cloned is cloud pictures, which can not be cloned; <br>3. The Target Album does not exist. <br>4. Insufficient system space. <br>5. Automatic renaming is not supported. <br>6. The clone task is interrupted. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let assets: Array<string> = ['/Docs/Download/test.jpg'];
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let target: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let clonedUris: Array<string> = await phAccessHelper.cloneAssetsByPath(assets, target);
    console.info(`cloneAssetsByPath success, count: ${clonedUris.length}`);
  } catch (err) {
    console.error(`cloneAssetsByPath failed with error: ${err.code}, ${err.message}`);
  }
}
```

## cloneToAlbum

```TypeScript
cloneToAlbum(assets: PhotoAsset[], target: Album, option?: BatchOperationOptions): Promise<PhotoAsset[]>
```

复制资产到目标相册。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-cloneToAlbum(assets: PhotoAsset[], target: Album, option?: BatchOperationOptions): Promise<PhotoAsset[]>--><!--Device-PhotoAccessHelper-cloneToAlbum(assets: PhotoAsset[], target: Album, option?: BatchOperationOptions): Promise<PhotoAsset[]>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | PhotoAsset[] | 是 | 资产 |
| target | Album | 是 | 相册 |
| option | [BatchOperationOptions](arkts-medialibrary-photoaccesshelper-batchoperationoptions-i-sys.md) | 否 | 批量操作选项 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PhotoAsset[]&gt; | Returns list of successful assets. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. Asset to be cloned has been deleted or hidden; <br>2. Asset to be cloned is cloud pictures, which can not be cloned; <br>3. The Target Album does not exist. <br>4. Insufficient system space. <br>5. Automatic renaming is not supported. <br>6. The clone task is interrupted. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let assetFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let assets: Array<photoAccessHelper.PhotoAsset> = await assetFetchResult.getAllObjects();
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let target: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let options: photoAccessHelper.BatchOperationOptions = {
      mode: 0
    };
    let clonedAssets: Array<photoAccessHelper.PhotoAsset> = await phAccessHelper.cloneToAlbum(assets, target, options);
    console.info(`cloneToAlbum success, count: ${clonedAssets.length}`);
  } catch (err) {
    console.error(`cloneToAlbum failed with error: ${err.code}, ${err.message}`);
  }
}
```

## cloneToDir

```TypeScript
cloneToDir(assets: string[], target: string, option?: BatchOperationOptions): Promise<string[]>
```

复制资产到文件管理目录中。使用Promise异步回调。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-cloneToDir(assets: string[], target: string, option?: BatchOperationOptions): Promise<string[]>--><!--Device-PhotoAccessHelper-cloneToDir(assets: string[], target: string, option?: BatchOperationOptions): Promise<string[]>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | string[] | 是 | 待复制的图库资产 |
| target | string | 是 | 文管公共目录 |
| option | [BatchOperationOptions](arkts-medialibrary-photoaccesshelper-batchoperationoptions-i-sys.md) | 否 | 批量操作选项 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string[]&gt; | Returns successed assets path. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. Asset to be cloned has been deleted or hidden; <br>2. Asset to be cloned is cloud pictures, which can not be cloned; <br>3. The Target Album does not exist. <br>4. Insufficient system space. <br>5. Automatic renaming is not supported. <br>6. The clone task is interrupted. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let assetFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let assets: Array<photoAccessHelper.PhotoAsset> = await assetFetchResult.getAllObjects();
    let assetUris: Array<string> = assets.map((item) => item.uri);
    let target: string = '/Docs/Download';
    let clonedPaths: Array<string> = await phAccessHelper.cloneToDir(assetUris, target);
    console.info(`cloneToDir success, count: ${clonedPaths.length}`);
  } catch (err) {
    console.error(`cloneToDir failed with error: ${err.code}, ${err.message}`);
  }
}
```

## convertAssetToCompatibleAsset

```TypeScript
convertAssetToCompatibleAsset(assets: Array<PhotoAsset>): Promise<Array<PhotoAsset>>
```

转换传入的PhotoAsset属性到媒体库兼容文件格式属性。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-convertAssetToCompatibleAsset(assets: Array<PhotoAsset>): Promise<Array<PhotoAsset>>--><!--Device-PhotoAccessHelper-convertAssetToCompatibleAsset(assets: Array<PhotoAsset>): Promise<Array<PhotoAsset>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | Array&lt;PhotoAsset&gt; | 是 | 需要转换。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;PhotoAsset&gt;&gt; | Promise用于返回已转换的资产。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. Invalid Array&lt;PhotoAsset&gt;. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [photoAccessHelper.PhotoKeys.URI, photoAccessHelper.PhotoKeys.WIDTH, photoAccessHelper.PhotoKeys.HEIGHT],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let assets: Array<photoAccessHelper.PhotoAsset> = await fetchResult.getAllObjects();
    let compatibleAssets: Array<photoAccessHelper.PhotoAsset> = await phAccessHelper.convertAssetToCompatibleAsset(assets);
    console.info(`convertAssetToCompatibleAsset successfully, compatibleAssets count: ${compatibleAssets.length}`);
  } catch (err) {
    console.error(`failed to convertAssetToCompatibleAsset with error: ${err.code}, ${err.message}`);
  }
}
```

## convertToAsset

```TypeScript
convertToAsset(path: string): Promise<PhotoAsset>
```

将文件管理公共目录中的资产转换为资产对象。使用Promise异步回调。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-convertToAsset(path: string): Promise<PhotoAsset>--><!--Device-PhotoAccessHelper-convertToAsset(path: string): Promise<PhotoAsset>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文管公共目录的图片。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PhotoAsset&gt; | Returns successed asset. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. Converted an image after filtering into an asset object; <br>2. File to be converted is not exist; <br>3. Only images in the public directory of filemanager can be converted. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let path: string = '/Docs/Download/test.jpg';
    let photoAsset: photoAccessHelper.PhotoAsset = await phAccessHelper.convertToAsset(path);
    console.info(`convertToAsset success, asset uri: ${photoAsset.uri}`);
  } catch (err) {
    console.error(`convertToAsset failed with error: ${err.code}, ${err.message}`);
  }
}
```

## createAlbum

```TypeScript
createAlbum(name: string, callback: AsyncCallback<Album>): void
```

创建相册。使用callback异步回调。 待创建的相册名参数规格为： - 相册名字符串长度为1~255。 - 不允许出现的非法英文字符，包括： . .. \ / : * ? " ' ` &lt; &gt; | { } [ ] - 相册名不允许重名。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [createAlbumRequest](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#createalbumrequest)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-createAlbum(name: string, callback: AsyncCallback<Album>): void--><!--Device-PhotoAccessHelper-createAlbum(name: string, callback: AsyncCallback<Album>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 待创建相册的相册名。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Album&gt; | 是 | callback返回创建的相册实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 13900015 | The file name already exists. |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createAlbumDemo');
  let albumName: string = 'newAlbumName' + new Date().getTime();
  phAccessHelper.createAlbum(albumName, (err, album) => {
    if (err) {
      console.error(`createAlbumCallback failed with err: ${err.code}, ${err.message}`);
      return;
    }
    console.info('createAlbumCallback successfully, album: ' + album.albumName + ' album uri: ' + album.albumUri);
  });
}
```

## createAlbum

```TypeScript
createAlbum(name: string): Promise<Album>
```

创建相册。使用Promise异步回调。 待创建的相册名参数规格为： - 相册名字符串长度为1~255。 - 不允许出现的非法英文字符，包括： . .. \ / : * ? " ' ` &lt; &gt; | { } [ ] - 相册名不允许重名。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [createAlbumRequest](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#createalbumrequest)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-createAlbum(name: string): Promise<Album>--><!--Device-PhotoAccessHelper-createAlbum(name: string): Promise<Album>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 待创建相册的相册名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Album&gt; | Promise对象，返回创建的相册实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 13900015 | The file name already exists. |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createAlbumDemo');
  let albumName: string = 'newAlbumName' + new Date().getTime();
  phAccessHelper.createAlbum(albumName).then((album) => {
    console.info('createAlbumPromise successfully, album: ' + album.albumName + ' album uri: ' + album.albumUri);
  }).catch((err: BusinessError) => {
    console.error(`createAlbumPromise failed with err: ${err.code}, ${err.message}`);
  });
}
```

## createAsset

```TypeScript
createAsset(displayName: string, callback: AsyncCallback<PhotoAsset>): void
```

指定待创建的图片或者视频的文件名，创建图片或视频资源。使用callback异步回调。 待创建的文件名参数规格为： - 应包含有效文件主名和图片或视频扩展名。 - 文件名字符串长度为1~255。 - 文件主名中不允许出现的非法英文字符。 API18开始，非法字符包括： \ / : * ? " &lt; &gt; | API10-17，非法字符包括：. .. \ / : * ? " ' ` &lt; &gt; | { } [ ]

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-createAsset(displayName: string, callback: AsyncCallback<PhotoAsset>): void--><!--Device-PhotoAccessHelper-createAsset(displayName: string, callback: AsyncCallback<PhotoAsset>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayName | string | 是 | 创建的图片或者视频文件名。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;PhotoAsset&gt; | 是 | callback返回创建的图片和视频结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000001 | Invalid display name |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetDemo');
  let testFileName: string = 'testFile' + Date.now() + '.jpg';
  phAccessHelper.createAsset(testFileName, (err, photoAsset) => {
    if (photoAsset !== undefined) {
      console.info('createAsset file displayName' + photoAsset.displayName);
      console.info('createAsset successfully');
    } else {
      console.error(`createAsset failed, error: ${err.code}, ${err.message}`);
    }
  });
}
```

## createAsset

```TypeScript
createAsset(displayName: string): Promise<PhotoAsset>
```

指定待创建的图片或者视频的文件名，创建图片或视频资源。使用Promise异步回调。 待创建的文件名参数规格为： - 应包含有效文件主名和图片或视频扩展名。 - 文件名字符串长度为1~255。 - 文件主名中不允许出现的非法英文字符。 API18开始，非法字符包括： \ / : * ? " &lt; &gt; | API10-17，非法字符包括：. .. \ / : * ? " ' ` &lt; &gt; | { } [ ]

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-createAsset(displayName: string): Promise<PhotoAsset>--><!--Device-PhotoAccessHelper-createAsset(displayName: string): Promise<PhotoAsset>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayName | string | 是 | 创建的图片或者视频文件名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PhotoAsset&gt; | Promise对象，返回创建的图片和视频结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000001 | Invalid display name |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetDemo');
  try {
    let testFileName: string = 'testFile' + Date.now() + '.jpg';
    let photoAsset: photoAccessHelper.PhotoAsset = await phAccessHelper.createAsset(testFileName);
    console.info('createAsset file displayName' + photoAsset.displayName);
    console.info('createAsset successfully');
  } catch (err) {
    console.error(`createAsset failed, error: ${err.code}, ${err.message}`);
  }
}
```

## createAsset

```TypeScript
createAsset(displayName: string, options: PhotoCreateOptions): Promise<PhotoAsset>
```

指定待创建的图片或者视频的文件名和创建选项，创建图片或视频资源。使用Promise异步回调。 待创建的文件名参数规格为： - 应包含有效文件主名和图片或视频扩展名。 - 文件名字符串长度为1~255。 - 文件主名中不允许出现的非法英文字符。 API18开始，非法字符包括： \ / : * ? " &lt; &gt; | API10-17，非法字符包括：. .. \ / : * ? " ' ` &lt; &gt; | { } [ ]

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-createAsset(displayName: string, options: PhotoCreateOptions): Promise<PhotoAsset>--><!--Device-PhotoAccessHelper-createAsset(displayName: string, options: PhotoCreateOptions): Promise<PhotoAsset>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayName | string | 是 | 创建的图片或者视频文件名。 |
| options | [PhotoCreateOptions](arkts-medialibrary-photoaccesshelper-photocreateoptions-i-sys.md) | 是 | 图片或视频的创建选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PhotoAsset&gt; | Promise对象，返回创建的图片和视频结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000001 | Invalid display name |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetDemo');
  try {
    let testFileName:string = 'testFile' + Date.now() + '.jpg';
    let createOption: photoAccessHelper.PhotoCreateOptions = {
      subtype: photoAccessHelper.PhotoSubtype.DEFAULT
    }
    let photoAsset: photoAccessHelper.PhotoAsset = await phAccessHelper.createAsset(testFileName, createOption);
    console.info('createAsset file displayName' + photoAsset.displayName);
    console.info('createAsset successfully');
  } catch (err) {
    console.error(`createAsset failed, error: ${err.code}, ${err.message}`);
  }
}
```

## createAsset

```TypeScript
createAsset(displayName: string, options: PhotoCreateOptions, callback: AsyncCallback<PhotoAsset>): void
```

指定待创建的图片或者视频的文件名和创建选项，创建图片或视频资源。使用callback异步回调。 待创建的文件名参数规格为： - 应包含有效文件主名和图片或视频扩展名。 - 文件名字符串长度为1~255。 - 文件主名中不允许出现的非法英文字符。 API18开始，非法字符包括： \ / : * ? " &lt; &gt; | API10-17，非法字符包括：. .. \ / : * ? " ' ` &lt; &gt; | { } [ ]

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-createAsset(displayName: string, options: PhotoCreateOptions, callback: AsyncCallback<PhotoAsset>): void--><!--Device-PhotoAccessHelper-createAsset(displayName: string, options: PhotoCreateOptions, callback: AsyncCallback<PhotoAsset>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| displayName | string | 是 | 创建的图片或者视频文件名。 |
| options | [PhotoCreateOptions](arkts-medialibrary-photoaccesshelper-photocreateoptions-i-sys.md) | 是 | 图片或视频的创建选项。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;PhotoAsset&gt; | 是 | callback返回创建的图片和视频结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000001 | Invalid display name |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetDemo');
  let testFileName: string = 'testFile' + Date.now() + '.jpg';
  let createOption: photoAccessHelper.PhotoCreateOptions = {
    subtype: photoAccessHelper.PhotoSubtype.DEFAULT
  }
  phAccessHelper.createAsset(testFileName, createOption, (err, photoAsset) => {
    if (photoAsset !== undefined) {
      console.info('createAsset file displayName' + photoAsset.displayName);
      console.info('createAsset successfully');
    } else {
      console.error(`createAsset failed, error: ${err.code}, ${err.message}`);
    }
  });
}
```

## createAssetsForApp

```TypeScript
createAssetsForApp(bundleName: string, appName: string, tokenId: long, photoCreationConfigs: Array<PhotoCreationConfig>): Promise<Array<string>>
```

调用接口代替应用创建媒体库uri列表。Uri已对tokenId对应的应用授权，支持应用使用uri写入图片/视频。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-createAssetsForApp(bundleName: string, appName: string, tokenId: long, photoCreationConfigs: Array<PhotoCreationConfig>): Promise<Array<string>>--><!--Device-PhotoAccessHelper-createAssetsForApp(bundleName: string, appName: string, tokenId: long, photoCreationConfigs: Array<PhotoCreationConfig>): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 需保存图片/视频文件的应用bundle name。 |
| appName | string | 是 | 需保存图片/视频文件的应用app name。 |
| tokenId | long | 是 | 需保存图片/视频文件的应用tokenId。 |
| photoCreationConfigs | Array&lt;[PhotoCreationConfig](arkts-medialibrary-photoaccesshelper-photocreationconfig-i.md)&gt; | 是 | 保存图片/视频到媒体库的配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | 对象，返回给接口调用方的媒体库文件uri列表。Uri已对tokenId对应的应用授权，支持应用写入数据。 如果生成uri异常，则返回批量创建错误码。 <br>返回-3006表不允许出现非法字符；返回-2004表示图片类型和后缀不符；返回-203表示文件操作异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument. Possible causes: <br>1. The photoCreationConfigs is empty; <br>2. Incorrect photoCreationConfigs format. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetsForAppDemo.');

  try {
    let bundleName: string = 'testBundleName';
    let appName: string = 'testAppName';
    let tokenId: number = 537197950;
    let photoCreationConfigs: Array<photoAccessHelper.PhotoCreationConfig> = [
      {
        title: 'test',
        fileNameExtension: 'jpg',
        photoType: photoAccessHelper.PhotoType.IMAGE,
        subtype: photoAccessHelper.PhotoSubtype.DEFAULT,
      }
    ];
    let desFileUris: Array<string> = await phAccessHelper.createAssetsForApp(bundleName, appName, tokenId, photoCreationConfigs);
    console.info('createAssetsForApp success, data is ' + desFileUris);
  } catch (err) {
    console.error(`createAssetsForApp failed with error: ${err.code}, ${err.message}`);
  }
}
```

## createAssetsForAppWithAlbum

```TypeScript
createAssetsForAppWithAlbum(source: PhotoCreationSource, albumUri: string, isAuthorized: boolean, photoCreationConfigs: Array<PhotoCreationConfig>): Promise<Array<string>>
```

为应用自己或者其他应用创建资产到指定来源或者用户相册。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-createAssetsForAppWithAlbum(source: PhotoCreationSource, albumUri: string, isAuthorized: boolean, photoCreationConfigs: Array<PhotoCreationConfig>): Promise<Array<string>>--><!--Device-PhotoAccessHelper-createAssetsForAppWithAlbum(source: PhotoCreationSource, albumUri: string, isAuthorized: boolean, photoCreationConfigs: Array<PhotoCreationConfig>): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| source | [PhotoCreationSource](arkts-medialibrary-photoaccesshelper-photocreationsource-i-sys.md) | 是 | 代替应用创建资产传入的应用信息。 |
| albumUri | string | 是 | 相册uri。 |
| isAuthorized | boolean | 是 | 是否授权其他应用。true表示授权，false表示不授权。 |
| photoCreationConfigs | Array&lt;[PhotoCreationConfig](arkts-medialibrary-photoaccesshelper-photocreationconfig-i.md)&gt; | 是 | 保存图片/视频到媒体库的配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回接口调用方的媒体库文件uri列表。 <br>uri已对appId对应的应用授权，支持应用写入数据。如果生成uri异常，则返回批量创建错误码。 <br>返回-3006表示不允许出现非法字符；返回-2004表示图片类型和后缀不符；返回-203表示文件操作异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetsForAppWithAlbumDemo.');

  try {
    let source: photoAccessHelper.PhotoCreationSource = {
      bundleName: 'testBundleName',
      appName: 'testAppName',
      appId: 'testAppId',
      tokenId: 537197950,
    }
    let albumUri: string = 'file://media/PhotoAlbum/10';
    let isAuthorized: boolean = true;
    let photoCreationConfigs: Array<photoAccessHelper.PhotoCreationConfig> = [
      {
        title: 'test',
        fileNameExtension: 'jpg',
        photoType: photoAccessHelper.PhotoType.IMAGE,
        subtype: photoAccessHelper.PhotoSubtype.DEFAULT,
      }
    ];
    let desFileUris: Array<string> = await phAccessHelper.createAssetsForAppWithAlbum(source, albumUri, isAuthorized, photoCreationConfigs);
    console.info('createAssetsForAppWithAlbum success, data is ' + desFileUris);
  } catch (err) {
    console.error(`createAssetsForAppWithAlbum failed with error: ${err.code}, ${err.message}`);
  }
}
```

## createAssetsForAppWithMode

```TypeScript
createAssetsForAppWithMode(
      bundleName: string,
      appName: string,
      appId: string,
      tokenId: long,
      authorizationMode: AuthorizationMode,
      photoCreationConfigs: Array<PhotoCreationConfig>
    ): Promise<Array<string>>
```

提供给应用保存短时授权。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-createAssetsForAppWithMode(      bundleName: string,      appName: string,      appId: string,      tokenId: long,      authorizationMode: AuthorizationMode,      photoCreationConfigs: Array<PhotoCreationConfig>    ): Promise<Array<string>>--><!--Device-PhotoAccessHelper-createAssetsForAppWithMode(      bundleName: string,      appName: string,      appId: string,      tokenId: long,      authorizationMode: AuthorizationMode,      photoCreationConfigs: Array<PhotoCreationConfig>    ): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 需要保存图片/视频文件的应用bundleName。 |
| appName | string | 是 | 需要保存图片/视频文件的应用appName。 |
| appId | string | 是 | 需要保存图片/视频文件的应用app id。 |
| tokenId | long | 是 | 需要短时授权应用的唯一标识。 |
| authorizationMode | [AuthorizationMode](arkts-medialibrary-photoaccesshelper-authorizationmode-e-sys.md) | 是 | 授权模式。授予应用短期内再次保存无需重复弹框确认。 |
| photoCreationConfigs | Array&lt;[PhotoCreationConfig](arkts-medialibrary-photoaccesshelper-photocreationconfig-i.md)&gt; | 是 | 保存图片/视频到媒体库的配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回给接口调用方的媒体库文件uri列表。Uri已对appId对应的应用授权，支持应用写入数据。如果生成uri异常，则返回批量创建错误码 。 <br>返回-3006表不允许出现非法字符；返回-2004表示图片类型和后缀不符；返回-203表示文件操作异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('createAssetsForAppWithModeDemo.');

  try {
    let photoCreationConfigs: Array<photoAccessHelper.PhotoCreationConfig> = [
      {
        title: '123456',
        fileNameExtension: 'jpg',
        photoType: photoAccessHelper.PhotoType.IMAGE,
        subtype: photoAccessHelper.PhotoSubtype.DEFAULT,
      }
    ];
    let bundleName: string = 'testBundleName';
    let appName: string = 'testAppName';
    let appId: string = 'testAppId';
    let tokenId: number = 537197950;
    let authorizationMode: photoAccessHelper.AuthorizationMode = photoAccessHelper.AuthorizationMode.SHORT_TIME_AUTHORIZATION;
    let result: Array<string> = await phAccessHelper.createAssetsForAppWithMode(bundleName, appName, appId, tokenId, authorizationMode, photoCreationConfigs);
    console.info(`result: ${JSON.stringify(result)}`);
    console.info('Photo createAssetsForAppWithMode success.');
  } catch (err) {
    console.error(`createAssetsForAppWithMode failed with error: ${err.code}, ${err.message}`);
  }
}
```

## createAssetsWithAlbum

```TypeScript
createAssetsWithAlbum(
      creationSettings: CreationSetting[], 
      isRealTimeThumb: boolean, 
      albumUri?: string): Promise<string[]>
```

批量创建资产 同时支持选择是否指定相册和是否立即生成缩略图

**起始版本：** 26.0.0

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-createAssetsWithAlbum(      creationSettings: CreationSetting[],       isRealTimeThumb: boolean,       albumUri?: string): Promise<string[]>--><!--Device-PhotoAccessHelper-createAssetsWithAlbum(      creationSettings: CreationSetting[],       isRealTimeThumb: boolean,       albumUri?: string): Promise<string[]>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| creationSettings | [CreationSetting](arkts-medialibrary-photoaccesshelper-creationsetting-i.md)[] | 是 | 待创建资产列表。 |
| isRealTimeThumb | boolean | 是 | 是否实时生成缩略图。 |
| albumUri | string | 否 | 创建资产的目标相册。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string[]&gt; | 返回资产uri，若某一条失败则为null |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scenario-specific parameters are incorrect. Possible causes are as follows: <br>1. The input parameter creationSettings is null or undefined. <br>2. The array length of creationSettings is bigger than 500. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    // 构造创建参数。
    let creationSettings: Array<photoAccessHelper.CreationSetting> = [
      {
        title: 'test',
        fileNameExtension: 'jpg',
        photoType: photoAccessHelper.PhotoType.IMAGE
      }
    ];
    // 创建资产时不实时生成缩略图。
    let isRealTimeThumb: boolean = false;
    // 指定相册地址。
    let albumUri: string = 'file://media/PhotoAlbum/10';
    // 调用接口，创建资产。
    let result: Array<string> = await phAccessHelper.createAssetsWithAlbum(
      creationSettings,
      isRealTimeThumb,
      albumUri
    );
    console.info('Succeeded in creating assets with album, uri is ' + result);
  } catch (err) {
    console.error(`createAssetsWithAlbum failed with error: ${err.code}, ${err.message}`);
  }
}
```

## deleteAlbums

```TypeScript
deleteAlbums(albums: Array<Album>, callback: AsyncCallback<void>): void
```

删除存在的用户相册。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [deleteAlbums](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#deletealbums)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-deleteAlbums(albums: Array<Album>, callback: AsyncCallback<void>): void--><!--Device-PhotoAccessHelper-deleteAlbums(albums: Array<Album>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| albums | Array&lt;Album&gt; | 是 | 待删除相册的数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | callback返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  // 示例代码为删除相册名为newAlbumName的相册。
  console.info('deleteAlbumsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo('album_name', 'newAlbumName');
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, fetchOptions);
  let album: photoAccessHelper.Album = await fetchResult.getFirstObject();
  phAccessHelper.deleteAlbums([album], (err) => {
    if (err) {
      console.error(`deletePhotoAlbumsCallback failed with err: ${err.code}, ${err.message}`);
      return;
    }
    console.info('deletePhotoAlbumsCallback successfully');
  });
  fetchResult.close();
}
```

## deleteAlbums

```TypeScript
deleteAlbums(albums: Array<Album>): Promise<void>
```

删除存在的用户相册。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [deleteAlbums](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c-sys.md#deletealbums)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-deleteAlbums(albums: Array<Album>): Promise<void>--><!--Device-PhotoAccessHelper-deleteAlbums(albums: Array<Album>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| albums | Array&lt;Album&gt; | 是 | 待删除相册的数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  // 示例代码为删除相册名为newAlbumName的相册。
  console.info('deleteAlbumsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo('album_name', 'newAlbumName');
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC, fetchOptions);
  let album: photoAccessHelper.Album = await fetchResult.getFirstObject();
  phAccessHelper.deleteAlbums([album]).then(() => {
    console.info('deletePhotoAlbumsPromise successfully');
    }).catch((err: BusinessError) => {
      console.error(`deletePhotoAlbumsPromise failed with err: ${err.code}, ${err.message}`);
  });
  fetchResult.close();
}
```

## deleteAssets

```TypeScript
deleteAssets(uriList: Array<string>, callback: AsyncCallback<void>): void
```

删除媒体文件，删除的文件进入到回收站。使用callback异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [deleteAssets](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md#deleteassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-deleteAssets(uriList: Array<string>, callback: AsyncCallback<void>): void--><!--Device-PhotoAccessHelper-deleteAssets(uriList: Array<string>, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uriList | Array&lt;string&gt; | 是 | 待删除的媒体文件uri数组。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | callback返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000002 | The uri format is incorrect or does not exist. |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('deleteAssetDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('asset not exist');
      return;
    }
    phAccessHelper.deleteAssets([asset.uri], (err) => {
      if (err === undefined) {
        console.info('deleteAssets successfully');
      } else {
        console.error(`deleteAssets failed with error: ${err.code}, ${err.message}`);
      }
    });
  } catch (err) {
    console.error(`fetch failed, error: ${err.code}, ${err.message}`);
  }
}
```

## deleteAssets

```TypeScript
deleteAssets(uriList: Array<string>): Promise<void>
```

删除媒体文件，删除的文件进入到回收站。使用Promise异步回调。

**起始版本：** 10

**废弃版本：** 11

**替代接口：** [deleteAssets](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md#deleteassets)

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-deleteAssets(uriList: Array<string>): Promise<void>--><!--Device-PhotoAccessHelper-deleteAssets(uriList: Array<string>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uriList | Array&lt;string&gt; | 是 | 待删除的媒体文件uri数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 14000002 | The uri format is incorrect or does not exist. |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('deleteDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let asset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
    if (asset === undefined) {
      console.error('asset not exist');
      return;
    }
    await phAccessHelper.deleteAssets([asset.uri]);
    console.info('deleteAssets successfully');
  } catch (err) {
    console.error(`deleteAssets failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getAlbumIdByBundleName

```TypeScript
getAlbumIdByBundleName(bundleName: string): Promise<int>
```

根据bundleName获取媒体库相册的ID。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-getAlbumIdByBundleName(bundleName: string): Promise<int>--><!--Device-PhotoAccessHelper-getAlbumIdByBundleName(bundleName: string): Promise<int>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用的bundleName |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | 返回对应bundleName的albumId |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The bundleName is invalid, such as null, undefined and empty. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getAlbumIdByBundleName');

  try {
      let albumId: number = await phAccessHelper.getAlbumIdByBundleName('test.bundleName');
      console.info('requestFile:: albumId: ', albumId);

      console.info('getAlbumIdByBundleName completed.');
      console.info(`albumId : ${albumId}`);
    } catch (err) {
      console.error(`getAlbumIdByBundleName failed: ${err.code}, ${err.message}`);
    }
}
```

## getAlbumsByIds

```TypeScript
getAlbumsByIds(albumIds: Array<int>): Promise<Map<int, Album>>
```

通过相册id查询相册信息。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-getAlbumsByIds(albumIds: Array<int>): Promise<Map<int, Album>>--><!--Device-PhotoAccessHelper-getAlbumsByIds(albumIds: Array<int>): Promise<Map<int, Album>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| albumIds | Array&lt;int&gt; | 是 | 相册id列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Map&lt;int, Album&gt;&gt; | Promise对象。返回相册信息map对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('startGetAlbumsByIdsDemo');

  try {
    // 获取需要保存到媒体库的位于应用沙箱的图片/视频uri。
    let albumIds: Array<number> = [
      12 // 实际场景请使用albumId
    ];
    let map: Map<number, photoAccessHelper.Album> = await phAccessHelper.getAlbumsByIds(albumIds);
    console.info('getAlbumsByIds success, size is ' + map.size);
  } catch (err) {
    console.error('getAlbumsByIds failed, errCode is ' + err.code + ', errMsg is ' + err.message);
  }
}
```

## getAssetCompatibleCapability

```TypeScript
getAssetCompatibleCapability(bundleName: string): Promise<AssetCompatibleCapability>
```

根据bundleName获取资产兼容能力。当应用程序获取文件时，可判断该应用程序是否需要进行兼容性转换。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-getAssetCompatibleCapability(bundleName: string): Promise<AssetCompatibleCapability>--><!--Device-PhotoAccessHelper-getAssetCompatibleCapability(bundleName: string): Promise<AssetCompatibleCapability>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 目标应用的BundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[AssetCompatibleCapability](arkts-medialibrary-photoaccesshelper-assetcompatiblecapability-i.md)&gt; | 返回指定的资产兼容能力。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The bundleName is invalid, such as null, undefined and empty. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let bundleName = "com.test.example";
    let capability : photoAccessHelper.AssetCompatibleCapability = await phAccessHelper.getAssetCompatibleCapability(bundleName);
  } catch (error) {
    console.error('failed to getAssetCompatibleCapability err', error);
  }
}
```

## getAssetCompatibleUris

```TypeScript
getAssetCompatibleUris(bundleName: string, assets: Array<PhotoAsset>, compatibleFlag?: int): Promise<Array<string>>
```

根据bundleName、photoAsset列表和compatibleFlag获取需要转码的URI列表。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-getAssetCompatibleUris(bundleName: string, assets: Array<PhotoAsset>, compatibleFlag?: int): Promise<Array<string>>--><!--Device-PhotoAccessHelper-getAssetCompatibleUris(bundleName: string, assets: Array<PhotoAsset>, compatibleFlag?: int): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用捆绑包名称 |
| assets | Array&lt;PhotoAsset&gt; | 是 | 资产的数组 |
| compatibleFlag | int | 否 | 兼容配置掩码标志 <br>取值范围为全体整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise用于返回需要转码的媒体库文件uri列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. The bundleName is invalid; <br>2. The compatibleFlag is invalid; |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let bundleName: string = 'com.example.helloWorld';
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [photoAccessHelper.PhotoKeys.URI, photoAccessHelper.PhotoKeys.WIDTH, photoAccessHelper.PhotoKeys.HEIGHT],
      predicates: predicates
    };
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
    let assets: Array<photoAccessHelper.PhotoAsset> = await fetchResult.getAllObjects();
    // compatibleFlag: Bit 0表示大图，Bit 1表示Heif图像
    let compatibleFlag: number = 0;
    let uris: Array<string> = await phAccessHelper.getAssetCompatibleUris(bundleName, assets, compatibleFlag);
    console.info(`getAssetCompatibleUris success, uri count: ${uris.length}`);
  } catch (err) {
    console.error(`getAssetCompatibleUris failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getClonedAlbumUris

```TypeScript
getClonedAlbumUris(oldUris: Array<string>): Promise<Map<string, string>>
```

通过克隆后的相册URI列表获取当前uri。使用Promise异步回调。 为控制数据库表空间占用规模，当前每次克隆时都会自动将上次存储的克隆数据进行清除，所以该接口只保存最近一次克隆时用户新/旧设备uri的对应关系。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-getClonedAlbumUris(oldUris: Array<string>): Promise<Map<string, string>>--><!--Device-PhotoAccessHelper-getClonedAlbumUris(oldUris: Array<string>): Promise<Map<string, string>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oldUris | Array&lt;string&gt; | 是 | 克隆前的旧URI数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Map&lt;string, string&gt;&gt; | Promise对象，返回由克隆后的URI组成的Map列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: The size of input parameter exceeds 100 or is 0. |

**示例**

phAccessHelper的创建请参考 [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
    console.info('getClonedAlbumUrisDemo');
    // 以下是URI媒体文件。
    let uris: Array<string> = [
        'file://media/PhotoAlbum/1',
        'file://media/PhotoAlbum/2',
        'file://media/AnalysisAlbum/3'
    ];
    try {
        let albums: Map<string, string> = await phAccessHelper.getClonedAlbumUris(uris);
        console.info(`Albums: ${albums}`);
    } catch (error) {
        console.error(`Error thrown: ${error}`);
    }
}
```

## getClonedAssetUris

```TypeScript
getClonedAssetUris(oldUris: Array<string>): Promise<Map<string, string>>
```

通过克隆后的资产URI列表获取当前uri。使用Promise异步回调。 为控制数据库表空间占用规模，当前每次克隆时都会自动将上次存储的克隆数据进行清除，所以该接口只保存最近一次克隆时用户新/旧设备uri的对应关系。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-getClonedAssetUris(oldUris: Array<string>): Promise<Map<string, string>>--><!--Device-PhotoAccessHelper-getClonedAssetUris(oldUris: Array<string>): Promise<Map<string, string>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oldUris | Array&lt;string&gt; | 是 | 克隆前的旧URI数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Map&lt;string, string&gt;&gt; | Promise对象，返回由克隆后URI组成的Map列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: The size of input parameter exceeds 100 or is 0. |

**示例**

phAccessHelper的创建请参考 [photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
    console.info('getClonedAssetUrisDemo');
    // 以下是URI媒体文件。
    let uris: Array<string> = [
        'file://media/Photo/1/IMG_datetime_0001/displayName1.jpg',
        'file://media/Photo/2/IMG_datetime_0002/displayName2.jpg',
        'file://media/Photo/3/IMG_datetime_0003/displayName3.jpg'
    ];
    try {
        let assets: Map<string, string> = await phAccessHelper.getClonedAssetUris(uris);
        console.info(`Assets: ${assets}`);
    } catch (error) {
        console.error(`Error thrown: ${error}`);
    }
}
```

## getDataAnalysisProgress

```TypeScript
getDataAnalysisProgress(analysisType?: AnalysisType): Promise<string>
```

获取资产的分析进度。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-getDataAnalysisProgress(analysisType?: AnalysisType): Promise<string>--><!--Device-PhotoAccessHelper-getDataAnalysisProgress(analysisType?: AnalysisType): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| analysisType | [AnalysisType](arkts-medialibrary-photoaccesshelper-analysistype-e-sys.md) | 否 | 需要获取的智慧分析类型，默认为空值。 <br>该参数在API version 12-21为必选参数，从API version 22开始及以后为可选。<br>**起始版本：** 23 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回一个json格式的字符串。表示资产分析的进度。 <br>参数为空时返回整体的进度，参数不为空时返回analysisType对应的进度。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Incorrect parameter types; <br>2. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('getDataAnalysisProgress test start');

    let result: string = await phAccessHelper.getDataAnalysisProgress();
    console.info('getDataAnalysisProgress:' + result);

  } catch (err) {
    console.error(`getDataAnalysisProgress failed, error: ${err.code}, ${err.message}`);
  }
}
```

## getDeepOptimizeSpace

```TypeScript
getDeepOptimizeSpace(): Promise<long>
```

获取可以深度优化存储空间的大小，单位为字节（byte）。使用Promise异步回调。 <br> Unit:Byte{s}. - 此接口耗时较长，建议先调用[canPerformDeepOptimizeSpace](#canperformdeepoptimizespace)确认当前系统状态是否允许执行。 - 仅在返回true时调用此接口。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-getDeepOptimizeSpace(): Promise<long>--><!--Device-PhotoAccessHelper-getDeepOptimizeSpace(): Promise<long>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | Promise对象。返回可以深度优化存储空间大小。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let canPerform: boolean = await phAccessHelper.canPerformDeepOptimizeSpace();
    if (canPerform) {
      let size: number = await phAccessHelper.getDeepOptimizeSpace();
      console.info(`getDeepOptimizeSpace result: ${size}`);
    }
  } catch (err) {
    console.error(`getDeepOptimizeSpace failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getHiddenAlbums

```TypeScript
getHiddenAlbums(mode: HiddenPhotosDisplayMode, options: FetchOptions, callback: AsyncCallback<FetchResult<Album>>): void
```

根据隐藏文件显示模式和检索选项获取系统中的隐藏相册。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO and ohos.permission.MANAGE_PRIVATE_PHOTOS

<!--Device-PhotoAccessHelper-getHiddenAlbums(mode: HiddenPhotosDisplayMode, options: FetchOptions, callback: AsyncCallback<FetchResult<Album>>): void--><!--Device-PhotoAccessHelper-getHiddenAlbums(mode: HiddenPhotosDisplayMode, options: FetchOptions, callback: AsyncCallback<FetchResult<Album>>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [HiddenPhotosDisplayMode](arkts-medialibrary-photoaccesshelper-hiddenphotosdisplaymode-e-sys.md) | 是 | 隐藏文件显示模式。 |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 是 | 检索选项。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;FetchResult&lt;Album&gt;&gt; | 是 | callback返回获取相册的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| 14000011 | System inner fail. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

// 获取系统中包含隐藏文件且相册名为'newAlbumName'的相册
async function getHiddenAlbumsView(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getHiddenAlbumsViewDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  predicates.equalTo('album_name', 'newAlbumName');
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  phAccessHelper.getHiddenAlbums(photoAccessHelper.HiddenPhotosDisplayMode.ALBUMS_MODE, fetchOptions,
    async (err, fetchResult) => {
      if (err !== undefined) {
        console.error(`getHiddenAlbumsViewCallback failed with error: ${err.code}, ${err.message}`);
        return;
      }
      if (fetchResult === undefined) {
        console.error('getHiddenAlbumsViewCallback fetchResult is undefined');
        return;
      }
      let album = await fetchResult.getFirstObject();
      if (album === undefined) {
        console.error('getHiddenAlbumsViewCallback album is undefined');
        fetchResult.close();
        return;
      }
      console.info('getHiddenAlbumsViewCallback successfully, album name: ' + album.albumName);
      fetchResult.close();
  });
}
```

## getHiddenAlbums

```TypeScript
getHiddenAlbums(mode: HiddenPhotosDisplayMode, callback: AsyncCallback<FetchResult<Album>>): void
```

根据隐藏文件显示模式获取系统中的隐藏相册。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO and ohos.permission.MANAGE_PRIVATE_PHOTOS

<!--Device-PhotoAccessHelper-getHiddenAlbums(mode: HiddenPhotosDisplayMode, callback: AsyncCallback<FetchResult<Album>>): void--><!--Device-PhotoAccessHelper-getHiddenAlbums(mode: HiddenPhotosDisplayMode, callback: AsyncCallback<FetchResult<Album>>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [HiddenPhotosDisplayMode](arkts-medialibrary-photoaccesshelper-hiddenphotosdisplaymode-e-sys.md) | 是 | Display mode of hidden albums. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;FetchResult&lt;Album&gt;&gt; | 是 | Callback used to return the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| 14000011 | System inner fail. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

// 获取系统预置的隐藏相册
async function getSysHiddenAlbum(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getSysHiddenAlbumDemo');
  phAccessHelper.getHiddenAlbums(photoAccessHelper.HiddenPhotosDisplayMode.ASSETS_MODE, async (err, fetchResult) => {
    if (fetchResult === undefined) {
      console.error('getSysHiddenAlbumCallback fetchResult is undefined');
      return;
    }
    let hiddenAlbum: photoAccessHelper.Album = await fetchResult.getFirstObject();
    if (hiddenAlbum === undefined) {
      console.error('getSysHiddenAlbumCallback hiddenAlbum is undefined');
      fetchResult.close();
      return;
    }
    console.info('getSysHiddenAlbumCallback successfully, albumUri: ' + hiddenAlbum.albumUri);
    fetchResult.close();
  });
}

// 获取隐藏相册-相册视图，即系统中包含隐藏文件的相册（不包含系统预置的隐藏相册本身和回收站相册）
async function getHiddenAlbumsView(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getHiddenAlbumsViewDemo');
  phAccessHelper.getHiddenAlbums(photoAccessHelper.HiddenPhotosDisplayMode.ALBUMS_MODE, async (err, fetchResult) => {
    if (fetchResult === undefined) {
      console.error('getHiddenAlbumsViewCallback fetchResult is undefined');
      return;
    }
    let albums: Array<photoAccessHelper.Album> = await fetchResult.getAllObjects();
    if (albums === undefined) {
      console.error('getHiddenAlbumsViewCallback albums is undefined');
      fetchResult.close();
      return;
    }
    console.info('getHiddenAlbumsViewCallback successfully, albums size: ' + albums.length);

    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    for (let i = 0; i < albums.length; i++) {
      // 获取相册中的隐藏文件。
      albums[i].getAssets(fetchOption, (err, assetFetchResult) => {
        if (assetFetchResult === undefined) {
          console.error('getHiddenAlbumsViewCallback assetFetchResult is undefined');
          return;
        }
        console.info('album get hidden assets successfully, getCount: ' + assetFetchResult.getCount());
      });
    }
    fetchResult.close();
  });
}
```

## getHiddenAlbums

```TypeScript
getHiddenAlbums(mode: HiddenPhotosDisplayMode, options?: FetchOptions): Promise<FetchResult<Album>>
```

根据隐藏文件显示模式和检索选项获取系统中的隐藏相册。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO and ohos.permission.MANAGE_PRIVATE_PHOTOS

<!--Device-PhotoAccessHelper-getHiddenAlbums(mode: HiddenPhotosDisplayMode, options?: FetchOptions): Promise<FetchResult<Album>>--><!--Device-PhotoAccessHelper-getHiddenAlbums(mode: HiddenPhotosDisplayMode, options?: FetchOptions): Promise<FetchResult<Album>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [HiddenPhotosDisplayMode](arkts-medialibrary-photoaccesshelper-hiddenphotosdisplaymode-e-sys.md) | 是 | 隐藏文件显示模式。 |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 否 | 检索选项，不填时默认根据隐藏文件显示模式检索。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;FetchResult&lt;Album&gt;&gt; | Promise对象，返回获取相册的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| 14000011 | System inner fail. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

// 获取系统预置的隐藏相册
async function getSysHiddenAlbum(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getSysHiddenAlbumDemo');
  phAccessHelper.getHiddenAlbums(photoAccessHelper.HiddenPhotosDisplayMode.ASSETS_MODE)
    .then( async (fetchResult) => {
      if (fetchResult === undefined) {
        console.error('getSysHiddenAlbumPromise fetchResult is undefined');
        return;
      }
      let hiddenAlbum: photoAccessHelper.Album = await fetchResult.getFirstObject();
      console.info('getAlbumsPromise successfully, albumUri: ' + hiddenAlbum.albumUri);
      fetchResult.close();
    }).catch((err: BusinessError) => {
      console.error(`getSysHiddenAlbumPromise failed with err: ${err.code}, ${err.message}`);
    });
}

// 获取隐藏相册-相册视图，即系统中包含隐藏文件的相册（不包含系统预置的隐藏相册本身和回收站相册）
async function getHiddenAlbumsView(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getHiddenAlbumsViewDemo');
  phAccessHelper.getHiddenAlbums(photoAccessHelper.HiddenPhotosDisplayMode.ALBUMS_MODE).then( async (fetchResult) => {
    if (fetchResult === undefined) {
      console.error('getHiddenAlbumsViewPromise fetchResult is undefined');
      return;
    }
    let albums: Array<photoAccessHelper.Album> = await fetchResult.getAllObjects();
    console.info('getHiddenAlbumsViewPromise successfully, albums size: ' + albums.length);

    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    for (let i = 0; i < albums.length; i++) {
      // 获取相册中的隐藏文件。
      albums[i].getAssets(fetchOption).then((assetFetchResult) => {
        console.info('album get hidden assets successfully, getCount: ' + assetFetchResult.getCount());
      }).catch((err: BusinessError) => {
        console.error(`album get hidden assets failed with error: ${err.code}, ${err.message}`);
      });
    }
    fetchResult.close();
  }).catch((err: BusinessError) => {
    console.error(`getHiddenAlbumsViewPromise failed with err: ${err.code}, ${err.message}`);
  });
}
```

## getIndexConstructProgress

```TypeScript
getIndexConstructProgress(): Promise<string>
```

获取索引构建进度。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-getIndexConstructProgress(): Promise<string>--><!--Device-PhotoAccessHelper-getIndexConstructProgress(): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回一个json格式的字符串。表示已完成智慧分析的图片数量、总数和已经完成智慧分析的视频数量、总数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {

  class indexProgress {
    finishedImageCount: number = 0;
    totalImageCount: number = 0;
    finishedVideoCount: number = 0;
    totalVideoCount: number = 0;
  }

  try {
    console.info('getIndexConstructProgress test start');
    let result: string = await phAccessHelper.getIndexConstructProgress();
    console.info('getIndexProgress:' + result);

    let jsonObj: indexProgress = JSON.parse(result);
    // ...使用获取到的索引构建进度数据。
  } catch (err) {
    console.error(`getIndexConstructProgress failed, error: ${err.code}, ${err.message}`);
  }
}
```

## getPhotoAlbumOrder

```TypeScript
getPhotoAlbumOrder(orderStyle: int, options?: FetchOptions): Promise<FetchResult<AlbumOrder>>
```

获取系统、用户和来源相册的排序信息。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-getPhotoAlbumOrder(orderStyle: int, options?: FetchOptions): Promise<FetchResult<AlbumOrder>>--><!--Device-PhotoAccessHelper-getPhotoAlbumOrder(orderStyle: int, options?: FetchOptions): Promise<FetchResult<AlbumOrder>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| orderStyle | int | 是 | 选择相册的排序风格。 <br>0：Phone风格。1：PC风格。 |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 否 | 检索选项，不填时默认根据相册类型检索。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;FetchResult&lt;[AlbumOrder](arkts-medialibrary-photoaccesshelper-albumorder-i-sys.md)&gt;&gt; | Promise对象，返回获取相册排序的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: The input parameter is not within the valid range. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getPhotoAlbumOrderDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let orderStyle: number = 0;
  phAccessHelper.getPhotoAlbumOrder(orderStyle, fetchOptions).then( async (fetchResult) => {
    if (fetchResult === undefined) {
      console.error('getPhotoAlbumOrderPromise fetchResult is undefined');
      return;
    }
    let albumOrders: photoAccessHelper.AlbumOrder[] = await fetchResult.getAllObjects();
    console.info(`getPhotoAlbumOrderPromise successfully, albumOrders length: ${albumOrders.length}`);
    fetchResult.close();
  }).catch((err: BusinessError) => {
    console.error(`getPhotoAlbumOrderPromise failed with err: ${err.code}, ${err.message}`);
  });
}
```

## getPhotoAlbums

```TypeScript
getPhotoAlbums(options?: FetchOptions):Promise<FetchResult<Album>>
```

根据指定的选项获取系统、用户和来源相册。使用Promise异步回调。 在获取相册之前，确保相册已存在。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-getPhotoAlbums(options?: FetchOptions):Promise<FetchResult<Album>>--><!--Device-PhotoAccessHelper-getPhotoAlbums(options?: FetchOptions):Promise<FetchResult<Album>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 否 | 检索选项，不填时默认根据相册类型检索。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;FetchResult&lt;Album&gt;&gt; | Promise对象，返回获取相册的结果集。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getPhotoAlbumsDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  phAccessHelper.getPhotoAlbums(fetchOptions).then( async (fetchResult) => {
    if (fetchResult === undefined) {
      console.error('getPhotoAlbumsPromise fetchResult is undefined');
      return;
    }
    let albums: photoAccessHelper.Album[] = await fetchResult.getAllObjects();
    console.info(`getPhotoAlbumsPromise successfully, albums length: ${albums.length}`);
    fetchResult.close();
  }).catch((err: BusinessError) => {
    console.error(`getPhotoAlbumsPromise failed with err: ${err.code}, ${err.message}`);
  });
}
```

## getPhotoAssets

```TypeScript
getPhotoAssets(assetsData: ValuesBucket[]): Promise<PhotoAsset[]>
```

将ValuesBucket记录转换为PhotoAsset对象。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-getPhotoAssets(assetsData: ValuesBucket[]): Promise<PhotoAsset[]>--><!--Device-PhotoAccessHelper-getPhotoAssets(assetsData: ValuesBucket[]): Promise<PhotoAsset[]>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assetsData | ValuesBucket[] | 是 | 资产记录的数组。 <br>数组中的每个元素包含资产的列名称及其对应的值。 <br>数组的大小不能超过500个。 <br>数组中的每个元素必须包含以下资产列信息：file_id、data、display_name、media_type、subtype。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PhotoAsset[]&gt; | Promise对象，返回PhotoAsset对象的数组（数组可能为空）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. Invalid value type in ValuesBucket; <br>2. Missing required column in ValuesBucket; <br>3. Array size exceeds 500. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getPhotoAssets demo');
  let valuesArr: photoAccessHelper.ValuesBucket[] = [];
  let resultSet: photoAccessHelper.ResultSet | undefined = undefined;
  let photoAssetArr: photoAccessHelper.PhotoAsset[] = [];
  let QUERY_SQL = 'SELECT file_id,data,display_name,media_type,subtype from Photos limit 100';
  try {
    resultSet = await phAccessHelper.query(QUERY_SQL);
    let index: number = 0;
    while(resultSet && index < resultSet.rowCount){
      resultSet.goToRow(index);
      valuesArr.push(resultSet.getRow());
      index++;
    }
    photoAssetArr = await phAccessHelper.getPhotoAssets(valuesArr);
    console.info('getPhotoAssets successfully');
  } catch (err) {
    console.error(`valuesArr failed: ${err.code}, ${err.message}`);
  }
}
```

## getPhotoIndex

```TypeScript
getPhotoIndex(photoUri: string, albumUri: string, options: FetchOptions, callback: AsyncCallback<int>): void
```

获取相册中图片或视频的位置。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-getPhotoIndex(photoUri: string, albumUri: string, options: FetchOptions, callback: AsyncCallback<int>): void--><!--Device-PhotoAccessHelper-getPhotoIndex(photoUri: string, albumUri: string, options: FetchOptions, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| photoUri | string | 是 | 所查询的图库资源的uri。 |
| albumUri | string | 是 | 相册uri，可以为空字符串，为空字符串时默认查询全部图库资源。 |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 是 | 检索选项，predicates中必须设置一种检索排序方式，不设置或多设置均会导致接口调用异常。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;int&gt; | 是 | callback返回相册中资源的索引。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('getPhotoIndexDemo');
    let predicatesForGetAsset: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOp: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicatesForGetAsset
    };
    // Obtain the uri of the album.
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.SYSTEM, photoAccessHelper.AlbumSubtype.FAVORITE, fetchOp);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    predicates.orderByAsc(photoAccessHelper.PhotoKeys.DATE_MODIFIED);
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [photoAccessHelper.PhotoKeys.DATE_MODIFIED],
      predicates: predicates
    };
    let photoFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOptions);
    let expectIndex = 1;
    // Obtain the uri of the second file.
    let photoAsset: photoAccessHelper.PhotoAsset = await photoFetchResult.getObjectByPosition(expectIndex);

    phAccessHelper.getPhotoIndex(photoAsset.uri, album.albumUri, fetchOptions, (err, index) => {
      if (err === undefined) {
        console.info(`getPhotoIndex successfully and index is : ${index}`);
      } else {
        console.error(`getPhotoIndex failed; error: ${err.code}, ${err.message}`);
      }
    });
  } catch (error) {
    console.error(`getPhotoIndex failed; error: ${error.code}, ${error.message}`);
  }
}
```

## getPhotoIndex

```TypeScript
getPhotoIndex(photoUri: string, albumUri: string, options: FetchOptions): Promise<int>
```

获取相册中图片或视频的位置。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-getPhotoIndex(photoUri: string, albumUri: string, options: FetchOptions): Promise<int>--><!--Device-PhotoAccessHelper-getPhotoIndex(photoUri: string, albumUri: string, options: FetchOptions): Promise<int>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| photoUri | string | 是 | 所查询的图库资源的uri。 |
| albumUri | string | 是 | 相册uri，可以为空字符串，为空字符串时默认查询全部图库资源。 |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 是 | 检索选项，predicates中必须设置一种检索排序方式，不设置或多设置均会导致接口调用异常。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | 返回相册中资源的索引。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| 13900012 | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| 14000011 | System inner fail |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('getPhotoIndexDemo');
    let predicatesForGetAsset: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOp: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicatesForGetAsset
    };
    // Obtain the uri of the album.
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.SYSTEM, photoAccessHelper.AlbumSubtype.FAVORITE, fetchOp);
    let album: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    predicates.orderByAsc(photoAccessHelper.PhotoKeys.DATE_MODIFIED);
    let fetchOptions: photoAccessHelper.FetchOptions = {
      fetchColumns: [photoAccessHelper.PhotoKeys.DATE_MODIFIED],
      predicates: predicates
    };
    let photoFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await album.getAssets(fetchOptions);
    let expectIndex = 1;
    // Obtain the uri of the second file.
    let photoAsset: photoAccessHelper.PhotoAsset = await photoFetchResult.getObjectByPosition(expectIndex);
    phAccessHelper.getPhotoIndex(photoAsset.uri, album.albumUri, fetchOptions).then((index) => {
      console.info(`getPhotoIndex successfully and index is : ${index}`);
    }).catch((err: BusinessError) => {
      console.error(`getPhotoIndex failed; error: ${err.code}, ${err.message}`);
    });
  } catch (error) {
    console.error(`getPhotoIndex failed; error: ${error.code}, ${error.message}`);
  }
}
```

## getPreferredCompatibleMode

```TypeScript
getPreferredCompatibleMode(bundleName: string): Promise<PreferredCompatibleMode>
```

根据bundleName获取应用配置的首选兼容模式。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-getPreferredCompatibleMode(bundleName: string): Promise<PreferredCompatibleMode>--><!--Device-PhotoAccessHelper-getPreferredCompatibleMode(bundleName: string): Promise<PreferredCompatibleMode>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[PreferredCompatibleMode](arkts-medialibrary-photoaccesshelper-preferredcompatiblemode-e.md)&gt; | 资产兼容能力。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The bundleName is invalid, such as null, undefined and empty. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function getPreferredCompatibleMode(
  phAccessHelper: photoAccessHelper.PhotoAccessHelper,
  bundleName: string
): Promise<photoAccessHelper.PreferredCompatibleMode> {
  console.info('getPreferredCompatibleModeDemo');
  let mode: photoAccessHelper.PreferredCompatibleMode = photoAccessHelper.PreferredCompatibleMode.DEFAULT;
  await phAccessHelper.getPreferredCompatibleMode(bundleName)
    .then((result: photoAccessHelper.PreferredCompatibleMode) => {
      mode = result;
      console.info('getPreferredCompatibleMode successfully');
    })
    .catch((err: BusinessError) => {
      console.error(`The getPreferredCompatibleMode call failed. error: ${err.code}, ${err.message}`);
    });
  return mode;
}
```

## getSharedPhotoAssets

```TypeScript
getSharedPhotoAssets(options: FetchOptions): Array<SharedPhotoAsset>
```

获取共享的照片资产。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_MEDIALIB_THUMB_DB

<!--Device-PhotoAccessHelper-getSharedPhotoAssets(options: FetchOptions): Array<SharedPhotoAsset>--><!--Device-PhotoAccessHelper-getSharedPhotoAssets(options: FetchOptions): Array<SharedPhotoAsset>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [FetchOptions](arkts-medialibrary-photoaccesshelper-fetchoptions-i.md) | 是 | 获取共享的照片资产选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;SharedPhotoAsset&gt; | 返回共享的照片资产。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };

  try {
    console.info('getSharedPhotoAssets test start');
    phAccessHelper.getSharedPhotoAssets(fetchOptions);
    console.info('getSharedPhotoAssets test end');
  } catch (err) {
    console.error(`getSharedPhotoAssets failed, error: ${err.code}, ${err.message}`);
  }
}
```

## grantPhotoUriPermission

```TypeScript
grantPhotoUriPermission(
      tokenId: long, 
      uri: string, 
      photoPermissionType: PhotoPermissionType, 
      hideSensitiveType: HideSensitiveType
    ): Promise<int>
```

给应用授予uri的访问权限。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-grantPhotoUriPermission(      tokenId: long,       uri: string,       photoPermissionType: PhotoPermissionType,       hideSensitiveType: HideSensitiveType    ): Promise<int>--><!--Device-PhotoAccessHelper-grantPhotoUriPermission(      tokenId: long,       uri: string,       photoPermissionType: PhotoPermissionType,       hideSensitiveType: HideSensitiveType    ): Promise<int>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenId | long | 是 | 应用标识，将访问权限授予给tokenId标识的应用。 |
| uri | string | 是 | 媒体资源的uri，uri表示的资源的访问权限将授予给应用。 |
| photoPermissionType | [PhotoPermissionType](arkts-medialibrary-photoaccesshelper-photopermissiontype-e-sys.md) | 是 | 权限类型，将photoPermissionType表示的权限授予给应用。权限的覆盖规则参考枚举类。 |
| hideSensitiveType | [HideSensitiveType](arkts-medialibrary-photoaccesshelper-hidesensitivetype-e-sys.md) | 是 | 脱敏类型，预留参数，目前可传枚举类中任一值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，0:授权成功。 1:已有权限。-1:授权失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument. Possible causes: <br>1. Incorrect uri format; <br>2. The value of photoPermissionType or hideSensitiveType is out of range. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('grantPhotoUriPermissionDemo');

  try {
    let tokenId = 502334412;
    let result = await phAccessHelper.grantPhotoUriPermission(tokenId,
        'file://media/Photo/1/IMG_datetime_0001/displayName.jpg',
        photoAccessHelper.PhotoPermissionType.TEMPORARY_READ_IMAGEVIDEO,
        photoAccessHelper.HideSensitiveType.HIDE_LOCATION_AND_SHOOTING_PARAM);

    console.info('grantPhotoUriPermission success, result=' + result);
  } catch (err) {
    console.error('grantPhotoUriPermission failed, error=' + err);
  }
}
```

## grantPhotoUrisPermission

```TypeScript
grantPhotoUrisPermission(
      tokenId: long, 
      uriList: Array<string>, 
      photoPermissionType: PhotoPermissionType, 
      hideSensitiveType: HideSensitiveType
    ): Promise<int>
```

给应用授予uri列表的访问权限。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-grantPhotoUrisPermission(      tokenId: long,       uriList: Array<string>,       photoPermissionType: PhotoPermissionType,       hideSensitiveType: HideSensitiveType    ): Promise<int>--><!--Device-PhotoAccessHelper-grantPhotoUrisPermission(      tokenId: long,       uriList: Array<string>,       photoPermissionType: PhotoPermissionType,       hideSensitiveType: HideSensitiveType    ): Promise<int>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tokenId | long | 是 | 应用标识，将访问权限授予给tokenId标识的应用。 |
| uriList | Array&lt;string&gt; | 是 | 媒体资源的uri列表，uri列表中的资源的访问权限将授予给应用。uri列表最多容纳 1000 条uri。 |
| photoPermissionType | [PhotoPermissionType](arkts-medialibrary-photoaccesshelper-photopermissiontype-e-sys.md) | 是 | 权限类型，将photoPermissionType表示的权限授予给应用。权限的覆盖规则参考枚举类。 |
| hideSensitiveType | [HideSensitiveType](arkts-medialibrary-photoaccesshelper-hidesensitivetype-e-sys.md) | 是 | 脱敏类型，预留参数，目前可传枚举类中任一值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，0: 授权成功。 -1:授权失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument. Possible causes: <br>1. Incorrect uri format; <br>2. The value of photoPermissionType or hideSensitiveType is out of range. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('grantPhotoUrisPermissionDemo');

  try {
    // 媒体资源的uri列表。
    let uris: Array<string> = [
      'file://media/Photo/11/IMG_datetime_0001/displayName1.jpg',
      'file://media/Photo/22/IMG_datetime_0002/displayName2.jpg'];
    let tokenId = 502334412;
    let result = await phAccessHelper.grantPhotoUrisPermission(tokenId, uris,
        photoAccessHelper.PhotoPermissionType.TEMPORARY_READ_IMAGEVIDEO,
        photoAccessHelper.HideSensitiveType.HIDE_LOCATION_AND_SHOOTING_PARAM);

    console.info('grantPhotoUrisPermission success, result=' + result);
  } catch (err) {
    console.error('grantPhotoUrisPermission failed, error=' + err);
  }
}
```

## invokeAnalysisTool

```TypeScript
invokeAnalysisTool(config: ToolInvokeConfig, callback: Callback<AnalysisToolResult>): Promise<string>
```

触发分析工具的执行。该接口使用promise返回结果。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.CONTROL_IMAGEVIDEO_ANALYSIS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-invokeAnalysisTool(config: ToolInvokeConfig, callback: Callback<AnalysisToolResult>): Promise<string>--><!--Device-PhotoAccessHelper-invokeAnalysisTool(config: ToolInvokeConfig, callback: Callback<AnalysisToolResult>): Promise<string>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ToolInvokeConfig](arkts-medialibrary-photoaccesshelper-toolinvokeconfig-i-sys.md) | 是 | 工具调用配置。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AnalysisToolResult](arkts-medialibrary-photoaccesshelper-analysistoolresult-i-sys.md)&gt; | 是 | 工具执行完成时调用的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise用于返回任务ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. Possible causes: <br>1. IPC timeout; <br>2. System exception. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. Unsupported tool type; <br>2. The length of **param** in **ToolInvokeConfig** exceeds 16KB. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
let callback = (result: photoAccessHelper.AnalysisToolResult) => {
  console.info('invokeAnalysisTool callback result: ' + JSON.stringify(result));
};

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('invokeAnalysisToolDemo');
  let config: photoAccessHelper.ToolInvokeConfig = {
    type: photoAccessHelper.AnalysisToolType.IMAGE_RETRIEVAL_TOOL_TYPE,
    param: '{"key":"value"}'
  };

  try {
    let taskId = await phAccessHelper.invokeAnalysisTool(config, callback);
    console.info('do invokeAnalysisTool successfully');
  } catch (err) {
    console.error('failed to do invokeAnalysisTool');
  }
}
```

## isCompatibleDuplicateSupported

```TypeScript
isCompatibleDuplicateSupported(bundleName: string): Promise<boolean>
```

检查是否要为指定应用创建JPEG格式的临时副本。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-isCompatibleDuplicateSupported(bundleName: string): Promise<boolean>--><!--Device-PhotoAccessHelper-isCompatibleDuplicateSupported(bundleName: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 需查询的应用包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | 检查是否要为指定应用创建JPEG格式的临时副本。true表示创建，false表示不创建。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. The IPC request timed out. <br>2. system running error |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |

**示例**

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('isCompatibleDuplicateSupportedPromiseDemo')
    let isSupport: boolean = await phAccessHelper.isCompatibleDuplicateSupported('com.example.helloworld');
    console.info(`isCompatibleDuplicateSupported: ${isSupport}`);
  } catch (err) {
    console.error(`isCompatibleDuplicateSupportedPromiseDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## isMediaDataReady

```TypeScript
isMediaDataReady(mediaDataKey: string): Promise<boolean>
```

判断指定的媒体数据是否已经准备完成。

**起始版本：** 24

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-isMediaDataReady(mediaDataKey: string): Promise<boolean>--><!--Device-PhotoAccessHelper-isMediaDataReady(mediaDataKey: string): Promise<boolean>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mediaDataKey | string | 是 | 查询的媒体数据类型。 <br>当前支持配置的取值为"date_added_year"，表示查询资产的添加时间（年月日）数据是否准备完成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示媒体数据准备完成；返回false表示媒体数据未准备完成。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails, unsupported media data type. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('isMediaDataReady demo');

  try {
    let ready: boolean = await phAccessHelper.isMediaDataReady('date_added_year');
    if (ready) {
      console.info('date_added_year media data is ready.');
    } else {
      console.info('date_added_year media data is not ready.');
    }
  } catch (err) {
    console.error(`isMediaDataReady failed: ${err.code}, ${err.message}`);
  }
}
```

## modifyAlbumDefaultCoverOrder

```TypeScript
modifyAlbumDefaultCoverOrder(coverOrderInfos: DefaultCoverOrderInfo[], 
    disableModification: boolean, 
    isAsyncRefreshAlbum: boolean): Promise<void>
```

修改相册的默认封面选择顺序

**起始版本：** 26.0.0

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-modifyAlbumDefaultCoverOrder(coverOrderInfos: DefaultCoverOrderInfo[],     disableModification: boolean,     isAsyncRefreshAlbum: boolean): Promise<void>--><!--Device-PhotoAccessHelper-modifyAlbumDefaultCoverOrder(coverOrderInfos: DefaultCoverOrderInfo[],     disableModification: boolean,     isAsyncRefreshAlbum: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| coverOrderInfos | [DefaultCoverOrderInfo](arkts-medialibrary-photoaccesshelper-defaultcoverorderinfo-c-sys.md)[] | 是 | 批量处理的相册封面修改信息 |
| disableModification | boolean | 是 | 去使能修改项 |
| isAsyncRefreshAlbum | boolean | 是 | 针对克隆等场景，若存在大量相册需要刷新相册，比较耗时，建议应用使用异步刷新 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回值 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: 1. Database corrupted; 2. The file system is abnormal; 3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. Only the system album can be set without lpath. Otherwise, the setting is not supported; <br>2. The orderKey and orderSubKey are not in the specified range; <br>3. The order type must be either descending or ascending. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function modifyAlbumDefaultCoverOrder(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let coverOrderInfos: Array<photoAccessHelper.DefaultCoverOrderInfo> = [];
    let coverOrderInfo: photoAccessHelper.DefaultCoverOrderInfo = {
      albumType: photoAccessHelper.AlbumType.USER,
      albumSubtype: photoAccessHelper.AlbumSubtype.USER_GENERIC,
      lpath: "/Pictures/Users/1",
      orderKey: photoAccessHelper.PhotoKeys.DATE_ADDED,
      orderSubKey: photoAccessHelper.PhotoKeys.DISPLAY_NAME,
      orderType: 1,
    }
    coverOrderInfos.push(coverOrderInfo);
    let disableModification: boolean = false;
    let isAsyncRefreshAlbum: boolean = false;
    await phAccessHelper.modifyAlbumDefaultCoverOrder(coverOrderInfos, disableModification, isAsyncRefreshAlbum);
    console.info(`Succeeded in modifying default cover order of user album 1`);
  } catch (err) {
    console.error(`modifyAlbumDefaultCoverOrder failed with error: ${err.code}, ${err.message}`);
  }
}
```

## modifyHiddenAlbumDefaultCoverOrder

```TypeScript
modifyHiddenAlbumDefaultCoverOrder(coverOrderInfos: DefaultCoverOrderInfo[], 
    disableModification: boolean, 
    isAsyncRefreshAlbum: boolean): Promise<void>
```

修改隐藏相册的默认封面选择顺序

**起始版本：** 26.0.0

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO and ohos.permission.MANAGE_PRIVATE_PHOTOS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-modifyHiddenAlbumDefaultCoverOrder(coverOrderInfos: DefaultCoverOrderInfo[],     disableModification: boolean,     isAsyncRefreshAlbum: boolean): Promise<void>--><!--Device-PhotoAccessHelper-modifyHiddenAlbumDefaultCoverOrder(coverOrderInfos: DefaultCoverOrderInfo[],     disableModification: boolean,     isAsyncRefreshAlbum: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| coverOrderInfos | [DefaultCoverOrderInfo](arkts-medialibrary-photoaccesshelper-defaultcoverorderinfo-c-sys.md)[] | 是 | 批量修改默认封面顺序信息 |
| disableModification | boolean | 是 | 去使能修改项 |
| isAsyncRefreshAlbum | boolean | 是 | 克隆等场景，若大量刷新相册封面，建议应用异步刷新相册 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: 1. Database corrupted; 2. The file system is abnormal; 3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. Only the system album can be set without lpath. Otherwise, the setting is not supported; <br>2. The orderKey and orderSubKey are not in the specified range; <br>3. The order type must be either descending or ascending. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function modifyHiddenAlbumDefaultCoverOrder(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let coverOrderInfos: Array<photoAccessHelper.DefaultCoverOrderInfo> = [];
    let coverOrderInfo: photoAccessHelper.DefaultCoverOrderInfo = {
      albumType: photoAccessHelper.AlbumType.SYSTEM,
      albumSubtype: photoAccessHelper.AlbumSubtype.HIDDEN,
      orderKey: photoAccessHelper.PhotoKeys.DATE_ADDED,
      orderSubKey: photoAccessHelper.PhotoKeys.DISPLAY_NAME,
      orderType: 1,
    }
    coverOrderInfos.push(coverOrderInfo);
    let disableModification: boolean = false;
    let isAsyncRefreshAlbum: boolean = false;
    await phAccessHelper.modifyHiddenAlbumDefaultCoverOrder(coverOrderInfos, disableModification, isAsyncRefreshAlbum);
    console.info(`Succeeded in modifying default cover order of hidden album`);
  } catch (err) {
    console.error(`modifyHiddenAlbumDefaultCoverOrder failed with error: ${err.code}, ${err.message}`);
  }
}
```

## moveAssetsByPath

```TypeScript
moveAssetsByPath(assets: string[], target: Album, option?: BatchOperationOptions): Promise<string[]>
```

将文件管理中的资产移动到目标相册中。使用Promise异步回调。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-moveAssetsByPath(assets: string[], target: Album, option?: BatchOperationOptions): Promise<string[]>--><!--Device-PhotoAccessHelper-moveAssetsByPath(assets: string[], target: Album, option?: BatchOperationOptions): Promise<string[]>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | string[] | 是 | 文管公共目录的资产 |
| target | Album | 是 | 图库相册 |
| option | [BatchOperationOptions](arkts-medialibrary-photoaccesshelper-batchoperationoptions-i-sys.md) | 否 | 批量操作的选项 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string[]&gt; | 返回成功的资产URI。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: 1. Database corrupted; 2. The file system is abnormal; 3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. Moving to the target Album is not supported; <br>2. Assets to be Moved does not exist; <br>3. Automatic renaming is not supported. <br>4. The task is interrupted. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let assets: Array<string> = ["/Docs/Download/test.jpg"];
    let albumFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.Album> = await phAccessHelper.getAlbums(photoAccessHelper.AlbumType.USER, photoAccessHelper.AlbumSubtype.USER_GENERIC);
    let target: photoAccessHelper.Album = await albumFetchResult.getFirstObject();
    let moveUris: Array<string> = await phAccessHelper.moveAssetsByPath(assets, target);
    console.info(`moveAssetsByPath success, count: ${moveUris.length}`);
  } catch (err) {
    console.error(`moveAssetsByPath failed with error: ${err.code}, ${err.message}`);
  }
}
```

## moveAssetsToDir

```TypeScript
moveAssetsToDir(assets: string[], target: string, option?: BatchOperationOptions): Promise<string[]>
```

移动资产到文件管理目录中。使用Promise异步回调。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-moveAssetsToDir(assets: string[], target: string, option?: BatchOperationOptions): Promise<string[]>--><!--Device-PhotoAccessHelper-moveAssetsToDir(assets: string[], target: string, option?: BatchOperationOptions): Promise<string[]>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assets | string[] | 是 | 媒体库沙箱资产uri |
| target | string | 是 | 文管公共目录 |
| option | [BatchOperationOptions](arkts-medialibrary-photoaccesshelper-batchoperationoptions-i-sys.md) | 否 | 批量操作的选项 <br>批量操作的选项 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string[]&gt; | 返回资产的路径 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. Moving to the target directory is not supported; <br>2. Assets to be Moved does not exist; <br>3. Automatic renaming is not supported. <br>4. The task is interrupted. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    let fetchOption: photoAccessHelper.FetchOptions = {
      fetchColumns: [],
      predicates: predicates
    };
    let assetFetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    let assets: Array<photoAccessHelper.PhotoAsset> = await assetFetchResult.getAllObjects();
    let assetUris: Array<string> = assets.map((item) => item.uri);
    let target: string = "/Docs/Download/";
    let movePaths: Array<string> = await phAccessHelper.moveAssetsToDir(assetUris, target);
    console.info(`moveAssetsToDir success, count: ${movePaths.length}`);
  } catch (err) {
    console.error(`moveAssetsToDir failed with error: ${err.code}, ${err.message}`);
  }
}
```

## offAnalysisAlbumChange

```TypeScript
offAnalysisAlbumChange(callback?: Callback<AlbumChangeInfos>): void
```

取消对智慧分析相册的监听。存在多个callback监听时，可以取消指定注册的callback监听；不指定callback时取消所有监听。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-offAnalysisAlbumChange(callback?: Callback<AlbumChangeInfos>): void--><!--Device-PhotoAccessHelper-offAnalysisAlbumChange(callback?: Callback<AlbumChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | 否 | 回调函数，返回变更的智慧分析相册信息，填入时取消 [onAnalysisAlbumChange](#onanalysisalbumchange) 注册时指定的callback监听；不填时，则取消 [onAnalysisAlbumChange](#onanalysisalbumchange) 注册的所有监听。 <br>**注意：** <br>取消注册的callback后，有智慧相册发生变化时，不会进入此回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper){
  console.info('offAnalysisAlbumChangeDemo.');

  try {
    // 注册onCallback1监听。
    phAccessHelper.onAnalysisAlbumChange(onCallback1);
    // 注册onCallback2监听。
    phAccessHelper.onAnalysisAlbumChange(onCallback2);

    // 关闭onCallback1监听，onCallback2继续监听。
    phAccessHelper.offAnalysisAlbumChange(onCallback1);
  } catch (error) {
    console.error('offAnalysisAlbumChangeDemo failed, errCode is', error);
  }
}
```

## offAnalysisPhotoChange

```TypeScript
offAnalysisPhotoChange(callback?: Callback<PhotoAssetChangeInfos>): void
```

取消对与智慧分析相册相关的媒体资产变更的监听。存在多个callback监听时，可以取消指定注册的callback监听；不指定callback时取消所有监听。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO and ohos.permission.MANAGE_PRIVATE_PHOTOS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-offAnalysisPhotoChange(callback?: Callback<PhotoAssetChangeInfos>): void--><!--Device-PhotoAccessHelper-offAnalysisPhotoChange(callback?: Callback<PhotoAssetChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | 否 | 回调函数，返回含对应智慧分析相册变更的媒体资产信息，填入时取消 [onAnalysisPhotoChange](#onanalysisphotochange) 注册时指定的callback监听；不填时，则取消对 [onAnalysisPhotoChange](#onanalysisphotochange) 的所有监听。 <br>**注意：** <br>取消注册的callback后，智慧分析相册的资产变更时，不再进入此回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback1 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback2 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('offAnalysisPhotoChangeDemo.');

  try {
    // 注册onCallback1监听。
    phAccessHelper.offAnalysisPhotoChange(onCallback1);
    // 注册onCallback2监听。
    phAccessHelper.offAnalysisPhotoChange(onCallback2);

    // 关闭onCallback1监听，onCallback2继续监听。
    phAccessHelper.offAnalysisPhotoChange(onCallback1);
  } catch (error) {
    console.error('offAnalysisPhotoChangeDemo failed, errCode is', error);
  }
}
```

## offHiddenPhotoChange

```TypeScript
offHiddenPhotoChange(callback?: Callback<PhotoAssetChangeInfos>): void
```

取消监听隐藏的媒体资产。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO and ohos.permission.MANAGE_PRIVATE_PHOTOS

<!--Device-PhotoAccessHelper-offHiddenPhotoChange(callback?: Callback<PhotoAssetChangeInfos>): void--><!--Device-PhotoAccessHelper-offHiddenPhotoChange(callback?: Callback<PhotoAssetChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | 否 | Callback used for unsubscription. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

## offShareAlbumChange

```TypeScript
offShareAlbumChange(callback?: Callback<AlbumChangeInfos>): void
```

注销共享相册的监听

**起始版本：** 26.1.0

**需要权限：** ohos.permission.MANAGE_SHARE_PHOTO

<!--Device-PhotoAccessHelper-offShareAlbumChange(callback?: Callback<AlbumChangeInfos>): void--><!--Device-PhotoAccessHelper-offShareAlbumChange(callback?: Callback<AlbumChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | 否 | 共享相册的监听回调 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

## offSharePhotoChange

```TypeScript
offSharePhotoChange(callback?: Callback<PhotoAssetChangeInfos>): void
```

注销共享相册图片和视频的监听

**起始版本：** 26.1.0

**需要权限：** ohos.permission.MANAGE_SHARE_PHOTO

<!--Device-PhotoAccessHelper-offSharePhotoChange(callback?: Callback<PhotoAssetChangeInfos>): void--><!--Device-PhotoAccessHelper-offSharePhotoChange(callback?: Callback<PhotoAssetChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | 否 | 监听图片和视频的回调 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

## offTrashedAlbumChange

```TypeScript
offTrashedAlbumChange(callback?: Callback<AlbumChangeInfos>): void
```

Unsubscribes from changes in the trashed album.

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-offTrashedAlbumChange(callback?: Callback<AlbumChangeInfos>): void--><!--Device-PhotoAccessHelper-offTrashedAlbumChange(callback?: Callback<AlbumChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | 否 | Callback used for unsubscription. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

## offTrashedPhotoChange

```TypeScript
offTrashedPhotoChange(callback?: Callback<PhotoAssetChangeInfos>): void
```

注销回收站媒体资产监听。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-offTrashedPhotoChange(callback?: Callback<PhotoAssetChangeInfos>): void--><!--Device-PhotoAccessHelper-offTrashedPhotoChange(callback?: Callback<PhotoAssetChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | 否 | 监听图片和视频的回调 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

## off('hiddenAlbumChange')

```TypeScript
off(type: 'hiddenAlbumChange', callback?: Callback<AlbumChangeInfos>): void
```

取消对'hiddenAlbumChange'隐藏相册的监听。存在多个callback监听时，可以取消指定注册的callback监听；不指定callback时取消所有监听。

**起始版本：** 20

**需要权限：** ohos.permission.READ_IMAGEVIDEO and ohos.permission.MANAGE_PRIVATE_PHOTOS

<!--Device-PhotoAccessHelper-off(type: 'hiddenAlbumChange', callback?: Callback<AlbumChangeInfos>): void--><!--Device-PhotoAccessHelper-off(type: 'hiddenAlbumChange', callback?: Callback<AlbumChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hiddenAlbumChange' | 是 | 取消监听隐藏相册，取值为'hiddenAlbumChange'。取消监听后，有隐藏相册发生变化时，不再通过callback返回变更信息。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | 否 | 取消 [on('hiddenAlbumChange')](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#onphotochange) 注册时指定的callback监听；不填时，则取消对'hiddenAlbumChange'的所有监听。 <br>**注意：** <br>取消注册的callback后，有隐藏相册发生变化时，不会进入此回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper){
  console.info('onHiddenAlbumChangeDemo.');

  try {
    // 注册onCallback1监听。
    phAccessHelper.on('hiddenAlbumChange', onCallback1);
    // 注册onCallback2监听。
    phAccessHelper.on('hiddenAlbumChange', onCallback2);

    // 关闭onCallback1监听，onCallback2继续监听。
    phAccessHelper.off('hiddenAlbumChange', onCallback1);
  } catch (error) {
    console.error('onHiddenAlbumChangeDemo failed, errCode is', error);
  }
}
```

## off('hiddenPhotoChange')

```TypeScript
off(type: 'hiddenPhotoChange', callback?: Callback<PhotoAssetChangeInfos>): void
```

取消对'hiddenPhotoChange'隐藏资产的监听。存在多个callback监听时，可以取消指定注册的callback监听；不指定callback时取消所有监听。

**起始版本：** 20

**需要权限：** ohos.permission.READ_IMAGEVIDEO and ohos.permission.MANAGE_PRIVATE_PHOTOS

<!--Device-PhotoAccessHelper-off(type: 'hiddenPhotoChange', callback?: Callback<PhotoAssetChangeInfos>): void--><!--Device-PhotoAccessHelper-off(type: 'hiddenPhotoChange', callback?: Callback<PhotoAssetChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hiddenPhotoChange' | 是 | 取消监听隐藏资产，取值为'hiddenPhotoChange'。取消监听后，有隐藏资产发生变化时，不再通过callback返回变更信息。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | 否 | 取消 [on('hiddenPhotoChange')](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#onphotochange) 注册时指定的callback监听；不填时，则取消对'hiddenPhotoChange'的所有监听。 <br>**注意：** <br>取消注册的callback后，有隐藏资产发生变化时，不会进入此回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper){
  console.info('offHiddenPhotoChangeDemo.');

  try {
    // 注册onCallback1监听。
    phAccessHelper.on('hiddenPhotoChange', onCallback1);
    // 注册onCallback2监听。
    phAccessHelper.on('hiddenPhotoChange', onCallback2);

    // 关闭onCallback1监听，onCallback2继续监听。
    phAccessHelper.off('hiddenPhotoChange', onCallback1);
  } catch (error) {
    console.error('offHiddenPhotoChange failed, errCode is', error);
  }
}
```

## off('trashedAlbumChange')

```TypeScript
off(type: 'trashedAlbumChange', callback?: Callback<AlbumChangeInfos>): void
```

取消对'trashedAlbumChange'回收站相册的监听。存在多个callback监听时，可以取消指定注册的callback监听；不指定callback时取消所有监听。

**起始版本：** 20

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-off(type: 'trashedAlbumChange', callback?: Callback<AlbumChangeInfos>): void--><!--Device-PhotoAccessHelper-off(type: 'trashedAlbumChange', callback?: Callback<AlbumChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'trashedAlbumChange' | 是 | 取消监听回收站相册，取值为'trashedAlbumChange'。取消监听后，有回收站相册发生变化时，不再通过callback返回变更信息。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | 否 | 取消 [on('trashedAlbumChange')](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#onphotochange) 注册时指定的callback监听；不填时，则取消对'trashedAlbumChange'的所有监听。 <br>**注意：** <br>取消注册的callback后，有回收站相册发生变化时，不会进入此回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onTrashedAlbumChangeDemo.');

  try {
    // 注册onCallback1监听。
    phAccessHelper.on('trashedAlbumChange', onCallback1);
    // 注册onCallback2监听。
    phAccessHelper.on('trashedAlbumChange', onCallback2);

    // 关闭onCallback1监听，onCallback2继续监听。
    phAccessHelper.off('trashedAlbumChange', onCallback1);
  } catch (error) {
    console.error('onTrashedAlbumChangeDemo failed, errCode is', error);
  }
}
```

## off('trashedPhotoChange')

```TypeScript
off(type: 'trashedPhotoChange', callback?: Callback<PhotoAssetChangeInfos>): void
```

取消对'trashedPhotoChange'回收站资产的监听。存在多个callback监听时，可以取消指定注册的callback监听；不指定callback时取消所有监听。

**起始版本：** 20

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-off(type: 'trashedPhotoChange', callback?: Callback<PhotoAssetChangeInfos>): void--><!--Device-PhotoAccessHelper-off(type: 'trashedPhotoChange', callback?: Callback<PhotoAssetChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'trashedPhotoChange' | 是 | 取消监听回收站资产，取值为'trashedPhotoChange'。取消监听后，有回收站资产发生变化时，不再通过callback返回变更信息。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | 否 | 取消 [on('trashedPhotoChange')](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#onphotochange) 注册时指定的callback监听；不填时，则取消对'trashedPhotoChange'的所有监听。 <br>**注意：** <br>取消注册的callback后，有回收站资产发生变化时，不会进入此回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback1 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback2 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('offTrashedPhotoChangeDemo.');

  try {
    // 注册onCallback1监听。
    phAccessHelper.on('trashedPhotoChange', onCallback1);
    // 注册onCallback2监听。
    phAccessHelper.on('trashedPhotoChange', onCallback2);

    // 关闭onCallback1监听，onCallback2继续监听。
    phAccessHelper.off('trashedPhotoChange', onCallback1);
  } catch (error) {
    console.error('offTrashedPhotoChangeDemo failed, errCode is', error);
  }
}
```

## offhiddenAlbumChange

```TypeScript
offhiddenAlbumChange(callback?: Callback<AlbumChangeInfos>): void
```

注销隐藏相册监听。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO and ohos.permission.MANAGE_PRIVATE_PHOTOS

<!--Device-PhotoAccessHelper-offhiddenAlbumChange(callback?: Callback<AlbumChangeInfos>): void--><!--Device-PhotoAccessHelper-offhiddenAlbumChange(callback?: Callback<AlbumChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | 否 | Callback used for unsubscription. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

## onAnalysisAlbumChange

```TypeScript
onAnalysisAlbumChange(callback: Callback<AlbumChangeInfos>): void
```

监听智慧分析相册，并通过callback方式返回相册变化结果，可以注册多个callback。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-onAnalysisAlbumChange(callback: Callback<AlbumChangeInfos>): void--><!--Device-PhotoAccessHelper-onAnalysisAlbumChange(callback: Callback<AlbumChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | 是 | 回调函数，返回变更的智慧分析相册信息 [AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)。 <br>**注意：** <br>该接口可以注册多个不同的callback监听， [offAnalysisAlbumChange](#offanalysisalbumchange) 既可以关闭所有监听，也可以关闭指定callback监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper){
  console.info('onAnalysisAlbumChangeDemo.');

  try {
    // 注册onCallback1监听。
    phAccessHelper.onAnalysisAlbumChange(onCallback1);
    // 注册onCallback2监听。
    phAccessHelper.onAnalysisAlbumChange(onCallback2);
  } catch (error) {
    console.error('onAnalysisAlbumChangeDemo failed, errCode is', error);
  }
}
```

## onAnalysisPhotoChange

```TypeScript
onAnalysisPhotoChange(callback: Callback<PhotoAssetChangeInfos>): void
```

监听与智慧分析相册相关的媒体资产的变更情况，该变更携带智慧分析相册变更信息，当且仅当资产变更涉及智慧分析相册信息变更时，才会发送该资产变更通知， 通过callback返回资产变化结果，可以注册多个callback。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO and ohos.permission.MANAGE_PRIVATE_PHOTOS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-onAnalysisPhotoChange(callback: Callback<PhotoAssetChangeInfos>): void--><!--Device-PhotoAccessHelper-onAnalysisPhotoChange(callback: Callback<PhotoAssetChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | 是 | 回调函数，返回含对应智慧分析相册变更的媒体资产信息 [PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)。 <br>**注意：** <br>该接口可以注册多个不同的callback监听， [offAnalysisPhotoChange](#offanalysisphotochange) 既可以关闭所有监听，也可以关闭指定callback监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback1 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback2 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onAnalysisPhotoChangeDemo.');

  try {
    // 注册onCallback1监听。
    phAccessHelper.onAnalysisPhotoChange(onCallback1);
    // 注册onCallback2监听。
    phAccessHelper.onAnalysisPhotoChange(onCallback2);
  } catch (error) {
    console.error('onAnalysisPhotoChangeDemo failed, errCode is', error);
  }
}
```

## onHiddenAlbumChange

```TypeScript
onHiddenAlbumChange(callback: Callback<AlbumChangeInfos>): void
```

注册隐藏相册监听。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO and ohos.permission.MANAGE_PRIVATE_PHOTOS

<!--Device-PhotoAccessHelper-onHiddenAlbumChange(callback: Callback<AlbumChangeInfos>): void--><!--Device-PhotoAccessHelper-onHiddenAlbumChange(callback: Callback<AlbumChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | 是 | Callback used to notify the application of the changes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

## onHiddenPhotoChange

```TypeScript
onHiddenPhotoChange(callback: Callback<PhotoAssetChangeInfos>): void
```

注册监听隐藏的媒体资产。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO and ohos.permission.MANAGE_PRIVATE_PHOTOS

<!--Device-PhotoAccessHelper-onHiddenPhotoChange(callback: Callback<PhotoAssetChangeInfos>): void--><!--Device-PhotoAccessHelper-onHiddenPhotoChange(callback: Callback<PhotoAssetChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | 是 | Callback used to notify the application of the changes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

## onShareAlbumChange

```TypeScript
onShareAlbumChange(callback: Callback<AlbumChangeInfos>): void
```

监听共享相册的变化

**起始版本：** 26.1.0

**需要权限：** ohos.permission.MANAGE_SHARE_PHOTO

<!--Device-PhotoAccessHelper-onShareAlbumChange(callback: Callback<AlbumChangeInfos>): void--><!--Device-PhotoAccessHelper-onShareAlbumChange(callback: Callback<AlbumChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | 是 | Callback used to notify the application of the changes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

## onSharePhotoChange

```TypeScript
onSharePhotoChange(callback: Callback<PhotoAssetChangeInfos>): void
```

共享相册资产的监听

**起始版本：** 26.1.0

**需要权限：** ohos.permission.MANAGE_SHARE_PHOTO

<!--Device-PhotoAccessHelper-onSharePhotoChange(callback: Callback<PhotoAssetChangeInfos>): void--><!--Device-PhotoAccessHelper-onSharePhotoChange(callback: Callback<PhotoAssetChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | 是 | Callback used to notify the application of the changes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

## onTrashedAlbumChange

```TypeScript
onTrashedAlbumChange(callback: Callback<AlbumChangeInfos>): void
```

Subscribes to changes of the trashed album.

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-onTrashedAlbumChange(callback: Callback<AlbumChangeInfos>): void--><!--Device-PhotoAccessHelper-onTrashedAlbumChange(callback: Callback<AlbumChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | 是 | Callback used to notify the application of the changes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

## onTrashedPhotoChange

```TypeScript
onTrashedPhotoChange(callback: Callback<PhotoAssetChangeInfos>): void
```

注册回收站媒体资产监听。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-onTrashedPhotoChange(callback: Callback<PhotoAssetChangeInfos>): void--><!--Device-PhotoAccessHelper-onTrashedPhotoChange(callback: Callback<PhotoAssetChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | 是 | Callback used to notify the application of the changes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

## on('hiddenAlbumChange')

```TypeScript
on(type: 'hiddenAlbumChange', callback: Callback<AlbumChangeInfos>): void
```

注册'hiddenAlbumChange'监听隐藏相册，并通过callback方式返回相册变化结果，可以注册多个callback。

**起始版本：** 20

**需要权限：** ohos.permission.READ_IMAGEVIDEO and ohos.permission.MANAGE_PRIVATE_PHOTOS

<!--Device-PhotoAccessHelper-on(type: 'hiddenAlbumChange', callback: Callback<AlbumChangeInfos>): void--><!--Device-PhotoAccessHelper-on(type: 'hiddenAlbumChange', callback: Callback<AlbumChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hiddenAlbumChange' | 是 | 注册监听隐藏相册，取值为'hiddenAlbumChange'。注册完成后，有隐藏相册发生变化时，通过callback返回变更信息。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | 是 | 返回变更的隐藏相册信息 [AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)。 <br>**注意：** <br>该接口可以注册多个不同的callback监听， [off('hiddenAlbumChange')](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#offphotochange) 既可以关闭所有监听，也可以关闭指定callback监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper){
  console.info('onHiddenAlbumChangeDemo.');

  try {
    // 注册onCallback1监听。
    phAccessHelper.on('hiddenAlbumChange', onCallback1);
    // 注册onCallback2监听。
    phAccessHelper.on('hiddenAlbumChange', onCallback2);
  } catch (error) {
    console.error('onHiddenAlbumChangeDemo failed, errCode is', error);
  }
}
```

## on('hiddenPhotoChange')

```TypeScript
on(type: 'hiddenPhotoChange', callback: Callback<PhotoAssetChangeInfos>): void
```

注册'hiddenPhotoChange'监听隐藏的媒体资产，并通过callback方式返回隐藏资产变化结果，可以注册多个callback。

**起始版本：** 20

**需要权限：** ohos.permission.READ_IMAGEVIDEO and ohos.permission.MANAGE_PRIVATE_PHOTOS

<!--Device-PhotoAccessHelper-on(type: 'hiddenPhotoChange', callback: Callback<PhotoAssetChangeInfos>): void--><!--Device-PhotoAccessHelper-on(type: 'hiddenPhotoChange', callback: Callback<PhotoAssetChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'hiddenPhotoChange' | 是 | 注册监听隐藏资产，取值为'hiddenPhotoChange'。注册完成后，有隐藏资产发生变化时，通过callback返回变更信息。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | 是 | 返回变更的隐藏媒体资产信息 [PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md). <br>**注意：** <br>该接口可以注册多个不同的callback监听， [off('hiddenPhotoChange')](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#offphotochange) 既可以关闭所有监听，也可以关闭指定callback监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper){
  console.info('onHiddenPhotoChangeDemo.');

  try {
    // 注册onCallback1监听。
    phAccessHelper.on('hiddenPhotoChange', onCallback1);
    // 注册onCallback2监听。
    phAccessHelper.on('hiddenPhotoChange', onCallback2);
  } catch (error) {
    console.error('onHiddenPhotoChange failed, errCode is', error);
  }
}
```

## on('trashedAlbumChange')

```TypeScript
on(type: 'trashedAlbumChange', callback: Callback<AlbumChangeInfos>): void
```

注册'trashedAlbumChange'监听回收站相册，并通过callback方式返回相册变化结果，可以注册多个callback。

**起始版本：** 20

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-on(type: 'trashedAlbumChange', callback: Callback<AlbumChangeInfos>): void--><!--Device-PhotoAccessHelper-on(type: 'trashedAlbumChange', callback: Callback<AlbumChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'trashedAlbumChange' | 是 | 注册监听回收站相册，取值为'trashedAlbumChange'。注册完成后，有回收站相册发生变化时，通过callback返回变更信息。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)&gt; | 是 | 返回变更的相册信息 [AlbumChangeInfos](arkts-medialibrary-photoaccesshelper-albumchangeinfos-i.md)。 <br>**注意：** <br>该接口可以注册多个不同的callback监听， [off('trashedAlbumChange')](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#offphotochange) 既可以关闭所有监听，也可以关闭指定callback监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback1 success, changeData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.AlbumChangeInfos) => {
    console.info('onCallback2 success, changeData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onTrashedAlbumChangeDemo.');

  try {
    // 注册onCallback1监听。
    phAccessHelper.on('trashedAlbumChange', onCallback1);
    // 注册onCallback2监听。
    phAccessHelper.on('trashedAlbumChange', onCallback2);
  } catch (error) {
    console.error('onTrashedAlbumChangeDemo failed, errCode is', error);
  }
}
```

## on('trashedPhotoChange')

```TypeScript
on(type: 'trashedPhotoChange', callback: Callback<PhotoAssetChangeInfos>): void
```

注册'trashedPhotoChange'监听回收站的媒体资产，并通过callback方式返回回收站资产变化结果，可以注册多个callback。

**起始版本：** 20

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-on(type: 'trashedPhotoChange', callback: Callback<PhotoAssetChangeInfos>): void--><!--Device-PhotoAccessHelper-on(type: 'trashedPhotoChange', callback: Callback<PhotoAssetChangeInfos>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'trashedPhotoChange' | 是 | 注册监听回收站资产，取值为'trashedPhotoChange'。注册完成后，有回收站资产发生变化时，通过callback返回变更信息。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md)&gt; | 是 | 返回变更的回收站媒体资产信息 [PhotoAssetChangeInfos](arkts-medialibrary-photoaccesshelper-photoassetchangeinfos-i.md). <br>**注意：** <br>该接口可以注册多个不同的callback监听， [off('trashedPhotoChange')](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#offphotochange) 既可以关闭所有监听，也可以关闭指定callback监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) |  |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

let onCallback1 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback1 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}
let onCallback2 = (changeData: photoAccessHelper.PhotoAssetChangeInfos) => {
    console.info('onCallback2 success, changData: ' + JSON.stringify(changeData));
  // file had changed, do something.
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper, context: Context){
  console.info('onTrashedPhotoChangeDemo.');

  try {
    // 注册onCallback1监听。
    phAccessHelper.on('trashedPhotoChange', onCallback1);
    // 注册onCallback2监听。
    phAccessHelper.on('trashedPhotoChange', onCallback2);
  } catch (error) {
    console.error('onTrashedPhotoChangeDemo failed, errCode is', error);
  }
}
```

## query

```TypeScript
query(sql: string): Promise<ResultSet>
```

根据指定的SQL语句查询数据库数据，不支持写操作和多级查询。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_MEDIALIB_THUMB_DB

<!--Device-PhotoAccessHelper-query(sql: string): Promise<ResultSet>--><!--Device-PhotoAccessHelper-query(sql: string): Promise<ResultSet>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sql | string | 是 | 指定要执行的SQL语句。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ResultSet&gt; | Promise对象，如果操作成功，则返回ResultSet对象。如果操作失败，则抛出异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. <br>Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. <br>Possible causes: The SQL statement is abnormal. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('query');
  try {
    let ret: photoAccessHelper.ResultSet = await phAccessHelper.query('SELECT * from Photos');
    while (ret.goToNextRow()) {
      let row = ret.getRow();
      Object.entries(row).forEach((entry) => {
        const key = entry[0];
        const value = entry[1];
      });
    }
    ret.close();
  } catch (err) {
    console.error(`query failed with error: ${err.code}, ${err.message}`);
  }
}
```

## releaseDebugDatabase

```TypeScript
releaseDebugDatabase(betaIssueId: string, dbFd: int): Promise<void>
```

Release medialibrary database backup resources incluses closing backup database fd and deleting temporary backup database file which only works on beta device.

**起始版本：** 23

<!--Device-PhotoAccessHelper-releaseDebugDatabase(betaIssueId: string, dbFd: int): Promise<void>--><!--Device-PhotoAccessHelper-releaseDebugDatabase(betaIssueId: string, dbFd: int): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| betaIssueId | string | 是 | The beta issue id. |
| dbFd | int | 是 | The backup database fd. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Return void. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800201](../errorcode-medialibrary.md#23800201-不支持的操作类型) | Unsupported operation type, this api only works on beta device. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs. Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. The betaIssueId parameter is invalid, such as null, undefined or empty string. <br>2. The daFd parameter is invalid, such as out of range 0~1023. |

## removeFormInfo

```TypeScript
removeFormInfo(info: FormInfo, callback: AsyncCallback<void>): void
```

从数据库中删除绑定单个图片的图库卡片信息。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-removeFormInfo(info: FormInfo, callback: AsyncCallback<void>): void--><!--Device-PhotoAccessHelper-removeFormInfo(info: FormInfo, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | FormInfo | 是 | 图库卡片信息，包括图库卡片的id和卡片绑定的图片的uri。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | callback返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| 14000011 | System inner fail. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('removeFormInfoDemo');
  let info: photoAccessHelper.FormInfo = {
    // formId是一个由纯数字组成的字符串，移除卡片的时候uri填空即可。
    formId: "20230116123",
    uri: "",
  }

  phAccessHelper.removeFormInfo(info, async (err: BusinessError) => {
    if (err == undefined) {
      console.info('removeFormInfo success');
    } else {
      console.error(`removeFormInfo fail with error: ${err.code}, ${err.message}`);
    }
  });
}
```

## removeFormInfo

```TypeScript
removeFormInfo(info: FormInfo): Promise<void>
```

从数据库中删除绑定单个图片的图库卡片信息。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-removeFormInfo(info: FormInfo): Promise<void>--><!--Device-PhotoAccessHelper-removeFormInfo(info: FormInfo): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | FormInfo | 是 | 图库卡片信息，包括图库卡片的id和卡片绑定的图片的uri。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| 14000011 | System inner fail. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('removeFormInfoDemo');
  let info: photoAccessHelper.FormInfo = {
    // formId是一个由纯数字组成的字符串，移除卡片的时候uri填空即可。
    formId: "20230116123",
    uri: "",
  }

  phAccessHelper.removeFormInfo(info).then(() => {
    console.info('removeFormInfo successfully');
  }).catch((err: BusinessError) => {
    console.error(`removeFormInfo failed with error: ${err.code}, ${err.message}`);
  });
}
```

## removeGalleryFormInfo

```TypeScript
removeGalleryFormInfo(info: GalleryFormInfo): Promise<void>
```

从数据库中删除绑定一组图片的图库卡片信息。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-removeGalleryFormInfo(info: GalleryFormInfo): Promise<void>--><!--Device-PhotoAccessHelper-removeGalleryFormInfo(info: GalleryFormInfo): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [GalleryFormInfo](arkts-medialibrary-photoaccesshelper-galleryforminfo-i-sys.md) | 是 | 图库卡片信息，包括图库卡片的id、卡片绑定的图片或相册的uri集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| 14000011 | System inner fail. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('removeGalleryFormInfoDemo');
  let info: photoAccessHelper.GalleryFormInfo = {
    // formId是一个由纯数字组成的字符串，移除卡片时assertUris不填。
    formId: "20230116123"
  }

  phAccessHelper.removeGalleryFormInfo(info).then(() => {
    console.info('removeGalleryFormInfo successfully');
  }).catch((err: BusinessError) => {
    console.error(`removeGalleryFormInfo failed with error: ${err.code}, ${err.message}`);
  });
}
```

## saveFormInfo

```TypeScript
saveFormInfo(info: FormInfo, callback: AsyncCallback<void>): void
```

将绑定单个图片的图库卡片信息保存到数据库中。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-saveFormInfo(info: FormInfo, callback: AsyncCallback<void>): void--><!--Device-PhotoAccessHelper-saveFormInfo(info: FormInfo, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | FormInfo | 是 | 图库卡片信息，包括图库卡片的id和卡片绑定的图片的uri。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | callback返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| 14000011 | System inner fail. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('saveFormInfoDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
  let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();

  let info: photoAccessHelper.FormInfo = {
    // formId是一个由纯数字组成的字符串，uri为图库中存在的图片的uri信息，图库中无图片创建卡片时uri需为空字符串。
    formId : "20230116123",
    uri: photoAsset.uri,
  }

  phAccessHelper.saveFormInfo(info, async (err: BusinessError) => {
    if (err == undefined) {
      console.info('saveFormInfo success');
    } else {
      console.error(`saveFormInfo fail with error: ${err.code}, ${err.message}`);
    }
  });
}
```

## saveFormInfo

```TypeScript
saveFormInfo(info: FormInfo): Promise<void>
```

将绑定单个图片的图库卡片信息保存到数据库中。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-saveFormInfo(info: FormInfo): Promise<void>--><!--Device-PhotoAccessHelper-saveFormInfo(info: FormInfo): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | FormInfo | 是 | 图库卡片信息，包括图库卡片的id和卡片绑定的图片的uri。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| 14000011 | System inner fail. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('saveFormInfoDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
  let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();

  let info: photoAccessHelper.FormInfo = {
    // formId是一个由纯数字组成的字符串，uri为图库中存在的图片的uri信息，图库中无图片创建卡片时uri需为空字符串。
    formId: "20230116123",
    uri: photoAsset.uri,
  }

  phAccessHelper.saveFormInfo(info).then(() => {
    console.info('saveFormInfo successfully');
  }).catch((err: BusinessError) => {
    console.error(`saveFormInfo failed with error: ${err.code}, ${err.message}`);
  });
}
```

## saveGalleryFormInfo

```TypeScript
saveGalleryFormInfo(info: GalleryFormInfo): Promise<void>
```

将绑定一组图片的图库卡片信息保存到数据库中。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-saveGalleryFormInfo(info: GalleryFormInfo): Promise<void>--><!--Device-PhotoAccessHelper-saveGalleryFormInfo(info: GalleryFormInfo): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [GalleryFormInfo](arkts-medialibrary-photoaccesshelper-galleryforminfo-i-sys.md) | 是 | 图库卡片信息，包括图库卡片的id、卡片绑定的图片或相册的uri集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| 14000011 | System inner fail. |

**示例**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('saveGalleryFormInfoDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
  if (fetchResult === undefined) {
    console.error('fetchResult is undefined');
    return;
  }  
  let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
  if (photoAsset === undefined) {
    console.error('photoAsset is undefined');
    return;
  }
  let uriList: Array<string> = [
    photoAsset.uri,
  ];
  let info: photoAccessHelper.GalleryFormInfo = {
    // formId是一个由纯数字组成的字符串，assetUris为图库中存在的图片或者相册的uri信息集合。
    formId: "20230116123",
    assetUris: uriList,
  }

  phAccessHelper.saveGalleryFormInfo(info).then(() => {
    console.info('saveGalleryFormInfo successfully');
  }).catch((err: BusinessError) => {
    console.error(`saveGalleryFormInfo failed with error: ${err.code}, ${err.message}`);
  });
}
```

## setAssetCompatibleCapability

```TypeScript
setAssetCompatibleCapability(bundleName: string, capability: AssetCompatibleCapability): Promise<void>
```

根据bundleName配置资产兼容能力。开发者可以获取兼容性能力，并决定是否根据兼容性能力进行兼容性转换。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-setAssetCompatibleCapability(bundleName: string, capability: AssetCompatibleCapability): Promise<void>--><!--Device-PhotoAccessHelper-setAssetCompatibleCapability(bundleName: string, capability: AssetCompatibleCapability): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用的bundleName。 |
| capability | [AssetCompatibleCapability](arkts-medialibrary-photoaccesshelper-assetcompatiblecapability-i.md) | 是 | 资产兼容能力。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The bundleName or capability is invalid. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    let bundleName = "com.test.example";
    let capability : photoAccessHelper.AssetCompatibleCapability = {
        supportedHighResolution : true,
    };
    await phAccessHelper.setAssetCompatibleCapability(bundleName, capability);
  } catch (error) {
    console.error('failed to setAssetCompatibleCapability err', error);
  }
}
```

## setPhotoAlbumOrder

```TypeScript
setPhotoAlbumOrder(orderStyle: int, albumOrders: Array<AlbumOrder>): Promise<void>
```

设置系统、用户和来源相册的排序。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-setPhotoAlbumOrder(orderStyle: int, albumOrders: Array<AlbumOrder>): Promise<void>--><!--Device-PhotoAccessHelper-setPhotoAlbumOrder(orderStyle: int, albumOrders: Array<AlbumOrder>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| orderStyle | int | 是 | 选择相册的排序风格。 <br>0：Phone风格。1：PC风格。 |
| albumOrders | Array&lt;[AlbumOrder](arkts-medialibrary-photoaccesshelper-albumorder-i-sys.md)&gt; | 是 | 待设置的相册排序结果数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. <br>Possible causes: 1.The input parameter is not within the valid range. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('setPhotoAlbumOrderDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let orderStyle: number = 0;
  phAccessHelper.getPhotoAlbumOrder(orderStyle, fetchOptions).then( async (fetchResult) => {
    if (fetchResult === undefined) {
      console.error('getPhotoAlbumOrderPromise fetchResult is undefined');
      return;
    }
    let albumOrder: photoAccessHelper.AlbumOrder = await fetchResult.getFirstObject();
    albumOrder.albumOrder = 10;
    albumOrder.orderSection = 0;
    albumOrder.orderType = 1;
    albumOrder.orderStatus = 1;
    await phAccessHelper.setPhotoAlbumOrder(orderStyle, [albumOrder]);
    console.info('setPhotoAlbumOrderPromise successfully.');
    fetchResult.close();
  }).catch((err: BusinessError) => {
    console.error(`setPhotoAlbumOrderPromise failed with err: ${err.code}, ${err.message}`);
  });
}
```

## setPreferredCompatibleMode

```TypeScript
setPreferredCompatibleMode(bundleName: string, compatibleMode: PreferredCompatibleMode): Promise<void>
```

根据bundleName配置应用程序设置的首选兼容模式。使用Promise异步回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-setPreferredCompatibleMode(bundleName: string, compatibleMode: PreferredCompatibleMode): Promise<void>--><!--Device-PhotoAccessHelper-setPreferredCompatibleMode(bundleName: string, compatibleMode: PreferredCompatibleMode): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用捆绑包名称。 |
| compatibleMode | [PreferredCompatibleMode](arkts-medialibrary-photoaccesshelper-preferredcompatiblemode-e.md) | 是 | 资产兼容能力。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The bundleName is invalid, such as null, undefined and empty. |

**示例**

phAccessHelper的创建方法请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例用法。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

async function setPreferredCompatibleMode(
  phAccessHelper: photoAccessHelper.PhotoAccessHelper,
  bundleName: string,
  preferredCompatibleMode: photoAccessHelper.PreferredCompatibleMode
): Promise<void> {
  console.info('setPreferredCompatibleModeDemo');
  phAccessHelper.setPreferredCompatibleMode(bundleName, preferredCompatibleMode)
    .then(() => {
      console.info('setPreferredCompatibleMode successfully');
    })
    .catch((err: BusinessError) => {
      console.error(`The setPreferredCompatibleMode call failed. error: ${err.code}, ${err.message}`);
    });
}
```

## startAssetAnalysis

```TypeScript
startAssetAnalysis(type: AnalysisType, assetUris?: Array<string>): Promise<int>
```

启动资产分析服务。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-startAssetAnalysis(type: AnalysisType, assetUris?: Array<string>): Promise<int>--><!--Device-PhotoAccessHelper-startAssetAnalysis(type: AnalysisType, assetUris?: Array<string>): Promise<int>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [AnalysisType](arkts-medialibrary-photoaccesshelper-analysistype-e-sys.md) | 是 | 需要启动的智慧分析类型，仅支持ANALYSIS_SEARCH_INDEX。 |
| assetUris | Array&lt;string&gt; | 否 | 资产uri的数组。 <br>- 填写：仅分析指定资产。 <br>- 不填：全量分析。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象。服务的任务id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(context: Context) {
  console.info('startAssetAnalysisDemo');
  try {
    let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
    let uris = ["file://media/Photo/14/IMG_1729066473_013/IMG_20241016_122253.jpg",
                "file://media/Photo/68/IMG_1729033213_018/IMG_20241016_100082.jpg"];
    let taskId = await phAccessHelper.startAssetAnalysis(photoAccessHelper.AnalysisType.ANALYSIS_SEARCH_INDEX,
        uris);
    console.info('startAssetAnalysis success, taskId=' + taskId);
  } catch (err) {
    console.error('startAssetAnalysis failed, error=' + err);
  }
}
```

## startAssetAnalysisAsync

```TypeScript
startAssetAnalysisAsync(config: AnalysisConfig, callback: Callback<AnalysisResult>): Promise<int>
```

启动异步资产分析。使用callback异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-startAssetAnalysisAsync(config: AnalysisConfig, callback: Callback<AnalysisResult>): Promise<int>--><!--Device-PhotoAccessHelper-startAssetAnalysisAsync(config: AnalysisConfig, callback: Callback<AnalysisResult>): Promise<int>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [AnalysisConfig](arkts-medialibrary-photoaccesshelper-analysisconfig-i-sys.md) | 是 | 资产分析配置，config中的uris从 [PhotoAsset](arkts-file-photoaccesshelper.md)对象中获取。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[AnalysisResult](arkts-medialibrary-photoaccesshelper-analysisresult-i-sys.md)&gt; | 是 | 回调函数，用于返回资产分析结果信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，返回服务的任务ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. Unsupported or invalid types of config; <br>2. The types or uris array size of config exceed max value. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
let callback = (result: photoAccessHelper.AnalysisResult) => {
  console.info('startAssetAnalysisAsync callback result: ' + JSON.stringify(result));
};

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('startAssetAnalysisAsyncDemo');
  let config: photoAccessHelper.AnalysisConfig = {
    types: [photoAccessHelper.AnalysisType.ANALYSIS_SEARCH_INDEX],
    uris: ['file://media/Photo/14/IMG_1729066473_013/IMG_20241016_122253.jpg'],
    extraInfos: '{"trigger":"manual"}'
  };

  try {
    let taskId = await phAccessHelper.startAssetAnalysisAsync(config, callback);
    console.info('startAssetAnalysisAsync success, taskId=' + taskId);
  } catch (err) {
    console.error(`startAssetAnalysisAsync failed with error: ${err.code}, ${err.message}`);
  }
}
```

## startDeepOptimizeSpace

```TypeScript
startDeepOptimizeSpace(callback?: Callback<DeepOptimizeSpaceProgress>): Promise<void>
```

开启深度优化存储空间。使用Promise异步回调。 建议先调用[canPerformDeepOptimizeSpace](#canperformdeepoptimizespace)确认当前系统状态是否允许执行，仅在返回true时调用此接口。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-startDeepOptimizeSpace(callback?: Callback<DeepOptimizeSpaceProgress>): Promise<void>--><!--Device-PhotoAccessHelper-startDeepOptimizeSpace(callback?: Callback<DeepOptimizeSpaceProgress>): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DeepOptimizeSpaceProgress](arkts-medialibrary-photoaccesshelper-deepoptimizespaceprogress-i-sys.md)&gt; | 否 | 深度优化存储空间进度回调函数 默认值： null。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800201](../errorcode-medialibrary.md#23800201-不支持的操作类型) | Unsupported operation type, Possible causes: <br>1. Restarted repeatedly; <br>2. system is busy. Please try again later; |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    await phAccessHelper.startDeepOptimizeSpace((progress: photoAccessHelper.DeepOptimizeSpaceProgress) => {
      console.info(`startDeepOptimizeSpace progress: state=${progress.state}, progress=${progress.progress}`);
    });
    console.info('startDeepOptimizeSpace successfully');
  } catch (err) {
    console.error(`startDeepOptimizeSpace failed with error: ${err.code}, ${err.message}`);
  }
}
```

## startThumbnailCreationTask

```TypeScript
startThumbnailCreationTask(predicate: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<void>): int
```

按指定规则生成缩略图。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-startThumbnailCreationTask(predicate: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<void>): int--><!--Device-PhotoAccessHelper-startThumbnailCreationTask(predicate: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<void>): int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | dataSharePredicates.DataSharePredicates | 是 | 生成缩略图选项。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当成功时标识通知任务结束，err为undefined，否则为错误对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回缩略图生成任务id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

function testCallBack() {

}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();

  try {
    console.info('startThumbnailCreationTask test start');
    phAccessHelper.startThumbnailCreationTask(predicates, testCallBack);
  } catch (err) {
    console.error(`startThumbnailCreationTask failed, error: ${err.code}, ${err.message}`);
  }
}
```

## startThumbnailCreationTask

```TypeScript
startThumbnailCreationTask(predicate: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<void>, response: AsyncCallback<int>): int
```

根据指定规则生成缩略图。使用callback异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-startThumbnailCreationTask(predicate: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<void>, response: AsyncCallback<int>): int--><!--Device-PhotoAccessHelper-startThumbnailCreationTask(predicate: dataSharePredicates.DataSharePredicates, callback: AsyncCallback<void>, response: AsyncCallback<int>): int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicate | dataSharePredicates.DataSharePredicates | 是 | 用于生成缩略图的查询条件。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当操作成功完成时通知任务结束。 |
| response | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;int&gt; | 是 | 回调函数。返回是否有未生成的缩略图，返回1表示所有缩略图已生成完成，返回0表示未生成完成。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回缩略图生成任务id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: The predicates invalid. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

function testCallBack() {
  console.info(`startThumbnailCreationTask: 第一个回调`);
}

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();

  try {
    console.info('startThumbnailCreationTask test start');
    phAccessHelper.startThumbnailCreationTask(predicates, testCallBack, (err, state) =>{
        if(err) {
          console.error("error message: " + err?.message)
          console.error("error code: " + err?.code)
          return
        }
        console.info(`startThumbnailCreationTask: response state ${state}`);
      });
  } catch (err) {
    console.error(`startThumbnailCreationTask failed, error: ${err.code}, ${err.message}`);
  }
}
```

## stopAssetAnalysis

```TypeScript
stopAssetAnalysis(config: AnalysisConfig): void
```

停止资产分析。

**起始版本：** 24

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-stopAssetAnalysis(config: AnalysisConfig): void--><!--Device-PhotoAccessHelper-stopAssetAnalysis(config: AnalysisConfig): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [AnalysisConfig](arkts-medialibrary-photoaccesshelper-analysisconfig-i-sys.md) | 是 | 资产分析配置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. Unsupported or invalid AnalysisType of config; <br>2. The types or uris array size of config exceed max value. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('stopAssetAnalysisDemo');
  let config: photoAccessHelper.AnalysisConfig = {
    types: [photoAccessHelper.AnalysisType.ANALYSIS_SEARCH_INDEX],
    uris: ['file://media/Photo/14/IMG_1729066473_013/IMG_20241016_122253.jpg']
  };

  try {
    phAccessHelper.stopAssetAnalysis(config);
    console.info('stopAssetAnalysis success');
  } catch (err) {
    console.error(`stopAssetAnalysis failed with error: ${err.code}, ${err.message}`);
  }
}
```

## stopDeepOptimizeSpace

```TypeScript
stopDeepOptimizeSpace(): Promise<void>
```

停止深度优化存储空间。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAccessHelper-stopDeepOptimizeSpace(): Promise<void>--><!--Device-PhotoAccessHelper-stopDeepOptimizeSpace(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application. |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    await phAccessHelper.stopDeepOptimizeSpace();
    console.info('stopDeepOptimizeSpace successfully');
  } catch (err) {
    console.error(`stopDeepOptimizeSpace failed with error: ${err.code}, ${err.message}`);
  }
}
```

## stopThumbnailCreationTask

```TypeScript
stopThumbnailCreationTask(taskId: int): void
```

停止生成缩略图。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-PhotoAccessHelper-stopThumbnailCreationTask(taskId: int): void--><!--Device-PhotoAccessHelper-stopThumbnailCreationTask(taskId: int): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| taskId | int | 是 | 需要停止的缩略图生成任务id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error |

**示例**

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  try {
    console.info('stopThumbnailCreationTask test start');
    let taskId: number = 75983;
    phAccessHelper.stopThumbnailCreationTask(taskId);
  } catch (err) {
    console.error(`stopThumbnailCreationTask failed, error: ${err.code}, ${err.message}`);
  }
}
```

## updateGalleryFormInfo

```TypeScript
updateGalleryFormInfo(info: GalleryFormInfo): Promise<void>
```

更新既存的图库卡片的相关信息，并保存到数据库中。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_IMAGEVIDEO

<!--Device-PhotoAccessHelper-updateGalleryFormInfo(info: GalleryFormInfo): Promise<void>--><!--Device-PhotoAccessHelper-updateGalleryFormInfo(info: GalleryFormInfo): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [GalleryFormInfo](arkts-medialibrary-photoaccesshelper-galleryforminfo-i-sys.md) | 是 | 图库卡片信息，包括图库卡片的id、卡片绑定的图片或相册的uri集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| 14000011 | System inner fail. |

**示例**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('updateGalleryFormInfoDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOptions: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOptions);
  let photoAsset: photoAccessHelper.PhotoAsset = await fetchResult.getFirstObject();
  let photoAssetLast: photoAccessHelper.PhotoAsset = await fetchResult.getLastObject();
  let uriList: Array<string> = [
    photoAsset.uri,
    photoAssetLast.uri
  ];
  let info: photoAccessHelper.GalleryFormInfo = {
    // formId是一个由纯数字组成的字符串，assetUris为图库中存在的图片或者相册的uri信息集合。
    formId: "20230116123",
    assetUris: uriList,
  }

  phAccessHelper.updateGalleryFormInfo(info).then(() => {
    console.info('updateGalleryFormInfo successfully');
  }).catch((err: BusinessError) => {
    console.error(`updateGalleryFormInfo failed with error: ${err.code}, ${err.message}`);
  });
}
```

