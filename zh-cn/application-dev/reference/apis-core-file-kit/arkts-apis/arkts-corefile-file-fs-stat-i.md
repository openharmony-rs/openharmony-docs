# Stat

文件具体信息，在调用Stat的方法前，需要先通过[stat()](../../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiostat)方法（同步或异步）构建一个Stat实例。

**起始版本：** 9

<!--Device-unnamed-declare interface Stat--><!--Device-unnamed-declare interface Stat-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## isBlockDevice

```TypeScript
isBlockDevice(): boolean
```

用于判断文件是否是块特殊文件。一个块特殊文件只能以块为粒度进行访问，且访问的时候带缓存。

**起始版本：** 9

<!--Device-Stat-isBlockDevice(): boolean--><!--Device-Stat-isBlockDevice(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示文件是否是块特殊设备。true：是块特殊设备；false：不是块特殊设备。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

**示例：**

```TypeScript
let filePath = pathDir + "/test.txt";
let isBLockDevice = fileIo.statSync(filePath).isBlockDevice();

```

## isCharacterDevice

```TypeScript
isCharacterDevice(): boolean
```

判断文件是否为字符特殊文件。字符特殊设备支持随机访问，且访问时无缓存。

**起始版本：** 9

<!--Device-Stat-isCharacterDevice(): boolean--><!--Device-Stat-isCharacterDevice(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示文件是否是字符特殊设备。true：是字符特殊设备；false：不是字符特殊设备。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

**示例：**

```TypeScript
let filePath = pathDir + "/test.txt";
let isCharacterDevice = fileIo.statSync(filePath).isCharacterDevice();

```

## isDirectory

```TypeScript
isDirectory(): boolean
```

判断文件是否为目录。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Stat-isDirectory(): boolean--><!--Device-Stat-isDirectory(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示文件是否是目录。true：是目录；false：不是目录。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

**示例：**

```TypeScript
let dirPath = pathDir + "/test";
let isDirectory = fileIo.statSync(dirPath).isDirectory();

```

## isFIFO

```TypeScript
isFIFO(): boolean
```

用于判断文件是否是命名管道（有时也称为FIFO）。命名管道通常用于进程间通信。

**起始版本：** 9

<!--Device-Stat-isFIFO(): boolean--><!--Device-Stat-isFIFO(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示文件是否是 FIFO。true：是FIFO；false：不是FIFO。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

**示例：**

```TypeScript
let filePath = pathDir + "/test.txt";
let isFIFO = fileIo.statSync(filePath).isFIFO();

```

## isFile

```TypeScript
isFile(): boolean
```

用于判断文件是否是普通文件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Stat-isFile(): boolean--><!--Device-Stat-isFile(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示文件是否是普通文件。true：是普通文件；false：不是普通文件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

**示例：**

```TypeScript
let filePath = pathDir + "/test.txt";
let isFile = fileIo.statSync(filePath).isFile();

```

## isSocket

```TypeScript
isSocket(): boolean
```

判断文件是否是套接字。

**起始版本：** 9

<!--Device-Stat-isSocket(): boolean--><!--Device-Stat-isSocket(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示文件是否是套接字。true：是套接字；false：不是套接字。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

**示例：**

```TypeScript
let filePath = pathDir + "/test.txt";
let isSocket = fileIo.statSync(filePath).isSocket();

```

## isSymbolicLink

```TypeScript
isSymbolicLink(): boolean
```

判断文件是否为符号链接。

**起始版本：** 9

<!--Device-Stat-isSymbolicLink(): boolean--><!--Device-Stat-isSymbolicLink(): boolean-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 表示文件是否是符号链接。true：是符号链接；false：不是符号链接。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

**示例：**

```TypeScript
let filePath = pathDir + "/test.txt";
let isSymbolicLink = fileIo.statSync(filePath).isSymbolicLink();

```

## atime

```TypeScript
readonly atime: number
```

上次访问该文件的时间，表示距1970年1月1日0时0分0秒的秒数。

**注意**：目前用户数据分区默认以“noatime”方式挂载，atime更新被禁用。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Stat-readonly atime: number--><!--Device-Stat-readonly atime: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## atimeNs

```TypeScript
readonly atimeNs?:bigint
```

上次访问该文件的时间，表示距1970年1月1日0时0分0秒的纳秒数。

**注意**：目前用户数据分区默认以“noatime”方式挂载，atime更新被禁用。

**类型：** bigint

**起始版本：** 15

<!--Device-Stat-readonly atimeNs?:bigint--><!--Device-Stat-readonly atimeNs?:bigint-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## ctime

```TypeScript
readonly ctime: number
```

最近改变文件状态的时间，表示距1970年1月1日0时0分0秒的秒数。

**类型：** number

**起始版本：** 9

<!--Device-Stat-readonly ctime: number--><!--Device-Stat-readonly ctime: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## ctimeNs

```TypeScript
readonly ctimeNs?:bigint
```

最近改变文件状态的时间，表示距1970年1月1日0时0分0秒的纳秒数。

**类型：** bigint

**起始版本：** 15

<!--Device-Stat-readonly ctimeNs?:bigint--><!--Device-Stat-readonly ctimeNs?:bigint-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## gid

```TypeScript
readonly gid: number
```

文件所有组的ID。

**类型：** number

**起始版本：** 9

<!--Device-Stat-readonly gid: number--><!--Device-Stat-readonly gid: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## ino

```TypeScript
readonly ino: bigint
```

标识该文件。通常同设备上的不同文件的INO不同。

**类型：** bigint

**起始版本：** 9

<!--Device-Stat-readonly ino: bigint--><!--Device-Stat-readonly ino: bigint-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## location

```TypeScript
readonly location: LocationType
```

文件的位置，表示该文件是本地文件或者云端文件。

**类型：** LocationType

**起始版本：** 11

<!--Device-Stat-readonly location: LocationType--><!--Device-Stat-readonly location: LocationType-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## mode

```TypeScript
readonly mode: number
```

表示文件权限，各特征位的含义如下：

**说明**：以下值为八进制，取得的返回值为十进制，请换算后查看。

- 0o400：用户读。对于普通文件，所有者可读取文件；对于目录，所有者可读取目录项。

- 0o200：用户写。对于普通文件，所有者可写入文件；对于目录，所有者可创建/删除目录项。

- 0o100：用户执行。对于普通文件，所有者可执行文件；对于目录，所有者可在目录中搜索给定路径名。

- 0o040：用户组读。对于普通文件，所有用户组可读取文件；对于目录，所有用户组可读取目录项。

- 0o020：用户组写。对于普通文件，所有用户组可写入文件；对于目录，所有用户组可创建/删除目录项。

- 0o010：用户组执行。对于普通文件，所有用户组可执行文件；对于目录，所有用户组是否可在目录中搜索给定路径名。

- 0o004：其他读。对于普通文件，其余用户可读取文件；对于目录，其他用户组可读取目录项。

- 0o002：其他写。对于普通文件，其余用户可写入文件；对于目录，其他用户组可创建/删除目录项。

- 0o001：其他执行。对于普通文件，其余用户可执行文件；对于目录，其他用户组可在目录中搜索给定路径名。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Stat-readonly mode: number--><!--Device-Stat-readonly mode: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## mtime

```TypeScript
readonly mtime: number
```

上次修改该文件的时间，表示距1970年1月1日0时0分0秒的秒数。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Stat-readonly mtime: number--><!--Device-Stat-readonly mtime: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## mtimeNs

```TypeScript
readonly mtimeNs?:bigint
```

上次修改该文件的时间，表示距1970年1月1日0时0分0秒的纳秒数。

**类型：** bigint

**起始版本：** 15

<!--Device-Stat-readonly mtimeNs?:bigint--><!--Device-Stat-readonly mtimeNs?:bigint-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## size

```TypeScript
readonly size: number
```

文件的大小，单位为Byte。仅对普通文件有效。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Stat-readonly size: number--><!--Device-Stat-readonly size: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## uid

```TypeScript
readonly uid: number
```

文件所有者的ID。

**类型：** number

**起始版本：** 9

<!--Device-Stat-readonly uid: number--><!--Device-Stat-readonly uid: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

