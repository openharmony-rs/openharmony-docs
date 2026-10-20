# PartitionTableInfo（系统接口）

```TypeScript
export interface PartitionTableInfo
```

分区表信息。

**起始版本：** 26.0.0

<!--Device-volumeManager-export interface PartitionTableInfo--><!--Device-volumeManager-export interface PartitionTableInfo-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## alignSector

```TypeScript
alignSector: number
```

对齐扇区。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PartitionTableInfo-alignSector: int--><!--Device-PartitionTableInfo-alignSector: int-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## diskId

```TypeScript
diskId: string
```

磁盘ID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PartitionTableInfo-diskId: string--><!--Device-PartitionTableInfo-diskId: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## partitionCount

```TypeScript
partitionCount: number
```

分区数量。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PartitionTableInfo-partitionCount: int--><!--Device-PartitionTableInfo-partitionCount: int-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## partitions

```TypeScript
partitions: Array<PartitionInfo>
```

分区信息数组。

**类型：** Array&lt;[PartitionInfo](arkts-corefile-volumemanager-partitioninfo-i-sys.md)&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PartitionTableInfo-partitions: Array<PartitionInfo>--><!--Device-PartitionTableInfo-partitions: Array<PartitionInfo>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## sectorSize

```TypeScript
sectorSize: number
```

扇区大小（单位：Byte）。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PartitionTableInfo-sectorSize: int--><!--Device-PartitionTableInfo-sectorSize: int-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## tableType

```TypeScript
tableType: string
```

分区表类型，如'gpt'或'mbr'。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PartitionTableInfo-tableType: string--><!--Device-PartitionTableInfo-tableType: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## totalSector

```TypeScript
totalSector: number
```

总扇区数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PartitionTableInfo-totalSector: long--><!--Device-PartitionTableInfo-totalSector: long-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。
