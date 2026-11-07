# OH_CloudDisk_SyncFolderEx
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @yangwei_814916-->
<!--Designer: @hwzhangchuang-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=ce0913c3ec9f03af65b8717b522431d902788443 translatedAt=2026-11-04T03:43:18.587Z pushedAt=2026-11-04T10:12:33.416Z nl=2 -->

 
```c
typedef struct OH_CloudDisk_SyncFolderEx {...} OH_CloudDisk_SyncFolderEx
```
 
## Overview
 
Attribute information of a sync root path with placeholders, including the sync root path, sync state, display name, and whether placeholders are supported. It is used for managing sync root paths with placeholders in the cloud disk sync feature. Before passing the structure to any API, you must set the version field to a valid version macro (for example, [OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1](capi-oh-cloud-disk-manager-h.md#macros)). At runtime, the version is used to determine which fields are valid; when a lower version is specified, fields introduced in a higher version are ignored.
 
**Since:** 26.0.1
 
**Related module**: [CloudDisk](capi-clouddisk.md)
 
**Header File:** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)
 
## Summary
 
### Member Variables
 
| Name | Description |
| -- | -- |
| uint32_t version | Version information of this structure. It must be initialized to a valid version macro, for example, [OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1](capi-oh-cloud-disk-manager-h.md#macros).<br>**Since:** 26.0.1 |
| CloudDisk_SyncFolderPath path | Sync root path, used to specify the location of the cloud disk sync root directory with placeholders.<br>**Since:** 26.0.1 |
| [CloudDisk_SyncFolderState](capi-oh-cloud-disk-manager-h.md#clouddisk_syncfolderstate) state | State of the sync root path.<br>**Since:** 26.0.1 |
| [CloudDisk_DisplayNameInfo](capi-clouddisk-clouddisk-displaynameinfo.md) displayNameInfo | Alias information of the sync root path, used to set the display name of the sync root path for easier user identification and management.<br>**Since:** 26.0.1 |
| bool isSupportPlaceHolder | Whether the sync root supports placeholders.<br>**Since:** 26.0.1 |