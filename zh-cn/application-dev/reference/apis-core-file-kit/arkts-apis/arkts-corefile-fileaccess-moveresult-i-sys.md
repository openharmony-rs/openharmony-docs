# MoveResult（系统接口）

表示移动操作失败时的返回信息，移动成功时则没有返回信息。

**起始版本：** 11

**废弃版本：** 23

<!--Device-fileAccess-interface MoveResult--><!--Device-fileAccess-interface MoveResult-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { fileAccess } from '@kit.CoreFileKit';
```

## destUri

```TypeScript
destUri: string
```

产生冲突的目标文件的 uri。如果非冲突导致的错误，则为空。

**类型：** string

**起始版本：** 11

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MoveResult-destUri: string--><!--Device-MoveResult-destUri: string-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## errCode

```TypeScript
errCode: number
```

错误码。接口抛出错误码的详细介绍请参见[文件管理错误码](docroot://reference/apis-core-file-kit/errorcode-filemanagement.md)。

**类型：** number

**起始版本：** 11

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MoveResult-errCode: number--><!--Device-MoveResult-errCode: number-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## errMsg

```TypeScript
errMsg: string
```

错误信息。

**类型：** string

**起始版本：** 11

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MoveResult-errMsg: string--><!--Device-MoveResult-errMsg: string-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## sourceUri

```TypeScript
sourceUri: string
```

源文件(夹) uri。

**类型：** string

**起始版本：** 11

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MoveResult-sourceUri: string--><!--Device-MoveResult-sourceUri: string-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

