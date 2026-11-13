# @ohos.file.volumeManager (Volume Management)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @ning-jingyou-->
<!--Designer: @renguang1116-->
<!--Tester: @zsyztt; @fuwei-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=a97d39336ba22e315d05dca3cc06cd148ea56822 translatedAt=2026-11-03T04:45:03.789Z pushedAt=2026-11-04T03:11:33.539Z nl=1 -->

This module provides functions for querying external storage disk device and volume device information, including obtaining external storage physical disk information and external storage volume device information. It is applicable to scenarios such as external storage device management and storage space query, helping developers obtain details of disk and volume devices of external storage devices.

**Since**: 9

## Modules to Import

```ts
import { volumeManager } from '@kit.CoreFileKit';
```

## volumeManager.getExternalDiskInfos

getExternalDiskInfos(): Promise&lt;Array&lt;ExternalDiskInfo&gt;&gt;

Obtains the information of all external storage physical disk devices. This API uses a promise to return the result asynchronously.

**Since:** 26.0.1

**Required permissions**: ohos.permission.GET_STORAGE_VOLUME_INFO

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;Array&lt;[ExternalDiskInfo](#externaldiskinfo)&gt;&gt; | Promise object that returns the list of external storage physical disk device information. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 13600001 | IPC error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

volumeManager.getExternalDiskInfos().then((disks: Array<volumeManager.ExternalDiskInfo>) => {
  console.info("getExternalDiskInfos successfully:" + JSON.stringify(disks));
}).catch((error: BusinessError) => {
  console.error(`Failed to getExternalDiskInfos. Code: ${error.code}, message: ${error.message}`);
});
```

## volumeManager.getExternalVolumeInfos

getExternalVolumeInfos(): Promise&lt;Array&lt;ExternalVolumeInfo&gt;&gt;

Obtains information about all external storage volume devices. This API uses a promise to return the result.

**Since:** 26.0.1

**Required Permissions**: ohos.permission.GET_STORAGE_VOLUME_INFO

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Return value**

| Type | Description |
| -------- | -------- |
| Promise&lt;Array&lt;[ExternalVolumeInfo](#externalvolumeinfo)&gt;&gt; | Promise object that returns the list of external storage volume device information. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 13600001 | IPC error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

volumeManager.getExternalVolumeInfos().then((volumes: Array<volumeManager.ExternalVolumeInfo>) => {
  console.info("getExternalVolumeInfos successfully:" + JSON.stringify(volumes));
}).catch((error: BusinessError) => {
  console.error(`Failed to getExternalVolumeInfos. Code: ${error.code}, message: ${error.message}`);
});
```

## ExternalDiskInfo

External disk information.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| diskId | string | No | No | Disk device ID, in the format disk-{major device number}-{minor device number}, for example, disk-8-0. |
| diskType | number | No | No | Disk device type:<br>1: SD card.<br>2: USB flash drive.<br>3: Optical disc (CD/DVD/BD).<br>The value is an integer. |
| volumeIds | Array&lt;string&gt; | No | No | List of volume device IDs on the disk. A disk can contain multiple volume devices, for example, ["vol-8-1", "vol-8-2"]. |
| vendorId | number | No | No | Vendor ID of the USB device, assigned by USB-IF to identify the device manufacturer. The value is an integer. |
| productId | number | No | No | Product ID of the USB device, assigned by the manufacturer to identify the specific product model. The value is an integer. |

## ExternalVolumeInfo

External volume device information.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

| Name | Type | Read-Only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| volumeId | string | No | No | Volume device ID, in the format of vol-{Major Device Number}-{Minor Device Number}, for example, vol-8-1. |
| uuid | string | No | No | UUID of the volume device, which is a universally unique identifier of the volume device. It does not change with the card insertion order, but formatting the volume device changes its UUID, for example, 3C16-F61F. |
| diskId | string | No | No | ID of the disk to which the volume device belongs. A disk can have one or more volume devices. The disk device ID is in the format of disk-{Major Device Number}-{Minor Device Number}, for example, disk-8-0. |
| description | string | No | No | Volume device description. Formatting the volume device changes its description, for example, "MyUSB". |
| state | number | No | No | Volume device state:<br>0: Unmounted state.<br>1: Checking state.<br>2: Mounted state.<br>3: Ejecting state.<br>The value is an integer. |
| totalSize | number | No | No | Total size of the volume device. Unit: Byte. |
| freeSize | number | No | No | Available size of the volume device. Unit: Byte. |
| path | string | No | No | Mount path of the volume device, generally /mnt/data/external/{uuid}. Formatting the volume device changes the mount path. |
| fsType | string | No | No | File system type. Common file systems include fat32, ntfs, exfat, ext4, udf, and iso9660. |
