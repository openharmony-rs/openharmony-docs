# getFileSyncState（系统接口）

## 导入模块

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

<a id="getfilesyncstate"></a>
## getFileSyncState

```TypeScript
function getFileSyncState(uri: Array<string>): Promise<Array<FileSyncState>>
```

异步方法获取文件同步状态。使用Promise异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-cloudSync-function getFileSyncState(uri: Array<string>): Promise<Array<FileSyncState>>--><!--Device-cloudSync-function getFileSyncState(uri: Array<string>): Promise<Array<FileSyncState>>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | Array&lt;string&gt; | 是 | 待获取同步状态的uri。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;FileSyncState&gt;&gt; | Promise对象，返回文件同步状态的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13900002 | No such file or directory. |
| 14000002 | Invalid uri. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let uris: Array<string> = ["file://uri"];
cloudSync.getFileSyncState(uris).then((syncStates: Array<cloudSync.FileSyncState>) => {
  for(let i = 0, len = syncStates.length; i < len; i++){
    console.info("get file sync state successfully" + syncStates[i]);
  }
}).catch((err: BusinessError) => {
  console.error(`get file sync state failed with error message: ${err.message}, error code: ${err.code}`);
});


```


<a id="getfilesyncstate-1"></a>
## getFileSyncState

```TypeScript
function getFileSyncState(uri: Array<string>, callback: AsyncCallback<Array<FileSyncState>>): void
```

异步方法获取文件同步状态。使用callback异步回调。

**起始版本：** 11

**需要权限：** ohos.permission.CLOUDFILE_SYNC

<!--Device-cloudSync-function getFileSyncState(uri: Array<string>, callback: AsyncCallback<Array<FileSyncState>>): void--><!--Device-cloudSync-function getFileSyncState(uri: Array<string>, callback: AsyncCallback<Array<FileSyncState>>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | Array&lt;string&gt; | 是 | 待获取同步状态的uri。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;FileSyncState&gt;&gt; | 是 | 回调函数。异步获取文件状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13600001 | IPC error. |
| 13900002 | No such file or directory. |
| 14000002 | Invalid uri. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let uris: Array<string> = ["file://uri"];
cloudSync.getFileSyncState(uris, (err: BusinessError, syncStates: Array<cloudSync.FileSyncState>) => {
  if (err) {
    console.error(`get file sync state with error message: ${err.message}, error code: ${err.code}`);
  } else {
    for(let i = 0, len = syncStates.length; i < len; i++){
      console.info("get file sync state successfully" + syncStates[i]);
  }
  }
});

```


<a id="getfilesyncstate-2"></a>
## getFileSyncState

```TypeScript
function getFileSyncState(uri: string): FileSyncState
```

获取文件同步状态。

**起始版本：** 12

<!--Device-cloudSync-function getFileSyncState(uri: string): FileSyncState--><!--Device-cloudSync-function getFileSyncState(uri: string): FileSyncState-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待下载文件uri。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FileSyncState](arkts-corefile-cloudsync-filesyncstate-e-sys.md) | 返回给定文件的同步状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission verification failed, application which is not a system application uses system API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13900002 | No such file or directory. |
| 13900004 | Interrupted system call |
| 13900010 | Try again |
| 13900012 | Permission denied by the file system |
| 13900031 | Function not implemented |
| 13900042 | Unknown error |
| 14000002 | Invalid uri. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);
try {
  let state = cloudSync.getFileSyncState(uri);
} catch (err) {
  let error:BusinessError = err as BusinessError;
  console.error("getFileSyncStatefailed with error: " + JSON.stringify(error));
}

```

