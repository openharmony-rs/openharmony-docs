# SharedDirectoryInfo（系统接口）

应用程序向系统捐献的目录信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-fileShare-export interface SharedDirectoryInfo--><!--Device-fileShare-export interface SharedDirectoryInfo-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

应用程序的包名。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SharedDirectoryInfo-bundleName: string--><!--Device-SharedDirectoryInfo-bundleName: string-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**系统接口：** 此接口为系统接口。

## path

```TypeScript
path: string
```

应用程序捐献的目录。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SharedDirectoryInfo-path: string--><!--Device-SharedDirectoryInfo-path: string-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**系统接口：** 此接口为系统接口。

## permissionMode

```TypeScript
permissionMode: int
```

应用程序捐献目录的权限，例如 { OperationMode.READ_MODE } 或 { OperationMode.READ_MODE | OperationMode.WRITE_MODE }。

**类型：** int

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SharedDirectoryInfo-permissionMode: int--><!--Device-SharedDirectoryInfo-permissionMode: int-End-->

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**系统接口：** 此接口为系统接口。

