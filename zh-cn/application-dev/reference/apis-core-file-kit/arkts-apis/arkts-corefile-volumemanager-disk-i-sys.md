# Disk（系统接口）

```TypeScript
export interface Disk
```

磁盘信息。

**起始版本：** 26.0.0

<!--Device-volumeManager-export interface Disk--><!--Device-volumeManager-export interface Disk-End-->

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

磁盘ID，格式为disk-{主设备号}-{次设备号}。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Disk-diskId: string--><!--Device-Disk-diskId: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## diskType

```TypeScript
diskType: DiskType
```

磁盘类型。

**类型：** [DiskType](arkts-corefile-volumemanager-disktype-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Disk-diskType: DiskType--><!--Device-Disk-diskType: DiskType-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## extraInfo

```TypeScript
extraInfo: string
```

磁盘信息扩展字段。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Disk-extraInfo: string--><!--Device-Disk-extraInfo: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## removable

```TypeScript
removable: boolean
```

磁盘是否可移除。true表示磁盘可移除。

**类型：** boolean

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Disk-removable: boolean--><!--Device-Disk-removable: boolean-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## sizeBytes

```TypeScript
sizeBytes: number
```

磁盘总大小。<br>单位：Byte。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Disk-sizeBytes: long--><!--Device-Disk-sizeBytes: long-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## volumeIds

```TypeScript
volumeIds: Array<string>
```

磁盘的卷设备列表。一个磁盘可能包含多个卷设备。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Disk-volumeIds: Array<string>--><!--Device-Disk-volumeIds: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。
