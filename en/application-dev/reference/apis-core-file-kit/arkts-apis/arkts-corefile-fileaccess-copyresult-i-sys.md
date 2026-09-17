# CopyResult (System API)

Defines the information returned when the file copy operation fails. If the copy operation is successful, no information is returned.

**Since:** 10

**Deprecated since:** 23

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { fileAccess } from '@kit.CoreFileKit';
```

## destUri

```TypeScript
destUri: string
```

URI of the conflicting file. If the error is not caused by a file conflict, **destUri** is empty.

**Type:** string

**Since:** 10

**Deprecated since:** 23

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## errCode

```TypeScript
errCode: number
```

Error code.

**Type:** number

**Since:** 10

**Deprecated since:** 23

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## errMsg

```TypeScript
errMsg: string
```

Error message.

**Type:** string

**Since:** 10

**Deprecated since:** 23

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## sourceUri

```TypeScript
sourceUri: string
```

URI of the source file or directory.

**Type:** string

**Since:** 10

**Deprecated since:** 23

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.
