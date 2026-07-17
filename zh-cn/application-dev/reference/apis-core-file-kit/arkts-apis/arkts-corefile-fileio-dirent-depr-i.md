# Dirent

在调用Dirent的方法前，需要先通过[dir.read()](arkts-corefile-fileio-read-f.md#read-1)方法（同步或异步）来构建一个Dirent实例。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1)

<!--Device-unnamed-declare interface Dirent--><!--Device-unnamed-declare interface Dirent-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## isBlockDevice

```TypeScript
isBlockDevice(): boolean
```

用于判断当前目录项是否是块特殊文件。一个块特殊文件只能以块为粒度进行访问，且访问的时候带缓存。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1)

<!--Device-Dirent-isBlockDevice(): boolean--><!--Device-Dirent-isBlockDevice(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示当前目录项是否是块特殊设备。true为是，false为不是。 |

**示例：**

```TypeScript
let dir = fileio.opendirSync(pathDir);
let isBLockDevice = dir.readSync().isBlockDevice();

```

## isCharacterDevice

```TypeScript
isCharacterDevice(): boolean
```

用于判断当前目录项是否是字符特殊设备。一个字符特殊设备可进行随机访问，且访问的时候不带缓存。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1)

<!--Device-Dirent-isCharacterDevice(): boolean--><!--Device-Dirent-isCharacterDevice(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示当前目录项是否是字符特殊设备。true为是，false为不是。 |

**示例：**

```TypeScript
let dir = fileio.opendirSync(pathDir);
let isCharacterDevice = dir.readSync().isCharacterDevice(); 

```

## isDirectory

```TypeScript
isDirectory(): boolean
```

用于判断当前目录项是否是目录。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1)

<!--Device-Dirent-isDirectory(): boolean--><!--Device-Dirent-isDirectory(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示当前目录项是否是目录。true为是，false为不是。 |

**示例：**

```TypeScript
let dir = fileio.opendirSync(pathDir);
let isDirectory = dir.readSync().isDirectory(); 

```

## isFIFO

```TypeScript
isFIFO(): boolean
```

用于判断当前目录项是否是命名管道（有时也称为FIFO）。命名管道通常用于进程间通信。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1)

<!--Device-Dirent-isFIFO(): boolean--><!--Device-Dirent-isFIFO(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示当前目录项是否是FIFO。true为是，false为不是。 |

**示例：**

```TypeScript
let dir = fileio.opendirSync(pathDir);
let isFIFO = dir.readSync().isFIFO(); 

```

## isFile

```TypeScript
isFile(): boolean
```

用于判断当前目录项是否是普通文件。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1)

<!--Device-Dirent-isFile(): boolean--><!--Device-Dirent-isFile(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示当前目录项是否是普通文件。true为是，false为不是。 |

**示例：**

```TypeScript
let dir = fileio.opendirSync(pathDir);
let isFile = dir.readSync().isFile(); 

```

## isSocket

```TypeScript
isSocket(): boolean
```

用于判断当前目录项是否是套接字。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1)

<!--Device-Dirent-isSocket(): boolean--><!--Device-Dirent-isSocket(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示当前目录项是否是套接字。true为是，false为不是。 |

**示例：**

```TypeScript
let dir = fileio.opendirSync(pathDir);
let isSocket = dir.readSync().isSocket(); 

```

## isSymbolicLink

```TypeScript
isSymbolicLink(): boolean
```

用于判断当前目录项是否是符号链接。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1)

<!--Device-Dirent-isSymbolicLink(): boolean--><!--Device-Dirent-isSymbolicLink(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示当前目录项是否是符号链接。true为是，false为不是。 |

**示例：**

```TypeScript
let dir = fileio.opendirSync(pathDir);
let isSymbolicLink = dir.readSync().isSymbolicLink();

```

## name

```TypeScript
readonly name: string
```

目录项的名称。

**类型：** string

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1)

<!--Device-Dirent-readonly name: string--><!--Device-Dirent-readonly name: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

