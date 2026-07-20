# moveFile

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

<a id="movefile"></a>
## moveFile

```TypeScript
declare function moveFile(src: string, dest: string, mode?: number): Promise<void>
```

移动文件，使用promise异步回调。

> **说明：**  
>  
> 该接口不支持在分布式文件路径下操作。

**起始版本：** 9

<!--Device-unnamed-declare function moveFile(src: string, dest: string, mode?: number): Promise<void>--><!--Device-unnamed-declare function moveFile(src: string, dest: string, mode?: number): Promise<void>-End-->

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
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900016 | Cross-device link |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900028 | Too many links |
| 13900032 | Directory not empty |
| 13900033 | Too many symbolic links encountered |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |


<a id="movefile-1"></a>
## moveFile

```TypeScript
declare function moveFile(src: string, dest: string, callback: AsyncCallback<void>): void
```

移动文件。如果移动位置存在同名文件，将强制覆盖。使用callback异步回调。

> **说明：**  
>  
> 该接口不支持在分布式文件路径下操作。

**起始版本：** 9

<!--Device-unnamed-declare function moveFile(src: string, dest: string, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function moveFile(src: string, dest: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源文件的应用沙箱路径。 |
| dest | string | 是 | 目标文件的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步移动文件之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900016 | Cross-device link |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900028 | Too many links |
| 13900032 | Directory not empty |
| 13900033 | Too many symbolic links encountered |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |


<a id="movefile-2"></a>
## moveFile

```TypeScript
declare function moveFile(src: string, dest: string, mode: number, callback: AsyncCallback<void>): void
```

移动文件，支持设置移动模式。使用callback异步回调。

> **说明：**  
>  
> 该接口不支持在分布式文件路径下操作。

**起始版本：** 9

<!--Device-unnamed-declare function moveFile(src: string, dest: string, mode: number, callback: AsyncCallback<void>): void--><!--Device-unnamed-declare function moveFile(src: string, dest: string, mode: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string | 是 | 源文件的应用沙箱路径。 |
| dest | string | 是 | 目标文件的应用沙箱路径。 |
| mode | number | 是 | 移动模式。若mode为0，移动位置存在同名文件时，强制移动覆盖。若mode为1，移动位置存在同名文件时，抛出异常。默认为0。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步移动文件之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900016 | Cross-device link |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900028 | Too many links |
| 13900032 | Directory not empty |
| 13900033 | Too many symbolic links encountered |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

