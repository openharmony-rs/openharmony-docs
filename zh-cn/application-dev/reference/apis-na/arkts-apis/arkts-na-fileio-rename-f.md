# rename

## rename

```TypeScript
function rename(oldPath: string, newPath: string): Promise<void>
```

重命名文件或目录。使用Promise异步回调。 > **说明：** > > 该接口不支持在分布式文件路径下操作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function rename(oldPath: string, newPath: string): Promise<void>--><!--Device-fileIo-function rename(oldPath: string, newPath: string): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oldPath | string | 是 | 文件或目录的应用沙箱原路径。 |
| newPath | string | 是 | 文件或目录的应用沙箱新路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900016 | Cross-device link |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900028 | Too many links |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900032 | Directory not empty |
| 13900001 | Operation not permitted |
| 13900033 | Too many symbolic links encountered |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900008 | Bad file descriptor |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 13900011 | Out of memory |


## rename

```TypeScript
function rename(oldPath: string, newPath: string, callback: AsyncCallback<void>): void
```

重命名文件或目录。使用callback异步回调。 > **说明：** > > 该接口不支持在分布式文件路径下操作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function rename(oldPath: string, newPath: string, callback: AsyncCallback<void>): void--><!--Device-fileIo-function rename(oldPath: string, newPath: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oldPath | string | 是 | 文件或目录的应用沙箱原路径。 |
| newPath | string | 是 | 文件或目录的应用沙箱新路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当重命名文件成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900016 | Cross-device link |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900028 | Too many links |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900032 | Directory not empty |
| 13900001 | Operation not permitted |
| 13900033 | Too many symbolic links encountered |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900008 | Bad file descriptor |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 13900011 | Out of memory |

