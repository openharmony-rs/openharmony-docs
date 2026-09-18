# PolicyInfo

需要授予或激活URI访问权限的策略信息。

@interface PolicyInfo

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

## 导入模块

```TypeScript
import { fileShare } from '@kit.CoreFileKit';
```

## operationMode

```TypeScript
operationMode: number
```

授予或激活权限的URI访问模式，例如 { OperationMode.READ_MODE } 或{ OperationMode.READ_MODE | OperationMode.WRITE_MODE }。

**类型：** number

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

## uri

```TypeScript
uri: string
```

需要授予或激活访问权限的URI，需符合URI格式规范。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization
