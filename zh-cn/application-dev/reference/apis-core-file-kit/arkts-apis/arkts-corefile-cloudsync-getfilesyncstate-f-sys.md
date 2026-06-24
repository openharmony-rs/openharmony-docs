# getFileSyncState（系统接口）

## getFileSyncState

```TypeScript
function getFileSyncState(uri: Array<string>): Promise<Array<FileSyncState>>
```

�첽������ȡ�ļ�ͬ��״̬��ʹ��Promise�첽�ص���

**起始版本：** 11

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | Array&lt;string&gt; | 是 | ����ȡͬ��״̬��uri�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;FileSyncState&gt;&gt; | Promise���󣬷����ļ�ͬ��״̬�Ľ���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed, application which is not a system application uses<br/>system API. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [14000002](../../errorcode-universal.md#14000002-Invalid) | Invalid uri. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let uris: Array<string> = ["file://uri"];
cloudSync.getFileSyncState(uris).then((syncStates: Array<cloudSync.FileSyncState>) => {
  for(let i = 0, len = syncStates.length; i < len; i++){
    console.info("get file sync state successfully" + syncStates[i]);
  }
}).catch((err: BusinessError) => {
  console.error("get file sync state failed with error message: " + err.message + ", error code: " + err.code);
});


```


## getFileSyncState

```TypeScript
function getFileSyncState(uri: Array<string>, callback: AsyncCallback<Array<FileSyncState>>): void
```

�첽������ȡ�ļ�ͬ��״̬��ʹ��callback�첽�ص���

**起始版本：** 11

**需要权限：** ohos.permission.CLOUDFILE_SYNC

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | Array&lt;string&gt; | 是 | ����ȡͬ��״̬��uri�� |
| callback | AsyncCallback&lt;Array&lt;FileSyncState&gt;&gt; | 是 | �ص��������첽��ȡ�ļ�״̬�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed, application which is not a system application uses<br/>system API. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [14000002](../../errorcode-universal.md#14000002-Invalid) | Invalid uri. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let uris: Array<string> = ["file://uri"];
cloudSync.getFileSyncState(uris, (err: BusinessError, syncStates: Array<cloudSync.FileSyncState>) => {
  if (err) {
    console.error("get file sync state with error message: " + err.message + ", error code: " + err.code);
  } else {
    for(let i = 0, len = syncStates.length; i < len; i++){
      console.info("get file sync state successfully" + syncStates[i]);
  }
  }
});

```


## getFileSyncState

```TypeScript
function getFileSyncState(uri: string): FileSyncState
```

��ȡ�ļ�ͬ��״̬��

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | �������ļ�uri�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FileSyncState | ���ظ����ļ���ͬ��״̬�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed, application which is not a system application uses<br/>system API. |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [13900004](../../errorcode-universal.md#13900004-Interrupted) | Interrupted system call |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied by the file system |
| [13900031](../../errorcode-universal.md#13900031-Function) | Function not implemented |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |
| [14000002](../../errorcode-universal.md#14000002-Invalid) | Invalid uri. |

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

