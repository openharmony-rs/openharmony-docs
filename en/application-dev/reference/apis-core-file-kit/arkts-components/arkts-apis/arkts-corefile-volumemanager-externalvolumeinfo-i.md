# ExternalVolumeInfo

```TypeScript
export interface ExternalVolumeInfo
```

External volume information.

**Since:** 26.0.1

**System capability:** SystemCapability.FileManagement.StorageService.Volume

## Modules to Import

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## description

```TypeScript
description: string
```

Description of the volume. Formatting the volume changes its description, such as **"MyUSB"**.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

## diskId

```TypeScript
diskId: string
```

ID of the disk to which the volume belongs. A disk can have one or more volumes. The disk ID is in the disk-{Primary device ID}-{Secondary device ID} format, such as **disk-8-0**.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

## freeSize

```TypeScript
freeSize: number
```

Available size of the volume. Unit: Byte.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

## fsType

```TypeScript
fsType: string
```

File system type. Common file systems are **fat32**, **ntfs**, **exfat**, **ext4**, **udf**, and **iso9660**.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

## path

```TypeScript
path: string
```

Path of the volume mounted. Generally, the path is **\/mnt/data/external/{uuid}**. Formatting the volume changes its mount path.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

## state

```TypeScript
state: number
```

Volume status. **0**: The volume is unmounted. **1**: The volume is being checked. **2**: The volume is mounted. **3**: The volume is being ejected. The value should be an integer.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

## totalSize

```TypeScript
totalSize: number
```

Total size of the volume. Unit: Byte.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

## uuid

```TypeScript
uuid: string
```

Volume UUID, which uniquely identifies a volume irrespective of the card insertion sequence. However, the UUID of a volume will change after the volume is formatted, such as **3C16-F61F**.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

## volumeId

```TypeScript
volumeId: string
```

Volume ID, in the vol-{Primary device ID}-{Secondary device ID} format, such as **vol-8-1**.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume
