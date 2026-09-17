# SharedDirectoryInfo (System API)

The directory information shared with the system by the application.

**Since:** 26.0.0

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { fileShare } from '@kit.CoreFileKit';
```

## bundleName

```TypeScript
bundleName: string
```

Indicates the bundle name of the application.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**System API:** This is a system API.

## path

```TypeScript
path: string
```

Indicates the path of the application's shared directory.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**System API:** This is a system API.

## permissionMode

```TypeScript
permissionMode: number
```

Indicates the permission for the application's shared directory, e.g., { OperationMode.READ_MODE } or { OperationMode.READ_MODE | OperationMode.WRITE_MODE }

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.AppFileService.FolderAuthorization

**System API:** This is a system API.
