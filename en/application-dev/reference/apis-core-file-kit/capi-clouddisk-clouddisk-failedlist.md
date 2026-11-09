# CloudDisk_FailedList
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=8f945fc466618eb449a6fc25874599465b1fce70 translatedAt=2026-11-03T03:41:49.297Z pushedAt=2026-11-04T03:11:33.428Z nl=1 -->

```c
typedef struct CloudDisk_FailedList {...} CloudDisk_FailedList
```

## Overview

Information about the files that failed in a synchronization operation. This structure contains the file path information and the specific error cause of the failure. It is used to locate the failed files and handle the failure cause after a synchronization operation fails.

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) pathInfo | Absolute path information of the file that failed to synchronize.|
| [CloudDisk_ErrorReason](capi-oh-cloud-disk-manager-h.md#clouddisk_errorreason) errorReason | Reason for file synchronization failure. For specific error types and their meanings, see [CloudDisk_ErrorReason](capi-oh-cloud-disk-manager-h.md#clouddisk_errorreason). |


