# WatchEventListener

事件监听类。

**起始版本：** 10

<!--Device-unnamed-export interface WatchEventListener--><!--Device-unnamed-export interface WatchEventListener-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## constructor

```TypeScript
(event: WatchEvent): void
```

Specifies the callback function to be invoked.

**起始版本：** 10

<!--Device-WatchEventListener-(event: WatchEvent): void--><!--Device-WatchEventListener-(event: WatchEvent): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [WatchEvent](arkts-corefile-file-fs-watchevent-i.md) | 是 | Event for the callback to invoke. |

