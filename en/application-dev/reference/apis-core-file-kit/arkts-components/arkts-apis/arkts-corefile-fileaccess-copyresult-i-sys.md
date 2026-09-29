# CopyResult (System API)

```TypeScript
interface CopyResult
```

Defines the information returned when the file copy operation fails. If the copy operation is successful, no information is returned.

**Since:** 10

**Deprecated since:** 23

<!--Device-fileAccess-interface CopyResult--><!--Device-fileAccess-interface CopyResult-End-->

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

<!--Device-CopyResult-destUri: string--><!--Device-CopyResult-destUri: string-End-->

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

<!--Device-CopyResult-errCode: number--><!--Device-CopyResult-errCode: number-End-->

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

<!--Device-CopyResult-errMsg: string--><!--Device-CopyResult-errMsg: string-End-->

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

<!--Device-CopyResult-sourceUri: string--><!--Device-CopyResult-sourceUri: string-End-->

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.
