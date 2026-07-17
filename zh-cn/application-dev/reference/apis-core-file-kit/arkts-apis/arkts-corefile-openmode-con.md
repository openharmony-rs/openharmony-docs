# 常量

## APPEND

```TypeScript
const APPEND = 0o2000
```

以追加方式打开，后续写将追加到文件末尾。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OpenMode-const APPEND = 0o2000--><!--Device-OpenMode-const APPEND = 0o2000-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## CREATE

```TypeScript
const CREATE = 0o100
```

若文件不存在，则创建文件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OpenMode-const CREATE = 0o100--><!--Device-OpenMode-const CREATE = 0o100-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## DIR

```TypeScript
const DIR = 0o200000
```

如果path不指向目录，则出错。

**起始版本：** 9

<!--Device-OpenMode-const DIR = 0o200000--><!--Device-OpenMode-const DIR = 0o200000-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## NOFOLLOW

```TypeScript
const NOFOLLOW = 0o400000
```

如果path指向符号链接，则出错。

**起始版本：** 9

<!--Device-OpenMode-const NOFOLLOW = 0o400000--><!--Device-OpenMode-const NOFOLLOW = 0o400000-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## NONBLOCK

```TypeScript
const NONBLOCK = 0o4000
```

如果path指向FIFO、块特殊文件或字符特殊文件，则本次打开及后续IO进行非阻塞操作。

**起始版本：** 9

<!--Device-OpenMode-const NONBLOCK = 0o4000--><!--Device-OpenMode-const NONBLOCK = 0o4000-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## READ_ONLY

```TypeScript
const READ_ONLY = 0o0
```

只读打开。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OpenMode-const READ_ONLY = 0o0--><!--Device-OpenMode-const READ_ONLY = 0o0-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## READ_WRITE

```TypeScript
const READ_WRITE = 0o2
```

读写打开。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OpenMode-const READ_WRITE = 0o2--><!--Device-OpenMode-const READ_WRITE = 0o2-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## SYNC

```TypeScript
const SYNC = 0o4010000
```

以同步IO的方式打开文件。

**起始版本：** 9

<!--Device-OpenMode-const SYNC = 0o4010000--><!--Device-OpenMode-const SYNC = 0o4010000-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## TRUNC

```TypeScript
const TRUNC = 0o1000
```

如果文件存在且以只写或读写的方式打开，则将其长度裁剪为零。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OpenMode-const TRUNC = 0o1000--><!--Device-OpenMode-const TRUNC = 0o1000-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## UNCACHE

```TypeScript
const UNCACHE = 0o10000000000
```

UNCACHE IO。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-OpenMode-const UNCACHE = 0o10000000000--><!--Device-OpenMode-const UNCACHE = 0o10000000000-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## WRITE_ONLY

```TypeScript
const WRITE_ONLY = 0o1
```

只写打开。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-OpenMode-const WRITE_ONLY = 0o1--><!--Device-OpenMode-const WRITE_ONLY = 0o1-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

