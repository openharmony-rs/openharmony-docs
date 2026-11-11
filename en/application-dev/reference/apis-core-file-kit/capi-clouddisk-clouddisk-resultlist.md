# CloudDisk_ResultList
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=8f945fc466618eb449a6fc25874599465b1fce70 translatedAt=2026-11-03T03:42:37.513Z pushedAt=2026-11-04T03:11:33.433Z nl=1 -->

```c
typedef struct CloudDisk_ResultList {...} CloudDisk_ResultList
```

## Overview

Indicates the result of a file synchronization operation. This structure contains file path information, the operation result (success or failure), and the synchronization state or failure reason. It is applicable to scenarios where the result of a file synchronization operation is queried. Developers can use isSuccess to determine whether the operation succeeded, and obtain the detailed state or failure reason through syncState or errorReason.

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) pathInfo | Absolute path information of the file.|
| bool isSuccess{false} | Whether the operation is successful. The value **true** indicates the operation is successful; the value **false** (default) indicates the opposite.  |
| [CloudDisk_SyncState](capi-oh-cloud-disk-manager-h.md#clouddisk_syncstate) syncState | Synchronization state of the file. For specific values and their meanings, see [CloudDisk_SyncState](capi-oh-cloud-disk-manager-h.md#clouddisk_syncstate). This field takes effect only when isSuccess is true. |
| [CloudDisk_ErrorReason](capi-oh-cloud-disk-manager-h.md#clouddisk_errorreason) errorReason | Reason for the failure of the file synchronization operation. For specific error types and their meanings, see [CloudDisk_ErrorReason](capi-oh-cloud-disk-manager-h.md#clouddisk_errorreason). This field takes effect only when isSuccess is false. |


