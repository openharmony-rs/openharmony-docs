# OH_CloudDisk_FetchData

```c
typedef struct OH_CloudDisk_FetchData {...} OH_CloudDisk_FetchData
```

## Overview

A struct that encapsulates fetched cloud file data.

<!--Device-struct OH_CloudDisk_FetchData {...}--><!--Device-struct OH_CloudDisk_FetchData {...}-End-->

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Since**: 26.0.1

**Related module**: [CloudDisk](capi-core-file-kit-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t offset | Start offset of the fetched data, in bytes.<br>**Since**: 26.0.1<br><!--Device-uint64_t offset--><!--Device-uint64_t offset-End--> |
| uint64_t size | Size of the fetched data, in bytes.<br>**Since**: 26.0.1<br><!--Device-uint64_t size--><!--Device-uint64_t size-End--> |
| uint64_t totalSize | Total size of the cloud file, in bytes. It is determined when **OH_CloudDisk_Execute()** is called for the first time. The size must be the same for subsequent calls.<br>**Since**: 26.0.1<br><!--Device-uint64_t totalSize--><!--Device-uint64_t totalSize-End--> |
| [OH_CloudDisk_DataBuf](capi-clouddisk-oh-clouddisk-databuf.md) data | File data buffer.<br>**Since**: 26.0.1<br><!--Device-OH_CloudDisk_DataBuf data--><!--Device-OH_CloudDisk_DataBuf data-End--> |
| bool isComplete | Whether the fetched data is the last data block.<br>**Since**: 26.0.1<br><!--Device-bool isComplete--><!--Device-bool isComplete-End--> |


