# getCoreFileSyncState

## getCoreFileSyncState

```TypeScript
function getCoreFileSyncState(uri: string): FileState
```

ͬ��������ȡ�����ļ�ͬ������״̬��

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | ����ȡ�����ļ�ͬ������״̬���ļ�URI�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| FileState | ���ظ��������ļ���ͬ������״̬�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13600001](../../errorcode-universal.md#13600001-IPC) | IPC error. Possible causes:<br/><br/>1.IPC failed or timed out. 2.Failed to load the service. |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [13900004](../../errorcode-universal.md#13900004-Interrupted) | Interrupted system call |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied by the file system |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument. Possible causes:<br/><br/>1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [13900031](../../errorcode-universal.md#13900031-Function) | Function not implemented |
| [14000002](../../errorcode-universal.md#14000002-Invalid) | Invalid URI. |
| [22400005](../../errorcode-universal.md#22400005-Inner) | Inner error. Possible causes:<br/><br/>1.Failed to access the database or execute the SQL statement.<br/><br/>2.System error, such as a null pointer, insufficient memory or a JS engine exception. |

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

