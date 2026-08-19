# mkdirSync

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
import { fileIo } from '@kit.CoreFileKit'
import { ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, TaskSignal } from '@kit.CoreFileKit';
```

## mkdirSync

```TypeScript
declare function mkdirSync(path: string): void
```

以同步方法创建单层目录，若父目录不存在则会报错。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function mkdirSync(path: string): void--><!--Device-unnamed-declare function mkdirSync(path: string): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目录的应用沙箱路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900018 | Not a directory |
| 13900028 | Too many links |
| 13900030 | File name too long |
| 13900025 | No space left on device |
| 13900001 | Operation not permitted |
| 13900033 | Too many symbolic links encountered |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900015 | File exists |
| 13900008 | Bad file descriptor |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 13900011 | Out of memory |


## mkdirSync

```TypeScript
declare function mkdirSync(path: string, recursion: boolean): void
```

以同步方法创建目录。当recursion指定为true，可递归创建目录。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function mkdirSync(path: string, recursion: boolean): void--><!--Device-unnamed-declare function mkdirSync(path: string, recursion: boolean): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 目录的应用沙箱路径。 |
| recursion | boolean | 是 | 是否递归创建目录。recursion指定为true时，可递归创建目录。recursion指定为false时，仅可创建单层目录。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900018 | Not a directory |
| 13900028 | Too many links |
| 13900030 | File name too long |
| 13900025 | No space left on device |
| 13900001 | Operation not permitted |
| 13900033 | Too many symbolic links encountered |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900015 | File exists |
| 13900008 | Bad file descriptor |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 13900011 | Out of memory |

