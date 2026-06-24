# moveFile

## moveFile

```TypeScript
declare function moveFile(src: string, dest: string, mode?: number): Promise<void>
```

移动文件，使用promise异步回调。

> **说明：**
>
> 该接口不支持在分布式文件路径下操作。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源文件的应用沙箱路径。 |
| dest | string | 是 | 目标文件的应用沙箱路径。 |
| mode | number | 否 | 移动模式。若mode为0，移动位置存在同名文件时，强制移动覆盖。若mode为1，移动位置存在同名文件时，抛出异常。默认为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900001](../../errorcode-universal.md#13900001-Operation) | Operation not permitted |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900014](../../errorcode-universal.md#13900014-Device) | Device or resource busy |
| [13900015](../../errorcode-universal.md#13900015-File) | File exists |
| [13900016](../../errorcode-universal.md#13900016-Crossdevice) | Cross-device link |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900019](../../errorcode-universal.md#13900019-Is) | Is a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device |
| [13900027](../../errorcode-universal.md#13900027-Readonly) | Read-only file system |
| [13900028](../../errorcode-universal.md#13900028-Too) | Too many links |
| [13900032](../../errorcode-universal.md#13900032-Directory) | Directory not empty |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900041](../../errorcode-universal.md#13900041-Quota) | Quota exceeded |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |


## moveFile

```TypeScript
declare function moveFile(src: string, dest: string, callback: AsyncCallback<void>): void
```

移动文件。如果移动位置存在同名文件，将强制覆盖。使用callback异步回调。

> **说明：**
>
> 该接口不支持在分布式文件路径下操作。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源文件的应用沙箱路径。 |
| dest | string | 是 | 目标文件的应用沙箱路径。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步移动文件之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900001](../../errorcode-universal.md#13900001-Operation) | Operation not permitted |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900014](../../errorcode-universal.md#13900014-Device) | Device or resource busy |
| [13900015](../../errorcode-universal.md#13900015-File) | File exists |
| [13900016](../../errorcode-universal.md#13900016-Crossdevice) | Cross-device link |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900019](../../errorcode-universal.md#13900019-Is) | Is a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device |
| [13900027](../../errorcode-universal.md#13900027-Readonly) | Read-only file system |
| [13900028](../../errorcode-universal.md#13900028-Too) | Too many links |
| [13900032](../../errorcode-universal.md#13900032-Directory) | Directory not empty |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900041](../../errorcode-universal.md#13900041-Quota) | Quota exceeded |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |


## moveFile

```TypeScript
declare function moveFile(src: string, dest: string, mode: number, callback: AsyncCallback<void>): void
```

移动文件，支持设置移动模式。使用callback异步回调。

> **说明：**
>
> 该接口不支持在分布式文件路径下操作。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源文件的应用沙箱路径。 |
| dest | string | 是 | 目标文件的应用沙箱路径。 |
| mode | number | 是 | 移动模式。若mode为0，移动位置存在同名文件时，强制移动覆盖。若mode为1，移动位置存在同名文件时，抛出异常。默认为0。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步移动文件之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900001](../../errorcode-universal.md#13900001-Operation) | Operation not permitted |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900014](../../errorcode-universal.md#13900014-Device) | Device or resource busy |
| [13900015](../../errorcode-universal.md#13900015-File) | File exists |
| [13900016](../../errorcode-universal.md#13900016-Crossdevice) | Cross-device link |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900019](../../errorcode-universal.md#13900019-Is) | Is a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device |
| [13900027](../../errorcode-universal.md#13900027-Readonly) | Read-only file system |
| [13900028](../../errorcode-universal.md#13900028-Too) | Too many links |
| [13900032](../../errorcode-universal.md#13900032-Directory) | Directory not empty |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900041](../../errorcode-universal.md#13900041-Quota) | Quota exceeded |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |

