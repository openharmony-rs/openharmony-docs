# CloudFileCache

云盘文件缓存对象，用来支撑文件管理应用原文件下载流程。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## cleanCache

```TypeScript
cleanCache(uri: string): void
```

同步方法删除文件缓存。

**起始版本：** 11

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待删除缓存文件的uri。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system applicationuses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are leftunspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13900002 | No such file or directory. |
| 14000002 | Invalid uri. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache("com.ohos.demo");
let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);

try {
  fileCache.cleanCache(uri);
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error(`clean cache failed with error message: ${error.message}, error code: ${error.code}`);
} 


```

## constructor

```TypeScript
constructor(bundleName: string)
```

A constructor used to create a CloudFileCache object.

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Name of the bundle that need to start download task and subscribes downloadprogress. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |

**示例：**

```TypeScript
let fileCache = new cloudSync.CloudFileCache("com.ohos.demo");

```

## getDownloadList

```TypeScript
getDownloadList(uris: Array<string>): Promise<Array<DownloadProgress>>
```

获取文件下载进度列表。使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uris | Array&lt;string&gt; | 是 | 待查询下载进度的文件URI数组，数组长度取值范围[1,100]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;DownloadProgress&gt;&gt; | - Promise对象，返回文件下载进度列表的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| 13900010 | Try again. |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified. 2.The length of the input parameter exceeds the upper limit.<br>3.The input parameter contains an invalid uri. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let fileCache = new cloudSync.CloudFileCache();
let path1 = "/data/storage/el2/cloud/1.txt";
let path2 = "/data/storage/el2/cloud/2.txt";
let uri1 = fileUri.getUriFromPath(path1);
let uri2 = fileUri.getUriFromPath(path2);
let uriArray = [uri1, uri2];

try {
  fileCache.getDownloadList(uriArray).then((downloadList: Array<cloudSync.DownloadProgress>) => {
    console.info("get download list successfully");
    for (let i = 0; i < downloadList.length; i++) {
      console.info("download progress - uri: ".concat(downloadList[i].uri, ", state: ").concat(downloadList[i].state.toString()));
      console.info("processed: ".concat(downloadList[i].processed.toString(), ", size: ").concat(downloadList[i].size.toString()));
      console.info("error: ".concat(downloadList[i].error.toString()));
    }
  }).catch((error: BusinessError) => {
    console.error("get download list failed with error message: " + error.message + ", error code: " + error.code);
  });
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("get download list failed with error message: " + error.message + ", error code: " + error.code);
}

```

