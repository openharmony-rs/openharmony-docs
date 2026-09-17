# CloudDisk_ResultList

```c
typedef struct CloudDisk_ResultList {...} CloudDisk_ResultList
```

## Overview

A struct that encapsulates the file sync result. It includes the absolute path of the file, sync result, and sync state or failure cause.

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) pathInfo | Absolute path information of the file.<br>**Since**: 21 |
| bool isSuccess{false} | Whether the operation is successful. The value true indicates the operation is successful; the value false (default) indicates the opposite.<br>**Since**: 21 |
| [CloudDisk_SyncState](capi-oh-cloud-disk-manager-h.md#clouddisk_syncstate) syncState | File sync state. It takes effect only when **isSuccess** is set to true.<br>**Since**: 21 |
| [CloudDisk_ErrorReason](capi-oh-cloud-disk-manager-h.md#clouddisk_errorreason) errorReason | Reason why the file sync state fails to be obtained. It takes effect only when **isSuccess** is set to **false**.<br>**Since**: 21 |


