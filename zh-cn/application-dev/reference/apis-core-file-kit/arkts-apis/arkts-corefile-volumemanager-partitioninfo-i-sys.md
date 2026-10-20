# PartitionInfo（系统接口）

```TypeScript
export interface PartitionInfo
```

分区信息。

**起始版本：** 26.0.0

<!--Device-volumeManager-export interface PartitionInfo--><!--Device-volumeManager-export interface PartitionInfo-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## diskId

```TypeScript
diskId: string
```

磁盘ID。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PartitionInfo-diskId: string--><!--Device-PartitionInfo-diskId: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## endSector

```TypeScript
endSector: number
```

分区的结束扇区。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PartitionInfo-endSector: long--><!--Device-PartitionInfo-endSector: long-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## fsType

```TypeScript
fsType: string
```

文件系统类型，常见有ext4、vfat、exfat、NTFS、f2fs和hmfs等。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PartitionInfo-fsType: string--><!--Device-PartitionInfo-fsType: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## partitionNum

```TypeScript
partitionNum: number
```

分区号。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PartitionInfo-partitionNum: int--><!--Device-PartitionInfo-partitionNum: int-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## sizeBytes

```TypeScript
sizeBytes: number
```

分区总大小。<br>单位：Byte。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PartitionInfo-sizeBytes: long--><!--Device-PartitionInfo-sizeBytes: long-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## startSector

```TypeScript
startSector: number
```

分区的起始扇区。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PartitionInfo-startSector: long--><!--Device-PartitionInfo-startSector: long-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。
