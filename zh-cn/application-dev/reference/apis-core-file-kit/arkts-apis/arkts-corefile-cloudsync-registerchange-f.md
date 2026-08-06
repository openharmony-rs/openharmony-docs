# registerChange

## registerChange

```TypeScript
function registerChange(uri: string, recursion: boolean, callback: Callback<ChangeData>): void
```

订阅监听指定文件的变化通知。callback返回更改的数据。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-cloudSync-function registerChange(uri: string, recursion: boolean, callback: Callback<ChangeData>): void--><!--Device-cloudSync-function registerChange(uri: string, recursion: boolean, callback: Callback<ChangeData>): void-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 待下载文件uri。 |
| recursion | boolean | 是 | true为监听该URI以及子文件和子目录，false为仅监听该URI文件。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;ChangeData&gt; | 是 | 回调函数，返回更改的数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The input parameter is invalid.Possible causes:1.Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2.Incorrect parameter types. |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory. |
| 13900012 | Permission denied |
| 14000002 | Invalid uri. |

**示例：**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```TypeScript
import { fileUri } from '@kit.CoreFileKit';

let path: string = "/data/storage/el2/cloud/1.txt";
let uri: string = fileUri.getUriFromPath(path);
let onCallback1 = (changeData: cloudSync.ChangeData): void => {
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

