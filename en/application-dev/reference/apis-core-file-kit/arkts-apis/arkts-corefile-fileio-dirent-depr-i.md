# Dirent

Provides information about files and directories. Before calling an API of the **Dirent** class, use [dir.read()](arkts-corefile-fileio-read-f.md) synchronously or asynchronously to create a **Dirent** instance.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [listFile](arkts-corefile-file-fs-listfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
```

## isBlockDevice

```TypeScript
isBlockDevice(): boolean
```

Checks whether this directory entry is a block special file. A block special file supports access by block only, and it is cached when accessed.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [listFile](arkts-corefile-file-fs-listfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if it is a block special file; returns **false** otherwise. |

**Examples**

```TypeScript
let dir = fileio.opendirSync(pathDir);
let isBLockDevice = dir.readSync().isBlockDevice();
```

## isCharacterDevice

```TypeScript
isCharacterDevice(): boolean
```

Checks whether this directory entry is a character special file. A character special file supports random access, and it is not cached when accessed.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [listFile](arkts-corefile-file-fs-listfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if it is a character special file; returns **false** otherwise. |

**Examples**

```TypeScript
let dir = fileio.opendirSync(pathDir);
let isCharacterDevice = dir.readSync().isCharacterDevice();
```

## isDirectory

```TypeScript
isDirectory(): boolean
```

Checks whether this directory entry is a directory.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [listFile](arkts-corefile-file-fs-listfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if it is a directory; returns **false** otherwise. |

**Examples**

```TypeScript
let dir = fileio.opendirSync(pathDir);
let isDirectory = dir.readSync().isDirectory();
```

## isFIFO

```TypeScript
isFIFO(): boolean
```

Checks whether this directory entry is a named pipe (also called FIFO). Named pipes are used for inter-process communication.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [listFile](arkts-corefile-file-fs-listfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if it is a named pipe; returns **false** otherwise. |

**Examples**

```TypeScript
let dir = fileio.opendirSync(pathDir);
let isFIFO = dir.readSync().isFIFO();
```

## isFile

```TypeScript
isFile(): boolean
```

Checks whether this directory entry is a regular file.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [listFile](arkts-corefile-file-fs-listfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if it is a regular file; returns **false** otherwise. |

**Examples**

```TypeScript
let dir = fileio.opendirSync(pathDir);
let isFile = dir.readSync().isFile();
```

## isSocket

```TypeScript
isSocket(): boolean
```

Checks whether this directory entry is a socket.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [listFile](arkts-corefile-file-fs-listfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if it is a socket; returns **false** otherwise. |

**Examples**

```TypeScript
let dir = fileio.opendirSync(pathDir);
let isSocket = dir.readSync().isSocket();
```

## isSymbolicLink

```TypeScript
isSymbolicLink(): boolean
```

Checks whether this directory entry is a symbolic link.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [listFile](arkts-corefile-file-fs-listfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if it is a symbolic link; returns **false** otherwise. |

**Examples**

```TypeScript
let dir = fileio.opendirSync(pathDir);
let isSymbolicLink = dir.readSync().isSymbolicLink();
```

## name

```TypeScript
readonly name: string
```

Directory entry name.

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [listFile](arkts-corefile-file-fs-listfile-f.md)

**System capability:** SystemCapability.FileManagement.File.FileIO
