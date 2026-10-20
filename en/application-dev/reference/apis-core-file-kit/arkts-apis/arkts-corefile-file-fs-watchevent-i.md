# WatchEvent

```TypeScript
export interface WatchEvent
```

Defines the event to observe.

**Since:** 10

<!--Device-unnamed-export interface WatchEvent--><!--Device-unnamed-export interface WatchEvent-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## cookie

```TypeScript
readonly cookie: number
```

Cookie bound with the event.

Currently, only the **IN_MOVED_FROM** and **IN_MOVED_TO** events are supported. The **IN_MOVED_FROM** and **IN_MOVED_TO** events of the same file have the same **cookie** value.

**Type:** number

**Since:** 10

<!--Device-WatchEvent-readonly cookie: number--><!--Device-WatchEvent-readonly cookie: number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## event

```TypeScript
readonly event: number
```

Events to observe. Multiple events can be separated by vertical bars (\|). <br>  
- <b>0x1: IN_ACCESS</b>: A file is accessed. <br>  
- <b>0x2: IN_MODIFY</b>: The file content is modified. <br>  
- <b>0x4: IN_ATTRIB</b>: Metadata is changed. <br>  
- <b>0x8: IN_CLOSE_WRITE</b>: A file is opened, written with data, and then closed. <br>  
- <b>0x10: IN_CLOSE_NOWRITE</b>: A file or directory is opened and then closed without being written. <br>  
- <b>0x20: IN_OPEN</b>: A file or directory is opened. <br>  
- <b>0x40: IN_MOVED_FROM</b>: A file in the observed directory is moved. <br>  
- <b>0x80: IN_MOVED_TO</b>: A file in the observed directory is moved. <br>  
- <b>0x100: IN_CREATE</b>: A file or directory is created in the observed directory. <br>  
- <b>0x200: IN_DELETE</b>: A file or directory is deleted from the observed directory. <br>  
- <b>0x400: IN_DELETE_SELF</b>: The observed directory is deleted. After the directory is deleted,  
the listening stops. <br>  
- <b>0x800: IN_MOVE_SELF</b>: The observed file or directory is moved. After the file or directory is moved,  
the listening continues. <br>  
- <b>0xfff: IN_ALL_EVENTS</b>: All events.

**Type:** number

**Since:** 10

<!--Device-WatchEvent-readonly event: number--><!--Device-WatchEvent-readonly event: number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## fileName

```TypeScript
readonly fileName: string
```

Sandbox path of the file to observe. The sandbox path contains the file name.

**Type:** string

**Since:** 10

<!--Device-WatchEvent-readonly fileName: string--><!--Device-WatchEvent-readonly fileName: string-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO
