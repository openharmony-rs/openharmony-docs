# @ohos.file.trash

The **file.trash** module provides APIs for querying, recovering, or permanently deleting the files or directories in
Recently deleted (trash). Currently, only local files and directories are supported.
You can use **delete()** of [@ohos.file.fileAccess](arkts-file-fileaccess.md#fileAccess) to move a file or
directory to the trash.

> **NOTE**
>
> - Currently, the APIs of this module can be called only by **FileManager**.

**起始版本：** 10

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[completelyDelete](arkts-corefile-trash-completelydelete-f-sys.md#completelyDelete-1) | Permanently deletes a file or directory from the **Recently deleted** list.<br/> |
| <!--DelRow-->[listFile](arkts-corefile-trash-listfile-f-sys.md#listFile-1) | Lists the files and directories in the **Recently deleted** list.<br/> |
| <!--DelRow-->[recover](arkts-corefile-trash-recover-f-sys.md#recover-1) | Recovers a file or directory from the trash.<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[FileInfo](arkts-corefile-trash-fileinfo-i-sys.md) | Represents information about a file or directory in the **Recently deleted** list.<br/> |

