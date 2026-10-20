# WatchEventListener

```TypeScript
export interface WatchEventListener
```

Defines a watch event listener. When the monitored file or directory changes, a callback is triggered.

**Since:** 10

<!--Device-unnamed-export interface WatchEventListener--><!--Device-unnamed-export interface WatchEventListener-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## [[Call]]

```TypeScript
(event: WatchEvent): void
```

Callback invoked when the monitored file or directory changes.

**Since:** 10

<!--Device-WatchEventListener-(event: WatchEvent): void--><!--Device-WatchEventListener-(event: WatchEvent): void-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [WatchEvent](arkts-corefile-file-fs-watchevent-i.md) | Yes | Event for the callback to invoke. |
