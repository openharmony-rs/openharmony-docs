# FileSystemRequestConfig (System API)

Parameters required to perform garbage collection (GC).

@interface FileSystemRequestConfig

**Since:** 23

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## triggerType

```TypeScript
triggerType: number
```

Specifies the trigger type for garbage collection (0-default Device GC).

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

## waitTime

```TypeScript
waitTime: number
```

Sets the maximum wait time (in seconds) for GC operation.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

## writeSize

```TypeScript
writeSize: number
```

Defines the target size (in MBytes) for garbage collection.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.
