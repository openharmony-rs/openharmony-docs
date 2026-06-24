# getFileAccessAbilityInfo（系统接口）

## getFileAccessAbilityInfo

```TypeScript
function getFileAccessAbilityInfo(callback: AsyncCallback<Array<Want>>): void
```

以异步方法获取系统内extension配置为fileAccess类型的所有Want信息。使用callback异步回调。

**起始版本：** 9

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER and ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;Want&gt;&gt; | 是 | The callback is used to return a Array object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900001](../../errorcode-universal.md#13900001-Operation) | Operation not permitted |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900004](../../errorcode-universal.md#13900004-Interrupted) | Interrupted system call |
| [13900006](../../errorcode-universal.md#13900006-No) | No such device or address |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900014](../../errorcode-universal.md#13900014-Device) | Device or resource busy |
| [13900015](../../errorcode-universal.md#13900015-File) | File exists |
| [13900017](../../errorcode-universal.md#13900017-No) | No such device |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900019](../../errorcode-universal.md#13900019-Is) | Is a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900022](../../errorcode-universal.md#13900022-Too) | Too many open files |
| [13900023](../../errorcode-universal.md#13900023-Text) | Text file busy |
| [13900024](../../errorcode-universal.md#13900024-File) | File too large |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device |
| [13900027](../../errorcode-universal.md#13900027-Readonly) | Read-only file system |
| [13900029](../../errorcode-universal.md#13900029-Resource) | Resource deadlock would occur |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900034](../../errorcode-universal.md#13900034-Operation) | Operation would block |
| [13900038](../../errorcode-universal.md#13900038-Value) | Value too large for defined data type |
| [13900041](../../errorcode-universal.md#13900041-Quota) | Quota exceeded |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |
| [14300001](../../errorcode-universal.md#14300001-IPC) | IPC error |
| [14300002](../../errorcode-universal.md#14300002-Invalid) | Invalid uri |
| [14300003](../../errorcode-universal.md#14300003-Fail) | Fail to get fileextension info |
| [14300004](../../errorcode-universal.md#14300004-Get) | Get wrong result |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';
async function getFileAccessAbilityInfo() {
  try {
    fileAccess.getFileAccessAbilityInfo((err: BusinessError, wantInfos: Array<Want>) => {
      if (err) {
        console.error("Failed to getFileAccessAbilityInfo in async, errCode:" + err.code + ", errMessage:" + err.message);
        return;
      }
      console.info("getFileAccessAbilityInfo data " + JSON.stringify(wantInfos));
    });
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("getFileAccessAbilityInfo failed, errCode:" + error.code + ", errMessage:" + error.message);
  }
}

```


## getFileAccessAbilityInfo

```TypeScript
function getFileAccessAbilityInfo(): Promise<Array<Want>>
```

以异步方法获取系统内extension配置为fileAccess类型的所有Want信息。使用Promise异步回调。

**起始版本：** 9

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER and ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Want&gt;&gt; | Returns the wants. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900001](../../errorcode-universal.md#13900001-Operation) | Operation not permitted |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900004](../../errorcode-universal.md#13900004-Interrupted) | Interrupted system call |
| [13900006](../../errorcode-universal.md#13900006-No) | No such device or address |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900014](../../errorcode-universal.md#13900014-Device) | Device or resource busy |
| [13900015](../../errorcode-universal.md#13900015-File) | File exists |
| [13900017](../../errorcode-universal.md#13900017-No) | No such device |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900019](../../errorcode-universal.md#13900019-Is) | Is a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900022](../../errorcode-universal.md#13900022-Too) | Too many open files |
| [13900023](../../errorcode-universal.md#13900023-Text) | Text file busy |
| [13900024](../../errorcode-universal.md#13900024-File) | File too large |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device |
| [13900027](../../errorcode-universal.md#13900027-Readonly) | Read-only file system |
| [13900029](../../errorcode-universal.md#13900029-Resource) | Resource deadlock would occur |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900034](../../errorcode-universal.md#13900034-Operation) | Operation would block |
| [13900038](../../errorcode-universal.md#13900038-Value) | Value too large for defined data type |
| [13900041](../../errorcode-universal.md#13900041-Quota) | Quota exceeded |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |
| [14300001](../../errorcode-universal.md#14300001-IPC) | IPC error |
| [14300002](../../errorcode-universal.md#14300002-Invalid) | Invalid uri |
| [14300003](../../errorcode-universal.md#14300003-Fail) | Fail to get fileextension info |
| [14300004](../../errorcode-universal.md#14300004-Get) | Get wrong result |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';
async function getFileAccessAbilityInfo() {
  let wantInfos: Array<Want> = [];
  try {
    wantInfos = await fileAccess.getFileAccessAbilityInfo();
    console.info("getFileAccessAbilityInfo data " + JSON.stringify(wantInfos));
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("getFileAccessAbilityInfo failed, errCode:" + error.code + ", errMessage:" + error.message);
  }
}

```

