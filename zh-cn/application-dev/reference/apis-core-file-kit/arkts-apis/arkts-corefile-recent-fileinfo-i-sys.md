# FileInfo（系统接口）

最近访问列表文件信息。

**起始版本：** 10

**废弃版本：** 23

<!--Device-recent-interface FileInfo--><!--Device-recent-interface FileInfo-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { recent } from '@kit.CoreFileKit';
```

## ctime

```TypeScript
readonly ctime: number
```

文件的创建时间。自1970年1月1日起至目标时间的秒数。

**类型：** number

**起始版本：** 10

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileInfo-readonly ctime: number--><!--Device-FileInfo-readonly ctime: number-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## fileName

```TypeScript
readonly fileName: string
```

文件名。

**类型：** string

**起始版本：** 10

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileInfo-readonly fileName: string--><!--Device-FileInfo-readonly fileName: string-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## mode

```TypeScript
readonly mode: number
```

[文件权限信息](arkts-corefile-file-fs-stat-i.md)。

**类型：** number

**起始版本：** 10

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileInfo-readonly mode: number--><!--Device-FileInfo-readonly mode: number-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## mtime

```TypeScript
readonly mtime: number
```

文件的修改时间。自1970年1月1日起至目标时间的毫秒数。

**类型：** number

**起始版本：** 10

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileInfo-readonly mtime: number--><!--Device-FileInfo-readonly mtime: number-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## size

```TypeScript
readonly size: number
```

文件的大小（单位：字节）。

**类型：** number

**起始版本：** 10

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileInfo-readonly size: number--><!--Device-FileInfo-readonly size: number-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## srcPath

```TypeScript
readonly srcPath: string
```

文件路径。

**类型：** string

**起始版本：** 10

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileInfo-readonly srcPath: string--><!--Device-FileInfo-readonly srcPath: string-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## uri

```TypeScript
readonly uri: string
```

文件URI。

**类型：** string

**起始版本：** 10

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileInfo-readonly uri: string--><!--Device-FileInfo-readonly uri: string-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

