# WatchEventListener

(event: WatchEvent): void

Provides APIs for observing events.

**Since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## [[Call]]

```TypeScript
(event: WatchEvent): void
```

Specifies the callback function to be invoked.

**Since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [WatchEvent](arkts-corefile-file-fs-watchevent-i.md) | Yes | Event for the callback to invoke. |
