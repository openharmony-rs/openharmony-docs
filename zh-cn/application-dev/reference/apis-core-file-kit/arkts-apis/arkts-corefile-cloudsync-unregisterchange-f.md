# unregisterChange

## unregisterChange

```TypeScript
function unregisterChange(uri: string): void
```

ȡ�����ļ���ָ���ļ��ı仯֪ͨ��

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | �������ļ�uri�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-The) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left<br/>unspecified;<br/><br/>2.Incorrect parameter types. |
| [13900001](../../errorcode-universal.md#13900001-Operation) | Operation not permitted |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory. |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [14000002](../../errorcode-universal.md#14000002-Invalid) | Invalid uri. |

**示例：**

```TypeScript
import { fileUri } from '@kit.CoreFileKit';

let path = "/data/storage/el2/cloud/1.txt";
let uri = fileUri.getUriFromPath(path);
let onCallback1 = (changeData: cloudSync.ChangeData) => {
  if (changeData.type == cloudSync.NotifyType.NOTIFY_ADDED) {
    // file has been added, do something
  } else if (changeData.type== cloudSync.NotifyType.NOTIFY_DELETED) {
    // file has been removed, do something
  }
}
cloudSync.registerChange(uri, false, onCallback1);
// 取消注册监听
cloudSync.unregisterChange(uri);

```

