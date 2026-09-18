# PolicyErrorResult

授予或激活权限失败的URI策略结果。

@interface { object }

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

## 导入模块

```TypeScript
import { fileShare } from '@kit.CoreFileKit';
```

## code

```TypeScript
code: PolicyErrorCode
```

授权策略失败的URI对应的错误码。

**类型：** [PolicyErrorCode](arkts-corefile-fileshare-policyerrorcode-e.md)

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

## message

```TypeScript
message: string
```

授权策略失败的URI对应的原因。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

## uri

```TypeScript
uri: string
```

授予或激活权限失败的URI。

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization
