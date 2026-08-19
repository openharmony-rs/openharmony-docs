# CloudMediaAssetManager（系统接口）

云端媒体资产管理类，该类用于管理云端资产的下载任务，以及删除云端资产在本地的数据和文件。

**起始版本：** 23

<!--Device-photoAccessHelper-class CloudMediaAssetManager--><!--Device-photoAccessHelper-class CloudMediaAssetManager-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## cancelDownloadCloudMedia

```TypeScript
cancelDownloadCloudMedia(): Promise<void>
```

取消云端媒体资产下载任务。

**起始版本：** 23

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

<!--Device-CloudMediaAssetManager-cancelDownloadCloudMedia(): Promise<void>--><!--Device-CloudMediaAssetManager-cancelDownloadCloudMedia(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; 2 <br>. The file system is abnormal; <br>3. The IPC request timed out. |

**示例**

```TypeScript
async function example(context: Context) {
  console.info('cancelDownloadCloudMediaDemo');
  try {
    let cloudMediaAssetManagerInstance: photoAccessHelper.CloudMediaAssetManager
      = photoAccessHelper.CloudMediaAssetManager.getCloudMediaAssetManagerInstance(context);
    await cloudMediaAssetManagerInstance.cancelDownloadCloudMedia();
  } catch (err) {
    console.error(`cancelDownloadCloudMediaDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## cancelDownloadSpecificCloudMedia

```TypeScript
cancelDownloadSpecificCloudMedia(assetUris: string[] | null): Promise<void>
```

取消云端媒体资产批量下载任务。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-CloudMediaAssetManager-cancelDownloadSpecificCloudMedia(assetUris: string[] | null): Promise<void>--><!--Device-CloudMediaAssetManager-cancelDownloadSpecificCloudMedia(assetUris: string[] | null): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assetUris | string[] \| null | 是 | 需要取消下载的原图和视频的uri列表。 <br>当传入null、undefined和空列表时，表示已存在的所有批量下载任务。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: The assetUris array size is bigger than 500. |

**示例**

```TypeScript
async function example(context: Context) {
  console.info('CancelDownloadSpecificCloudMediaDemo');
  try {
    let assetURIs: Array<string> = [
       'file://media/Photo/12/IMG_1755046662_091/IMG_20250801_175331.jpg'];
    let cloudMediaAssetManagerInstance: photoAccessHelper.CloudMediaAssetManager
      = photoAccessHelper.CloudMediaAssetManager.getCloudMediaAssetManagerInstance(context);
    await cloudMediaAssetManagerInstance.cancelDownloadSpecificCloudMedia(assetURIs);
  } catch (err) {
    console.error(`failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getCloudMediaAssetManagerInstance

```TypeScript
static getCloudMediaAssetManagerInstance(context: Context): CloudMediaAssetManager
```

获取云端媒体资产管理类实例。

**起始版本：** 14

<!--Device-CloudMediaAssetManager-static getCloudMediaAssetManagerInstance(context: Context): CloudMediaAssetManager--><!--Device-CloudMediaAssetManager-static getCloudMediaAssetManagerInstance(context: Context): CloudMediaAssetManager-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | 传入Ability实例的Context。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CloudMediaAssetManager](arkts-medialibrary-photoaccesshelper-cloudmediaassetmanager-c-sys.md) | 返回云端媒体资产管理类实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**示例**

```TypeScript
async function example(context: Context) {
  console.info('getCloudMediaAssetManagerInstanceDemo');
  try {
    let cloudMediaAssetManagerInstance: photoAccessHelper.CloudMediaAssetManager
      = photoAccessHelper.CloudMediaAssetManager.getCloudMediaAssetManagerInstance(context);
    await cloudMediaAssetManagerInstance.pauseDownloadCloudMedia();
  } catch (err) {
    console.error(`getCloudMediaAssetManagerInstanceDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getCloudMediaAssetManagerInstance

```TypeScript
static getCloudMediaAssetManagerInstance(context: Context): CloudMediaAssetManager | null
```

获取云端媒体资产管理类实例。

**起始版本：** 23

<!--Device-CloudMediaAssetManager-static getCloudMediaAssetManagerInstance(context: Context): CloudMediaAssetManager | null--><!--Device-CloudMediaAssetManager-static getCloudMediaAssetManagerInstance(context: Context): CloudMediaAssetManager | null-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | 是 | Obtains a CloudMediaAssetManager instance. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CloudMediaAssetManager](arkts-medialibrary-photoaccesshelper-cloudmediaassetmanager-c-sys.md) | Returns cloud media asset manager instance, if the operation fails, returns null |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |

## getCloudMediaAssetStatus

```TypeScript
getCloudMediaAssetStatus(): Promise<CloudMediaAssetStatus>
```

查询云端媒体资产下载任务状态。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-CloudMediaAssetManager-getCloudMediaAssetStatus(): Promise<CloudMediaAssetStatus>--><!--Device-CloudMediaAssetManager-getCloudMediaAssetStatus(): Promise<CloudMediaAssetStatus>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[CloudMediaAssetStatus](arkts-medialibrary-photoaccesshelper-cloudmediaassetstatus-i-sys.md)&gt; | Promise对象，返回云端媒体资产下载任务状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**示例**

```TypeScript
async function example(context: Context) {
  console.info('getCloudMediaAssetStatusDemo');
  try {
    let cloudMediaAssetManagerInstance: photoAccessHelper.CloudMediaAssetManager
      = photoAccessHelper.CloudMediaAssetManager.getCloudMediaAssetManagerInstance(context);
    const cloudMediaAssetStatus: photoAccessHelper.CloudMediaAssetStatus = await cloudMediaAssetManagerInstance.getCloudMediaAssetStatus();
    let taskStatus = cloudMediaAssetStatus.taskStatus;
    let taskInfo = cloudMediaAssetStatus.taskInfo;
    let errorCode = cloudMediaAssetStatus.errorCode;
    let message = `taskStatus: ${taskStatus}, taskInfo: ${taskInfo}, errorCode: ${errorCode}`;
    console.info(message);
  } catch (err) {
    console.error(`getCloudMediaAssetStatusDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## offDownloadProgressChange

```TypeScript
offDownloadProgressChange(callback?: Callback<CloudAssetDownloadProgressInfo>): void
```

取消监听云端媒体资产批量下载进度相关通知。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-CloudMediaAssetManager-offDownloadProgressChange(callback?: Callback<CloudAssetDownloadProgressInfo>): void--><!--Device-CloudMediaAssetManager-offDownloadProgressChange(callback?: Callback<CloudAssetDownloadProgressInfo>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[CloudAssetDownloadProgressInfo](arkts-medialibrary-photoaccesshelper-cloudassetdownloadprogressinfo-i-sys.md)&gt; | 否 | 取消监听 onDownloadProgressChange注册指定的callback监听；不填时，则取消所有进度相关监听。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |

**示例**

```TypeScript
async function example(context: Context) {
  console.info('OffDownloadProgressChangeDemo');
  try {
    let cloudMediaAssetManagerInstance: photoAccessHelper.CloudMediaAssetManager
      = photoAccessHelper.CloudMediaAssetManager.getCloudMediaAssetManagerInstance(context);
    cloudMediaAssetManagerInstance.offDownloadProgressChange();
  } catch (err) {
    console.error(`failed with error: ${err.code}, ${err.message}`);
  }
}
```

## onDownloadProgressChange

```TypeScript
onDownloadProgressChange(callback: Callback<CloudAssetDownloadProgressInfo>): void
```

监听云端媒体资产批量下载进度。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-CloudMediaAssetManager-onDownloadProgressChange(callback: Callback<CloudAssetDownloadProgressInfo>): void--><!--Device-CloudMediaAssetManager-onDownloadProgressChange(callback: Callback<CloudAssetDownloadProgressInfo>): void-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[CloudAssetDownloadProgressInfo](arkts-medialibrary-photoaccesshelper-cloudassetdownloadprogressinfo-i-sys.md)&gt; | 是 | 注册指定的callback监听，回调返回批量下载进度相关通知。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |

**示例**

```TypeScript
let onCallback = (changeData: photoAccessHelper.CloudAssetDownloadProgressInfo) => {
  console.info('batchdownload downloadProgressChange onCallback success, changData: ' + JSON.stringify(changeData));
}
async function example(context: Context) {
  console.info('OnDownloadProgressChangeDemo');
  try {
      let cloudMediaAssetManagerInstance: photoAccessHelper.CloudMediaAssetManager
        = photoAccessHelper.CloudMediaAssetManager.getCloudMediaAssetManagerInstance(context);
      // 注册onCallback监听。
      cloudMediaAssetManagerInstance.onDownloadProgressChange(onCallback);
  } catch (err) {
    console.error(`failed with error: ${err.code}, ${err.message}`);
  }
}
```

## pauseDownloadCloudMedia

```TypeScript
pauseDownloadCloudMedia(): Promise<void>
```

暂停云端媒体资产下载任务。

**起始版本：** 23

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

<!--Device-CloudMediaAssetManager-pauseDownloadCloudMedia(): Promise<void>--><!--Device-CloudMediaAssetManager-pauseDownloadCloudMedia(): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**示例**

```TypeScript
async function example(context: Context) {
  console.info('pauseDownloadCloudMediaDemo');
  try {
    let cloudMediaAssetManagerInstance: photoAccessHelper.CloudMediaAssetManager
      = photoAccessHelper.CloudMediaAssetManager.getCloudMediaAssetManagerInstance(context);
    await cloudMediaAssetManagerInstance.pauseDownloadCloudMedia();
  } catch (err) {
    console.error(`pauseDownloadCloudMediaDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## pauseDownloadSpecificCloudMedia

```TypeScript
pauseDownloadSpecificCloudMedia(assetUris: string[] | null): Promise<void>
```

暂停云端媒体资产批量下载任务。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-CloudMediaAssetManager-pauseDownloadSpecificCloudMedia(assetUris: string[] | null): Promise<void>--><!--Device-CloudMediaAssetManager-pauseDownloadSpecificCloudMedia(assetUris: string[] | null): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assetUris | string[] \| null | 是 | 需要暂停下载的原图和视频的uri列表。 <br>当传入null、undefined和空列表时，表示已存在的所有批量下载任务。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: The assetUris array size is bigger than 500. |

**示例**

```TypeScript
async function example(context: Context) {
  console.info('PauseDownloadSpecificCloudMediaDemo');
  try {
    let assetURIs: Array<string> = [
       'file://media/Photo/12/IMG_1755046662_091/IMG_20250801_175331.jpg'];
    let cloudMediaAssetManagerInstance: photoAccessHelper.CloudMediaAssetManager
      = photoAccessHelper.CloudMediaAssetManager.getCloudMediaAssetManagerInstance(context);
    await cloudMediaAssetManagerInstance.pauseDownloadSpecificCloudMedia(assetURIs);
  } catch (err) {
    console.error(`failed with error: ${err.code}, ${err.message}`);
  }
}
```

## queryDownloadSpecificCloudMediaDetails

```TypeScript
queryDownloadSpecificCloudMediaDetails(predicates: dataSharePredicates.DataSharePredicates): Promise<CloudAssetDownloadStatus>
```

查询云端媒体资产批量下载任务信息。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-CloudMediaAssetManager-queryDownloadSpecificCloudMediaDetails(predicates: dataSharePredicates.DataSharePredicates): Promise<CloudAssetDownloadStatus>--><!--Device-CloudMediaAssetManager-queryDownloadSpecificCloudMediaDetails(predicates: dataSharePredicates.DataSharePredicates): Promise<CloudAssetDownloadStatus>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | dataSharePredicates.DataSharePredicates | 是 | 谓词查询，显示过滤条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[CloudAssetDownloadStatus](arkts-medialibrary-photoaccesshelper-cloudassetdownloadstatus-i-sys.md)&gt; | Promise对象，返回下载任务信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |

**示例**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

async function example(context: Context) {
  console.info('QueryDownloadSpecificCloudMediaDetailsDemo');
  try {
    let cloudMediaAssetManagerInstance: photoAccessHelper.CloudMediaAssetManager
      = photoAccessHelper.CloudMediaAssetManager.getCloudMediaAssetManagerInstance(context);
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    predicates.orderByAsc("file_id");
    let taskListStatus : photoAccessHelper.CloudAssetDownloadStatus =
       await cloudMediaAssetManagerInstance.queryDownloadSpecificCloudMediaDetails(predicates);
  } catch (err) {
    console.error(`failed with error: ${err.code}, ${err.message}`);
  }
}
```

## queryDownloadSpecificCloudMediaTaskCount

```TypeScript
queryDownloadSpecificCloudMediaTaskCount(predicates: dataSharePredicates.DataSharePredicates): Promise<int>
```

查询云端媒体资产批量下载任务总量。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-CloudMediaAssetManager-queryDownloadSpecificCloudMediaTaskCount(predicates: dataSharePredicates.DataSharePredicates): Promise<int>--><!--Device-CloudMediaAssetManager-queryDownloadSpecificCloudMediaTaskCount(predicates: dataSharePredicates.DataSharePredicates): Promise<int>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| predicates | dataSharePredicates.DataSharePredicates | 是 | 谓词查询，显示过滤条件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | Promise对象，返回总量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |

**示例**

```TypeScript
import { dataSharePredicates } from '@kit.ArkData'

async function example(context: Context) {
  console.info('QueryDownloadSpecificCloudMediaTaskCountDemo');
  try {
    let cloudMediaAssetManagerInstance: photoAccessHelper.CloudMediaAssetManager
      = photoAccessHelper.CloudMediaAssetManager.getCloudMediaAssetManagerInstance(context);
    let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
    predicates.orderByAsc("file_id");
    let count : number =
       await cloudMediaAssetManagerInstance.queryDownloadSpecificCloudMediaTaskCount(predicates);
  } catch (err) {
    console.error(`failed with error: ${err.code}, ${err.message}`);
  }
}
```

## resumeDownloadSpecificCloudMedia

```TypeScript
resumeDownloadSpecificCloudMedia(assetUris: string[] | null): Promise<void>
```

恢复云端媒体资产批量下载任务。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-CloudMediaAssetManager-resumeDownloadSpecificCloudMedia(assetUris: string[] | null): Promise<void>--><!--Device-CloudMediaAssetManager-resumeDownloadSpecificCloudMedia(assetUris: string[] | null): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assetUris | string[] \| null | 是 | 需要恢复下载的原图和视频的uri列表。 <br>当传入null、undefined和空列表时，表示已存在的所有批量下载任务。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: The assetUris array size is bigger than 500. |

**示例**

```TypeScript
async function example(context: Context) {
  console.info('ResumeDownloadSpecificCloudMediaDemo');
  try {
    let assetURIs: Array<string> = [
       'file://media/Photo/12/IMG_1755046662_091/IMG_20250801_175331.jpg'];
    let cloudMediaAssetManagerInstance: photoAccessHelper.CloudMediaAssetManager
      = photoAccessHelper.CloudMediaAssetManager.getCloudMediaAssetManagerInstance(context);
    await cloudMediaAssetManagerInstance.resumeDownloadSpecificCloudMedia(assetURIs);
  } catch (err) {
    console.error(`failed with error: ${err.code}, ${err.message}`);
  }
}
```

## retainCloudMediaAsset

```TypeScript
retainCloudMediaAsset(retainType: CloudMediaRetainType): Promise<void>
```

删除云端媒体资产在本地的元数据和文件。

**起始版本：** 23

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

<!--Device-CloudMediaAssetManager-retainCloudMediaAsset(retainType: CloudMediaRetainType): Promise<void>--><!--Device-CloudMediaAssetManager-retainCloudMediaAsset(retainType: CloudMediaRetainType): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| retainType | [CloudMediaRetainType](arkts-medialibrary-photoaccesshelper-cloudmediaretaintype-e-sys.md) | 是 | 云端媒体资产的删除方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**示例**

```TypeScript
async function example(context: Context) {
  console.info('retainCloudMediaAssetDemo');
  try {
    let cloudMediaAssetManagerInstance: photoAccessHelper.CloudMediaAssetManager
      = photoAccessHelper.CloudMediaAssetManager.getCloudMediaAssetManagerInstance(context);
    await cloudMediaAssetManagerInstance.retainCloudMediaAsset(photoAccessHelper.CloudMediaRetainType.RETAIN_FORCE);
  } catch (err) {
    console.error(`retainCloudMediaAssetDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## startDownloadCloudMedia

```TypeScript
startDownloadCloudMedia(downloadType: CloudMediaDownloadType): Promise<void>
```

开始或恢复云端媒体资产下载任务。

**起始版本：** 23

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

<!--Device-CloudMediaAssetManager-startDownloadCloudMedia(downloadType: CloudMediaDownloadType): Promise<void>--><!--Device-CloudMediaAssetManager-startDownloadCloudMedia(downloadType: CloudMediaDownloadType): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| downloadType | [CloudMediaDownloadType](arkts-medialibrary-photoaccesshelper-cloudmediadownloadtype-e-sys.md) | 是 | 云端媒体资产的下载方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，返回void。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| 14000011 | Internal system error. It is recommended to retry and check the logs. <br>Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |

**示例**

```TypeScript
async function example(context: Context) {
  console.info('startDownloadCloudMediaDemo');
  try {
    let cloudMediaAssetManagerInstance: photoAccessHelper.CloudMediaAssetManager
      = photoAccessHelper.CloudMediaAssetManager.getCloudMediaAssetManagerInstance(context);
    await cloudMediaAssetManagerInstance.startDownloadCloudMedia(photoAccessHelper.CloudMediaDownloadType.DOWNLOAD_FORCE);
  } catch (err) {
    console.error(`startDownloadCloudMediaDemo failed with error: ${err.code}, ${err.message}`);
  }
}
```

## startDownloadSpecificCloudMedia

```TypeScript
startDownloadSpecificCloudMedia(assetUris: string[]): Promise<Map<string, CloudAssetDownloadCode>>
```

开始云端媒体资产批量下载任务。使用Promise异步回调。

**起始版本：** 23

**需要权限：** ohos.permission.READ_IMAGEVIDEO

<!--Device-CloudMediaAssetManager-startDownloadSpecificCloudMedia(assetUris: string[]): Promise<Map<string, CloudAssetDownloadCode>>--><!--Device-CloudMediaAssetManager-startDownloadSpecificCloudMedia(assetUris: string[]): Promise<Map<string, CloudAssetDownloadCode>>-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| assetUris | string[] | 是 | 需要下载的原图和视频的uri列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Map&lt;string, [CloudAssetDownloadCode](arkts-medialibrary-photoaccesshelper-cloudassetdownloadcode-e-sys.md)&gt;&gt; | Promise对象，返回uri列表对应的下载任务是否添加成功。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes: <br>1. Database corrupted; <br>2. The file system is abnormal; <br>3. The IPC request timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes: <br>1. The assetUris array is empty; <br>2. The assetUris array size is bigger than 500. |

**示例**

```TypeScript
async function example(context: Context) {
  console.info('StartDownloadSpecificCloudMediaDemo');
  try {
    let assetURIs: Array<string> = [
       'file://media/Photo/12/IMG_1755046662_091/IMG_20250801_175331.jpg'];
    let cloudMediaAssetManagerInstance: photoAccessHelper.CloudMediaAssetManager
      = photoAccessHelper.CloudMediaAssetManager.getCloudMediaAssetManagerInstance(context);
    let taskRespMap : Map<string, photoAccessHelper.CloudAssetDownloadCode> =
      await cloudMediaAssetManagerInstance.startDownloadSpecificCloudMedia(assetURIs);
  } catch (err) {
    console.error(`failed with error: ${err.code}, ${err.message}`);
  }
}
```

