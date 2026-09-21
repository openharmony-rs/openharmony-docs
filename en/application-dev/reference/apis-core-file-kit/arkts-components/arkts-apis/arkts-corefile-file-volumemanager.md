# @ohos.file.volumeManager(Volume Management)

The **volumeManager** module provides APIs for querying and managing volumes and disks, including querying volume information, mounting or unmounting a volume, partitioning a disk, and formatting a volume.

**Since:** 9

**System capability:** SystemCapability.FileManagement.StorageService.Volume

## Modules to Import

```TypeScript
import { volumeManager } from '@kit.CoreFileKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getExternalDiskInfos](arkts-corefile-volumemanager-getexternaldiskinfos-f.md) | Obtains information about all external storage physical disks. This API uses a promise to return the result. |
| [getExternalVolumeInfos](arkts-corefile-volumemanager-getexternalvolumeinfos-f.md) | Obtains information about all external storage volumes. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [burn](arkts-corefile-volumemanager-burn-f-sys.md) | Burns data to a volume. This API uses a promise to return the result. |
| [createIsoImage](arkts-corefile-volumemanager-createisoimage-f-sys.md) | Creates an ISO image from a volume. This API uses a promise to return the result. |
| [createPartition](arkts-corefile-volumemanager-createpartition-f-sys.md) | Creates a partition on a disk. This API uses a promise to return the result. |
| [deletePartition](arkts-corefile-volumemanager-deletepartition-f-sys.md) | Deletes a partition on a disk. This API uses a promise to return the result. |
| [eject](arkts-corefile-volumemanager-eject-f-sys.md) | Ejects a volume. This API uses a promise to return the result. |
| [erase](arkts-corefile-volumemanager-erase-f-sys.md) | Erases a volume. This API uses a promise to return the result. |
| [format](arkts-corefile-volumemanager-format-f-sys.md#format) | Formats a volume. This API uses an asynchronous callback to return the result. Currently, only the virtual file allocation table (VFAT), ext4 and exFAT file systems are supported. Only unmounted volumes can be formatted. After a volume is formatted, the UUID, mounting path, and description of the volume will change. |
| [format](arkts-corefile-volumemanager-format-f-sys.md#format-1) | Formats a volume. This API uses a promise to return the result. Currently, only the virtual file allocation table (VFAT), ext4 and exFAT file systems are supported. Only unmounted volumes can be formatted. After a volume is formatted, the UUID, mounting path, and description of the volume will change. |
| [formatPartition](arkts-corefile-volumemanager-formatpartition-f-sys.md) | Formats a partition on a disk. This API uses a promise to return the result. |
| [getAllDisks](arkts-corefile-volumemanager-getalldisks-f-sys.md) | Querying Information About All Disks. |
| [getAllVolumes](arkts-corefile-volumemanager-getallvolumes-f-sys.md#getallvolumes) | Obtains information about all volumes of this external storage device. This API uses an asynchronous callback to return the result. |
| [getAllVolumes](arkts-corefile-volumemanager-getallvolumes-f-sys.md#getallvolumes-1) | Obtains information about all volumes of this external storage device. This API uses a promise to return the result. |
| [getDiskById](arkts-corefile-volumemanager-getdiskbyid-f-sys.md) | Querying disk information based on the disk ID. |
| [getOpProcess](arkts-corefile-volumemanager-getopprocess-f-sys.md) | Gets the operation progress of a volume. This API uses a promise to return the result. |
| [getPartitionTable](arkts-corefile-volumemanager-getpartitiontable-f-sys.md) | Obtains partition table information based on the disk ID. This API uses a promise to return the result. |
| [getVolumeById](arkts-corefile-volumemanager-getvolumebyid-f-sys.md#getvolumebyid) | Obtains information about a volume based on the volume ID. This API uses an asynchronous callback to return the result. |
| [getVolumeById](arkts-corefile-volumemanager-getvolumebyid-f-sys.md#getvolumebyid-1) | Obtains information about a volume based on the volume ID. This API uses a promise to return the result. |
| [getVolumeByUuid](arkts-corefile-volumemanager-getvolumebyuuid-f-sys.md#getvolumebyuuid) | Obtains information about a volume based on the UUID. This API uses an asynchronous callback to return the result. |
| [getVolumeByUuid](arkts-corefile-volumemanager-getvolumebyuuid-f-sys.md#getvolumebyuuid-1) | Obtains information about a volume based on the universally unique identifier (UUID). This API uses a promise to return the result. |
| [isVolumeInUse](arkts-corefile-volumemanager-isvolumeinuse-f-sys.md) | Query whether the specified volume is currently in use. This API uses a promise to return the result. |
| [mount](arkts-corefile-volumemanager-mount-f-sys.md#mount) | Mounts a volume. This API uses an asynchronous callback to return the result. Currently, only the FAT, exFAT, ext4 and NTFS file systems are supported. |
| [mount](arkts-corefile-volumemanager-mount-f-sys.md#mount-1) | Mounts a volume. This API uses a promise to return the result. Currently, only the FAT, exFAT, ext4 and NTFS file systems are supported. |
| [partition](arkts-corefile-volumemanager-partition-f-sys.md#partition) | Partitions a disk. This API uses an asynchronous callback to return the result. The system supports access to multi-partition disks. Currently, this API can partition a disk into only one partition. |
| [partition](arkts-corefile-volumemanager-partition-f-sys.md#partition-1) | Partitions a disk. This API uses a promise to return the result. The system supports access to multi-partition disks. Currently, this API can partition a disk into only one partition. |
| [setVolumeDescription](arkts-corefile-volumemanager-setvolumedescription-f-sys.md#setvolumedescription) | Sets volume description. This API uses an asynchronous callback to return the result. |
| [setVolumeDescription](arkts-corefile-volumemanager-setvolumedescription-f-sys.md#setvolumedescription-1) | Sets volume description. This API uses a promise to return the result. |
| [unmount](arkts-corefile-volumemanager-unmount-f-sys.md#unmount) | Unmounts a volume. This API uses an asynchronous callback to return the result. |
| [unmount](arkts-corefile-volumemanager-unmount-f-sys.md#unmount-1) | Unmounts a volume. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [ExternalDiskInfo](arkts-corefile-volumemanager-externaldiskinfo-i.md) | External disk information. |
| [ExternalVolumeInfo](arkts-corefile-volumemanager-externalvolumeinfo-i.md) | External volume information. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [Disk](arkts-corefile-volumemanager-disk-i-sys.md) | Disk information. |
| [FormatParams](arkts-corefile-volumemanager-formatparams-i-sys.md) | Format options for partition formatting. |
| [PartitionInfo](arkts-corefile-volumemanager-partitioninfo-i-sys.md) | Partition information. |
| [PartitionParams](arkts-corefile-volumemanager-partitionparams-i-sys.md) | Partition creation options. |
| [PartitionTableInfo](arkts-corefile-volumemanager-partitiontableinfo-i-sys.md) | Partition table information. |
| [Volume](arkts-corefile-volumemanager-volume-i-sys.md) | Get All Volumes. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [DiskType](arkts-corefile-volumemanager-disktype-e-sys.md) | Disk type. |
<!--DelEnd-->
