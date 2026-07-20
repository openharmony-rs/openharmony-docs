# mkdtempSync

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

<a id="mkdtempsync"></a>
## mkdtempSync

```TypeScript
declare function mkdtempSync(prefix: string): string
```

以同步的方法创建临时目录。

**起始版本：** 9

<!--Device-unnamed-declare function mkdtempSync(prefix: string): string--><!--Device-unnamed-declare function mkdtempSync(prefix: string): string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| prefix | string | 是 | 指定目录路径，命名时需要以"XXXXXX"作为结尾。路径末尾的"XXXXXX"字符串将被替换为随机字符，以创建唯一的目录名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 产生的唯一目录路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900015 | File exists |
| 13900018 | Not a directory |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900028 | Too many links |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

