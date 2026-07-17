# ReaderIteratorResult

文件读取迭代器返回结果，支持ReaderIterator接口使用。

**起始版本：** 11

<!--Device-unnamed-export interface ReaderIteratorResult--><!--Device-unnamed-export interface ReaderIteratorResult-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## done

```TypeScript
done: boolean
```

迭代器是否已完成迭代。true：已完成迭代；false：未完成迭代。

**类型：** boolean

**起始版本：** 11

<!--Device-ReaderIteratorResult-done: boolean--><!--Device-ReaderIteratorResult-done: boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## value

```TypeScript
value: string
```

逐行读取的文件文本内容。

**类型：** string

**起始版本：** 11

<!--Device-ReaderIteratorResult-value: string--><!--Device-ReaderIteratorResult-value: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

