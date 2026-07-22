# lstatSync

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## lstatSync

```TypeScript
declare function lstatSync(path: string): Stat
```

以同步方法获取符号链接文件信息。

**起始版本：** 9

<!--Device-unnamed-declare function lstatSync(path: string): Stat--><!--Device-unnamed-declare function lstatSync(path: string): Stat-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件的应用沙箱路径path或URI。<br>**说明**：从API version 22开始，支持传入URI。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Stat](arkts-corefile-file-fs-stat-i.md) | 表示文件的具体信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900038 | Value too large for defined data type |
| 13900042 | Unknown error |

