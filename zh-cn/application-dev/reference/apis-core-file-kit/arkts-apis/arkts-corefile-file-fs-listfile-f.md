# listFile

## listFile

```TypeScript
declare function listFile(
  path: string,
  options?: ListFileOptions
): Promise<string[]>
```

默认列出当前目录下所有文件名和目录名。支持过滤。使用promise异步回调。

可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目录的应用沙箱路径。 |
| options | ListFileOptions | 否 | 文件过滤选项。默认不进行过滤。 [since 11] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string[]&gt; | Promise对象。返回文件名数组，默认以'utf-8'编码。<br/>default. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |


## listFile

```TypeScript
declare function listFile(path: string, callback: AsyncCallback<string[]>): void
```

默认列出当前目录下所有文件名和目录名。支持过滤。使用callback异步回调。

可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目录的应用沙箱路径。 |
| callback | AsyncCallback&lt;string[]&gt; | 是 | 异步列出文件名数组之后的回调，默认以'utf-8'编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |


## listFile

```TypeScript
declare function listFile(
  path: string,
  options: ListFileOptions,
  callback: AsyncCallback<string[]>
): void
```

默认列出当前目录下所有文件名和目录名。支持过滤。使用callback异步回调。

可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目录的应用沙箱路径。 |
| options | ListFileOptions | 是 | 文件过滤选项。默认不进行过滤。 [since 11] |
| callback | AsyncCallback&lt;string[]&gt; | 是 | 异步列出文件名数组之后的回调，默认以'utf-8'编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |

