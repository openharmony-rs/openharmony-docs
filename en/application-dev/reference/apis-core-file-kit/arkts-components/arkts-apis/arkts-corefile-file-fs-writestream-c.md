# WriteStream

Defines a writeable stream. You need to use [fileIo.createWriteStream](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiocreatewritestream12) to create a **WriteStream** instance, which is inherited from [stream.Writable](../../apis-arkts/arkts-apis/arkts-arkts-stream-writable-c.md).

**Inheritance/Implementation:** WriteStream extends [stream.Writable](../../apis-arkts/arkts-apis/arkts-arkts-stream-writable-c.md)

**Since:** 12

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## close

```TypeScript
close(): void
```

Closes this writeable stream.

**Since:** 12

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**Examples**

```TypeScript
const filePath = pathDir + "/test.txt";
const ws = fileIo.createWriteStream(filePath);
ws.close();
```

## constructor

```TypeScript
constructor()
```

The WriteStream constructor.

**Since:** 12

**System capability:** SystemCapability.FileManagement.File.FileIO

## seek

```TypeScript
seek(offset: number, whence?: WhenceType): number
```

Adjusts the position of the writeable stream offset pointer.

**Since:** 12

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Relative offset, in bytes. |
| whence | [WhenceType](arkts-corefile-file-fs-whencetype-e.md) | No | Where to start the offset. The default value is **SEEK_SET**, which indicates the beginning of the file. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Position of the current offset pointer (offset relative to the file header, in bytes). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error |
| 13900020 | Invalid argument |
| 13900026 | Illegal seek |
| 13900042 | Unknown error |

**Examples**

```TypeScript
const filePath = pathDir + "/test.txt";
const ws = fileIo.createWriteStream(filePath);
const curOff = ws.seek(5, fileIo.WhenceType.SEEK_SET);
console.info(`Succeeded in seeking, current offset is ${curOff}`);
ws.close();
```

## bytesWritten

```TypeScript
readonly bytesWritten: number
```

Number of bytes written to the writable stream.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900042 | Unknown error |

## path

```TypeScript
readonly path: string
```

Path of the file corresponding to the writeable stream.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900042 | Unknown error |
