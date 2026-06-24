# RootIterator（系统接口）

表示设备根目录的迭代器对象。

**起始版本：** 9

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## next

```TypeScript
next(): { value: RootInfo, done: boolean }
```

通过next同步方法获取下一级设备根目录。

**起始版本：** 9

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| { value: RootInfo, done: boolean } | Returns RootInfo Object and boolean flag. |

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
| [14000001](../../errorcode-universal.md#14000001-Invalid) | Invalid display name |
| [14000002](../../errorcode-universal.md#14000002-Invalid) | Invalid uri |
| [14000003](../../errorcode-universal.md#14000003-Invalid) | Invalid file extension |
| [14000004](../../errorcode-universal.md#14000004-File) | File has been put into trash bin |
| [14300001](../../errorcode-universal.md#14300001-IPC) | IPC error |
| [14300002](../../errorcode-universal.md#14300002-Invalid) | Invalid uri |
| [14300003](../../errorcode-universal.md#14300003-Fail) | Fail to get fileextension info |
| [14300004](../../errorcode-universal.md#14300004-Get) | Get wrong result |

