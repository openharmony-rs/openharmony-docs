# truncate

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

<a id="truncate"></a>
## truncate

```TypeScript
declare function truncate(file: string | number, len?: number): Promise<void>
```

截断文件，使用promise异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function truncate(file: string | number, len?: number): Promise<void>--><!--Device-unnamed-declare function truncate(file: string | number, len?: number): Promise<void>-End-->

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
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900027 | Read-only file system |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900042 | Unknown error |


<a id="truncate-1"></a>
## truncate

```TypeScript
declare function truncate(file: string | number, callback: AsyncCallback<void>): void
```

截断文件，使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function truncate(file: string | number, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function truncate(file: string | number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string \| number | 是 | 文件的应用沙箱路径或已打开的文件描述符fd。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，本调用无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900027 | Read-only file system |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900042 | Unknown error |


<a id="truncate-2"></a>
## truncate

```TypeScript
declare function truncate(file: string | number, len: number, callback: AsyncCallback<void>): void
```

截断文件，使用callback异步回调。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function truncate(file: string | number, len: number, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function truncate(file: string | number, len: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string \| number | 是 | 文件的应用沙箱路径或已打开的文件描述符fd。 |
| len | number | 是 | 文件截断后的长度，单位为Byte。默认为0。<br>**起始版本：** 11 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数，本调用无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900027 | Read-only file system |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900042 | Unknown error |

