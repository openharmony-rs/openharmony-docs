# copy

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

<a id="copy"></a>
## copy

```TypeScript
declare function copy(srcUri: string, destUri: string, options?: CopyOptions): Promise<void>
```

拷贝文件或目录，使用promise异步回调。

支持跨设备拷贝。强制覆盖拷贝。入参支持文件或目录URI。

跨端拷贝时，最多同时存在10个拷贝任务；单次拷贝的文件数量不得超过500个。

**起始版本：** 11

<!--Device-unnamed-declare function copy(srcUri: string, destUri: string, options?: CopyOptions): Promise<void>--><!--Device-unnamed-declare function copy(srcUri: string, destUri: string, options?: CopyOptions): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcUri | string | 是 | 待复制文件或目录的URI。 |
| destUri | string | 是 | 目标文件或目录的URI。 |
| options | [CopyOptions](../../apis-arkui/arkts-apis/arkts-arkui-copyoptions-e.md) | 否 | options中提供拷贝进度回调。不填该参数则无拷贝进度回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900011 | Out of memory |
| 13900012 | Permission denied by the file system |
| 13900015 | File exists |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900021 | File table overflow |
| 13900022 | Too many open files |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900028 | Too many links |
| 13900030 | File name too long |
| 13900031 | Function not implemented |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 13900044 | Network is unreachable<br>**适用版本：** 12+ |


<a id="copy-1"></a>
## copy

```TypeScript
declare function copy(srcUri: string, destUri: string, callback: AsyncCallback<void>): void
```

拷贝文件或者目录，使用callback异步回调。

支持跨设备拷贝。强制覆盖拷贝。入参支持文件或目录URI。

跨端拷贝时，最多同时存在10个拷贝任务；单次拷贝的文件数量不得超过500个。

**起始版本：** 11

<!--Device-unnamed-declare function copy(srcUri: string, destUri: string, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function copy(srcUri: string, destUri: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcUri | string | 是 | 待复制文件或目录的URI。 |
| destUri | string | 是 | 目标文件或目录的URI。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步拷贝之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900011 | Out of memory |
| 13900012 | Permission denied by the file system |
| 13900015 | File exists |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900021 | File table overflow |
| 13900022 | Too many open files |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900028 | Too many links |
| 13900030 | File name too long |
| 13900031 | Function not implemented |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |


<a id="copy-2"></a>
## copy

```TypeScript
declare function copy(srcUri: string, destUri: string, options: CopyOptions, callback: AsyncCallback<void>): void
```

拷贝文件或者目录，使用callback异步回调。

支持跨设备拷贝。强制覆盖拷贝。入参支持文件或目录URI。

跨端拷贝时，最多同时存在10个拷贝任务；单次拷贝的文件数量不得超过500个。

**起始版本：** 11

<!--Device-unnamed-declare function copy(srcUri: string, destUri: string, options: CopyOptions, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function copy(srcUri: string, destUri: string, options: CopyOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| srcUri | string | 是 | 待复制文件或目录的URI。 |
| destUri | string | 是 | 目标文件或目录的URI。 |
| options | [CopyOptions](../../apis-arkui/arkts-apis/arkts-arkui-copyoptions-e.md) | 是 | 拷贝进度回调。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步拷贝之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameter types. |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900011 | Out of memory |
| 13900012 | Permission denied by the file system |
| 13900015 | File exists |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900021 | File table overflow |
| 13900022 | Too many open files |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900028 | Too many links |
| 13900030 | File name too long |
| 13900031 | Function not implemented |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

