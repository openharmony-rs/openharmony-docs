# @ohos.file.fs

FileIO

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [fileIo](arkts-na-fileio-n.md) | FileIO |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ConflictFiles](arkts-na-file-fs-conflictfiles-i.md) | 冲突文件信息，支持copyDir及moveDir接口使用。 |
| [FileFilter](arkts-na-file-fs-filefilter-i.md) | 文件名过滤器接口，可通过该接口自定义文件名过滤规则。 |
| [Filter](arkts-na-file-fs-filter-i.md) | 文件过滤配置项，支持listFile接口使用。 |
| [ListFileExtOptions](arkts-na-file-fs-listfileextoptions-i.md) | 可选项类型，支持listFileExt接口使用。 |
| [ListFileOptions](arkts-na-file-fs-listfileoptions-i.md) | 可选项类型，支持listFile接口使用。 |
| [Options](arkts-na-file-fs-options-i.md) | 可选项类型，支持readLines接口使用。 |
| [RandomAccessFileOptions](arkts-na-file-fs-randomaccessfileoptions-i.md) | 可选项类型，支持 createRandomAccessFile 接口使用。 |
| [ReadOptions](arkts-na-file-fs-readoptions-i.md) | 可选项类型，支持read接口使用。 |
| [ReadStreamOptions](arkts-na-file-fs-readstreamoptions-i.md) | 可选项类型，支持 createReadStream 接口使用。 |
| [ReadTextOptions](arkts-na-file-fs-readtextoptions-i.md) | 可选项类型，支持readText接口使用，ReadTextOptions继承自[ReadOptions](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-readoptions-i.md#ReadOptions)。 |
| [ReaderIteratorResult](arkts-na-file-fs-readeriteratorresult-i.md) | 文件读取迭代器返回结果，支持ReaderIterator接口使用。 |
| [WatchEvent](arkts-na-file-fs-watchevent-i.md) | 事件类 |
| [WriteOptions](arkts-na-file-fs-writeoptions-i.md) | 可选项类型，支持write接口使用，WriteOptions继承自[Options](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-options-i.md#Options)。 |
| [WriteStreamOptions](arkts-na-file-fs-writestreamoptions-i.md) | 可选项类型，支持 createWriteStream 接口使用。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [AtomicFile](arkts-na-atomicfile-t.md) | AtomicFile类。 |
| [TaskSignal](arkts-na-tasksignal-t.md) | 拷贝中断信号。 |
| [WatchEventListener](arkts-na-watcheventlistener-t.md) | 事件监听类，当监听的文件或目录发生变动事件时触发回调。 |
| [Watcher](arkts-na-watcher-t.md) | 文件目录变化监听对象。由createWatcher接口获得。 |

