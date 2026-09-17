# oh_cloud_disk_manager.h

## Overview

This file defines the APIs for the cloud disk management module.

**Library**: libohclouddiskmanager.so

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) | CloudDisk_PathInfo | A struct that encapsulates the file path information. |
| [CloudDisk_FileSyncState](capi-clouddisk-clouddisk-filesyncstate.md) | CloudDisk_FileSyncState | A struct that encapsulates the file sync state. |
| [CloudDisk_ChangeData](capi-clouddisk-clouddisk-changedata.md) | CloudDisk_ChangeData | A struct that encapsulates the event data generated when a single file under the sync root path is changed. It includes the file's unique ID, the parent directory's unique ID, relative path, change type, file size, and timestamp. |
| [CloudDisk_ChangesResult](capi-clouddisk-clouddisk-changesresult.md) | CloudDisk_ChangesResult | A struct that encapsulates the file change result under the sync root path. It includes the next change sequence number, end flag, and an array of change data items. |
| [CloudDisk_FailedList](capi-clouddisk-clouddisk-failedlist.md) | CloudDisk_FailedList | A struct that encapsulates the list of files that failed to synchronize. It includes the file path information and the specific failure cause. |
| [CloudDisk_ResultList](capi-clouddisk-clouddisk-resultlist.md) | CloudDisk_ResultList | A struct that encapsulates the file sync result. It includes the absolute path of the file, sync result, and sync state or failure cause. |
| [CloudDisk_DisplayNameInfo](capi-clouddisk-clouddisk-displaynameinfo.md) | CloudDisk_DisplayNameInfo | A struct that encapsulates the display name of the sync root path. |
| [CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md) | CloudDisk_SyncFolder | A struct that encapsulates the sync root property information. |
| [OH_CloudDisk_SyncFolderEx](capi-clouddisk-oh-clouddisk-syncfolderex.md) | OH_CloudDisk_SyncFolderEx | Defines the sync folder of cloud disk with placeholder support.<br> The version field must be set to a valid version macro (e.g. {@link OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1}) before passing this structure to any API. The runtime uses version to determine which fields are valid; fields introduced in a later version are ignored when a lower version is specified. |
| [OH_CloudDisk_PlaceholderInfo](capi-clouddisk-oh-clouddisk-placeholderinfo.md) | OH_CloudDisk_PlaceholderInfo | Metadata information for the placeholder file. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [CloudDisk_SyncState](#clouddisk_syncstate) | CloudDisk_SyncState | Enumerates the file sync states. |
| [CloudDisk_OperationType](#clouddisk_operationtype) | CloudDisk_OperationType | Enumerates the file change types. |
| [CloudDisk_ErrorReason](#clouddisk_errorreason) | CloudDisk_ErrorReason | Enumerates the file sync failure causes. |
| [CloudDisk_SyncFolderState](#clouddisk_syncfolderstate) | CloudDisk_SyncFolderState | Enumerates the sync root path states. |

### Macro

| Name | Description |
| -- | -- |
| OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1 1 | Indicates the version 1 of OH_CloudDisk_SyncFolderEx.<br> When the structure is extended, a new version macro will be defined. The runtime uses the version field to determine which fields are valid.<br>**Since**: 26.1.0 |

### Function

| Name | Description |
| -- | -- |
| [CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, void (\*callback)(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_ChangeData changeDatas[], size_t bufferLength))](#oh_clouddisk_registersyncfolderchanges) | Registers a callback to obtain file changes in the sync root path. |
| [CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath)](#oh_clouddisk_unregistersyncfolderchanges) | Unregisters the callback for file changes in the sync root path. |
| [CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, uint64_t startUsn, size_t count, CloudDisk_ChangesResult **changesResult)](#oh_clouddisk_getsyncfolderchanges) | Obtains the change history in the sync root path. |
| [CloudDisk_ErrorCode OH_CloudDisk_SetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_FileSyncState fileSyncStates[], size_t bufferLength, CloudDisk_FailedList **failedLists, size_t *failedCount)](#oh_clouddisk_setfilesyncstates) | Sets the file sync state in the sync root path. |
| [CloudDisk_ErrorCode OH_CloudDisk_GetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo paths[], size_t bufferLength, CloudDisk_ResultList **resultLists, size_t *resultCount)](#oh_clouddisk_getfilesyncstates) | Obtains the file sync state in the sync root path. |
| [CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolder(const CloudDisk_SyncFolder *syncFolder)](#oh_clouddisk_registersyncfolder) | Registers a sync root. |
| [CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)](#oh_clouddisk_unregistersyncfolder) | Unregisters the sync root. |
| [CloudDisk_ErrorCode OH_CloudDisk_ActiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)](#oh_clouddisk_activesyncfolder) | Activates the sync root. |
| [CloudDisk_ErrorCode OH_CloudDisk_DeactiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)](#oh_clouddisk_deactivesyncfolder) | Deactivates the sync root. |
| [CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolders(CloudDisk_SyncFolder **syncFolders, size_t *count)](#oh_clouddisk_getsyncfolders) | Obtains all sync roots. |
| [CloudDisk_ErrorCode OH_CloudDisk_UpdateCustomAlias(const CloudDisk_SyncFolderPath syncFolderPath, const char *customAlias, size_t customAliasLength)](#oh_clouddisk_updatecustomalias) | Updates the sync root alias. |
| [CloudDisk_ErrorCode OH_CloudDisk_CreatePlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, const OH_CloudDisk_PlaceholderInfo placeholderInfo)](#oh_clouddisk_createplaceholder) | Creates a placeholder in a registered sync folder. |
| [CloudDisk_ErrorCode OH_CloudDisk_IsPlaceholderFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, bool *isPlaceholder)](#oh_clouddisk_isplaceholderfile) | Checks whether a file in a sync folder is a placeholder file. |
| [CloudDisk_ErrorCode OH_CloudDisk_ConvertPlaceholderToFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo)](#oh_clouddisk_convertplaceholdertofile) | Converts a placeholder file to a 0-byte normal file. |
| [CloudDisk_ErrorCode OH_CloudDisk_UpdatePlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, const OH_CloudDisk_PlaceholderInfo placeholderInfo)](#oh_clouddisk_updateplaceholder) | Updates file metadata (supports placeholder and normal files). |
| [CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolderEx(const OH_CloudDisk_SyncFolderEx *syncFolder)](#oh_clouddisk_registersyncfolderex) | Registers a sync folder with placeholder support info. |
| [CloudDisk_ErrorCode OH_CloudDisk_GetSyncFoldersEx(OH_CloudDisk_SyncFolderEx **syncFolders, size_t *count)](#oh_clouddisk_getsyncfoldersex) | Gets the sync folders with placeholder support info. |

### Variable

| Name | Description |
| -- | -- |
| CloudDisk_PathInfo CloudDisk_FileIdInfo | a struct that encapsulates the file ID.<br>**Since**: 21 |
| CloudDisk_PathInfo CloudDisk_SyncFolderPath | a struct that encapsulates the sync root path.<br>**Since**: 21 |

## Enum type description

### CloudDisk_SyncState

```c
enum CloudDisk_SyncState
```

**Description**

Enumerates the file sync states.

**Since**: 21

| Enum item | Description |
| -- | -- |
| IDLE = 0 | The file is idle, and no sync operation is performed.<br>**Since**: 21 |
| SYNCING = 1 | The file is being synced.<br>**Since**: 21 |
| SYNC_SUCCEEDED = 2 | The file is synced successfully.<br>**Since**: 21 |
| SYNC_FAILED = 3 | The file fails to be synced.<br>**Since**: 21 |
| SYNC_CANCELED = 4 | The file sync is canceled.<br>**Since**: 21 |
| SYNC_CONFLICTED = 5 | The file sync conflicts.<br>**Since**: 21 |

### CloudDisk_OperationType

```c
enum CloudDisk_OperationType
```

**Description**

Enumerates the file change types.

**Since**: 21

| Enum item | Description |
| -- | -- |
| CREATE = 0 | Create a file or directory.<br>**Since**: 21 |
| DELETE = 1 | Delete a file or directory.<br>**Since**: 21 |
| MOVE_FROM = 2 | Move this file or directory.<br>**Since**: 21 |
| MOVE_TO = 3 | Move to this file or directory.<br>**Since**: 21 |
| CLOSE_WRITE = 4 | Close the file after the write operation.<br>**Since**: 21 |
| SYNC_FOLDER_INVALID = 5 | Invalid sync root path.<br>**Since**: 21 |
| OH_CLOUD_DISK_CLOSE_MODIFY = 6 | Close a file after modifying content.<br>**Since**: 26.1.0 |

### CloudDisk_ErrorReason

```c
enum CloudDisk_ErrorReason
```

**Description**

Enumerates the file sync failure causes.

**Since**: 21

| Enum item | Description |
| -- | -- |
| INVALID_ARGUMENT = 0 | The input parameter is invalid.<br>**Since**: 21 |
| NO_SUCH_FILE = 1 | The file or directory does not exist.<br>**Since**: 21 |
| NO_SPACE_LEFT = 2 | The remaining space on the device is insufficient.<br>**Since**: 21 |
| OUT_OF_RANGE = 3 | The file is not in the sync root path.<br>**Since**: 21 |
| NO_SYNC_STATE = 4 | The sync state is not set.<br>**Since**: 21 |

### CloudDisk_SyncFolderState

```c
enum CloudDisk_SyncFolderState
```

**Description**

Enumerates the sync root path states.

**Since**: 21

| Enum item | Description |
| -- | -- |
| INACTIVE = 0 | The sync root path is inactive.<br>**Since**: 21 |
| ACTIVE = 1 | The sync root path is active.<br>**Since**: 21 |


## Function description

### OH_CloudDisk_RegisterSyncFolderChanges()

```c
CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, void (*callback)(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_ChangeData changeDatas[], size_t bufferLength))
```

**Description**

Registers a callback to obtain file changes in the sync root path.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| onst CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md). |
| void (\*callback)(const CloudDisk_SyncFolderPath syncFolderPath | Registered callback. |

**Returns**:

| Type | Description |
| -- | -- |
| CloudDisk_ErrorCode | Returns {@link CLOUD_DISK_OK} if the API is called successfully; returns {@link CloudDisk_ErrorCode}      otherwise. |

### OH_CloudDisk_UnregisterSyncFolderChanges()

```c
CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath)
```

**Description**

Unregisters the callback for file changes in the sync root path.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md). |

**Returns**:

| Type | Description |
| -- | -- |
| CloudDisk_ErrorCode | Returns {@link CLOUD_DISK_OK} if the API is called successfully; returns {@link CloudDisk_ErrorCode}      otherwise. |

### OH_CloudDisk_GetSyncFolderChanges()

```c
CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, uint64_t startUsn, size_t count, CloudDisk_ChangesResult **changesResult)
```

**Description**

Obtains the change history in the sync root path.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md). |
| uint64_t startUsn | Start change sequence number. The value range is [0, 2^64 – 1]. |
| size_t count | Number of file changes. The value range is [1, 100]. |
| [CloudDisk_ChangesResult](capi-clouddisk-clouddisk-changesresult.md) **changesResult | File change result. For details, see [CloudDisk_ChangesResult](capi-clouddisk-clouddisk-changesresult.md). |

**Returns**:

| Type | Description |
| -- | -- |
| CloudDisk_ErrorCode | Returns {@link CLOUD_DISK_OK} if the API is called successfully; returns {@link CloudDisk_ErrorCode}      otherwise. |

### OH_CloudDisk_SetFileSyncStates()

```c
CloudDisk_ErrorCode OH_CloudDisk_SetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_FileSyncState fileSyncStates[], size_t bufferLength, CloudDisk_FailedList **failedLists, size_t *failedCount)
```

**Description**

Sets the file sync state in the sync root path.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md). |
| [const CloudDisk_FileSyncState](capi-clouddisk-clouddisk-filesyncstate.md) fileSyncStates[] | The array of [CloudDisk_FileSyncState](capi-clouddisk-clouddisk-filesyncstate.md) specifying the file paths and their target sync states. |
| size_t bufferLength | Length of the sync state array to be set. The value range is [1, 100]. |
| [CloudDisk_FailedList](capi-clouddisk-clouddisk-failedlist.md) **failedLists | Double pointer to the [CloudDisk_FailedList](capi-clouddisk-clouddisk-failedlist.md) array that contains files whose sync states failed to be set. |
| size_t *failedCount | Pointer to the length of the file list array whose sync states failed to be set. |

**Returns**:

| Type | Description |
| -- | -- |
| CloudDisk_ErrorCode | Returns {@link CLOUD_DISK_OK} if the API is called successfully; returns {@link CloudDisk_ErrorCode}      otherwise. |

### OH_CloudDisk_GetFileSyncStates()

```c
CloudDisk_ErrorCode OH_CloudDisk_GetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo paths[], size_t bufferLength, CloudDisk_ResultList **resultLists, size_t *resultCount)
```

**Description**

Obtains the file sync state in the sync root path.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md). |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) paths[] | The array of file paths to query. |
| size_t bufferLength | Length of the sync state array. The value range is [1, 100]. |
| [CloudDisk_ResultList](capi-clouddisk-clouddisk-resultlist.md) **resultLists | Double pointer to the file sync result. For details, see [CloudDisk_ResultList](capi-clouddisk-clouddisk-resultlist.md). |
| size_t *resultCount | Pointer to the number of files that fail to be synchronized. |

**Returns**:

| Type | Description |
| -- | -- |
| CloudDisk_ErrorCode | Returns {@link CLOUD_DISK_OK} if the API is called successfully; returns {@link CloudDisk_ErrorCode}      otherwise. |

### OH_CloudDisk_RegisterSyncFolder()

```c
CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolder(const CloudDisk_SyncFolder *syncFolder)
```

**Description**

Registers a sync root.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md) *syncFolder | Sync root path to be registered. For details, see [CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md). |

**Returns**:

| Type | Description |
| -- | -- |
| CloudDisk_ErrorCode | Returns {@link CLOUD_DISK_OK} if the API is called successfully; returns {@link CloudDisk_ErrorCode}      otherwise. |

### OH_CloudDisk_UnregisterSyncFolder()

```c
CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)
```

**Description**

Unregisters the sync root.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md). |

**Returns**:

| Type | Description |
| -- | -- |
| CloudDisk_ErrorCode | Returns {@link CLOUD_DISK_OK} if the API is called successfully; returns {@link CloudDisk_ErrorCode}      otherwise. |

### OH_CloudDisk_ActiveSyncFolder()

```c
CloudDisk_ErrorCode OH_CloudDisk_ActiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)
```

**Description**

Activates the sync root.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md). |

**Returns**:

| Type | Description |
| -- | -- |
| CloudDisk_ErrorCode | Returns {@link CLOUD_DISK_OK} if the API is called successfully; returns {@link CloudDisk_ErrorCode}      otherwise. |

### OH_CloudDisk_DeactiveSyncFolder()

```c
CloudDisk_ErrorCode OH_CloudDisk_DeactiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)
```

**Description**

Deactivates the sync root.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md). |

**Returns**:

| Type | Description |
| -- | -- |
| CloudDisk_ErrorCode | Returns {@link CLOUD_DISK_OK} if the API is called successfully; returns {@link CloudDisk_ErrorCode}      otherwise. |

### OH_CloudDisk_GetSyncFolders()

```c
CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolders(CloudDisk_SyncFolder **syncFolders, size_t *count)
```

**Description**

Obtains all sync roots.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| [CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md) **syncFolders | Double pointer to the sync root path array [CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md). |
| size_t *count | Pointer to the number of sync roots registered by the current cloud disk. |

**Returns**:

| Type | Description |
| -- | -- |
| CloudDisk_ErrorCode | Returns {@link CLOUD_DISK_OK} if the API is called successfully; returns {@link CloudDisk_ErrorCode}      otherwise. |

### OH_CloudDisk_UpdateCustomAlias()

```c
CloudDisk_ErrorCode OH_CloudDisk_UpdateCustomAlias(const CloudDisk_SyncFolderPath syncFolderPath, const char *customAlias, size_t customAliasLength)
```

**Description**

Updates the sync root alias.

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md). |
| const char *customAlias | Indicates the user-defined alias. |
| size_t customAliasLength | Length of the custom alias. Value range: [0, 255]. |

**Returns**:

| Type | Description |
| -- | -- |
| CloudDisk_ErrorCode | Returns {@link CLOUD_DISK_OK} if the API is called successfully; returns {@link CloudDisk_ErrorCode}      otherwise. |

### OH_CloudDisk_CreatePlaceholder()

```c
CloudDisk_ErrorCode OH_CloudDisk_CreatePlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, const OH_CloudDisk_PlaceholderInfo placeholderInfo)
```

**Description**

Creates a placeholder in a registered sync folder.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Indicates the registered sync folder path. |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | Indicates the relative path in the sync folder. |
| [const OH_CloudDisk_PlaceholderInfo](capi-clouddisk-oh-clouddisk-placeholderinfo.md) placeholderInfo | Indicates the placeholder metadata information. |

**Returns**:

| Type | Description |
| -- | -- |
| CloudDisk_ErrorCode | Returns {@link CLOUD_DISK_OK} if the API is called successfully;<br>    <br>returns {@link CloudDisk_ErrorCode} otherwise. |

### OH_CloudDisk_IsPlaceholderFile()

```c
CloudDisk_ErrorCode OH_CloudDisk_IsPlaceholderFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, bool *isPlaceholder)
```

**Description**

Checks whether a file in a sync folder is a placeholder file.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Indicates the registered sync folder path. |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | Indicates the relative path in the sync folder. |
| bool *isPlaceholder | Output parameter. The value is valid only when the return value is {@link CLOUD_DISK_OK}. Returns true if the file is a placeholder file; returns false otherwise. The value is set to false on error. |

**Returns**:

| Type | Description |
| -- | -- |
| CloudDisk_ErrorCode | Returns {@link CLOUD_DISK_OK} if the API is called successfully;<br>    <br>returns {@link CloudDisk_ErrorCode} otherwise. |

### OH_CloudDisk_ConvertPlaceholderToFile()

```c
CloudDisk_ErrorCode OH_CloudDisk_ConvertPlaceholderToFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo)
```

**Description**

Converts a placeholder file to a 0-byte normal file.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Indicates the registered sync folder path. |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | Indicates the relative path in the sync folder. |

**Returns**:

| Type | Description |
| -- | -- |
| CloudDisk_ErrorCode | Returns {@link CLOUD_DISK_OK} if the API is called successfully;<br>    <br>returns {@link CloudDisk_ErrorCode} otherwise. |

### OH_CloudDisk_UpdatePlaceholder()

```c
CloudDisk_ErrorCode OH_CloudDisk_UpdatePlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, const OH_CloudDisk_PlaceholderInfo placeholderInfo)
```

**Description**

Updates file metadata (supports placeholder and normal files).

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Indicates the registered sync folder path. |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | Indicates the relative path in the sync folder. |
| [const OH_CloudDisk_PlaceholderInfo](capi-clouddisk-oh-clouddisk-placeholderinfo.md) placeholderInfo | Indicates the placeholder metadata. |

**Returns**:

| Type | Description |
| -- | -- |
| CloudDisk_ErrorCode | Returns {@link CLOUD_DISK_OK} if the API is called successfully;<br>    <br>returns {@link CloudDisk_ErrorCode} otherwise. |

### OH_CloudDisk_RegisterSyncFolderEx()

```c
CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolderEx(const OH_CloudDisk_SyncFolderEx *syncFolder)
```

**Description**

Registers a sync folder with placeholder support info.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_CloudDisk_SyncFolderEx](capi-clouddisk-oh-clouddisk-syncfolderex.md) *syncFolder | [in] Indicates the sync folder with placeholder support. |

**Returns**:

| Type | Description |
| -- | -- |
| CloudDisk_ErrorCode | Returns {@link CLOUD_DISK_OK} if the operation is successful;<br>    <br> returns an error code defined in {@link CloudDisk_ErrorCode} otherwise. |

### OH_CloudDisk_GetSyncFoldersEx()

```c
CloudDisk_ErrorCode OH_CloudDisk_GetSyncFoldersEx(OH_CloudDisk_SyncFolderEx **syncFolders, size_t *count)
```

**Description**

Gets the sync folders with placeholder support info.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_CloudDisk_SyncFolderEx](capi-clouddisk-oh-clouddisk-syncfolderex.md) **syncFolders | [out] Output parameter. <br> Returns the array of [OH_CloudDisk_SyncFolderEx](capi-clouddisk-oh-clouddisk-syncfolderex.md) to store the sync folders. |
| size_t *count | [out] Output parameter. Returns the number of sync folders. |

**Returns**:

| Type | Description |
| -- | -- |
| CloudDisk_ErrorCode | Returns {@link CLOUD_DISK_OK} if the operation is successful;<br>    <br> returns an error code defined in {@link CloudDisk_ErrorCode} otherwise. |


