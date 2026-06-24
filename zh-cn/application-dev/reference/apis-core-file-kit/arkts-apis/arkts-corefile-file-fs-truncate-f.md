# truncate

## truncate

```TypeScript
declare function truncate(file: string | number, len?: number): Promise<void>
```

截断文件，使用promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string \| number | 是 | 文件的应用沙箱路径或已打开的文件描述符fd。 |
| len | number | 否 | 文件截断后的长度，单位为Byte。默认为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900001](../../errorcode-universal.md#13900001-Operation) | Operation not permitted |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900004](../../errorcode-universal.md#13900004-Interrupted) | Interrupted system call |
| [13900005](../../errorcode-universal.md#13900005-IO) | I/O error |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900019](../../errorcode-universal.md#13900019-Is) | Is a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900023](../../errorcode-universal.md#13900023-Text) | Text file busy |
| [13900024](../../errorcode-universal.md#13900024-File) | File too large |
| [13900027](../../errorcode-universal.md#13900027-Readonly) | Read-only file system |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |


## truncate

```TypeScript
declare function truncate(file: string | number, callback: AsyncCallback<void>): void
```

截断文件，使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string \| number | 是 | 文件的应用沙箱路径或已打开的文件描述符fd。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，本调用无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900001](../../errorcode-universal.md#13900001-Operation) | Operation not permitted |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900004](../../errorcode-universal.md#13900004-Interrupted) | Interrupted system call |
| [13900005](../../errorcode-universal.md#13900005-IO) | I/O error |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900019](../../errorcode-universal.md#13900019-Is) | Is a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900023](../../errorcode-universal.md#13900023-Text) | Text file busy |
| [13900024](../../errorcode-universal.md#13900024-File) | File too large |
| [13900027](../../errorcode-universal.md#13900027-Readonly) | Read-only file system |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |


## truncate

```TypeScript
declare function truncate(file: string | number, len: number, callback: AsyncCallback<void>): void
```

截断文件，使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string \| number | 是 | 文件的应用沙箱路径或已打开的文件描述符fd。 |
| len | number | 是 | 文件截断后的长度，单位为Byte。默认为0。 [since 11] |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，本调用无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900001](../../errorcode-universal.md#13900001-Operation) | Operation not permitted |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900004](../../errorcode-universal.md#13900004-Interrupted) | Interrupted system call |
| [13900005](../../errorcode-universal.md#13900005-IO) | I/O error |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900019](../../errorcode-universal.md#13900019-Is) | Is a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900023](../../errorcode-universal.md#13900023-Text) | Text file busy |
| [13900024](../../errorcode-universal.md#13900024-File) | File too large |
| [13900027](../../errorcode-universal.md#13900027-Readonly) | Read-only file system |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |

