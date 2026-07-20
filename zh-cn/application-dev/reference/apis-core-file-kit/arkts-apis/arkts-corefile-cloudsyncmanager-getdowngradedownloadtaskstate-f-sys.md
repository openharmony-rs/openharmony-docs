# getDowngradeDownloadTaskState（系统接口）

## 导入模块

```TypeScript
import { cloudSyncManager } from '@kit.CoreFileKit';
```

<a id="getdowngradedownloadtaskstate"></a>
## getDowngradeDownloadTaskState

```TypeScript
function getDowngradeDownloadTaskState(bundleNames: Array<string>): Promise<Array<DownloadProgress>>
```

查询接入云盘的应用的全量下载任务状态。使用Promise异步回调。

由于返回的DownloadProgress对象中不包含包名信息，因此在批量查询多个应用时，调用方需自行记录应用包名。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDFILE_SYNC_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-cloudSyncManager-function getDowngradeDownloadTaskState(bundleNames: Array<string>): Promise<Array<DownloadProgress>>--><!--Device-cloudSyncManager-function getDowngradeDownloadTaskState(bundleNames: Array<string>): Promise<Array<DownloadProgress>>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleNames | Array&lt;string&gt; | 是 | 需要查询的应用包名数组，每个元素为应用的包名字符串，包名数组大小上限为20个。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;DownloadProgress&gt;&gt; | - Promise对象，返回查询的全量下载任务的状态信息数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13900010 | Try again. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameter are left unspecified. 2.The length of the input parameter exceeds the upper limit.<br>3.The input parameter contains an invalid bundleName. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let bundles: Array<string> = ['com.example.app1', 'com.example.app2'];
cloudSyncManager.getDowngradeDownloadTaskState(bundles).then((results: Array<cloudSyncManager.DownloadProgress>) => {
  results.forEach((item) => {
    console.info(`state: ${item.state}, downloadedSize: ${item.downloadedSize}, totalSize: ${item.totalSize}`);
    console.info(`successfulCount: ${item.successfulCount}, failedCount: ${item.failedCount}, totalCount: ${item.totalCount}`);
    if (item.state == cloudSyncManager.DownloadState.STOPPED) {
      console.info(`stopReason: ${item.stopReason}`);
    }
  });
}).catch((err: BusinessError) => {
  console.error(`getDowngradeDownloadTaskState failed, code: ${err.code}, message: ${err.message}`);
});

```

