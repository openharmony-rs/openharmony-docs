# getFileAccessAbilityInfo（系统接口）

## 导入模块

```TypeScript
import { fileAccess } from '@kit.CoreFileKit';
```

## getFileAccessAbilityInfo

```TypeScript
function getFileAccessAbilityInfo(callback: AsyncCallback<Array<Want>>): void
```

以异步方法获取系统内extension配置为fileAccess类型的所有Want信息。使用callback异步回调。

**起始版本：** 9

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER and ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-fileAccess-function getFileAccessAbilityInfo(callback: AsyncCallback<Array<Want>>): void--><!--Device-fileAccess-function getFileAccessAbilityInfo(callback: AsyncCallback<Array<Want>>): void-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<Want>> | 是 | The callback is used to return a Array&lt;Want&gt; object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

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

<!--Device-fileAccess-function getFileAccessAbilityInfo(): Promise<Array<Want>>--><!--Device-fileAccess-function getFileAccessAbilityInfo(): Promise<Array<Want>>-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<Want>> | Returns the wants. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

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

