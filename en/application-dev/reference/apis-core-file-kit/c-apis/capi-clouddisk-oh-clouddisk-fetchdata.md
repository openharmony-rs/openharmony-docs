# OH_CloudDisk_FetchData

```c
struct OH_CloudDisk_FetchData {...}
```

## Overview

A struct that encapsulates fetched cloud file data.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Since**: 26.0.1

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t offset | Start offset of the fetched data, in bytes.<br>**Since**: 26.0.1 |
| uint64_t size | Size of the fetched data, in bytes.<br>**Since**: 26.0.1 |
| uint64_t totalSize | Total size of the cloud file, in bytes.<br>**Since**: 26.0.1 |
| [OH_CloudDisk_DataBuf](capi-clouddisk-oh-clouddisk-databuf.md) data | File data buffer.<br>**Since**: 26.0.1 |
| bool isComplete | Whether the fetched data is the last data block.<br>**Since**: 26.0.1 |


