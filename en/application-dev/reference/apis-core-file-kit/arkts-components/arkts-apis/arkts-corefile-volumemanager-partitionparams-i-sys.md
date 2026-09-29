# PartitionParams (System API)

```TypeScript
export interface PartitionParams
```

Partition creation options.

**Since:** 26.0.0

<!--Device-volumeManager-export interface PartitionParams--><!--Device-volumeManager-export interface PartitionParams-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## endSector

```TypeScript
endSector: number
```

End sector of the partition.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PartitionParams-endSector: long--><!--Device-PartitionParams-endSector: long-End-->

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

<!--Device-PartitionParams-partitionNum: int--><!--Device-PartitionParams-partitionNum: int-End-->

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

<!--Device-PartitionParams-startSector: long--><!--Device-PartitionParams-startSector: long-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## typeCode

```TypeScript
typeCode: string
```

The code of file system. Common file systems are **ext4**, **vfat**, **exfat**, **NTFS**, **f2fs**, and **hmfs**.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PartitionParams-typeCode: string--><!--Device-PartitionParams-typeCode: string-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.
