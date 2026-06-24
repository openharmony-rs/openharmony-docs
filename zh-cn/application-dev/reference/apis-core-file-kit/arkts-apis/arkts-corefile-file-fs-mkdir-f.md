# mkdir

## mkdir

```TypeScript
declare function mkdir(path: string): Promise<void>
```

创建目录，使用promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目录的应用沙箱路径。 |

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
| [13900015](../../errorcode-universal.md#13900015-File) | File exists |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device |
| [13900028](../../errorcode-universal.md#13900028-Too) | Too many links |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900041](../../errorcode-universal.md#13900041-Quota) | Quota exceeded |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |


## mkdir

```TypeScript
declare function mkdir(path: string, recursion: boolean): Promise<void>
```

创建目录，使用promise异步回调。当recursion指定为true时，可递归创建目录。

**起始版本：** 11

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目录的应用沙箱路径。 |
| recursion | boolean | 是 | 是否递归创建目录。recursion指定为true时，可递归创建目录。recursion指定为false时，仅可创建单层目录。 |

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
| [13900015](../../errorcode-universal.md#13900015-File) | File exists |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device |
| [13900028](../../errorcode-universal.md#13900028-Too) | Too many links |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900041](../../errorcode-universal.md#13900041-Quota) | Quota exceeded |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |


## mkdir

```TypeScript
declare function mkdir(path: string, callback: AsyncCallback<void>): void
```

创建目录，使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目录的应用沙箱路径。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步创建目录操作完成之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900001](../../errorcode-universal.md#13900001-Operation) | Operation not permitted |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900015](../../errorcode-universal.md#13900015-File) | File exists |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device |
| [13900028](../../errorcode-universal.md#13900028-Too) | Too many links |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900041](../../errorcode-universal.md#13900041-Quota) | Quota exceeded |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |


## mkdir

```TypeScript
declare function mkdir(path: string, recursion: boolean, callback: AsyncCallback<void>): void
```

创建目录，使用callback异步回调。当recursion指定为true，可递归创建目录。

**起始版本：** 11

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目录的应用沙箱路径。 |
| recursion | boolean | 是 | 是否递归创建目录。recursion指定为true时，可递归创建目录。recursion指定为false时，仅可创建单层目录。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步创建目录操作完成之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900001](../../errorcode-universal.md#13900001-Operation) | Operation not permitted |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900015](../../errorcode-universal.md#13900015-File) | File exists |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device |
| [13900028](../../errorcode-universal.md#13900028-Too) | Too many links |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900041](../../errorcode-universal.md#13900041-Quota) | Quota exceeded |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |

