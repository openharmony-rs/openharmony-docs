# @ohos.file.trash(Trash)

The **file.trash** module provides APIs for querying, recovering, or permanently deleting the files or directories in Recently deleted (trash). Currently, only local files and directories are supported. You can use **delete()** of [@ohos.file.fileAccess](arkts-corefile-file-fileaccess.md) to move a file or directory to the trash.

> **NOTE:** 
> 
> - Currently, the APIs of this module can be called only by **FileManager**.

**Since:** 10

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { trash } from '@kit.CoreFileKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [completelyDelete](arkts-corefile-trash-completelydelete-f-sys.md) | Permanently deletes a file or directory from the **Recently deleted** list. |
| [listFile](arkts-corefile-trash-listfile-f-sys.md) | Lists the files and directories in the **Recently deleted** list. |
| [recover](arkts-corefile-trash-recover-f-sys.md) | Recovers a file or directory from the trash. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [FileInfo](arkts-corefile-trash-fileinfo-i-sys.md) | Represents information about a file or directory in the **Recently deleted** list. |
<!--DelEnd-->
