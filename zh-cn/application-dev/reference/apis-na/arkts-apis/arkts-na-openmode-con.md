# 常量

## APPEND

```TypeScript
const APPEND: int
```

以追加方式打开，后续写将追加到文件末尾。值为 0o2000。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenMode-const APPEND: int--><!--Device-OpenMode-const APPEND: int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## CREATE

```TypeScript
const CREATE: int
```

若文件不存在，则创建文件。值为 0o100。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenMode-const CREATE: int--><!--Device-OpenMode-const CREATE: int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## DIR

```TypeScript
const DIR: int
```

如果path不指向目录，则出错。值为 0o200000。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenMode-const DIR: int--><!--Device-OpenMode-const DIR: int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## NOFOLLOW

```TypeScript
const NOFOLLOW: int
```

如果path指向符号链接，则出错。值为 0o400000。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenMode-const NOFOLLOW: int--><!--Device-OpenMode-const NOFOLLOW: int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## NONBLOCK

```TypeScript
const NONBLOCK: int
```

如果path指向FIFO、块特殊文件或字符特殊文件，则本次打开及后续 IO 进行非阻塞操作。值为 0o4000。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenMode-const NONBLOCK: int--><!--Device-OpenMode-const NONBLOCK: int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## READ_ONLY

```TypeScript
const READ_ONLY: int
```

只读打开。值为 0o0。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenMode-const READ_ONLY: int--><!--Device-OpenMode-const READ_ONLY: int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## READ_WRITE

```TypeScript
const READ_WRITE: int
```

读写打开。值为 0o2。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenMode-const READ_WRITE: int--><!--Device-OpenMode-const READ_WRITE: int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## SYNC

```TypeScript
const SYNC: int
```

以同步IO的方式打开文件。值为 0o4010000。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenMode-const SYNC: int--><!--Device-OpenMode-const SYNC: int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## TRUNC

```TypeScript
const TRUNC: int
```

如果文件存在且以只写或读写的方式打开，则将其长度裁剪为零。值为 0o1000

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenMode-const TRUNC: int--><!--Device-OpenMode-const TRUNC: int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## UNCACHE

```TypeScript
const UNCACHE: int
```

读写文件不进行页缓存。值为 0o10000000000。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenMode-const UNCACHE: int--><!--Device-OpenMode-const UNCACHE: int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## WRITE_ONLY

```TypeScript
const WRITE_ONLY: int
```

只写打开。值为 0o1。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-OpenMode-const WRITE_ONLY: int--><!--Device-OpenMode-const WRITE_ONLY: int-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

