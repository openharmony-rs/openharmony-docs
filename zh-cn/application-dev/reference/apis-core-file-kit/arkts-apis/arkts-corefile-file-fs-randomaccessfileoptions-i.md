# RandomAccessFileOptions

可选项类型，支持 createRandomAccessFile 接口使用。

**起始版本：** 12

<!--Device-unnamed-export interface RandomAccessFileOptions--><!--Device-unnamed-export interface RandomAccessFileOptions-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## end

```TypeScript
end?: number
```

表示期望读取结束的位置，单位为Byte。可选，默认文件末尾。

**类型：** number

**起始版本：** 12

<!--Device-RandomAccessFileOptions-end?: number--><!--Device-RandomAccessFileOptions-end?: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## start

```TypeScript
start?: number
```

表示期望读取文件的位置，单位为Byte。可选，默认从当前位置开始读。

**类型：** number

**起始版本：** 12

<!--Device-RandomAccessFileOptions-start?: number--><!--Device-RandomAccessFileOptions-start?: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

