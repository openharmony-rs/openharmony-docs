# @ohos.file.environment(Directory Environment Capability)

The **Environment** module provides ArkTS APIs for obtaining the root directories of the storage and user files.

**Since:** 11

**System capability:** SystemCapability.FileManagement.File.Environment

## Modules to Import

```TypeScript
import { Environment } from '@kit.CoreFileKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getUserDesktopDir](arkts-corefile-environment-getuserdesktopdir-f.md) | Obtains the sandbox path of the pre-authorized **Desktop** directory. |
| [getUserDocumentDir](arkts-corefile-environment-getuserdocumentdir-f.md) | Obtains the sandbox path of the pre-authorized **Document** directory. |
| [getUserDownloadDir](arkts-corefile-environment-getuserdownloaddir-f.md) | Obtains the sandbox path of the pre-authorized **Download** directory. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getExternalStorageDir](arkts-corefile-environment-getexternalstoragedir-f-sys.md) | Obtains the sandbox path of the root directory of an external storage card. This API is available only to the devices with the SystemCapability.FileManagement.File.Environment.FolderObtain system capability. |
| [getStorageDataDir](arkts-corefile-environment-getstoragedatadir-f-sys.md) | Obtains the root directory of the memory. This API uses a promise to return the result. |
| [getStorageDataDir](arkts-corefile-environment-getstoragedatadir-f-sys.md) | Obtains the root directory of the memory. This API uses an asynchronous callback to return the result. |
| [getUserDataDir](arkts-corefile-environment-getuserdatadir-f-sys.md) | Obtains the root directory of user files. This API uses a promise to return the result. |
| [getUserDataDir](arkts-corefile-environment-getuserdatadir-f-sys.md) | Obtains the root directory of user files. This API uses an asynchronous callback to return the result. |
| [getUserHomeDir](arkts-corefile-environment-getuserhomedir-f-sys.md) | Obtains the sandbox path of the built-in card directory of the current user. This API is available only to the devices with the SystemCapability.FileManagement.File.Environment.FolderObtain system capability. |
<!--DelEnd-->
