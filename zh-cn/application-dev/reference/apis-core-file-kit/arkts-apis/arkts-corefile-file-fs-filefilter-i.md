# FileFilter

文件名过滤器接口，可通过该接口自定义文件名过滤规则。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface FileFilter--><!--Device-unnamed-export interface FileFilter-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
import { fileIo } from '@kit.CoreFileKit'
import { ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, TaskSignal } from '@kit.CoreFileKit';
```

## filter

```TypeScript
filter(name: string): boolean
```

用于[listFileExt](arkts-corefile-file-fs-listfileext-f.md)或[listFileExtSync](arkts-corefile-file-fs-listfileextsync-f.md)接口的文件过滤，判断指定文件名是否应包含在返回的文件列表中。 注意：此函数被频繁调用。尽量避免文件I/O、网络请求等耗时操作。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileFilter-filter(name: string): boolean--><!--Device-FileFilter-filter(name: string): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 待过滤的文件名或文件相对路径。递归模式下为文件的相对路径，相对路径以"/"开头。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示是否包含在返回的文件列表中。true：包含该文件；false：不包含该文件。 |

