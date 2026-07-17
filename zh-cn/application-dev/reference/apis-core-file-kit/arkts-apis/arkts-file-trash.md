# @ohos.file.trash

The **file.trash** module provides APIs for querying, recovering, or permanently deleting the files or directories in Recently deleted (trash). Currently, only local files and directories are supported.You can use **delete()** of [@ohos.file.fileAccess](arkts-file-fileaccess.md) to move a file or directory to the trash.

> **NOTE**  
>  
> - Currently, the APIs of this module can be called only by **FileManager**.

**起始版本：** 10

**废弃版本：** 23

<!--Device-unnamed-declare namespace trash--><!--Device-unnamed-declare namespace trash-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { trash } from '@kit.CoreFileKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [completelyDelete](arkts-corefile-trash-completelydelete-f-sys.md#completelydelete-1) | Permanently deletes a file or directory from the **Recently deleted** list. |
| [listFile](arkts-corefile-trash-listfile-f-sys.md#listfile-1) | Lists the files and directories in the **Recently deleted** list. |
| [recover](arkts-corefile-trash-recover-f-sys.md#recover-1) | Recovers a file or directory from the trash. |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FileInfo](arkts-corefile-trash-fileinfo-i-sys.md) | Represents information about a file or directory in the **Recently deleted** list. |
<!--DelEnd-->

