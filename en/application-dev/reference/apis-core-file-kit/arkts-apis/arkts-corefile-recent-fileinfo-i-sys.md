# FileInfo (System API)

Represents information about the recent file list.

**Since:** 10

**Deprecated since:** 23

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { recent } from '@kit.CoreFileKit';
```

## ctime

```TypeScript
readonly ctime: number
```

Time when the file was created. <br>Unit: second.

**Type:** number

**Since:** 10

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## fileName

```TypeScript
readonly fileName: string
```

File name.

**Type:** string

**Since:** 10

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## mode

```TypeScript
readonly mode: number
```

[Permissions on the file](arkts-corefile-file-fs-stat-i.md).

**Type:** number

**Since:** 10

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## mtime

```TypeScript
readonly mtime: number
```

Time when the file was last modified. <br>Unit: ms.

**Type:** number

**Since:** 10

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## size

```TypeScript
readonly size: number
```

File size, in bytes.

**Type:** number

**Since:** 10

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## srcPath

```TypeScript
readonly srcPath: string
```

File path.

**Type:** string

**Since:** 10

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## uri

```TypeScript
readonly uri: string
```

File URI.

**Type:** string

**Since:** 10

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.
