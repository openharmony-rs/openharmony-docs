# OH_CloudDisk_SyncFolderEx
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=63f676f930e02731b3b56880e25a7af9eeee92f4 translatedAt=2026-11-03T03:45:58.107Z pushedAt=2026-11-04T03:11:33.453Z nl=1 -->

```c
typedef struct OH_CloudDisk_SyncFolderEx {...} OH_CloudDisk_SyncFolderEx
```

## Overview

Attribute information of a sync root path with placeholders, including the sync root path, sync state, display name, and whether placeholders are supported. It is used for managing sync root paths with placeholders in the cloud disk sync feature. Before passing the structure to any API, you must set the version field to a valid version macro (for example, [OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1](capi-oh-cloud-disk-manager-h.md#macros)). At runtime, the version is used to determine which fields are valid; when a lower version is specified, fields introduced in a higher version are ignored.

**Since:** 26.0.1

**Related module:** [CloudDisk](capi-clouddisk.md)

**Header file:** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint32_t version | Version information of this structure. It must be initialized to a valid version macro, for example, [OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1](capi-oh-cloud-disk-manager-h.md#macros).<br>**Since:** 26.0.1 |
| CloudDisk_SyncFolderPath path | Sync root path, used to specify the location of the cloud disk sync root directory with placeholders.<br>**Since:** 26.0.1 |
| [CloudDisk_SyncFolderState](capi-oh-cloud-disk-manager-h.md#clouddisk_syncfolderstate) state | State of the sync root path.<br>**Since:** 26.0.1 |
| [CloudDisk_DisplayNameInfo](capi-clouddisk-clouddisk-displaynameinfo.md) displayNameInfo | Alias information of the sync root path, used to set the display name of the sync root path for easier user identification and management.<br>**Since:** 26.0.1 |
| bool isSupportPlaceHolder | Whether the sync root supports placeholders.<br>**Since:** 26.0.1 |
