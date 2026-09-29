# OH_CloudDisk_FetchRangeDataRequest

```c
struct OH_CloudDisk_FetchRangeDataRequest {...}
```

## Overview

A struct that encapsulates the fetch range data request information.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Since**: 26.2.0

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) filePath | Relative file path in the sync root path.<br>**Since**: 26.2.0 |
| uint64_t offset | Start offset of the fetched range data, in bytes.<br>**Since**: 26.2.0 |
| uint64_t size | Size of the fetched range data, in bytes.<br>**Since**: 26.2.0 |
| OH_CloudDisk_DataBuf *data | The data that needs to be read.<br>**Since**: 26.2.0 |


