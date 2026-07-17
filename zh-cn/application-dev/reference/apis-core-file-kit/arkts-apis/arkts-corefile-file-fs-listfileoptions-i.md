# ListFileOptions

可选项类型，支持ListFile接口使用。

**起始版本：** 11

<!--Device-unnamed-export interface ListFileOptions--><!--Device-unnamed-export interface ListFileOptions-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## filter

```TypeScript
filter?: Filter
```

文件过滤配置项。 可选，设置过滤条件。

**类型：** Filter

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ListFileOptions-filter?: Filter--><!--Device-ListFileOptions-filter?: Filter-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## listNum

```TypeScript
listNum?: number
```

列出文件名数量。可选，当设置0时，列出所有文件，默认为0。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ListFileOptions-listNum?: number--><!--Device-ListFileOptions-listNum?: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## recursion

```TypeScript
recursion?: boolean
```

是否递归子目录下文件名。可选，默认为false。当recursion为false时，返回当前目录下满足过滤要求的文件名及目录名。当recursion为true时，返回此目录下所有满足过滤要求的文件的相对路径（以“/”开头）。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ListFileOptions-recursion?: boolean--><!--Device-ListFileOptions-recursion?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

