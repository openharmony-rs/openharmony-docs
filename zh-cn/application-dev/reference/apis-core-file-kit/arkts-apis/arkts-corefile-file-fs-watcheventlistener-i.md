# WatchEventListener

事件监听类，当监听的文件或目录发生变动事件时触发回调。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## [[Call]]

```TypeScript
(event: WatchEvent): void
```

文件或目录发生变动事件时触发的回调。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [WatchEvent](arkts-corefile-file-fs-watchevent-i.md) | 是 | 回调的事件类。 |
