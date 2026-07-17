# access

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## access

```TypeScript
declare function access(path: string, mode?: AccessModeType): Promise<boolean>
```

检查文件或目录是否存在，或校验操作权限，使用promise异步回调。

校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function access(path: string, mode?: AccessModeType): Promise<boolean>--><!--Device-unnamed-declare function access(path: string, mode?: AccessModeType): Promise<boolean>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件或目录应用沙箱路径。 |
| mode | [AccessModeType](arkts-corefile-file-fs-accessmodetype-e.md) | 否 | 文件或目录校验的权限。不填该参数则默认校验文件是否存在。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象。返回布尔值。返回true，表示文件存在；返回false，表示文件不存在。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900020 | Invalid argument |
| 13900023 | Text file busy |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900042 | Unknown error |


## access

```TypeScript
declare function access(path: string, callback: AsyncCallback<boolean>): void
```

检查文件或目录是否存在，使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function access(path: string, callback: AsyncCallback<boolean>): void--><!--Device-unnamed-declare function access(path: string, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件或目录应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean> | 是 | 异步检查文件或目录是否存在的回调。如果存在，回调返回true；否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900020 | Invalid argument |
| 13900023 | Text file busy |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900042 | Unknown error |


## access

```TypeScript
declare function access(path: string, mode: AccessModeType, flag: AccessFlagType): Promise<boolean>
```

检查文件或目录是否在本地，或校验操作权限，使用promise异步回调。

校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。

**起始版本：** 12

<!--Device-unnamed-declare function access(path: string, mode: AccessModeType, flag: AccessFlagType): Promise<boolean>--><!--Device-unnamed-declare function access(path: string, mode: AccessModeType, flag: AccessFlagType): Promise<boolean>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件或目录应用沙箱路径。 |
| mode | [AccessModeType](arkts-corefile-file-fs-accessmodetype-e.md) | 是 | 文件或目录校验的权限。 |
| flag | [AccessFlagType](arkts-corefile-file-fs-accessflagtype-e.md) | 是 | 文件或目录校验的位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean> | Promise对象。返回布尔值。返回true，表示文件或目录在本地且校验权限存在；返回false，表示文件或目录不存在或者文件或目录在云端或其他分布式设备上。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13900005 | I/O error |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900020 | Invalid argument |
| 13900023 | Text file busy |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |

