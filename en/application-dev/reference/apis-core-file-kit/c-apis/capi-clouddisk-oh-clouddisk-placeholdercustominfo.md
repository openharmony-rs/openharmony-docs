# OH_CloudDisk_PlaceholderCustomInfo

```c
typedef struct OH_CloudDisk_PlaceholderCustomInfo {...} OH_CloudDisk_PlaceholderCustomInfo
```

## Overview

Opaque custom information associated with a placeholder.

<!--Device-struct OH_CloudDisk_PlaceholderCustomInfo {...}--><!--Device-struct OH_CloudDisk_PlaceholderCustomInfo {...}-End-->

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Since**: 26.0.1

**Related module**: [CloudDisk](capi-core-file-kit-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| size_t dataLength | Length of the custom information, in bytes.<br>**Since**: 26.0.1<br><!--Device-size_t dataLength--><!--Device-size_t dataLength-End--> |
| const uint8_t *data | Pointer to the custom information.<br>**Since**: 26.0.1<br><!--Device-const uint8_t *data--><!--Device-const uint8_t *data-End--> |


