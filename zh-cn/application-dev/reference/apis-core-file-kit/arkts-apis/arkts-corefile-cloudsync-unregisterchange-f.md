# unregisterChange

## 导入模块

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

<a id="unregisterchange"></a>
## unregisterChange

```TypeScript
function unregisterChange(uri: string): void
```

取消订阅监听指定文件的变化通知。

**起始版本：** 12

<!--Device-cloudSync-function unregisterChange(uri: string): void--><!--Device-cloudSync-function unregisterChange(uri: string): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待下载文件uri。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory. |
| 13900012 | Permission denied |
| 14000002 | Invalid uri. |

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

