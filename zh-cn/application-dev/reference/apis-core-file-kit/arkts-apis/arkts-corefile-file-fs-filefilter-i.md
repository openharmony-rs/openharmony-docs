# FileFilter

文件名过滤器，支持listFileExt接口使用。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface FileFilter--><!--Device-unnamed-export interface FileFilter-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## filter

```TypeScript
filter(name: string): boolean
```

过滤函数，判断指定的文件名是否应该包含在文件列表中。

注意：此函数被频繁调用。尽量避免文件I/O、网络请求等耗时操作。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileFilter-filter(name: string): boolean--><!--Device-FileFilter-filter(name: string): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 需要过滤的文件名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果应该包含文件，则返回true，否则返回false。 |

