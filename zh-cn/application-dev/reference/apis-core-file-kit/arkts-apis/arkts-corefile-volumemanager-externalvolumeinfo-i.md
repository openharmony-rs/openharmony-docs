# ExternalVolumeInfo

```TypeScript
export interface ExternalVolumeInfo
```

外置卷设备信息。

**起始版本：** 26.0.1

<!--Device-volumeManager-export interface ExternalVolumeInfo--><!--Device-volumeManager-export interface ExternalVolumeInfo-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

## 导入模块

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## description

```TypeScript
description: string
```

卷设备描述。格式化卷设备会改变其描述，如**"MyUSB"**。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExternalVolumeInfo-description: string--><!--Device-ExternalVolumeInfo-description: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

## diskId

```TypeScript
diskId: string
```

卷设备所属的磁盘ID，一个磁盘可以有一个或者多个卷设备。磁盘设备ID的格式为disk-{主设备号}-{次设备号}，如**disk-8-0**。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExternalVolumeInfo-diskId: string--><!--Device-ExternalVolumeInfo-diskId: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

## freeSize

```TypeScript
freeSize: number
```

卷设备的可用大小。单位：Byte。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExternalVolumeInfo-freeSize: long--><!--Device-ExternalVolumeInfo-freeSize: long-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

## fsType

```TypeScript
fsType: string
```

文件系统类型，常见有fat32、ntfs、exfat、ext4、udf和iso9660等。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExternalVolumeInfo-fsType: string--><!--Device-ExternalVolumeInfo-fsType: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

## path

```TypeScript
path: string
```

卷设备的挂载地址，一般为/mnt/data/external/{uuid}。格式化卷设备会改变其挂载路径。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExternalVolumeInfo-path: string--><!--Device-ExternalVolumeInfo-path: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

## state

```TypeScript
state: number
```

卷设备状态。**0**：卸载状态。**1**：检查状态。**2**：挂载状态。**3**：正在弹出状态。取值应为整数。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExternalVolumeInfo-state: int--><!--Device-ExternalVolumeInfo-state: int-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

## totalSize

```TypeScript
totalSize: number
```

卷设备的总大小。单位：Byte。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExternalVolumeInfo-totalSize: long--><!--Device-ExternalVolumeInfo-totalSize: long-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

## uuid

```TypeScript
uuid: string
```

卷设备uuid是卷设备的通用唯一识别码，不会随着插卡顺序变化而变化，但是卷设备的格式化会改变卷设备的uuid，如**3C16-F61F**。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExternalVolumeInfo-uuid: string--><!--Device-ExternalVolumeInfo-uuid: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

## volumeId

```TypeScript
volumeId: string
```

卷设备ID，格式为vol-{主设备号}-{次设备号}，如**vol-8-1**。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExternalVolumeInfo-volumeId: string--><!--Device-ExternalVolumeInfo-volumeId: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume
