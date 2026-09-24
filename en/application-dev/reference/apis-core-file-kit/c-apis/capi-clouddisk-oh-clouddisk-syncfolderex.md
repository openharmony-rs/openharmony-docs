# OH_CloudDisk_SyncFolderEx

```c
typedef struct OH_CloudDisk_SyncFolderEx {...} OH_CloudDisk_SyncFolderEx
```

## Overview

Defines the sync folder of cloud disk with placeholder support.<br> The version field must be set to a valid version macro (e.g. {@link OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1}) before passing this structure to any API. The runtime uses version to determine which fields are valid; fields introduced in a later version are ignored when a lower version is specified.

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Since**: 26.0.1

**Related module**: [CloudDisk](capi-clouddisk.md)

**Header file**: [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t version | Indicates the version of this structure. Must be initialized to a valid version macro such as {@link OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1}.<br>**Since**: 26.0.1 |
| CloudDisk_SyncFolderPath path | Indicates the path of sync folder.<br>**Since**: 26.0.1 |
| [CloudDisk_SyncFolderState](capi-oh-cloud-disk-manager-h.md#clouddisk_syncfolderstate) state | Indicates the state of sync folder.<br>**Since**: 26.0.1 |
| [CloudDisk_DisplayNameInfo](capi-clouddisk-clouddisk-displaynameinfo.md) displayNameInfo | Indicates the displayName info of sync folder.<br>**Since**: 26.0.1 |
| bool isSupportPlaceHolder | Indicates whether the sync folder supports placeholder.<br>**Since**: 26.0.1 |


