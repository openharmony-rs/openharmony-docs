# FileInfo（系统接口）

Represents information about a file or directory in the **Recently deleted** list.

**起始版本：** 10

**废弃版本：** 23

<!--Device-trash-interface FileInfo--><!--Device-trash-interface FileInfo-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { trash } from '@kit.CoreFileKit';
```

## ctime

```TypeScript
readonly ctime: number
```

Time when the file or directory was created. It is the number of seconds elapsed since the Unix epoch (00:00:00UTC on January 1, 1970).

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

Name of the file or directory.

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

Permission on the file or directory.

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

Time when the file or directory was last modified. It is the number of milliseconds elapsed since the Unix epoch(00:00:00 UTC on January 1, 1970).

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

Size of a file or directory, in bytes.

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

Path of the file or directory before being deleted.

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

URI of the file or directory.

**类型：** string

**起始版本：** 10

**废弃版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileInfo-readonly uri: string--><!--Device-FileInfo-readonly uri: string-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

