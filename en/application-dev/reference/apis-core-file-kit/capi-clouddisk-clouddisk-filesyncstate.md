# CloudDisk_FileSyncState
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=8f945fc466618eb449a6fc25874599465b1fce70 translatedAt=2026-11-03T03:41:51.493Z pushedAt=2026-11-04T03:11:33.429Z nl=1 -->

```c
typedef struct CloudDisk_FileSyncState {...} CloudDisk_FileSyncState
```

## Overview

File synchronization status information, used to describe the cloud disk synchronization status corresponding to a specified file path.

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) filePathInfo | File path information.|
| [CloudDisk_SyncState](capi-oh-cloud-disk-manager-h.md#clouddisk_syncstate) syncState | Synchronization state of the file. For details about the values and their meanings, see [CloudDisk_SyncState](capi-oh-cloud-disk-manager-h.md#clouddisk_syncstate). |


