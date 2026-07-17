# NotifyMessage（系统接口）

通知回调函数的值。

**起始版本：** 10

**废弃版本：** 23

**替代接口：** WatchEvent

<!--Device-fileAccess-interface NotifyMessage--><!--Device-fileAccess-interface NotifyMessage-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { fileAccess } from '@kit.CoreFileKit';
```

## type

```TypeScript
type: NotifyType
```

变更的通知类型。

**类型：** NotifyType

**起始版本：** 10

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotifyMessage-type: NotifyType--><!--Device-NotifyMessage-type: NotifyType-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

## uris

```TypeScript
uris: Array<string>
```

所变更文件的uri集合，目前仅支持单条通知，后序支持多条通知。

**类型：** Array<string>

**起始版本：** 10

**废弃版本：** 23

**需要权限：** ohos.permission.FILE_ACCESS_MANAGER

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NotifyMessage-uris: Array<string>--><!--Device-NotifyMessage-uris: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.UserFileService

**系统接口：** 此接口为系统接口。

