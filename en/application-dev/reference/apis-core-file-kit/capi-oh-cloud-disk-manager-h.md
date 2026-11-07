# oh_cloud_disk_manager.h
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @yangwei_814916-->
<!--Designer: @hwzhangchuang-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=054fc5e77d4aade491541c0c5d73757a31378403 translatedAt=2026-11-04T03:46:21.849Z pushedAt=2026-11-04T10:12:33.437Z nl=1 -->

## Overview

Defines the interfaces of the cloud disk management module, providing the capabilities to register, activate, listen to, and query cloud disk sync root paths. It supports listening to file changes, setting and querying file sync status, as well as creating, determining, and converting placeholder files and updating file metadata. It is applicable to scenarios where cloud disk file sync and change listening need to be implemented within an application.

**File to include**: <filemanagement/clouddiskmanager/oh_cloud_disk_manager.h>

**Library**: libohclouddiskmanager.so

**System capability**: SystemCapability.FileManagement.CloudDiskManager

**Since**: 21

**Related module**: [CloudDisk](capi-clouddisk.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) | CloudDisk_PathInfo/CloudDisk_FileIdInfo/CloudDisk_SyncFolderPath | **CloudDisk_PathInfo**: a struct that encapsulates the file path information.<br> **CloudDisk_FileIdInfo**: a struct that encapsulates the file ID.<br> **CloudDisk_SyncFolderPath**: a struct that encapsulates the sync root path.|
| [CloudDisk_FileSyncState](capi-clouddisk-clouddisk-filesyncstate.md) | CloudDisk_FileSyncState | A struct that encapsulates the file sync state.|
| [CloudDisk_ChangeData](capi-clouddisk-clouddisk-changedata.md) | CloudDisk_ChangeData | A struct that encapsulates the event data generated when a single file under the sync root path is changed. It includes the file's unique ID, the parent directory's unique ID, relative path, change type, file size, and timestamp.|
| [CloudDisk_ChangesResult](capi-clouddisk-clouddisk-changesresult.md) | CloudDisk_ChangesResult | A struct that encapsulates the file change result under the sync root path. It includes the next change sequence number, end flag, and an array of change data items.|
| [CloudDisk_FailedList](capi-clouddisk-clouddisk-failedlist.md) | CloudDisk_FailedList | A struct that encapsulates the list of files that failed to synchronize. It includes the file path information and the specific error cause.|
| [CloudDisk_ResultList](capi-clouddisk-clouddisk-resultlist.md) | CloudDisk_ResultList | A struct that encapsulates the file sync result. It includes the absolute path of the file, sync result, and sync state or failure cause.|
| [CloudDisk_DisplayNameInfo](capi-clouddisk-clouddisk-displaynameinfo.md) | CloudDisk_DisplayNameInfo | A struct that encapsulates the display name of the sync root path.|
| [CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md) | CloudDisk_SyncFolder | Attribute information of a sync root path. |
| [OH_CloudDisk_PlaceholderInfo](capi-clouddisk-oh-clouddisk-placeholderinfo.md) | OH_CloudDisk_PlaceholderInfo | File metadata information used by placeholder-related operations. |
| [OH_CloudDisk_PlaceholderCustomInfo](capi-clouddisk-oh-clouddisk-placeholdercustominfo.md) | OH_CloudDisk_PlaceholderCustomInfo | Opaque custom information associated with a placeholder. |
| [OH_CloudDisk_SyncFolderEx](capi-clouddisk-oh-clouddisk-syncfolderex.md) | OH_CloudDisk_SyncFolderEx | Attribute information of a sync root path that supports placeholders. When using it, the version field must be set to a valid version macro (for example, [OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1](#macros)) before the structure is passed to any API. At runtime, the version is used to determine field validity; when a lower version is specified, fields introduced in higher versions are ignored. |
| [OH_CloudDisk_DataBuf](capi-clouddisk-oh-clouddisk-databuf.md) | OH_CloudDisk_DataBuf | Cloud disk data buffer information. |
| [OH_CloudDisk_CallbackReqHead](capi-clouddisk-oh-clouddisk-callbackreqhead.md) | OH_CloudDisk_CallbackReqHead | Cloud disk callback request header information. |
| [OH_CloudDisk_DehydrateInfo](capi-clouddisk-oh-clouddisk-dehydrateinfo.md) | OH_CloudDisk_DehydrateInfo | Dehydration authorization information. |
| [OH_CloudDisk_FetchDataRequest](capi-clouddisk-oh-clouddisk-fetchdatarequest.md) | OH_CloudDisk_FetchDataRequest | Data fetch request information. |
| [OH_CloudDisk_CallbackContext](capi-clouddisk-oh-clouddisk-callbackcontext.md) | OH_CloudDisk_CallbackContext | Union of callback request context information. |
| [OH_CloudDisk_FetchData](capi-clouddisk-oh-clouddisk-fetchdata.md) | OH_CloudDisk_FetchData | Result of fetching cloud file data. |
| [OH_CloudDisk_CallbackResponse](capi-clouddisk-oh-clouddisk-callbackresponse.md) | OH_CloudDisk_CallbackResponse | Union of callback response information. |

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [CloudDisk_SyncState](#clouddisk_syncstate) | CloudDisk_SyncState | Enumerates the file sync states.|
| [CloudDisk_OperationType](#clouddisk_operationtype) | CloudDisk_OperationType | Enumerates the file change types.|
| [CloudDisk_ErrorReason](#clouddisk_errorreason) | CloudDisk_ErrorReason | Enumerates the file sync failure causes.|
| [CloudDisk_SyncFolderState](#clouddisk_syncfolderstate) | CloudDisk_SyncFolderState | Enumerates the sync root path states.|
| [OH_CloudDisk_CallbackType](#oh_clouddisk_callbacktype) | OH_CloudDisk_CallbackType | Cloud disk callback type enum value. |
| [OH_CloudDisk_HydratePriority](#oh_clouddisk_hydratepriority) | OH_CloudDisk_HydratePriority | Hydrate priority enum value. |
| [OH_CloudDisk_PlaceholderState](#oh_clouddisk_placeholderstate) | OH_CloudDisk_PlaceholderState | Placeholder state enum value. |

### Macros
 
| Name | Description |
| -- | -- |
| OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1 1 | Used to identify the version of the OH_CloudDisk_SyncFolderEx structure. When new fields are added to the structure, a new version macro will be defined. At runtime, valid fields are determined by the version information. The reader should verify the version in the OH_CloudDisk_SyncFolderEx structure before accessing the corresponding fields to avoid accessing undefined memory.<br>**Since version:** 26.0.1 |

### Function

| Name| Description|
| -- | -- |
| [CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, void (\*callback)(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_ChangeData changeDatas[], size_t bufferLength))](#oh_clouddisk_registersyncfolderchanges) | The application registers a callback function to obtain file changes under the sync root path. It is applicable to scenarios that require real-time monitoring of file creation, deletion, modification, and other change events under the sync root path. |
| [CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath)](#oh_clouddisk_unregistersyncfolderchanges) | The application cancels the registration of the callback for file changes under the sync root path. It is applicable to scenarios where the application no longer needs to monitor file changes, switches accounts, or releases monitoring resources. |
| [CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, uint64_t startUsn, size_t count, CloudDisk_ChangesResult **changesResult)](#oh_clouddisk_getsyncfolderchanges) | The application obtains the historical operation records under the sync root path. It is applicable to scenarios that require querying file change history on demand, resuming sync progress after reconnection, or troubleshooting sync issues. |
| [CloudDisk_ErrorCode OH_CloudDisk_SetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_FileSyncState fileSyncStates[], size_t bufferLength, CloudDisk_FailedList **failedLists, size_t *failedCount)](#oh_clouddisk_setfilesyncstates) | The application sets the sync status of files under the sync root path. It is applicable to scenarios that require manually controlling file sync behavior. |
| [CloudDisk_ErrorCode OH_CloudDisk_GetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo paths[], size_t bufferLength, CloudDisk_ResultList **resultLists, size_t *resultCount)](#oh_clouddisk_getfilesyncstates) | The application queries the sync status of files under the sync root path. It is applicable to scenarios that require displaying sync status in the UI, determining whether a file has completed syncing, or checking whether file sync has failed. |
| [CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolder(const CloudDisk_SyncFolder *syncFolder)](#oh_clouddisk_registersyncfolder) | The application registers a sync root. It is applicable to scenarios that require setting a local directory as a cloud disk sync directory. |
| [CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)](#oh_clouddisk_unregistersyncfolder) | The application cancels the registration of a sync root. It is applicable to scenarios that require removing a cloud disk sync directory. It is usually called after deactivating the sync root. |
| [CloudDisk_ErrorCode OH_CloudDisk_ActiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)](#oh_clouddisk_activesyncfolder) | The application activates a sync root. It is applicable to scenarios that require starting or resuming file sync. |
| [CloudDisk_ErrorCode OH_CloudDisk_DeactiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)](#oh_clouddisk_deactivesyncfolder) | The application deactivates a sync root. It is applicable to scenarios that require pausing file sync or releasing sync resources. |
| [CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolders(CloudDisk_SyncFolder **syncFolders, size_t *count)](#oh_clouddisk_getsyncfolders) | The application obtains all sync roots. It is applicable to scenarios that require querying currently registered sync directories, displaying a sync directory list, or restoring sync status. |
| [CloudDisk_ErrorCode OH_CloudDisk_UpdateCustomAlias(const CloudDisk_SyncFolderPath syncFolderPath, const char *customAlias, size_t customAliasLength)](#oh_clouddisk_updatecustomalias) | The application updates the alias of a sync root. It is applicable to scenarios that require setting a custom display name for a sync directory, distinguishing multiple sync directories, or displaying a friendly directory name in the UI. |
| [CloudDisk_ErrorCode OH_CloudDisk_CreatePlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, const OH_CloudDisk_PlaceholderInfo placeholderInfo, const OH_CloudDisk_PlaceholderCustomInfo *customInfo)](#oh_clouddisk_createplaceholder) | Creates a placeholder file under the registered sync root path. |
| [CloudDisk_ErrorCode OH_CloudDisk_IsPlaceholderFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, bool *isPlaceholder)](#oh_clouddisk_isplaceholderfile) | Determines whether a file under the registered sync root path is a placeholder file. |
| [CloudDisk_ErrorCode OH_CloudDisk_GetPlaceholderState(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, OH_CloudDisk_PlaceholderState *state)](#oh_clouddisk_getplaceholderstate) | Obtains the placeholder state of a file under the registered sync root path. |
| [CloudDisk_ErrorCode OH_CloudDisk_ConvertPlaceholderToFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo)](#oh_clouddisk_convertplaceholdertofile) | Converts a placeholder file under the registered sync root path into a 0-byte regular file. |
| [CloudDisk_ErrorCode OH_CloudDisk_MarkFileAsPlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo)](#oh_clouddisk_markfileasplaceholder) | Marks a regular file as a fully hydrated placeholder file without changing its data or metadata. |
| [CloudDisk_ErrorCode OH_CloudDisk_UnmarkPlaceholderFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo)](#oh_clouddisk_unmarkplaceholderfile) | Converts a fully hydrated placeholder file into a regular file without changing its data or metadata. |
| [CloudDisk_ErrorCode OH_CloudDisk_HydratePlaceholder(const CloudDisk_SyncFolderPath *syncFolderPath, const CloudDisk_PathInfo *filePath, OH_CloudDisk_CallbackType type, OH_CloudDisk_HydratePriority priority)](#oh_clouddisk_hydrateplaceholder) | Actively hydrates a placeholder file or cancels hydration. |
| [CloudDisk_ErrorCode OH_CloudDisk_Execute(const OH_CloudDisk_CallbackReqHead reqHead, OH_CloudDisk_CallbackContext reqContext, OH_CloudDisk_CallbackResponse rsp)](#oh_clouddisk_execute) | Responds to a callback request. |
| [CloudDisk_ErrorCode OH_CloudDisk_DehydrateFile(const CloudDisk_SyncFolderPath *syncFolderPath, const CloudDisk_PathInfo *filePath)](#oh_clouddisk_dehydratefile) | Performs dehydration on a fully or partially hydrated placeholder file. |
| [CloudDisk_ErrorCode OH_CloudDisk_UpdatePlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, const OH_CloudDisk_PlaceholderInfo placeholderInfo, const OH_CloudDisk_PlaceholderCustomInfo *customInfo)](#oh_clouddisk_updateplaceholder) | Updates file metadata. It supports both placeholder files and regular files. |
| [CloudDisk_ErrorCode OH_CloudDisk_GetPlaceholderCustomInfo(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, uint8_t *dataBuf, size_t *inOutDataLength)](#oh_clouddisk_getplaceholdercustominfo) | Obtains the opaque custom information associated with a placeholder. |
| [CloudDisk_ErrorCode OH_CloudDisk_RegisterCallbackTable(const CloudDisk_SyncFolderPath syncFolderPath, void (\*callback)(const OH_CloudDisk_CallbackReqHead reqHead, OH_CloudDisk_CallbackContext reqContext))](#oh_clouddisk_registercallbacktable) | Registers the callback table for hydration and dehydration requests. |
| [CloudDisk_ErrorCode OH_CloudDisk_UnregisterCallbackTable(const CloudDisk_SyncFolderPath syncFolderPath)](#oh_clouddisk_unregistercallbacktable) | Unregisters the callback table for hydration and dehydration requests. |
| [CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolderEx(const OH_CloudDisk_SyncFolderEx *syncFolder)](#oh_clouddisk_registersyncfolderex) | The application registers a sync root with placeholder information. |
| [CloudDisk_ErrorCode OH_CloudDisk_GetSyncFoldersEx(OH_CloudDisk_SyncFolderEx **syncFolders, size_t *count)](#oh_clouddisk_getsyncfoldersex) | The application obtains all sync roots with placeholder information. |

## Enum Description

### CloudDisk_SyncState

```c
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

```c
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
| OH_CLOUD_DISK_CLOSE_MODIFY = 6 | The file is closed after its content is modified.<br>**Since version:** 26.0.1 |

### CloudDisk_ErrorReason

```c
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

```c
enum CloudDisk_SyncFolderState
```

**Description**

Enumerates the sync root path states.

**Since**: 21

| Value| Description|
| -- | -- |
| INACTIVE = 0 | The sync root path is inactive.|
| ACTIVE = 1 | The sync root path is active.|

### OH_CloudDisk_CallbackType

```c
enum OH_CloudDisk_CallbackType
```

**Description**

Cloud disk callback type enum value.

**Since:** 26.0.1

| Enum Item | Description |
| -- | -- |
| OH_CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA = 0 | Obtains cloud file data for hydration.<br>**Since version:** 26.0.1 |
| OH_CLOUD_DISK_CALLBACK_TYPE_CANCEL_FETCH_DATA = 1 | Cancels the retrieval of cloud file data.<br>**Since version:** 26.0.1 |
| OH_CLOUD_DISK_CALLBACK_TYPE_DEHYDRATE = 2 | Requests dehydration authorization.<br>**Since version:** 26.0.1 |

### OH_CloudDisk_HydratePriority

```c
enum OH_CloudDisk_HydratePriority
```

**Description**

Hydrate priority enum value.

**Since:** 26.0.1

| Enum Item | Description |
| -- | -- |
| OH_CLOUD_DISK_HYDRATE_PRIORITY_LOW = 0 | Low priority.<br>**Since**: 26.0.1 |
| OH_CLOUD_DISK_HYDRATE_PRIORITY_NORMAL = 1 | Normal priority.<br>**Since**: 26.0.1 |
| OH_CLOUD_DISK_HYDRATE_PRIORITY_HIGH = 2 | High priority.<br>**Since**: 26.0.1 |

### OH_CloudDisk_PlaceholderState

```c
enum OH_CloudDisk_PlaceholderState
```

**Description**

Placeholder state enum value.

**Since:** 26.0.1

| Enum Item | Description |
| -- | -- |
| OH_CLOUD_DISK_PLACEHOLDER_STATE_NONE = 0 | The file is not a placeholder.<br>**Since**: 26.0.1 |
| OH_CLOUD_DISK_PLACEHOLDER_STATE_UNHYDRATED = 1 | The placeholder has no local data.<br>**Since**: 26.0.1 |
| OH_CLOUD_DISK_PLACEHOLDER_STATE_PARTIALLY_HYDRATED = 2 | The placeholder has partial local data.<br>**Since**: 26.0.1 |
| OH_CLOUD_DISK_PLACEHOLDER_STATE_FULLY_HYDRATED = 3 | The placeholder has complete local data.<br>**Since**: 26.0.1 |

## Function Description

### OH_CloudDisk_RegisterSyncFolderChanges()

```c
CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, void (*callback)(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_ChangeData changeDatas[], size_t bufferLength))
```

**Description**

Registers a callback to obtain file changes in the sync root path.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md).|
| callback | Registered callback.|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_UnregisterSyncFolderChanges()

```c
CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath)
```

**Description**

Unregisters the callback for file changes in the sync root path.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md).|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_GetSyncFolderChanges()

```c
CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, uint64_t startUsn, size_t count, CloudDisk_ChangesResult **changesResult)
```

**Description**

Obtains the change history in the sync root path.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md).|
| uint64_t startUsn | Start change sequence number. The value range is [0, 2^64 – 1].|
| size_t count | Number of file changes. The value range is [1, 100].|
| [CloudDisk_ChangesResult](capi-clouddisk-clouddisk-changesresult.md) **changesResult | File change result. For details, see [CloudDisk_ChangesResult](capi-clouddisk-clouddisk-changesresult.md).|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_SetFileSyncStates()

```c
CloudDisk_ErrorCode OH_CloudDisk_SetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_FileSyncState fileSyncStates[], size_t bufferLength, CloudDisk_FailedList **failedLists, size_t *failedCount)
```

**Description**

Sets the file sync state in the sync root path.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md).|
| [const CloudDisk_FileSyncState](capi-clouddisk-clouddisk-filesyncstate.md) fileSyncStates[] | [CloudDisk_FileSyncState](capi-clouddisk-clouddisk-filesyncstate.md) array of the file path and its target sync state.|
| size_t bufferLength | Length of the sync state array to be set. The value range is [1, 100].|
| [CloudDisk_FailedList](capi-clouddisk-clouddisk-failedlist.md) **failedLists | Double pointer to the [CloudDisk_FailedList](capi-clouddisk-clouddisk-failedlist.md) array that contains files whose sync states failed to be set.|
| size_t *failedCount | Pointer to the length of the file list array whose sync states failed to be set.|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_GetFileSyncStates()

```c
CloudDisk_ErrorCode OH_CloudDisk_GetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo paths[], size_t bufferLength, CloudDisk_ResultList **resultLists, size_t *resultCount)
```

**Description**

Obtains the file sync state in the sync root path.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md).|
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) paths[] | [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) array of the sync state.|
| size_t bufferLength | Length of the sync state array. The value range is [1, 100].|
| [CloudDisk_ResultList](capi-clouddisk-clouddisk-resultlist.md) **resultLists | Double pointer to the file sync result. For details, see [CloudDisk_ResultList](capi-clouddisk-clouddisk-resultlist.md).|
| size_t *resultCount | Pointer to the number of files that fail to be synchronized.|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_RegisterSyncFolder()

```c
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

### OH_CloudDisk_RegisterSyncFolderEx()
 
```c
CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolderEx(const OH_CloudDisk_SyncFolderEx *syncFolder)
```
 
**Description**
 
Registers a sync root with placeholder information for an application. This API is applicable to scenarios where a local directory needs to be set as a cloud disk sync directory and whether placeholders are supported needs to be marked.
 
**Since:** 26.0.1
 
**Parameters**
 
| Parameter | Description |
| -- | -- |
| [const OH_CloudDisk_SyncFolderEx](capi-clouddisk-oh-clouddisk-syncfolderex.md) *syncFolder | Sync root path with placeholder to be registered. |
 
**Return**
 
| Type | Description |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise. |

### OH_CloudDisk_UnregisterSyncFolder()

```c
CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)
```

**Description**

Unregisters the sync root.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md).|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_ActiveSyncFolder()

```c
CloudDisk_ErrorCode OH_CloudDisk_ActiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)
```

**Description**

Activates the sync root.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md).|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_DeactiveSyncFolder()

```c
CloudDisk_ErrorCode OH_CloudDisk_DeactiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)
```

**Description**

Deactivates the sync root.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md).|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_GetSyncFolders()

```c
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

### OH_CloudDisk_GetSyncFoldersEx()
 
```c
CloudDisk_ErrorCode OH_CloudDisk_GetSyncFoldersEx(OH_CloudDisk_SyncFolderEx **syncFolders, size_t *count)
```
 
**Description**
 
The application retrieves all sync roots with placeholders. This is applicable to scenarios such as querying the currently registered sync directories with placeholders, displaying the sync directory list, or restoring the sync status.
 
**Since:** 26.0.1
 
**Parameters**
 
| Parameter | Description |
| -- | -- |
| [OH_CloudDisk_SyncFolderEx](capi-clouddisk-oh-clouddisk-syncfolderex.md) **syncFolders | Output parameter. Returns the array of sync root paths with placeholders [OH_CloudDisk_SyncFolderEx](capi-clouddisk-oh-clouddisk-syncfolderex.md). |
| size_t *count | Output parameter. The number of sync roots with placeholders registered by the current application. The value is 0 when there is no sync root with placeholders. |
 
**Return**
 
| Type | Description |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise. |

### OH_CloudDisk_UpdateCustomAlias()

```c
CloudDisk_ErrorCode OH_CloudDisk_UpdateCustomAlias(const CloudDisk_SyncFolderPath syncFolderPath, const char *customAlias, size_t customAliasLength)
```

**Description**

Updates the sync root alias.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | Sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md).|
| const char *customAlias | Pointer to the custom alias, which cannot contain the following characters: \\\/\*\?\<\>\|\:\". Additionally, the full name cannot be composed solely of spaces, a single dot (.), or two consecutive dots (..).| |
| size_t customAliasLength | Length of the custom alias. Value range: [0, 255].|

**Returns**

| Type| Description|
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns [CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) if the API is called successfully; returns [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) otherwise.|

### OH_CloudDisk_CreatePlaceholder()

```c
CloudDisk_ErrorCode OH_CloudDisk_CreatePlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, const OH_CloudDisk_PlaceholderInfo placeholderInfo, const OH_CloudDisk_PlaceholderCustomInfo *customInfo)
```

**Description**

Creates a placeholder file under the registered sync root path.

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | The registered sync root path. |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | The relative path of the placeholder file under the sync root path. The path cannot be empty, cannot start or end with "/", and cannot contain "./" or "../" path segments. |
| [const OH_CloudDisk_PlaceholderInfo](capi-clouddisk-oh-clouddisk-placeholderinfo.md) placeholderInfo | The metadata used when creating the placeholder file. |
| [const OH_CloudDisk_PlaceholderCustomInfo](capi-clouddisk-oh-clouddisk-placeholdercustominfo.md) *customInfo | Optional opaque custom information. Pass NULL to indicate that it is not provided. |

**Return**

| Type | Description |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns CLOUD_DISK_OK if the API call succeeds; otherwise returns the cloud disk management module error code CloudDisk_ErrorCode. |

### OH_CloudDisk_IsPlaceholderFile()

```c
CloudDisk_ErrorCode OH_CloudDisk_IsPlaceholderFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, bool *isPlaceholder)
```

**Description**

Checks whether a specified file under a registered sync root path is a placeholder file.

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | The registered sync root path. |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | Relative path of the file to be checked under the sync root path. For details, see [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md). |
| bool *isPlaceholder | Output parameter. This parameter is valid only when the return value is CLOUD_DISK_OK. true indicates that the file is a placeholder file; false indicates that the file is not a placeholder file. When an error code other than CLOUD_DISK_NOT_SUPPORTED is returned, this value is set to false; when CLOUD_DISK_NOT_SUPPORTED is returned, this value is not modified. |

**Return**

| Type | Description |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | If the interface call succeeds, CLOUD_DISK_OK is returned; if the current device does not support this feature, CLOUD_DISK_NOT_SUPPORTED is returned; otherwise, an error code CloudDisk_ErrorCode of the cloud disk management module is returned. |

### OH_CloudDisk_ConvertPlaceholderToFile()

```c
CloudDisk_ErrorCode OH_CloudDisk_ConvertPlaceholderToFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo)
```

**Description**

Converts a placeholder file under the registered sync root path into a 0-byte regular file.

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | The registered sync root path. |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | The relative path information of the placeholder file to be converted under the sync root path. |

**Return**

| Type | Description |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | If the interface call succeeds, CLOUD_DISK_OK is returned; if the file is not a placeholder, OH_CLOUD_DISK_NOT_A_PLACEHOLDER is returned; otherwise, the error code CloudDisk_ErrorCode of the cloud disk management module is returned. |

### OH_CloudDisk_GetPlaceholderState()

```c
CloudDisk_ErrorCode OH_CloudDisk_GetPlaceholderState(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, OH_CloudDisk_PlaceholderState *state)
```

**Description**

Obtains the placeholder state of a file under the registered sync root path.

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | The registered sync root path. |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | Relative path information of the file to be queried under the sync root path. |
| [OH_CloudDisk_PlaceholderState](#oh_clouddisk_placeholderstate) *state | Output parameter. Placeholder state. On error, this value is set to OH_CLOUD_DISK_PLACEHOLDER_STATE_NONE. |

**Return**

| Type | Description |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | If the interface is called successfully, CLOUD_DISK_OK is returned; if the stored state is invalid, OH_CLOUD_DISK_INVALID_PLACEHOLDER_STATE is returned; otherwise, the cloud disk management module error code CloudDisk_ErrorCode is returned. |

### OH_CloudDisk_MarkFileAsPlaceholder()

```c
CloudDisk_ErrorCode OH_CloudDisk_MarkFileAsPlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo)
```

**Description**

Marks a regular file as a fully hydrated placeholder file without changing its data or metadata.

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | The registered sync root path. |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | Relative path information of the file to be marked under the sync root path. |

**Return**

| Type | Description |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | If the interface call succeeds, CLOUD_DISK_OK is returned; if the file is already a placeholder, OH_CLOUD_DISK_IS_A_PLACEHOLDER is returned; otherwise, the error code CloudDisk_ErrorCode of the cloud disk management module is returned. |

### OH_CloudDisk_UnmarkPlaceholderFile()

```c
CloudDisk_ErrorCode OH_CloudDisk_UnmarkPlaceholderFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo)
```

**Description**

Converts a fully hydrated placeholder file into a regular file without changing its data or metadata.

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | The registered sync root path. |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | The relative path information of the placeholder file to be converted under the sync root path. |

**Return**

| Type | Description |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | If the interface is called successfully, CLOUD_DISK_OK is returned; if the file is not a placeholder, OH_CLOUD_DISK_NOT_A_PLACEHOLDER is returned; if it is not fully hydrated, OH_CLOUD_DISK_PLACEHOLDER_NOT_FULLY_HYDRATED is returned; otherwise, the cloud disk management module error code CloudDisk_ErrorCode is returned. |

### OH_CloudDisk_HydratePlaceholder()

```c
CloudDisk_ErrorCode OH_CloudDisk_HydratePlaceholder(const CloudDisk_SyncFolderPath *syncFolderPath, const CloudDisk_PathInfo *filePath, OH_CloudDisk_CallbackType type, OH_CloudDisk_HydratePriority priority)
```

**Description**

Actively hydrates a placeholder file or cancels hydration. The specific behavior is determined by the [type](#oh_clouddisk_callbacktype) parameter: hydration is performed when the value is OH_CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA, and hydration is canceled when the value is OH_CLOUD_DISK_CALLBACK_TYPE_CANCEL_FETCH_DATA. This function returns after the task is submitted, without waiting for the callback or for the file hydration to complete.

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath *syncFolderPath | Pointer to the registered sync root path information. |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) *filePath | Pointer to the relative path information of the file under the sync root path. |
| [OH_CloudDisk_CallbackType](#oh_clouddisk_callbacktype) type | Hydration callback type, which must be OH_CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA or OH_CLOUD_DISK_CALLBACK_TYPE_CANCEL_FETCH_DATA. |
| [OH_CloudDisk_HydratePriority](#oh_clouddisk_hydratepriority) priority | Hydration priority. This value is not used for cancellation operations. |

**Return**

| Type | Description |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns CLOUD_DISK_OK if the task is queued or canceled; otherwise returns the cloud disk management module error code CloudDisk_ErrorCode. |

### OH_CloudDisk_Execute()

```c
CloudDisk_ErrorCode OH_CloudDisk_Execute(const OH_CloudDisk_CallbackReqHead reqHead, OH_CloudDisk_CallbackContext reqContext, OH_CloudDisk_CallbackResponse rsp)
```

**Description**

Responds to a callback request and writes the obtained data block into the active placeholder hydration task. A single data block cannot exceed 128 KiB. The function copies all input fields and data before returning.

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| [const OH_CloudDisk_CallbackReqHead](capi-clouddisk-oh-clouddisk-callbackreqhead.md) reqHead | Callback request header received by the application. |
| [OH_CloudDisk_CallbackContext](capi-clouddisk-oh-clouddisk-callbackcontext.md) reqContext | Callback request context, which contains the relative file path of the callback request. |
| [OH_CloudDisk_CallbackResponse](capi-clouddisk-oh-clouddisk-callbackresponse.md) rsp | Data block obtained by the application. |

**Return**

| Type | Description |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns CLOUD_DISK_OK if the API call succeeds; otherwise returns the cloud disk management module error code CloudDisk_ErrorCode. |

### OH_CloudDisk_DehydrateFile()

```c
CloudDisk_ErrorCode OH_CloudDisk_DehydrateFile(const CloudDisk_SyncFolderPath *syncFolderPath, const CloudDisk_PathInfo *filePath)
```

**Description**

Performs a dehydrate operation on a fully or partially hydrated placeholder after the application is authorized. For a partially hydrated placeholder, the downloaded data is discarded.

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath *syncFolderPath | Pointer to the registered sync root path information. |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) *filePath | Pointer to the relative path information of the file under the sync root path. |

**Return**

| Type | Description |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | If the interface call succeeds, CLOUD_DISK_OK is returned; if the application denies the dehydrate operation, OH_CLOUD_DISK_DEHYDRATE_DENIED is returned; otherwise, the error code CloudDisk_ErrorCode of the cloud disk management module is returned. |

### OH_CloudDisk_UpdatePlaceholder()

```c
CloudDisk_ErrorCode OH_CloudDisk_UpdatePlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, const OH_CloudDisk_PlaceholderInfo placeholderInfo, const OH_CloudDisk_PlaceholderCustomInfo *customInfo)
```

**Description**

Updates the metadata of a file under the sync root path. Supports both placeholder files and regular files.

**Since:** 26.0.1

**Parameters:**

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | The registered sync root path. |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | The relative path information of the file whose metadata is to be updated. |
| [const OH_CloudDisk_PlaceholderInfo](capi-clouddisk-oh-clouddisk-placeholderinfo.md) placeholderInfo | The file metadata information to be updated. For details, see [OH_CloudDisk_PlaceholderInfo](capi-clouddisk-oh-clouddisk-placeholderinfo.md). |
| [const OH_CloudDisk_PlaceholderCustomInfo](capi-clouddisk-oh-clouddisk-placeholdercustominfo.md) *customInfo | Optional opaque custom information. Pass NULL to retain the existing value. |

**Returns:**

| Type | Description |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns CLOUD_DISK_OK if the API call succeeds; otherwise returns the cloud disk management module error code CloudDisk_ErrorCode. |

### OH_CloudDisk_GetPlaceholderCustomInfo()

```c
CloudDisk_ErrorCode OH_CloudDisk_GetPlaceholderCustomInfo(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, uint8_t *dataBuf, size_t *inOutDataLength)
```

**Description**

Obtains the opaque custom information associated with a placeholder.

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | The registered sync root path. |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | Relative path information of the placeholder file to be queried under the sync root path. |
| uint8_t *dataBuf | Output parameter. Output buffer allocated by the caller. If the buffer capacity is insufficient, the function returns the error code INVALID_ARG. |
| size_t *inOutDataLength | Output parameter. Passes in the preallocated buffer capacity when called; after the function is executed, it is modified to the length of data actually written. If the buffer capacity is insufficient, the function returns the error code INVALID_ARG, and inOutDataLength is set to the data length required for a successful write. |

**Return**

| Type | Description |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | If the interface is called successfully, CLOUD_DISK_OK is returned; if the placeholder has no custom information, OH_CLOUD_DISK_PLACEHOLDER_CUSTOM_INFO_NOT_FOUND is returned; in other cases, an error code CloudDisk_ErrorCode of the cloud disk management module is returned. |

### OH_CloudDisk_RegisterCallbackTable()

```c
CloudDisk_ErrorCode OH_CloudDisk_RegisterCallbackTable(const CloudDisk_SyncFolderPath syncFolderPath, void (*callback)(const OH_CloudDisk_CallbackReqHead reqHead, OH_CloudDisk_CallbackContext reqContext))
```

**Description**

Registers a callback table for hydration and dehydration requests.<br>The handling of different callback types is as follows:<br>- FETCH_DATA: asynchronous notification. The application must deep-copy the request before the callback returns, and call [OH_CloudDisk_Execute()](#oh_clouddisk_execute) later to respond.<br>- CANCEL_FETCH_DATA: asynchronous notification. The application must stop the matching download, and does not need to call OH_CloudDisk_Execute as confirmation.<br>- DEHYDRATE: synchronous notification. Complete the processing before the callback returns.<br>All pointers in the callback request are borrowed pointers and are valid only before the callback returns.

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | The registered sync root path. |
| void (*callback)(const OH_CloudDisk_CallbackReqHead reqHead, OH_CloudDisk_CallbackContext reqContext) | Callback to register. |

**Return**

| Type | Description |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns CLOUD_DISK_OK if the API call succeeds; otherwise returns the cloud disk management module error code CloudDisk_ErrorCode. |

### OH_CloudDisk_UnregisterCallbackTable()

```c
CloudDisk_ErrorCode OH_CloudDisk_UnregisterCallbackTable(const CloudDisk_SyncFolderPath syncFolderPath)
```

**Description**

Unregisters the callback table for hydration and dehydration requests.

**Since:** 26.0.1

**Parameters**

| Parameter | Description |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | The registered sync root path. |

**Return**

| Type | Description |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | Returns CLOUD_DISK_OK if the API call succeeds; otherwise returns the cloud disk management module error code CloudDisk_ErrorCode. |
