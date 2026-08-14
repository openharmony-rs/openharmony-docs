# rmdir

## rmdir

```TypeScript
function rmdir(path: string): Promise<void>
```

删除目录及其所有子目录和文件。使用Promise异步回调。 > **说明：** > > 该接口支持删除单个文件，但不推荐使用此方法删除单个文件，推荐使用unlink接口删除单个文件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function rmdir(path: string): Promise<void>--><!--Device-fileIo-function rmdir(path: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目录的应用沙箱路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900032 | Directory not empty |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900018 | Not a directory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900030 | File name too long |
| 13900042 | Unknown error |
| 13900011 | Out of memory |
| 13900027 | Read-only file system |


## rmdir

```TypeScript
function rmdir(path: string, callback: AsyncCallback<void>): void
```

删除目录及其所有子目录和文件。使用callback异步回调。 > **说明：** > > 该接口支持删除单个文件，但不推荐使用此方法删除单个文件，推荐使用unlink接口删除单个文件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function rmdir(path: string, callback: AsyncCallback<void>): void--><!--Device-fileIo-function rmdir(path: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目录的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当删除目录成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900032 | Directory not empty |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900018 | Not a directory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900030 | File name too long |
| 13900042 | Unknown error |
| 13900011 | Out of memory |
| 13900027 | Read-only file system |

