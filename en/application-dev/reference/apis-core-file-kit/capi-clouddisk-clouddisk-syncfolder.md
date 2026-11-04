# CloudDisk_SyncFolder
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=8f945fc466618eb449a6fc25874599465b1fce70 translatedAt=2026-11-03T03:43:02.603Z pushedAt=2026-11-04T03:11:33.435Z nl=1 -->

```c
typedef struct CloudDisk_SyncFolder {...} CloudDisk_SyncFolder
```

## Overview

Sync root path attribute information, including the sync root path, sync state, and display name. Developers can obtain the complete attributes of a sync root path through this structure for sync root path management in the cloud disk sync feature.

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| CloudDisk_SyncFolderPath path | Sync root path, used to specify the root directory location for cloud disk synchronization. |
| [CloudDisk_SyncFolderState](capi-oh-cloud-disk-manager-h.md#clouddisk_syncfolderstate) state | Sync root path state. For details about the values and their meanings, see [CloudDisk_SyncFolderState](capi-oh-cloud-disk-manager-h.md#clouddisk_syncfolderstate). |
| [CloudDisk_DisplayNameInfo](capi-clouddisk-clouddisk-displaynameinfo.md) displayNameInfo | Sync root path alias information, used to set the display name of the sync root path for easy user identification and management. |


