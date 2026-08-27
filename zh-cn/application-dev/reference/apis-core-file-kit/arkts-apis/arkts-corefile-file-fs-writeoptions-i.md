# WriteOptions

可选项类型，支持write接口使用，WriteOptions继承自[Options](arkts-corefile-file-fs-options-i.md)。

**继承/实现关系：** WriteOptions extends [Options](arkts-corefile-file-fs-options-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## length

```TypeScript
length?: number
```

期望写入数据的长度，单位为Byte。可选，默认缓冲区长度。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

## offset

```TypeScript
offset?: number
```

期望写入文件位置，单位为Byte。可选，默认从当前位置开始写。

**类型：** number

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO
