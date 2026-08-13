# PolicyInfo

需要授予或激活URI访问权限的策略信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-fileShare-export interface PolicyInfo--><!--Device-fileShare-export interface PolicyInfo-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

## operationMode

```TypeScript
operationMode: int
```

授予或激活权限的URI访问模式，例如 { OperationMode.READ_MODE } 或 { OperationMode.READ_MODE | OperationMode.WRITE_MODE }。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PolicyInfo-operationMode: int--><!--Device-PolicyInfo-operationMode: int-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

## uri

```TypeScript
uri: string
```

需要授予或激活访问权限的URI，需符合URI格式规范。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PolicyInfo-uri: string--><!--Device-PolicyInfo-uri: string-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

