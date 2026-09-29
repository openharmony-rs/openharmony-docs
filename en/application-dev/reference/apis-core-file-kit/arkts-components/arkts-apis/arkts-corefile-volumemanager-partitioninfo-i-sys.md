# PartitionInfo (System API)

```TypeScript
export interface PartitionInfo
```

Partition information.

**Since:** 26.0.0

<!--Device-volumeManager-export interface PartitionInfo--><!--Device-volumeManager-export interface PartitionInfo-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## diskId

```TypeScript
diskId: string
```

Disk ID.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PartitionInfo-diskId: string--><!--Device-PartitionInfo-diskId: string-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## endSector

```TypeScript
endSector: number
```

End sector of the partition.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PartitionInfo-endSector: long--><!--Device-PartitionInfo-endSector: long-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## fsType

```TypeScript
fsType: string
```

File system type. Common file systems are **ext4**, **vfat**, **exfat**, **NTFS**, **f2fs**, and **hmfs**.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PartitionInfo-fsType: string--><!--Device-PartitionInfo-fsType: string-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## partitionNum

```TypeScript
partitionNum: number
```

Partition number.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PartitionInfo-partitionNum: int--><!--Device-PartitionInfo-partitionNum: int-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## sizeBytes

```TypeScript
sizeBytes: number
```

Partition total size. <br>Unit: Byte.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PartitionInfo-sizeBytes: long--><!--Device-PartitionInfo-sizeBytes: long-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## startSector

```TypeScript
startSector: number
```

Start sector of the partition.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PartitionInfo-startSector: long--><!--Device-PartitionInfo-startSector: long-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.
