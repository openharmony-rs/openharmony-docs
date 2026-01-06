# CloudDisk_SyncFolder
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct CloudDisk_SyncFolder {...} CloudDisk_SyncFolder
```

## Overview

A struct that encapsulates the sync root property information.

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| CloudDisk_SyncFolderPath path | Sync root path.|
| [CloudDisk_SyncFolderState](capi-oh-cloud-disk-manager-h.md#clouddisk_syncfolderstate) state | State of the sync root path.|
| [CloudDisk_DisplayNameInfo](capi-clouddisk-clouddisk-displaynameinfo.md) displayNameInfo | Alias of the sync root path.|
