# CloudDisk_ChangeData

```c
typedef struct CloudDisk_ChangeData {...} CloudDisk_ChangeData
```

## Overview

A struct that encapsulates the event data generated when a single file under the sync root path is changed. It includes the file's unique ID, the parent directory's unique ID, relative path, change type, file size, and timestamp.

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t updateSequenceNumber{0} | Update sequence number of the change event. It is incremented by 1 monotonically each time a file is changed, and is used for incremental change query. Value range: [0, 2^64 – 1]<br>**Since**: 21 |
| CloudDisk_FileIdInfo fileId | Globally unique file ID. It remains unchanged within the lifecycle of the file.<br>**Since**: 21 |
| CloudDisk_FileIdInfo parentFileId | Unique ID of the parent directory to which the file or directory belongs.<br>**Since**: 21 |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | Relative path of the file under the sync root path.<br>**Since**: 21 |
| [CloudDisk_OperationType](capi-oh-cloud-disk-manager-h.md#clouddisk_operationtype) operationType | Change operation type of the file (for example, create, delete, and move).<br>**Since**: 21 |
| uint64_t size{0} | File size, in bytes.<br>**Since**: 21 |
| uint64_t mtime{0} | File modification time, in milliseconds.<br>**Since**: 21 |
| uint64_t timeStamp{0} | Time when a change event occurs, in milliseconds.<br>**Since**: 21 |


