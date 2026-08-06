# listFile

## listFile

```TypeScript
function listFile(
  path: string,
  options?: ListFileOptions
): Promise<string[]>
```

默认列出当前目录下所有文件名和目录名，返回文件名数组，支持按后缀、文件名等条件过滤。使用Promise异步回调。 可通过配置ListFileOptions中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function listFile(  path: string,  options?: ListFileOptions): Promise<string[]>--><!--Device-fileIo-function listFile(  path: string,  options?: ListFileOptions): Promise<string[]>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目录的应用沙箱路径。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 文件过滤选项。默认不进行过滤。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string[]&gt; | Promise对象，返回文件名数组，默认以'utf-8'编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900018 | Not a directory |
| 13900042 | Unknown error |


## listFile

```TypeScript
function listFile(path: string, callback: AsyncCallback<string[]>): void
```

默认列出当前目录下所有文件名和目录名，返回文件名数组。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function listFile(path: string, callback: AsyncCallback<string[]>): void--><!--Device-fileIo-function listFile(path: string, callback: AsyncCallback<string[]>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目录的应用沙箱路径。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;string[]&gt; | 是 | 回调函数，返回文件名数组，默认以'utf-8'编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900018 | Not a directory |
| 13900042 | Unknown error |


## listFile

```TypeScript
function listFile(
  path: string,
  options: ListFileOptions,
  callback: AsyncCallback<string[]>
): void
```

默认列出当前目录下所有文件名和目录名，返回文件名数组，支持按后缀、文件名等条件过滤。使用callback异步回调。 可通过配置ListFileOptions中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function listFile(  path: string,  options: ListFileOptions,  callback: AsyncCallback<string[]>): void--><!--Device-fileIo-function listFile(  path: string,  options: ListFileOptions,  callback: AsyncCallback<string[]>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目录的应用沙箱路径。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 文件过滤选项。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;string[]&gt; | 是 | 回调函数，返回文件名数组，默认以'utf-8'编码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900018 | Not a directory |
| 13900042 | Unknown error |

