# oh_cloud_disk_manager.h
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @foryourself-->

## Overview

This file defines the APIs for the cloud disk management module.

**File to include**: <filemanagement/cloud_disk_manager/oh_cloud_disk_manager.h>

**Library**: libohclouddiskmanager.so

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) | CloudDisk_PathInfo | A struct that encapsulates the file path information.|
| [CloudDisk_FileSyncState](capi-clouddisk-clouddisk-filesyncstate.md) | CloudDisk_FileSyncState | A struct that encapsulates the file sync state.|
| [CloudDisk_ChangeData](capi-clouddisk-clouddisk-changedata.md) | CloudDisk_ChangeData | A struct that encapsulates the event data generated when a single file under the sync root path is changed. It includes the file's unique ID, the parent directory's unique ID, relative path, change type, file size, and timestamp.|
| [CloudDisk_ChangesResult](capi-clouddisk-clouddisk-changesresult.md) | CloudDisk_ChangesResult | A struct that encapsulates the file change result under the sync root path. It includes the next change sequence number, end flag, and an array of change data items.|
| [CloudDisk_FailedList](capi-clouddisk-clouddisk-failedlist.md) | CloudDisk_FailedList | A struct that encapsulates the list of files that failed to synchronize. It includes the file path information and the specific error cause.|
| [CloudDisk_ResultList](capi-clouddisk-clouddisk-resultlist.md) | CloudDisk_ResultList | A struct that encapsulates the file sync result. It includes the absolute path of the file, sync result, and sync state or failure cause.|
| [CloudDisk_DisplayNameInfo](capi-clouddisk-clouddisk-displaynameinfo.md) | CloudDisk_DisplayNameInfo | A struct that encapsulates the display name of the sync root path.|
| [CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md) | CloudDisk_SyncFolder | A struct that encapsulates the sync root property information.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [CloudDisk_SyncState](#clouddisk_syncstate) | CloudDisk_SyncState | Enumerates the file sync states.|
| [CloudDisk_OperationType](#clouddisk_operationtype) | CloudDisk_OperationType | Enumerates the file change types.|
| [CloudDisk_ErrorReason](#clouddisk_errorreason) | CloudDisk_ErrorReason | Enumerates the file sync failure causes.|
| [CloudDisk_SyncFolderState](#clouddisk_syncfolderstate) | CloudDisk_SyncFolderState | Enumerates the sync root path states.|

### Function

| Name| Description|
| -- | -- |
| [CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, void (\*callback)(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_ChangeData changeDatas[], size_t bufferLength))](#oh_clouddisk_registersyncfolderchanges) | Registers a callback to obtain file changes in the sync root path.|
| [CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath)](#oh_clouddisk_unregistersyncfolderchanges) | Unregisters the callback for file changes in the sync root path.|
| [CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, uint64_t startUsn, size_t count, CloudDisk_ChangesResult **changesResult)](#oh_clouddisk_getsyncfolderchanges) | Obtains the change history in the sync root path.|
| [CloudDisk_ErrorCode OH_CloudDisk_SetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_FileSyncState fileSyncStates[], size_t bufferLength, CloudDisk_FailedList **failedLists, size_t *failedCount)](#oh_clouddisk_setfilesyncstates) | Sets the file sync state in the sync root path.|
| [CloudDisk_ErrorCode OH_CloudDisk_GetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo paths[], size_t bufferLength, CloudDisk_ResultList **resultLists, size_t *resultCount)](#oh_clouddisk_getfilesyncstates) | Obtains the file sync state in the sync root path.|
| [CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolder(const CloudDisk_SyncFolder *syncFolder)](#oh_clouddisk_registersyncfolder) | Registers a sync root.|
| [CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)](#oh_clouddisk_unregistersyncfolder) | Unregisters the sync root.|
| [CloudDisk_ErrorCode OH_CloudDisk_ActiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)](#oh_clouddisk_activesyncfolder) | Activates the sync root.|
| [CloudDisk_ErrorCode OH_CloudDisk_DeactiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)](#oh_clouddisk_deactivesyncfolder) | Deactivates the sync root.|
| [CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolders(CloudDisk_SyncFolder **syncFolders, size_t *count)](#oh_clouddisk_getsyncfolders) | Obtains all sync roots.|
| [CloudDisk_ErrorCode OH_CloudDisk_UpdateCustomAlias(const CloudDisk_SyncFolderPath syncFolderPath, const char *customAlias, size_t customAliasLength)](#oh_clouddisk_updatecustomalias) | Updates the sync root alias.|

## Enum Description

### CloudDisk_SyncState

```
enum CloudDisk_SyncState
```

**Description**

Enumerates the file sync states.

**Since**: 21

| Value| Description|
| -- | -- |
| IDLE = 0 | The file is idle, and no sync operation is performed.|
| SYNCING = 1 | The file is being synced.|
| SYNC_SUCCEEDED = 2 | The file is synced successfully.|
| SYNC_FAILED = 3 | The file fails to be synced.|
| SYNC_CANCELED = 4 | The file sync is canceled.|
| SYNC_CONFLICTED = 5 | The file sync conflicts.|

### CloudDisk_OperationType

```
enum CloudDisk_OperationType
```

**Description**

Enumerates the file change types.

**Since**: 21

| Value| Description|
| -- | -- |
| CREATE = 0 | Create a file or directory.|
| DELETE = 1 | Delete a file or directory.|
| MOVE_FROM = 2 | Move this file or directory.|
| MOVE_TO = 3 | Move to this file or directory.|
| CLOSE_WRITE = 4 | Close the file after the write operation.|
| SYNC_FOLDER_INVALID = 5 | Invalid sync root path.|

### CloudDisk_ErrorReason

```
enum CloudDisk_ErrorReason
```

**Description**

Enumerates the file sync failure causes.

**Since**: 21

| Value| Description|
| -- | -- |
| INVALID_ARGUMENT = 0 | The input parameter is invalid.|
| NO_SUCH_FILE = 1 | The file or directory does not exist.|
| NO_SPACE_LEFT = 2 | The remaining space on the device is insufficient.|
| OUT_OF_RANGE = 3 | The file is not in the sync root path.|
| NO_SYNC_STATE = 4 | The sync state is not set.|

### CloudDisk_SyncFolderState

```
enum CloudDisk_SyncFolderState
```

**Description**

Enumerates the sync root path states.

**Since**: 21

| Value| Description|
| -- | -- |
| INACTIVE = 0 | The sync root path is inactive.|
| ACTIVE = 1 | The sync root path is active.|


## Function Description

### OH_CloudDisk_RegisterSyncFolderChanges()

```
CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, void (*callback)(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_ChangeData changeDatas[], size_t bufferLength))
```

**Description**

Registers a callback to obtain file changes in the sync root path.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see {@link CloudDisk_SyncFolderPath}.|
| callback | Registered callback.|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_UnregisterSyncFolderChanges()

```
CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath)
```

**Description**

Unregisters the callback for file changes in the sync root path.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see {@link CloudDisk_SyncFolderPath}.|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_GetSyncFolderChanges()

```
CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, uint64_t startUsn, size_t count, CloudDisk_ChangesResult **changesResult)
```

**Description**

Obtains the change history in the sync root path.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see {@link CloudDisk_SyncFolderPath}.|
| uint64_t startUsn | Start change sequence number. The value range is [0, 2^64 – 1].|
| size_t count | Number of file changes. The value range is [1, 100].|
| [CloudDisk_ChangesResult](capi-clouddisk-clouddisk-changesresult.md) **changesResult | File change result. For details, see [CloudDisk_ChangesResult](capi-clouddisk-clouddisk-changesresult.md).|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_SetFileSyncStates()

```
CloudDisk_ErrorCode OH_CloudDisk_SetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_FileSyncState fileSyncStates[], size_t bufferLength, CloudDisk_FailedList **failedLists, size_t *failedCount)
```

**Description**

Sets the file sync state in the sync root path.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see {@link CloudDisk_SyncFolderPath}.|
| [const CloudDisk_FileSyncState](capi-clouddisk-clouddisk-filesyncstate.md) fileSyncStates[] | [CloudDisk_FileSyncState](capi-clouddisk-clouddisk-filesyncstate.md) array of the file path and its target sync state.|
| size_t bufferLength | Length of the sync state array to be set. The value range is [1, 100].|
| [CloudDisk_FailedList](capi-clouddisk-clouddisk-failedlist.md) **failedLists | Double pointer to the [CloudDisk_FailedList](capi-clouddisk-clouddisk-failedlist.md) array that contains files whose sync states failed to be set.|
| size_t *failedCount | Pointer to the length of the file list array whose sync states failed to be set.|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_GetFileSyncStates()

```
CloudDisk_ErrorCode OH_CloudDisk_GetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo paths[], size_t bufferLength, CloudDisk_ResultList **resultLists, size_t *resultCount)
```

**Description**

Obtains the file sync state in the sync root path.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see {@link CloudDisk_SyncFolderPath}.|
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) paths[] | [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) array of the sync state.|
| size_t bufferLength | Length of the sync state array. The value range is [1, 100].|
| [CloudDisk_ResultList](capi-clouddisk-clouddisk-resultlist.md) **resultLists | Double pointer to the file sync result. For details, see [CloudDisk_ResultList](capi-clouddisk-clouddisk-resultlist.md).|
| size_t *resultCount | Pointer to the number of files that fail to be synchronized.|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_RegisterSyncFolder()

```
CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolder(const CloudDisk_SyncFolder *syncFolder)
```

**Description**

Registers a sync root.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| [const CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md) *syncFolder | Sync root path to be registered. For details, see [CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md).|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_UnregisterSyncFolder()

```
CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)
```

**Description**

Unregisters the sync root.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path to be unregistered. For details, see {@link CloudDisk_SyncFolderPath}.|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_ActiveSyncFolder()

```
CloudDisk_ErrorCode OH_CloudDisk_ActiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)
```

**Description**

Activates the sync root.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path to be activated. For details, see {@link CloudDisk_SyncFolderPath}.|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_DeactiveSyncFolder()

```
CloudDisk_ErrorCode OH_CloudDisk_DeactiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)
```

**Description**

Deactivates the sync root.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path to be deactivated. For details, see {@link CloudDisk_SyncFolderPath}.|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_GetSyncFolders()

```
CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolders(CloudDisk_SyncFolder **syncFolders, size_t *count)
```

**Description**

Obtains all sync roots.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| [CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md) **syncFolders | Double pointer to the sync root path array [CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md).|
| size_t *count | Pointer to the number of sync roots registered by the current cloud disk.|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_UpdateCustomAlias()

```
CloudDisk_ErrorCode OH_CloudDisk_UpdateCustomAlias(const CloudDisk_SyncFolderPath syncFolderPath, const char *customAlias, size_t customAliasLength)
```

**Description**

Updates the sync root alias.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path of the alias to be updated. For details, see {@link CloudDisk_SyncFolderPath}.|
| const char *customAlias | Pointer to the new custom alias, which cannot contain the following characters: [\/:*?<>\|"]. Additionally, the full name cannot be composed solely of spaces, a single dot (.), or two consecutive dots (..).| |
| size_t customAliasLength | Length of the custom alias. Value range: [0, 255].|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|
