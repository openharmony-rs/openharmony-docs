# createFileAccessHelper（系统接口）

## 导入模块

```TypeScript
import { fileAccess } from '@kit.CoreFileKit';
```

## createFileAccessHelper

```TypeScript
function createFileAccessHelper(context: Context): FileAccessHelper
```

以同步方法创建连接当前系统内所有文件管理服务的helper对象。

**起始版本：** 9

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER and ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-fileAccess-function createFileAccessHelper(context: Context): FileAccessHelper--><!--Device-fileAccess-function createFileAccessHelper(context: Context): FileAccessHelper-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | Indicates the application context. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FileAccessHelper](arkts-corefile-fileaccess-fileaccesshelper-i-sys.md) | Returns the fileAccessHelper. |

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
import { common } from '@kit.AbilityKit';
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext; 
function createFileAccessHelper02(context: common.UIAbilityContext) {
  let fileAccessHelperAllServer: fileAccess.FileAccessHelper;
  // 创建连接系统内所有配置fileAccess的文件管理类服务的helper对象
  try {
    // context 是EntryAbility 传过来的context
    fileAccessHelperAllServer = fileAccess.createFileAccessHelper(context);
    if (!fileAccessHelperAllServer) {
      console.error("createFileAccessHelper interface returns an undefined object");
    }
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("createFileAccessHelper failed, errCode:" + error.code + ", errMessage:" + error.message);
  }
}

```


## createFileAccessHelper

```TypeScript
function createFileAccessHelper(context: Context, wants: Array<Want>): FileAccessHelper
```

以同步方法创建连接指定wants的helper对象。

**起始版本：** 9

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER and ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-fileAccess-function createFileAccessHelper(context: Context, wants: Array<Want>): FileAccessHelper--><!--Device-fileAccess-function createFileAccessHelper(context: Context, wants: Array<Want>): FileAccessHelper-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | Indicates the application context. |
| wants | Array&lt;Want&gt; | 是 | Represents the connected data provider. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FileAccessHelper](arkts-corefile-fileaccess-fileaccesshelper-i-sys.md) | Returns the fileAccessHelper. |

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
import { common } from '@kit.AbilityKit';
// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext; 
function createFileAccessHelper01(context: common.UIAbilityContext) {
  let fileAccessHelper: fileAccess.FileAccessHelper;
  // wantInfos 从getFileAccessAbilityInfo()获取
  let wantInfos: Array<Want> = [
    {
      bundleName: "com.ohos.UserFile.ExternalFileManager",
      abilityName: "FileExtensionAbility",
    },
  ]
  try {
    // context 是EntryAbility 传过来的context
    fileAccessHelper = fileAccess.createFileAccessHelper(context, wantInfos);
    if (!fileAccessHelper) {
      console.error("createFileAccessHelper interface returns an undefined object");
    }
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("createFileAccessHelper failed, errCode:" + error.code + ", errMessage:" + error.message);
  }
}

```

