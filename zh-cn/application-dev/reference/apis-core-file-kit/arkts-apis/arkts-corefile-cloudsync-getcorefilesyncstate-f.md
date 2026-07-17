# getCoreFileSyncState

## 导入模块

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## getCoreFileSyncState

```TypeScript
function getCoreFileSyncState(uri: string): FileState
```

同步方法获取云盘文件同步上行状态。

**起始版本：** 20

<!--Device-cloudSync-function getCoreFileSyncState(uri: string): FileState--><!--Device-cloudSync-function getCoreFileSyncState(uri: string): FileState-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待获取云盘文件同步上行状态的文件URI。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FileState](arkts-corefile-cloudsync-filestate-e.md) | 返回给定云盘文件的同步上行状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13600001 | IPC error. Possible causes:<br>1.IPC failed or timed out. 2.Failed to load the service. |
| 13900002 | No such file or directory. |
| 13900004 | Interrupted system call |
| 13900010 | Try again |
| 13900012 | Permission denied by the file system |
| 13900020 | Invalid argument. Possible causes:<br>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 13900031 | Function not implemented |
| 14000002 | Invalid URI. |
| 22400005 | Inner error. Possible causes:<br>1.Failed to access the database or execute the SQL statement.<br>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileUri } from '@kit.CoreFileKit';

let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);
try {
  let state = cloudSync.getCoreFileSyncState(uri);
} catch (err) {
  let error:BusinessError = err as BusinessError;
  console.error(`getCoreFileSyncState failed with error ${error.code}, message is ${error.message}`);
}

```

