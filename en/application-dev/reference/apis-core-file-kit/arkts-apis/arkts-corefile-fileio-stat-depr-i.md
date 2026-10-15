# Stat

```TypeScript
declare interface Stat
```

Provides detailed file information. Before calling a method of the **Stat** class, use the [stat()](arkts-corefile-fileio-stat-f.md) method synchronously or asynchronously to create a **Stat** instance.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [Stat](arkts-corefile-file-fs-stat-i.md)

<!--Device-unnamed-declare interface Stat--><!--Device-unnamed-declare interface Stat-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
```

## isBlockDevice

```TypeScript
isBlockDevice(): boolean
```

Checks whether this file is a block special file. A block special file supports access by block only, and it is cached when accessed.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [isBlockDevice](arkts-corefile-file-fs-stat-i.md#isblockdevice)

<!--Device-Stat-isBlockDevice(): boolean--><!--Device-Stat-isBlockDevice(): boolean-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if it is a block special file; returns **false** otherwise. |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let isBLockDevice = fileio.statSync(filePath).isBlockDevice();
```

## isCharacterDevice

```TypeScript
isCharacterDevice(): boolean
```

Checks whether this file is a character special file. A character special file supports random access, and it is not cached when accessed.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [isCharacterDevice](arkts-corefile-file-fs-stat-i.md#ischaracterdevice)

<!--Device-Stat-isCharacterDevice(): boolean--><!--Device-Stat-isCharacterDevice(): boolean-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if it is a character special file; returns **false** otherwise. |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let isCharacterDevice = fileio.statSync(filePath).isCharacterDevice();
```

## isDirectory

```TypeScript
isDirectory(): boolean
```

Checks whether this file is a directory.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [isDirectory](arkts-corefile-file-fs-stat-i.md#isdirectory)

<!--Device-Stat-isDirectory(): boolean--><!--Device-Stat-isDirectory(): boolean-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if it is a directory; returns **false** otherwise. |

**Examples**

```TypeScript
let dirPath = pathDir + "/test";
let isDirectory = fileio.statSync(dirPath).isDirectory();
```

## isFIFO

```TypeScript
isFIFO(): boolean
```

Checks whether this file is a named pipe (or FIFO). Named pipes are used for inter-process communication.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [isFIFO](arkts-corefile-file-fs-stat-i.md#isfifo)

<!--Device-Stat-isFIFO(): boolean--><!--Device-Stat-isFIFO(): boolean-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if it is a named pipe; returns **false** otherwise. |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let isFIFO = fileio.statSync(filePath).isFIFO();
```

## isFile

```TypeScript
isFile(): boolean
```

Checks whether this file is a regular file.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [isFile](arkts-corefile-file-fs-stat-i.md#isfile)

<!--Device-Stat-isFile(): boolean--><!--Device-Stat-isFile(): boolean-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if it is a regular file; returns **false** otherwise. |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let isFile = fileio.statSync(filePath).isFile();
```

## isSocket

```TypeScript
isSocket(): boolean
```

Checks whether this file is a socket.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [isSocket](arkts-corefile-file-fs-stat-i.md#issocket)

<!--Device-Stat-isSocket(): boolean--><!--Device-Stat-isSocket(): boolean-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if it is a socket; returns **false** otherwise. |

**Examples**

```TypeScript
let filePath = pathDir + "/test.txt";
let isSocket = fileio.statSync(filePath).isSocket();
```

## isSymbolicLink

```TypeScript
isSymbolicLink(): boolean
```

Checks whether this file is a symbolic link.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [isSymbolicLink](arkts-corefile-file-fs-stat-i.md#issymboliclink)

<!--Device-Stat-isSymbolicLink(): boolean--><!--Device-Stat-isSymbolicLink(): boolean-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if it is a symbolic link; returns **false** otherwise. |

**Examples**

```TypeScript
let filePath = pathDir + "/test";
let isSymbolicLink = fileio.statSync(filePath).isSymbolicLink();
```

## atime

```TypeScript
readonly atime: number
```

Time when the file was last accessed. The value is the number of seconds elapsed since 00:00:00 on January 1, 1970.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [atime](arkts-corefile-file-fs-stat-i.md#atime)

<!--Device-Stat-readonly atime: number--><!--Device-Stat-readonly atime: number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## blocks

```TypeScript
readonly blocks: number
```

Number of blocks occupied by a file. Each block is 512 bytes.

**Type:** number

**Since:** 6

**Deprecated since:** 9

<!--Device-Stat-readonly blocks: number--><!--Device-Stat-readonly blocks: number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## ctime

```TypeScript
readonly ctime: number
```

Time of the last status change of the file. The value is the number of seconds elapsed since 00:00:00 on January 1, 1970.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [ctime](arkts-corefile-file-fs-stat-i.md#ctime)

<!--Device-Stat-readonly ctime: number--><!--Device-Stat-readonly ctime: number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## dev

```TypeScript
readonly dev: number
```

Major device number.

**Type:** number

**Since:** 6

**Deprecated since:** 9

<!--Device-Stat-readonly dev: number--><!--Device-Stat-readonly dev: number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## gid

```TypeScript
readonly gid: number
```

ID of the user group of the file.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [gid](arkts-corefile-file-fs-stat-i.md#gid)

<!--Device-Stat-readonly gid: number--><!--Device-Stat-readonly gid: number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## ino

```TypeScript
readonly ino: number
```

File identifier, which varies with files on the same device.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [ino](arkts-corefile-file-fs-stat-i.md#ino)

<!--Device-Stat-readonly ino: number--><!--Device-Stat-readonly ino: number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## mode

```TypeScript
readonly mode: number
```

File type and permissions. The first four bits indicate the file type, and the last 12 bits indicate the permissions. The bit fields are described as follows:  
- **0o170000**: mask used to obtain the file type.  
- **0o140000**: The file is a socket.  
- **0o120000**: The file is a symbolic link.  
- **0o100000**: The file is a regular file.  
- **0o060000**: The file is a block device.  
- **0o040000**: The file is a directory.  
- **0o020000**: The file is a character device.  
- **0o010000**: The file is a named pipe (FIFO).  
- **0o0700**: mask used to obtain the owner permissions.  
- **0o0400**: The owner has the permission to read a regular file or a directory entry.  
- **0o0200**: The owner has the permission to write a regular file or create and delete a directory entry.  
- **0o0100**: The owner has the permission to execute a regular file or search for the specified path in a  
directory.  
- **0o0070**: mask used to obtain the user group permissions.  
- **0o0040**: The user group has the permission to read a regular file or a directory entry.  
- **0o0020**: The user group has the permission to write a regular file or create and delete a directory entry.  
- **0o0010**: The user group has the permission to execute a regular file or search for the specified path in a  
directory.  
- **0o0007**: mask used to obtain the permissions of other users.  
- **0o0004**: Other users have the permission to read a regular file or a directory entry.  
- **0o0002**: Other users have the permission to write a regular file or create and delete a directory entry.  
- **0o0001**: Other users have the permission to execute a regular file or search for the specified path in a  
directory.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [mode](arkts-corefile-file-fs-stat-i.md#mode)

<!--Device-Stat-readonly mode: number--><!--Device-Stat-readonly mode: number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## mtime

```TypeScript
readonly mtime: number
```

Time when the file content was last modified. The value is the number of seconds elapsed since 00:00:00 on January 1, 1970.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [mtime](arkts-corefile-file-fs-stat-i.md#mtime)

<!--Device-Stat-readonly mtime: number--><!--Device-Stat-readonly mtime: number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## nlink

```TypeScript
readonly nlink: number
```

Number of hard links in the file.

**Type:** number

**Since:** 6

**Deprecated since:** 9

<!--Device-Stat-readonly nlink: number--><!--Device-Stat-readonly nlink: number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## rdev

```TypeScript
readonly rdev: number
```

Minor device number.

**Type:** number

**Since:** 6

**Deprecated since:** 9

<!--Device-Stat-readonly rdev: number--><!--Device-Stat-readonly rdev: number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## size

```TypeScript
readonly size: number
```

File size, in bytes. This parameter is valid only for regular files.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [size](arkts-corefile-file-fs-stat-i.md#size)

<!--Device-Stat-readonly size: number--><!--Device-Stat-readonly size: number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## uid

```TypeScript
readonly uid: number
```

ID of the file owner.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [uid](arkts-corefile-file-fs-stat-i.md#uid)

<!--Device-Stat-readonly uid: number--><!--Device-Stat-readonly uid: number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO
