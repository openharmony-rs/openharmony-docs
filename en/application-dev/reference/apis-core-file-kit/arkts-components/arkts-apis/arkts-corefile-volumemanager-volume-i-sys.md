# Volume (System API)

Get All Volumes.

**Since:** 9

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## description

```TypeScript
description: string
```

Description of the volume.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## diskId

```TypeScript
diskId: string
```

ID of the disk to which the volume belongs. A disk can have one or more volumes. The disk ID is in the disk-{Primary device ID}-{Secondary device ID} format, which is similar to the volume ID.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## extraInfo

```TypeScript
extraInfo?: string
```

Extra information of the volume.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## fsType

```TypeScript
fsType: string
```

File system type. Common file systems are **ext2**, **vfat**, and **NTFS**.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## id

```TypeScript
id: string
```

Volume ID, in the vol-{Primary device ID}-{Secondary device ID} format. The primary device IDs identify devices of different types. The secondary device IDs identify different devices of the same type. The volume IDs vary depending on the card insertion sequence.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## partitionNum

```TypeScript
partitionNum?: number
```

Partition number.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## path

```TypeScript
path: string
```

Path of the volume mounted. Generally, the path is **\/mnt/data/external/{uuid}**.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## removable

```TypeScript
removable: boolean
```

Whether the volume can be removed. Currently, only removable storage devices are supported. The value **true** means the device can be removed; the value **false** means the opposite.

**Type:** boolean

**Since:** 9

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## state

```TypeScript
state: number
```

Volume status.

**0**: The volume is unmounted.

**1**: The volume is being checked.

**2**: The volume is mounted.

**3**: The volume is being ejected.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## uuid

```TypeScript
uuid: string
```

Volume UUID, which uniquely identifies a volume irrespective of the card insertion sequence. However, the UUID of a volume will change after the volume is formatted.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.
