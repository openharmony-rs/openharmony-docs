# OH_CloudDisk_PlaceholderInfo

```c
typedef struct OH_CloudDisk_PlaceholderInfo {...} OH_CloudDisk_PlaceholderInfo
```

## Overview

Metadata information for the placeholder file.

**Since**: 26.1.0

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t logicalSize | Logical size of the placeholder file, in bytes, which reflects the actual size of the cloud file.<br>**Since**: 26.1.0 |
| uint64_t atimeMs | Time when the placeholder file is created, which maps the actual time when the file is created on the cloud.<br>**Since**: 26.1.0 |
| uint64_t mtimeMs | Modification time of the placeholder file, which maps the actual modification time of the cloud file.<br>**Since**: 26.1.0 |


