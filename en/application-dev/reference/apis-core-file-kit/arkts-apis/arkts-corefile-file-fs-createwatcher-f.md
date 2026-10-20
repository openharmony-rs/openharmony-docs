# createWatcher

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## createWatcher

```TypeScript
declare function createWatcher(path: string, events: number, listener: WatchEventListener): Watcher
```

Creates a <b>Watcher</b> object to listen for file or directory changes such as creating, deleting, and modifying.

**Since:** 10

<!--Device-unnamed-declare function createWatcher(path: string, events: number, listener: WatchEventListener): Watcher--><!--Device-unnamed-declare function createWatcher(path: string, events: number, listener: WatchEventListener): Watcher-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the file or directory to observe. |
| events | number | Yes | Events to observe. Multiple events can be separated by vertical bars (\&#124;). <br>           - <b>0x1: IN_ACCESS</b>: A file is accessed. <br>           - <b>0x2: IN_MODIFY</b>: The file content is modified. <br>           - <b>0x4: IN_ATTRIB</b>: Metadata is changed. <br>           - <b>0x8: IN_CLOSE_WRITE</b>: A file is opened, written with data, and then closed. <br>           - <b>0x10: IN_CLOSE_NOWRITE</b>: A file or directory is opened and then closed without being written. <br>           - <b>0x20: IN_OPEN</b>: A file or directory is opened. <br>           - <b>0x40: IN_MOVED_FROM</b>: A file in the observed directory is moved. <br>           - <b>0x80: IN_MOVED_TO</b>: A file in the observed directory is moved. <br>           - <b>0x100: IN_CREATE</b>: A file or directory is created in the observed directory. <br>           - <b>0x200: IN_DELETE</b>: A file or directory is deleted from the observed directory. <br>           - <b>0x400: IN_DELETE_SELF</b> : The observed directory is deleted. After the directory is deleted,   the listening stops. <br>           - <b>0x800: IN_MOVE_SELF</b>: The observed file or directory is moved. After the file or directory is moved,   the listening continues. <br>           - <b>0xfff: IN_ALL_EVENTS</b>: All events. |
| listener | [WatchEventListener](arkts-corefile-file-fs-watcheventlistener-i.md) | Yes | Callback invoked when an observed event occurs. The callback will be invoked each time an observed event occurs. |

**Return value:**

| Type | Description |
| --- | --- |
| [Watcher](arkts-corefile-file-fs-watcher-i.md) | <b>Watcher</b> object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900015 | File exists |
| 13900018 | Not a directory |
| 13900020 | Invalid argument |
| 13900021 | File table overflow |
| 13900022 | Too many open files |
| 13900025 | No space left on device |
| 13900030 | File name too long |
| 13900042 | Unknown error |
