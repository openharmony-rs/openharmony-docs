# createFileAccessHelper (System API)

## Modules to Import

```TypeScript
import { fileAccess } from '@kit.CoreFileKit';
```

## createFileAccessHelper

```TypeScript
function createFileAccessHelper(context: Context): FileAccessHelper
```

Creates a **Helper** object to bind with all file management services in the system. This API returns the result synchronously.

**Since:** 9

**Deprecated since:** 23

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER and ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Indicates the application context. |

**Return value:**

| Type | Description |
| --- | --- |
| [FileAccessHelper](arkts-corefile-fileaccess-fileaccesshelper-i-sys.md) | Returns the fileAccessHelper. |

**Error codes:**

| Error Code ID | Error Message |
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

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { Want } from '@kit.AbilityKit';
import { common } from '@kit.AbilityKit';
// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext; 
function createFileAccessHelper01(context: common.UIAbilityContext) {
  let fileAccessHelper: fileAccess.FileAccessHelper;
  // Obtain wantInfos by using getFileAccessAbilityInfo().
  let wantInfos: Array<Want> = [
    {
      bundleName: "com.ohos.UserFile.ExternalFileManager",
      abilityName: "FileExtensionAbility",
    },
  ]
  try {
    // context is passed by EntryAbility.
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

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext; 
function createFileAccessHelper02(context: common.UIAbilityContext) {
  let fileAccessHelperAllServer: fileAccess.FileAccessHelper;
  // Create a Helper object to interact with all file management services configured with fileAccess in the system.
  try {
    // context is passed by EntryAbility.
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

Creates a **Helper** object to bind with the specified Wants. This API returns the result synchronously. The **Helper** object provides file access and management capabilities.

**Since:** 9

**Deprecated since:** 23

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER and ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Indicates the application context. |
| wants | Array&lt;[Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)&gt; | Yes | Represents the connected data provider. |

**Return value:**

| Type | Description |
| --- | --- |
| [FileAccessHelper](arkts-corefile-fileaccess-fileaccesshelper-i-sys.md) | Returns the fileAccessHelper. |

**Error codes:**

| Error Code ID | Error Message |
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

**Examples**

See [createFileAccessHelper](#createfileaccesshelper)
