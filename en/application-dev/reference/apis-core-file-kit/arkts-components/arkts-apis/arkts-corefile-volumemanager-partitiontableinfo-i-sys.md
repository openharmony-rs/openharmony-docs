# PartitionTableInfo (System API)

Partition table information.

**Since:** 26.0.0

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## alignSector

```TypeScript
alignSector: number
```

Alignment sector.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## diskId

```TypeScript
diskId: string
```

Disk ID.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## partitionCount

```TypeScript
partitionCount: number
```

Number of partitions.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## partitions

```TypeScript
partitions: Array<PartitionInfo>
```

Array of partition information.

**Type:** Array&lt;[PartitionInfo](arkts-corefile-volumemanager-partitioninfo-i-sys.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## sectorSize

```TypeScript
sectorSize: number
```

Sector size in bytes.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## tableType

```TypeScript
tableType: string
```

Partition table type, such as 'gpt' or 'mbr'.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.

## totalSector

```TypeScript
totalSector: number
```

Total number of sectors.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.StorageService.Volume

**System API:** This is a system API.
