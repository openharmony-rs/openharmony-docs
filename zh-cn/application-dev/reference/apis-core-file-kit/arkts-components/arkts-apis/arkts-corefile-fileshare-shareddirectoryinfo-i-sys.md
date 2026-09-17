# SharedDirectoryInfo（系统接口）

应用程序向系统捐献的目录信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { fileShare } from '@kit.CoreFileKit';
```

## bundleName

```TypeScript
bundleName: string
```

应用程序的包名。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**系统接口：** 此接口为系统接口。

## path

```TypeScript
path: string
```

应用程序捐献的目录。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**系统接口：** 此接口为系统接口。

## permissionMode

```TypeScript
permissionMode: number
```

应用程序捐献目录的权限，例如 { OperationMode.READ_MODE } 或{ OperationMode.READ_MODE | OperationMode.WRITE_MODE }。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**系统接口：** 此接口为系统接口。
