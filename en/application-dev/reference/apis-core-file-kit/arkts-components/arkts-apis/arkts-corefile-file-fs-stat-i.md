# Stat

```TypeScript
declare interface Stat
```

Represents detailed file information. Before calling any API of the **Stat()** class, use [stat()](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiostat) to create a **Stat** instance.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## isBlockDevice

```TypeScript
isBlockDevice(): boolean
```

Checks whether this file is a block special file. A block special file supports access by block only, and it is cached when accessed.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the file is a block special file. The value **true** means the file is a block special file; the value **false** means the file is not a block special file. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let isBLockDevice = fileIo.statSync(filePath).isBlockDevice();
```

## isCharacterDevice

```TypeScript
isCharacterDevice(): boolean
```

Checks whether this file is a character special file. A character special device supports random access, and it is not cached when accessed.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the file is a character special device. The value **true** means the file is a character special device; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let isCharacterDevice = fileIo.statSync(filePath).isCharacterDevice();
```

## isDirectory

```TypeScript
isDirectory(): boolean
```

Checks whether this file is a directory.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the file is a directory. The value **true** means the file is a directory; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

**Examples**

```TypeScript
let dirPath = pathDir + "/test";
let isDirectory = fileIo.statSync(dirPath).isDirectory();
```

## isFIFO

```TypeScript
isFIFO(): boolean
```

Checks whether this file is a named pipe (or FIFO). Named pipes are used for inter-process communication.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the file is an FIFO. The value **true** means the file is an FIFO; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let isFIFO = fileIo.statSync(filePath).isFIFO();
```

## isFile

```TypeScript
isFile(): boolean
```

Checks whether this file is a regular file.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the file is a regular file. The value **true** means that the file is a regular file; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let isFile = fileIo.statSync(filePath).isFile();
```

## isSocket

```TypeScript
isSocket(): boolean
```

Checks whether this file is a socket.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the file is a socket. The value **true** means that the file is a socket; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let isSocket = fileIo.statSync(filePath).isSocket();
```

## isSymbolicLink

```TypeScript
isSymbolicLink(): boolean
```

Checks whether this file is a symbolic link.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the file is a symbolic link. The value **true** means that the file is a symbolic link; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let isSymbolicLink = fileIo.statSync(filePath).isSymbolicLink();
```

## atime

```TypeScript
readonly atime: number
```

Time when the file was last accessed. The value is the number of seconds elapsed since 00:00:00 on January 1, 1970.

**Note:**  Currently, user data partitions are mounted in **noatime** mode by default, and **atime** update is disabled.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

## atimeNs

```TypeScript
readonly atimeNs?:bigint
```

Time of the last access to the file. The value is the number of nanoseconds elapsed since 00:00:00 on January 1, 1970.

**Note:**  Currently, user data partitions are mounted in **noatime** mode by default, and **atime** update is disabled.

**Type:** bigint

**Since:** 15

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900042 | Internal error |

## ctime

```TypeScript
readonly ctime: number
```

Time when the file metadata was last modified. The value is the number of seconds elapsed since 00:00:00 on January 1, 1970.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

## ctimeNs

```TypeScript
readonly ctimeNs?:bigint
```

Time of the last status change of the file. The value is the number of nanoseconds elapsed since 00:00:00 on January 1, 1970.

**Type:** bigint

**Since:** 15

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900042 | Internal error |

## gid

```TypeScript
readonly gid: number
```

ID of the user group of the file.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

## ino

```TypeScript
readonly ino: bigint
```

File ID. Different files on the same device have different **ino**s.

**Type:** bigint

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

## location

```TypeScript
readonly location: LocationType
```

File location, which indicates whether the file is stored in a local device or in the cloud.

**Type:** [LocationType](arkts-corefile-file-fs-locationtype-e.md)

**Since:** 11

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900042 | Unknown error |

## mode

```TypeScript
readonly mode: number
```

File permissions. The meaning of each bit is as follows:

Note: The following values are in octal format. The return values are in decimal format. You need to convert the values.

- **0o400**: The user has the read permission on a regular file or a directory entry.  
- **0o200**: The user has the permission to write a regular file or create and delete a directory entry.  
- **0o100**: The user has the permission to execute a regular file or search for the specified path in a directory.  
- **0o040**: The user group has the read permission on a regular file or a directory entry.  
- **0o020**: The user group has the permission to write a regular file or create and delete a directory entry.  
- **0o010**: The user group has the permission to execute a regular file or search for the specified path in a  
directory.  
- **0o004**: Other users have the permission to read a regular file or read a directory entry.  
- **0o002**: Other users have the permission to write a regular file or create and delete a directory entry.  
- **0o001**: Other users have the permission to execute a regular file or search for the specified path in a  
directory.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

## mtime

```TypeScript
readonly mtime: number
```

Time when the file content was last modified. The value is the number of seconds elapsed since 00:00:00 on January 1, 1970.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

## mtimeNs

```TypeScript
readonly mtimeNs?:bigint
```

Time of the last modification to the file. The value is the number of nanoseconds elapsed since 00:00:00 on January 1, 1970.

**Type:** bigint

**Since:** 15

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900042 | Internal error |

## size

```TypeScript
readonly size: number
```

File size, in bytes. This parameter is valid only for regular files.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

## uid

```TypeScript
readonly uid: number
```

ID of the file owner.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |
