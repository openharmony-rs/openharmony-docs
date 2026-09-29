# ExternalDiskInfo

```TypeScript
export interface ExternalDiskInfo
```

External disk information.

**Since:** 26.0.1

<!--Device-volumeManager-export interface ExternalDiskInfo--><!--Device-volumeManager-export interface ExternalDiskInfo-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Volume

## Modules to Import

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## diskId

```TypeScript
diskId: string
```

Disk ID, in the disk-{Primary device ID}-{Secondary device ID} format, such as **disk-8-0**.

**Type:** string

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExternalDiskInfo-diskId: string--><!--Device-ExternalDiskInfo-diskId: string-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Volume

## diskType

```TypeScript
diskType: number
```

Disk device type. **1**: SD card. **2**: USB flash disk. **3**: CD/DVD/BD. The value should be an integer.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExternalDiskInfo-diskType: int--><!--Device-ExternalDiskInfo-diskType: int-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Volume

## productId

```TypeScript
productId: number
```

Product ID of the USB device, assigned by the manufacturer to identify a specific product model. The value should be an integer.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExternalDiskInfo-productId: int--><!--Device-ExternalDiskInfo-productId: int-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Volume

## vendorId

```TypeScript
vendorId: number
```

Vendor ID of the USB device, assigned by USB-IF to identify the device manufacturer. The value should be an integer.

**Type:** number

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExternalDiskInfo-vendorId: int--><!--Device-ExternalDiskInfo-vendorId: int-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Volume

## volumeIds

```TypeScript
volumeIds: Array<string>
```

Volume ID list on the disk. A disk can contain multiple volumes, such as **["vol-8-1", "vol-8-2"]**.

**Type:** Array&lt;string&gt;

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExternalDiskInfo-volumeIds: Array<string>--><!--Device-ExternalDiskInfo-volumeIds: Array<string>-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Volume
