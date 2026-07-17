# Stat

文件具体信息，在调用Stat的方法前，需要先通过[stat()](arkts-corefile-fileio-stat-f.md#stat-1)方法（同步或异步）来构建一个Stat实例。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:Stat](arkts-corefile-file-fs-stat-i.md)

<!--Device-unnamed-declare interface Stat--><!--Device-unnamed-declare interface Stat-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## isBlockDevice

```TypeScript
isBlockDevice(): boolean
```

用于判断文件是否是块特殊文件。一个块特殊文件只能以块为粒度进行访问，且访问的时候带缓存。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [isBlockDevice](arkts-corefile-file-fs-stat-i.md#isblockdevice-1)

<!--Device-Stat-isBlockDevice(): boolean--><!--Device-Stat-isBlockDevice(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示文件是否是块特殊设备。true为是，false为不是。 |

**示例：**

```TypeScript
let filePath = pathDir + "/test.txt";
let isBLockDevice = fileio.statSync(filePath).isBlockDevice();

```

## isCharacterDevice

```TypeScript
isCharacterDevice(): boolean
```

用于判断文件是否是字符特殊文件。一个字符特殊设备可进行随机访问，且访问的时候不带缓存。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [isCharacterDevice](arkts-corefile-file-fs-stat-i.md#ischaracterdevice-1)

<!--Device-Stat-isCharacterDevice(): boolean--><!--Device-Stat-isCharacterDevice(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示文件是否是字符特殊设备。true为是，false为不是。 |

**示例：**

```TypeScript
let filePath = pathDir + "/test.txt";
let isCharacterDevice = fileio.statSync(filePath).isCharacterDevice();

```

## isDirectory

```TypeScript
isDirectory(): boolean
```

用于判断文件是否是目录。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [isDirectory](arkts-corefile-file-fs-stat-i.md#isdirectory-1)

<!--Device-Stat-isDirectory(): boolean--><!--Device-Stat-isDirectory(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示文件是否是目录。true为是，false为不是。 |

**示例：**

```TypeScript
let dirPath = pathDir + "/test";
let isDirectory = fileio.statSync(dirPath).isDirectory(); 

```

## isFIFO

```TypeScript
isFIFO(): boolean
```

用于判断文件是否是命名管道（有时也称为FIFO）。命名管道通常用于进程间通信。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [isFIFO](arkts-corefile-file-fs-stat-i.md#isfifo-1)

<!--Device-Stat-isFIFO(): boolean--><!--Device-Stat-isFIFO(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示文件是否是?FIFO。true为是，false为不是。 |

**示例：**

```TypeScript
let filePath = pathDir + "/test.txt";
let isFIFO = fileio.statSync(filePath).isFIFO(); 

```

## isFile

```TypeScript
isFile(): boolean
```

用于判断文件是否是普通文件。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [isFile](arkts-corefile-file-fs-stat-i.md#isfile-1)

<!--Device-Stat-isFile(): boolean--><!--Device-Stat-isFile(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示文件是否是普通文件。true为是，false为不是。 |

**示例：**

```TypeScript
let filePath = pathDir + "/test.txt";
let isFile = fileio.statSync(filePath).isFile();

```

## isSocket

```TypeScript
isSocket(): boolean
```

用于判断文件是否是套接字。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [isSocket](arkts-corefile-file-fs-stat-i.md#issocket-1)

<!--Device-Stat-isSocket(): boolean--><!--Device-Stat-isSocket(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示文件是否是套接字。true为是，false为不是。 |

**示例：**

```TypeScript
let filePath = pathDir + "/test.txt";
let isSocket = fileio.statSync(filePath).isSocket(); 

```

## isSymbolicLink

```TypeScript
isSymbolicLink(): boolean
```

用于判断文件是否是符号链接。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [isSymbolicLink](arkts-corefile-file-fs-stat-i.md#issymboliclink-1)

<!--Device-Stat-isSymbolicLink(): boolean--><!--Device-Stat-isSymbolicLink(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示文件是否是符号链接。true为是，false为不是。 |

**示例：**

```TypeScript
let filePath = pathDir + "/test";
let isSymbolicLink = fileio.statSync(filePath).isSymbolicLink(); 

```

## atime

```TypeScript
readonly atime: number
```

上次访问该文件的时间，表示距1970年1月1日0时0分0秒的秒数。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [atime](arkts-corefile-file-fs-stat-i.md#atime)

<!--Device-Stat-readonly atime: number--><!--Device-Stat-readonly atime: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## blocks

```TypeScript
readonly blocks: number
```

文件占用的块数，计算时块大小按512B计算。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

<!--Device-Stat-readonly blocks: number--><!--Device-Stat-readonly blocks: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## ctime

```TypeScript
readonly ctime: number
```

最近改变文件状态的时间，表示距1970年1月1日0时0分0秒的秒数。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [ctime](arkts-corefile-file-fs-stat-i.md#ctime)

<!--Device-Stat-readonly ctime: number--><!--Device-Stat-readonly ctime: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## dev

```TypeScript
readonly dev: number
```

标识包含该文件的主设备号。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

<!--Device-Stat-readonly dev: number--><!--Device-Stat-readonly dev: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## gid

```TypeScript
readonly gid: number
```

文件所有组的ID。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [gid](arkts-corefile-file-fs-stat-i.md#gid)

<!--Device-Stat-readonly gid: number--><!--Device-Stat-readonly gid: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## ino

```TypeScript
readonly ino: number
```

标识该文件。通常同设备上的不同文件的INO不同。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** ino

<!--Device-Stat-readonly ino: number--><!--Device-Stat-readonly ino: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## mode

```TypeScript
readonly mode: number
```

表示文件类型及权限，其首?4?位表示文件类型，后?12?位表示权限。各特征位的含义如下：  
-?0o170000：可用于获取文件类型的掩码。  
-?0o140000：文件是套接字。  
-?0o120000：文件是符号链接。  
-?0o100000：文件是一般文件。  
-?0o060000：文件属于块设备。  
-?0o040000：文件是目录。  
-?0o020000：文件是字符设备。  
-?0o010000：文件是命名管道，即FIFO。  
-?0o0700：可用于获取用户权限的掩码。  
-?0o0400：用户读，对于普通文件，所有者可读取文件；对于目录，所有者可读取目录项。  
-?0o0200：用户写，对于普通文件，所有者可写入文件；对于目录，所有者可创建/删除目录项。  
-?0o0100：用户执行，对于普通文件，所有者可执行文件；对于目录，所有者可在目录中搜索给定路径名。  
-?0o0070：可用于获取用户组权限的掩码。  
-?0o0040：用户组读，对于普通文件，所有用户组可读取文件；对于目录，所有用户组可读取目录项。  
-?0o0020：用户组写，对于普通文件，所有用户组可写入文件；对于目录，所有用户组可创建/删除目录项。  
-?0o0010：用户组执行，对于普通文件，所有用户组可执行文件；对于目录，所有用户组是否可在目录中搜索给定路径名。  
-?0o0007：可用于获取其他用户权限的掩码。  
-?0o0004：其他读，对于普通文件，其余用户可读取文件；对于目录，其他用户组可读取目录项。  
-?0o0002：其他写，对于普通文件，其余用户可写入文件；对于目录，其他用户组可创建/删除目录项。  
-?0o0001：其他执行，对于普通文件，其余用户可执行文件；对于目录，其他用户组可在目录中搜索给定路径名。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [mode](arkts-corefile-file-fs-stat-i.md#mode)

<!--Device-Stat-readonly mode: number--><!--Device-Stat-readonly mode: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## mtime

```TypeScript
readonly mtime: number
```

上次修改该文件的时间，表示距1970年1月1日0时0分0秒的秒数。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [mtime](arkts-corefile-file-fs-stat-i.md#mtime)

<!--Device-Stat-readonly mtime: number--><!--Device-Stat-readonly mtime: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## nlink

```TypeScript
readonly nlink: number
```

文件的硬链接数。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

<!--Device-Stat-readonly nlink: number--><!--Device-Stat-readonly nlink: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## rdev

```TypeScript
readonly rdev: number
```

标识包含该文件的从设备号。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

<!--Device-Stat-readonly rdev: number--><!--Device-Stat-readonly rdev: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## size

```TypeScript
readonly size: number
```

文件的大小，单位为Byte。仅对普通文件有效。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [size](arkts-corefile-file-fs-stat-i.md#size)

<!--Device-Stat-readonly size: number--><!--Device-Stat-readonly size: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## uid

```TypeScript
readonly uid: number
```

文件所有者的ID。

**类型：** number

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [uid](arkts-corefile-file-fs-stat-i.md#uid)

<!--Device-Stat-readonly uid: number--><!--Device-Stat-readonly uid: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

