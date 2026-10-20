# ExternalDiskInfo

```TypeScript
export interface ExternalDiskInfo
```

外置磁盘信息。

**起始版本：** 26.0.1

<!--Device-volumeManager-export interface ExternalDiskInfo--><!--Device-volumeManager-export interface ExternalDiskInfo-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

## 导入模块

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## diskId

```TypeScript
diskId: string
```

磁盘ID，格式为disk-{主设备号}-{次设备号}，如**disk-8-0**。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExternalDiskInfo-diskId: string--><!--Device-ExternalDiskInfo-diskId: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

## diskType

```TypeScript
diskType: number
```

磁盘设备类型。**1**：SD卡。**2**：U盘。**3**：CD/DVD/BD。取值应为整数。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExternalDiskInfo-diskType: int--><!--Device-ExternalDiskInfo-diskType: int-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

## productId

```TypeScript
productId: number
```

USB设备的产品ID，由制造商分配，用于标识特定产品型号。取值应为整数。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExternalDiskInfo-productId: int--><!--Device-ExternalDiskInfo-productId: int-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

## vendorId

```TypeScript
vendorId: number
```

USB设备的厂商ID，由USB-IF分配，用于标识设备制造商。取值应为整数。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExternalDiskInfo-vendorId: int--><!--Device-ExternalDiskInfo-vendorId: int-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

## volumeIds

```TypeScript
volumeIds: Array<string>
```

磁盘上的卷设备ID列表。一个磁盘可以包含多个卷设备，如**["vol-8-1", "vol-8-2"]**。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ExternalDiskInfo-volumeIds: Array<string>--><!--Device-ExternalDiskInfo-volumeIds: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Volume
