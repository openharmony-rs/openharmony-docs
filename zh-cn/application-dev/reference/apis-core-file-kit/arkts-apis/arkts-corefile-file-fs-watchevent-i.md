# WatchEvent

事件类

**起始版本：** 10

<!--Device-unnamed-export interface WatchEvent--><!--Device-unnamed-export interface WatchEvent-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## cookie

```TypeScript
readonly cookie: number
```

绑定相关事件的cookie。当前仅支持事件IN_MOVED_FROM与IN_MOVED_TO，同一个文件的移动事件IN_MOVED_FROM和IN_MOVED_TO具有相同的cookie值。

**类型：** number

**起始版本：** 10

<!--Device-WatchEvent-readonly cookie: number--><!--Device-WatchEvent-readonly cookie: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## event

```TypeScript
readonly event: number
```

监听变动的事件集，多个事件通过或(|)的方式进行集合。

- 0x1: IN_ACCESS， 文件被访问。

- 0x2: IN_MODIFY，文件内容被修改。

- 0x4: IN_ATTRIB，文件元数据被修改。

- 0x8: IN_CLOSE_WRITE，文件在打开时进行了写操作，然后被关闭。

- 0x10: IN_CLOSE_NOWRITE，文件或目录在打开时未进行写操作，然后被关闭。

- 0x20: IN_OPEN，文件或目录被打开。

- 0x40: IN_MOVED_FROM，监听目录中文件被移动走。

- 0x80: IN_MOVED_TO，监听目录中文件被移动过来。

- 0x100: IN_CREATE，监听目录中文件或子目录被创建。

- 0x200: IN_DELETE，监听目录中文件或子目录被删除。

- 0x400: IN_DELETE_SELF，监听的目录被删除，删除后监听停止。

- 0x800: IN_MOVE_SELF，监听的文件或目录被移动，移动后监听继续。

- 0xfff: IN_ALL_EVENTS，监听以上所有事件。

**类型：** number

**起始版本：** 10

<!--Device-WatchEvent-readonly event: number--><!--Device-WatchEvent-readonly event: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## fileName

```TypeScript
readonly fileName: string
```

发生监听事件对应文件的沙箱路径，该沙箱路径包含文件名称。

**类型：** string

**起始版本：** 10

<!--Device-WatchEvent-readonly fileName: string--><!--Device-WatchEvent-readonly fileName: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

