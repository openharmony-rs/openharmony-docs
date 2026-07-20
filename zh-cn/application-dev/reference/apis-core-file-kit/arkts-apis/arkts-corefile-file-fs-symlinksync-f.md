# symlinkSync

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

<a id="symlinksync"></a>
## symlinkSync

```TypeScript
declare function symlinkSync(target: string, srcPath: string): void
```

以同步的方法基于文件路径创建符号链接。

> **说明：**  
>  
> 从API version 11开始，不支持三方应用使用。

**起始版本：** 9

<!--Device-unnamed-declare function symlinkSync(target: string, srcPath: string): void--><!--Device-unnamed-declare function symlinkSync(target: string, srcPath: string): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| target | string | 是 | 要链接的目标文件的应用沙箱路径。 |
| srcPath | string | 是 | 符号链接文件的应用沙箱路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900015 | File exists |
| 13900018 | Not a directory |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900030 | File name too long |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

