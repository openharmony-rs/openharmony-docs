# PartitionParams（系统接口）

```TypeScript
export interface PartitionParams
```

分区创建参数。

**起始版本：** 26.0.0

<!--Device-volumeManager-export interface PartitionParams--><!--Device-volumeManager-export interface PartitionParams-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## endSector

```TypeScript
endSector: number
```

分区的结束扇区。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PartitionParams-endSector: long--><!--Device-PartitionParams-endSector: long-End-->

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

<!--Device-PartitionParams-partitionNum: int--><!--Device-PartitionParams-partitionNum: int-End-->

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

<!--Device-PartitionParams-startSector: long--><!--Device-PartitionParams-startSector: long-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## typeCode

```TypeScript
typeCode: string
```

文件系统代码，常见有ext4、vfat、exfat、NTFS、f2fs和hmfs等。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PartitionParams-typeCode: string--><!--Device-PartitionParams-typeCode: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。
