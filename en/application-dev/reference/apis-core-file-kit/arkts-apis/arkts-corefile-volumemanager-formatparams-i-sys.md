# FormatParams (System API)

Format options for partition formatting.

**Since:** 26.0.0

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## fsType

```TypeScript
fsType: string
```

File system type, Common file systems are **ext4**, **vfat**, and **exfat**.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## quickFormat

```TypeScript
quickFormat?: boolean
```

Whether to perform quick format, default value is true.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## volumeName

```TypeScript
volumeName?: string
```

Volume name after formatting.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.
