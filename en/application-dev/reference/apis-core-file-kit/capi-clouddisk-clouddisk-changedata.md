# CloudDisk_ChangeData
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=8f945fc466618eb449a6fc25874599465b1fce70 translatedAt=2026-11-03T03:40:55.893Z pushedAt=2026-11-04T03:11:33.424Z nl=1 -->

```c
typedef struct CloudDisk_ChangeData {...} CloudDisk_ChangeData
```

## Overview

Defines the data structure of a single file change event under the sync root path. This structure contains detailed information about the file change, including the update sequence number, unique ID, unique ID of the parent directory, relative path, change type, file size, file modification time, and the time when the change event occurred. It is applicable to scenarios such as cloud disk file synchronization and incremental update queries.

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint64_t updateSequenceNumber{0} | Update sequence number of the change event. It monotonically increases by 1 each time the file changes and is used for incremental change queries. Range: [0, 2^64 - 1]. It is recommended to record the sequence number of the last query and continue to obtain subsequent changes from that sequence number in the next query. |
| CloudDisk_FileIdInfo fileId | Globally unique file ID. It remains unchanged within the lifecycle of the file.|
| CloudDisk_FileIdInfo parentFileId | Unique ID of the parent directory to which the file or directory belongs.|
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | Path information of the file relative to the sync root path. |
| [CloudDisk_OperationType](capi-oh-cloud-disk-manager-h.md#clouddisk_operationtype) operationType | Change operation type of this file. For details about the specific enumeration values and their meanings, see [CloudDisk_OperationType](capi-oh-cloud-disk-manager-h.md#clouddisk_operationtype). |
| uint64_t size{0} | File size, in bytes.|
| uint64_t mtime{0} | File modification time, in milliseconds.|
| uint64_t timeStamp{0} | Time when a change event occurs, in milliseconds.|


