# OH_CloudDisk_OperationTypeArray

```c
typedef struct OH_CloudDisk_OperationTypeArray {...} OH_CloudDisk_OperationTypeArray
```

## Overview

Array that stores the enumeration of file change types.

<!--Device-struct OH_CloudDisk_OperationTypeArray {...}--><!--Device-struct OH_CloudDisk_OperationTypeArray {...}-End-->

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Since**: 26.1.0

**Related module**: [CloudDisk](capi-core-file-kit-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [const CloudDisk_OperationType](capi-oh-cloud-disk-manager-h.md#clouddisk_operationtype) *data | Pointer to an array of element type [CloudDisk_OperationType](capi-oh-cloud-disk-manager-h.md#clouddisk_operationtype).<br>**Since**: 26.1.0<br><!--Device-const CloudDisk_OperationType *data--><!--Device-const CloudDisk_OperationType *data-End--> |
| int64_t length | Length of an array. The value ranges from 1 to 8.<br>**Since**: 26.1.0<br><!--Device-int64_t length--><!--Device-int64_t length-End--> |


