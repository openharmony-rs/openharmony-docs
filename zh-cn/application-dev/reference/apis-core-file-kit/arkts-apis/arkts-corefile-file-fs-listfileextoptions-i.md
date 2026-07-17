# ListFileExtOptions

可选项类型，支持listFileExt接口使用自定义过滤规则。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface ListFileExtOptions--><!--Device-unnamed-export interface ListFileExtOptions-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## fileFilter

```TypeScript
fileFilter?: FileFilter
```

文件名过滤器接口。可选，设置自定义文件名过滤规则。

**类型：** FileFilter

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListFileExtOptions-fileFilter?: FileFilter--><!--Device-ListFileExtOptions-fileFilter?: FileFilter-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## listNum

```TypeScript
listNum?: number
```

列出文件名数量。可选，当设置0时，列出所有文件，默认为0。取值限定为整数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListFileExtOptions-listNum?: number--><!--Device-ListFileExtOptions-listNum?: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## recursion

```TypeScript
recursion?: boolean
```

是否递归子目录下文件名。可选，默认为false。当recursion为false时，返回当前目录下满足过滤要求的文件名及目录名。当recursion为true时，返回此目录下所有满足过滤要求的文件的相对路径（以“/”开头）。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListFileExtOptions-recursion?: boolean--><!--Device-ListFileExtOptions-recursion?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

