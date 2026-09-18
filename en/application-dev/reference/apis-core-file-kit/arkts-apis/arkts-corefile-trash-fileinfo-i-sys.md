# FileInfo (System API)

Represents information about a file or directory in the **Recently deleted** list.

**Since:** 10

**Deprecated since:** 23

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { trash } from '@kit.CoreFileKit';
```

## ctime

```TypeScript
readonly ctime: number
```

Time when the file or directory was created. It is the number of seconds elapsed since the Unix epoch (00:00:00 UTC on January 1, 1970).

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

Name of the file or directory.

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

Permission on the file or directory.

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

Time when the file or directory was last modified. It is the number of milliseconds elapsed since the Unix epoch (00:00:00 UTC on January 1, 1970).

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

Size of a file or directory, in bytes.

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

Path of the file or directory before being deleted.

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

URI of the file or directory.

**Type:** string

**Since:** 10

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.
