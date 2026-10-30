# Cloud Disk Service Foundation Adaptation Guide
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @lcm_kiku-->
<!--Designer: @wangyanyue-->
<!--Tester: @zsyztt-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=e4dec04fa8e8c0a22d3f9bd967b695e5ca3e7425 translatedAt=2026-10-29T10:30:53.763Z pushedAt=2026-10-29T10:30:53.763Z nl=1 -->

## When to Use

The cloud disk service foundation provides efficient and secure file management capabilities for managing and querying the status of cloud disk sync roots and their subdirectories, and listening for changes. These APIs are provided by the CloudDisk module. For details, see [oh_cloud_disk_manager.h](../reference/apis-core-file-kit/capi-oh-cloud-disk-manager-h.md).

This development guide covers the following four aspects, which have layered dependencies on one another:

- [Sync Root Management](#sync-root-management): registers/unregisters and activates/deactivates sync roots. This is a prerequisite for the other three capabilities.
- [File Change Perception and Sync Status Management](#file-change-perception-and-sync-status-management): listens for file changes under a sync root, queries historical operation records, and manages file sync status. These capabilities require a registered sync root.
- [Placeholder File Operation](#placeholder-file-operation): creates, updates, and identifies placeholder files under the sync root, and queries the hydration status and reads/writes custom information. Placeholder files are the objects of hydration/dehydration operations, and this capability depends on a registered sync root.
- [On-Demand Hydration and Dehydration](#on-demand-hydration-and-dehydration): triggers hydration/dehydration after registering the callback table. This depends on created placeholder files and a registered sync root.

## Constraints

To use the APIs related to the cloud disk service foundation capabilities, ensure that the device has the following system capability: SystemCapability.FileManagement.CloudDiskManager

## Environment Setup

The IDE and SDK version requirements vary for different cloud disk service foundation capabilities. Select the version based on the capabilities you actually use:

- [Sync Root Management](#sync-root-management) and [File Change Perception and Sync Status Management](#file-change-perception-and-sync-status-management): DevEco Studio 6.0.0 Release or later, and SDK API version 21 or later.
- [Placeholder File Operation](#placeholder-file-operation) and [On-Demand Hydration and Dehydration](#on-demand-hydration-and-dehydration): DevEco Studio 26.0.0 Release or later, and SDK API version 26.0.1 or later.

To use all capabilities of the cloud disk service foundation, use DevEco Studio 26.0.0 Release and above, with SDK API version 26.0.1 and above. IDE download address: [DevEco Studio official website](https://developer.huawei.com/consumer/en/deveco-studio/).

**Linking Dynamic Libraries**

Add the following libraries to **CMakeLists.txt**:

```txt
target_link_libraries(sample PUBLIC libohclouddiskmanager.so)
```

**Adding Header Files**

``` C++
#include "filemanagement/clouddiskmanager/oh_cloud_disk_manager.h"
```

## Sync Root Management

Cloud disk provider applications can register, unregister, activate, and deactivate sync roots. After registration, a cloud disk entry appears in the File Manager sidebar. Applications can also query registered sync roots and update custom aliases. Unregistering a sync root automatically removes its placeholder files in batches while retaining regular files. Sync root management underpins the other cloud disk service foundation capabilities: file change listening, placeholder file operations, and on-demand hydration and dehydration all require a registered sync root.

### Available APIs

| Name | Description |
| -------- | -------- |
| CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolder(const CloudDisk_SyncFolder *syncFolder) | Registers a sync root for the application.<br>**Note:** This API is supported since API version 21. |
| CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath) | Unregisters a sync root for the application.<br>**Note:** This API is supported since API version 21. |
| CloudDisk_ErrorCode OH_CloudDisk_ActiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath) | Activates a sync root for the application.<br>**Note:** This API is supported since API version 21. |
| CloudDisk_ErrorCode OH_CloudDisk_DeactiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath) | Deactivates a sync root for the application.<br>**Note:** This API is supported since API version 21. |
| CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolders(CloudDisk_SyncFolder **syncFolders, size_t *count) | Obtains all registered sync roots for the application.<br>**Note:** This API is supported since API version 21. |
| CloudDisk_ErrorCode OH_CloudDisk_UpdateCustomAlias(const CloudDisk_SyncFolderPath syncFolderPath, const char *customAlias, size_t customAliasLength) | Updates the sync root alias for the application.<br>**Note:** This API is supported since API version 21. |

### Sample Code

**Registering a Sync Root**

When the application is first connected, you can call **OH_CloudDisk_RegisterSyncFolder()** to register the user-authorized cloud disk directory as a sync root. Only after registration is successful will the cloud disk entry be displayed in the sidebar of File Manager, and the system will begin recording file changes under that directory. This is the first step in connecting to the cloud disk service foundation. Subsequent capabilities such as change listening, placeholder creation, and hydration/dehydration all depend on registered sync roots.

<!-- @[register_sync_folder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value RegisterSyncFolder(napi_env env, napi_callback_info info)
{
    // Parse the JS input parameters: sync root path + display name (both strings).
    char* path = GetStringParam(env, info, 0);
    char* displayName = GetStringParam(env, info, 1);
    if (!path || !displayName) {
        // Return CLOUD_DISK_INVALID_ARG (invalid argument error code) directly when the parameters are invalid.
        LOGE("RegisterSyncFolder invalid params.");
        delete[] path;
        delete[] displayName;
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    // Construct the sync root information struct.
    CloudDisk_SyncFolder syncFolder = {};
    syncFolder.path = MakePathInfo(path);              // Sync root path.
    syncFolder.state = INACTIVE;                       // Initial state: inactive (must be activated separately to start sync).
    syncFolder.displayNameInfo.displayNameResId = 0;   // System resource ID name (0 means not used).
    syncFolder.displayNameInfo.customAlias = displayName;         // Custom alias (a user-configurable display name).
    syncFolder.displayNameInfo.customAliasLength = strlen(displayName); // Custom alias length.

    // ...
    // Call the cloud disk SDK to register the sync root.
    auto ret = OH_CloudDisk_RegisterSyncFolder(&syncFolder);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_RegisterSyncFolder failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_RegisterSyncFolder success.");
    }

    delete[] path;
    delete[] displayName;

    napi_value result;
    napi_create_int32(env, ret, &result);
    return result;
}
```

**Unregistering a Sync Root**

When an application no longer needs a sync root, or when the sync root directory needs to be replaced, call the **OH_CloudDisk_UnregisterSyncFolder()** API to unregister the sync root. After unregistration, the placeholder files under the sync root are automatically cleaned up in batches, while regular files are retained.

> **NOTE**
>
> Each application can register a maximum of 10 sync root directories. When the limit is exceeded, unregister one sync root directory before registering a new one.

<!-- @[unregister_sync_folder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value UnregisterSyncFolder(napi_env env, napi_callback_info info)
{
    char* path = GetStringParam(env, info, 0);
    if (!path) {
        LOGE("UnregisterSyncFolder path is empty.");
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    // Construct the sync root path information.
    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(path);
    // ...
    // Call the cloud disk SDK to unregister the sync root.
    auto ret = OH_CloudDisk_UnregisterSyncFolder(syncFolderPath);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_UnregisterSyncFolder failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_UnregisterSyncFolder success.");
    }

    delete[] path;

    napi_value result;
    napi_create_int32(env, ret, &result);
    return result;
}
```

**Activating a Sync Root**

A sync root is inactive by default after registration. At application startup, you can call **OH_CloudDisk_ActiveSyncFolder()** to activate the sync root. After activation, users can view the sync status of each file under the sync root in the file manager UI.

<!-- @[active_sync_folder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value ActiveSyncFolder(napi_env env, napi_callback_info info)
{
    char* path = GetStringParam(env, info, 0);
    if (!path) {
        LOGE("ActiveSyncFolder path is empty.");
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(path);
    // ...
    // Call the cloud disk SDK to activate the sync root.
    auto ret = OH_CloudDisk_ActiveSyncFolder(syncFolderPath);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_ActiveSyncFolder failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_ActiveSyncFolder success.");
    }

    delete[] path;

    napi_value result;
    napi_create_int32(env, ret, &result);
    return result;
}
```

**Deactivate the Sync Root**

When the application exits or no longer needs to display the sync root, you can call **OH_CloudDisk_DeactiveSyncFolder()** to deactivate the sync root. After deactivation, the file manager no longer displays the sync status of the sync root, but the registration relationship is retained.

<!-- @[deactive_sync_folder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value DeactiveSyncFolder(napi_env env, napi_callback_info info)
{
    char* path = GetStringParam(env, info, 0);
    if (!path) {
        LOGE("DeactiveSyncFolder path is empty.");
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(path);
    // ...
    // Call the cloud disk SDK to deactivate the sync root.
    auto ret = OH_CloudDisk_DeactiveSyncFolder(syncFolderPath);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_DeactiveSyncFolder failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_DeactiveSyncFolder success.");
    }

    delete[] path;

    napi_value result;
    napi_create_int32(env, ret, &result);
    return result;
}
```

**Obtain All Registered Sync Roots**

At application startup or when the configuration page needs to display all currently registered sync roots, or to determine whether the registration limit has been reached, you can call **OH_CloudDisk_GetSyncFolders()** to query the list of all registered sync roots.

<!-- @[get_sync_folders](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value GetAllSyncFolder(napi_env env, napi_callback_info info)
{
    CloudDisk_SyncFolder* syncFolders = nullptr;
    size_t count = 0;
    // Query all sync roots (the SDK allocates memory and returns the array pointer and count).
    auto ret = OH_CloudDisk_GetSyncFolders(&syncFolders, &count);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_GetSyncFolders failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_GetSyncFolders success, count: %{public}zu.", count);
    }
    if (ret != CLOUD_DISK_OK || count == 0) {
        // Return an empty array when there is no sync root, to avoid complicating the null-check logic on the JS side.
        napi_value emptyArray;
        napi_create_array_with_length(env, 0, &emptyArray);
        return emptyArray;
    }

    // Create a JS array and convert each C struct into a JS object, then add it to the array.
    napi_value jsArray;
    napi_create_array_with_length(env, count, &jsArray);
    for (size_t i = 0; i < count; i++) {
        napi_value syncFolderValue = ParseNapiSyncFolder(env, &syncFolders[i]);
        napi_set_element(env, jsArray, i, syncFolderValue);
    }
    return jsArray;
}
```

**Updating the Sync Root Alias**

When the user changes the display name of a cloud disk directory on the application side, you can call **OH_CloudDisk_UpdateCustomAlias()** to update the custom alias of the sync root. After the update, the file manager sidebar displays the cloud disk entry with the new alias.

<!-- @[update_custom_alias](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value UpdateDisplayName(napi_env env, napi_callback_info info)
{
    // Parse the input parameters: sync root path + new display name.
    char* path = GetStringParam(env, info, 0);
    char* alias = GetStringParam(env, info, 1);
    if (!path || !alias) {
        LOGE("UpdateDisplayName invalid params.");
        delete[] path;
        delete[] alias;
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(path);
    // ...
    // Call the cloud disk SDK to update the alias (pass both the alias and its length).
    auto ret = OH_CloudDisk_UpdateCustomAlias(syncFolderPath, alias, strlen(alias));
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_UpdateCustomAlias failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_UpdateCustomAlias success.");
    }

    delete[] path;
    delete[] alias;

    napi_value result;
    napi_create_int32(env, ret, &result);
    return result;
}
```

## File Change Perception and Sync Status Management

File change detection under a sync root helps cloud disk provider applications synchronize files. This includes listening for file changes, querying historical operation records incrementally, and setting and querying file sync status. Callbacks notify the application of file additions, deletions, and modifications in real time so that it can synchronize local and cloud data. The capabilities in this section require a sync root that has been registered and activated as described in [Sync Root Management](#sync-root-management).

### Available APIs

| Name | Description |
| -------- | -------- |
| CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, void (*callback)(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_ChangeData changeDatas[], size_t bufferLength)) | Registers a callback for the application to obtain file changes under the sync root path.<br>**Note:** This API is supported since API version 21. |
| CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath) | Unregisters the callback for file changes under the sync root path.<br>**Note:** This API is supported since API version 21. |
| CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, uint64_t startUsn, size_t count, CloudDisk_ChangesResult **changesResult) | Obtains the historical operation records under the sync root path.<br>**Note:** This API is supported since API version 21. |
| CloudDisk_ErrorCode OH_CloudDisk_SetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_FileSyncState fileSyncStates[], size_t bufferLength, CloudDisk_FailedList **failedLists, size_t *failedCount) | Sets the sync status of files under the sync root path.<br>**Note:** This API is supported since API version 21. |
| CloudDisk_ErrorCode OH_CloudDisk_GetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo paths[], size_t bufferLength, CloudDisk_ResultList **resultLists, size_t *resultCount) | Queries the sync status of files under the sync root path.<br>**Note:** This API is supported since API version 21. |

### Sample Code

**Registering a Sync Root Change Listener**

To detect file additions, deletions, and modifications under a sync root in real time and drive application synchronization, call **OH_CloudDisk_RegisterSyncFolderChanges()** to register a listener. After registration, callbacks notify the application of file changes in real time.<br>

1. **OnChangeDataCallback()** is the listening callback function.

   <!-- @[on_change_data_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static void OnChangeDataCallback(const CloudDisk_SyncFolderPath syncFolderPath,
                                    const CloudDisk_ChangeData changeDatas[], size_t length)
   {
       LOGI("OnChangeDataCallback: path=%{public}s, length=%{public}zu.",
            syncFolderPath.value ? syncFolderPath.value : "(null)", length);
       // Print the change data one by one (for debugging and observing the changes).
       for (size_t i = 0; i < length; ++i) {
           auto& data = changeDatas[i];
           LOGI("  change[%{public}zu]: opType=%{public}d, relativePath=%{public}s.",
                i, data.operationType, data.relativePathInfo.value ? data.relativePathInfo.value : "(null)");
       }
       if (g_tsFn) {
           // Post the message to the JS thread through a thread-safe function (the string created with new is released by CallJs).
           std::string msg = "CloudDiskChange";
           napi_call_threadsafe_function(g_tsFn, new std::string(msg), napi_tsfn_blocking);
       }
   }
   ```
2. **OH_CloudDisk_RegisterSyncFolderChanges()** registers a change listener for the sync root.

   <!-- @[register_sync_folder_changes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static napi_value RegisterSyncFolderChange(napi_env env, napi_callback_info info)
   {
       char* path = GetStringParam(env, info, 0);
       if (!path) {
           LOGE("RegisterSyncFolderChange path is empty.");
           napi_value result;
           napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
           return result;
       }
   
       CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(path);
       // ...
       // Register the change callback (the C-layer callback is OnChangeDataCallback).
       auto ret = OH_CloudDisk_RegisterSyncFolderChanges(syncFolderPath, &OnChangeDataCallback);
       if (ret != CLOUD_DISK_OK) {
           LOGE("OH_CloudDisk_RegisterSyncFolderChanges failed, errorCode: %{public}d.", ret);
       } else {
           LOGI("OH_CloudDisk_RegisterSyncFolderChanges success.");
       }
   
       delete[] path;
   
       napi_value val;
       napi_create_int32(env, ret, &val);
       return val;
   }
   ```

**Unregistering the Sync Root Change Listener**

When the application exits or no longer needs to receive sync root file change notifications, call **OH_CloudDisk_UnregisterSyncFolderChanges()** to unregister the sync root change listener, avoiding unnecessary callbacks and resource usage.

<!-- @[unregister_sync_folder_changes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value UnregisterSyncFolderChange(napi_env env, napi_callback_info info)
{
    char* path = GetStringParam(env, info, 0);
    if (!path) {
        LOGE("UnregisterSyncFolderChange path is empty.");
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(path);
    // ...
    // Unregister the change subscription.
    auto ret = OH_CloudDisk_UnregisterSyncFolderChanges(syncFolderPath);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_UnregisterSyncFolderChanges failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_UnregisterSyncFolderChanges success.");
    }

    delete[] path;

    napi_value val;
    napi_create_int32(env, ret, &val);
    return val;
}
```

**Query Historical Operation Records Under the Sync Root**

When the application needs to pull changes missed while offline at application startup, or to realign the change progress because callbacks were lost, call **OH_CloudDisk_GetSyncFolderChanges()** to incrementally query historical operation records under the sync root based on the last change sequence number.

> **NOTE**
>
> A maximum of 100 records can be queried per request.

<!-- @[get_sync_folder_changes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value GetSyncFolderChanges(napi_env env, napi_callback_info info)
{
    // Parse the input parameters: sync root path, starting USN, and number of records to pull.
    char* path = GetStringParam(env, info, 0);
    int64_t usn = GetNumberParam(env, info, 1);
    int64_t count = GetNumberParam(env, info, 2);
    if (!path) {
        LOGE("GetSyncFolderChanges path is empty.");
        napi_value nullVal;
        napi_get_null(env, &nullVal);
        return nullVal;
    }

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(path);

    // Call the SDK to incrementally obtain changes. The SDK allocates the memory and returns a struct pointer.
    CloudDisk_ChangesResult* changesResult = nullptr;
    // ...
    auto ret = OH_CloudDisk_GetSyncFolderChanges(syncFolderPath, static_cast<uint64_t>(usn),
        static_cast<size_t>(count), &changesResult);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_GetSyncFolderChanges failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_GetSyncFolderChanges success.");
    }

    delete[] path;

    // Return null on failure or when there is no data.
    if (ret != CLOUD_DISK_OK || !changesResult) {
        napi_value nullVal;
        napi_get_null(env, &nullVal);
        return nullVal;
    }
    // Convert the C struct to a JS object (ChangesResult) and return it.
    return ParseNapiChangesResult(env, changesResult);
}
```

**Setting the Sync Status of Files Under the Sync Root Path**

After completing the upload or download sync of a file, you can call the **OH_CloudDisk_SetFileSyncStates()** API to mark the sync status of the file (for example, sync successful or sync failed) for the file manager to display the sync result.

> **NOTE**
>
> A maximum of 100 file paths can be passed per request.

<!-- @[set_file_sync_states](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value SetFileSyncStates(napi_env env, napi_callback_info info)
{
    size_t argc = 3;
    napi_value args[3] = {nullptr};
    GetArgs(env, info, argc, args);

    // Define the parameter indexes of SetFileSyncStates.
    enum ArgIndex {
        ARG_SYNC_PATH = 0,
        ARG_LENGTH = 1,
        ARG_STATE_ARRAY = 2,
    };

    // Parse the input parameters: sync root path, status array length, and file sync status array.
    char* path = GetStringParam(env, args[ARG_SYNC_PATH]);
    if (!path) {
        LOGE("SetFileSyncStates path is empty.");
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }
    uint64_t length = static_cast<uint64_t>(GetNumberParam(env, args[ARG_LENGTH]));

    // Convert the JS array to a C struct array (memory is allocated internally and must be freed after use).
    CloudDisk_FileSyncState* fileSyncStates = nullptr;
    size_t arraySize = 0;
    ConvertToFileSyncStates(env, args[ARG_STATE_ARRAY], &fileSyncStates, &arraySize);

    // Set the sync status in batches. Failed items are written to failedLists (path + failure reason).
    CloudDisk_FailedList* failedLists = nullptr;
    size_t failedCount = 0;
    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(path);

    // ...
    auto ret = OH_CloudDisk_SetFileSyncStates(syncFolderPath, fileSyncStates, length, &failedLists, &failedCount);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_SetFileSyncStates failed, errorCode: %{public}d, failedCount: %{public}zu.",
             ret, failedCount);
    } else {
        LOGI("OH_CloudDisk_SetFileSyncStates success, failedCount: %{public}zu.", failedCount);
    }

    // Print the failed items (path + error reason) for troubleshooting.
    if (failedCount != 0 && failedLists) {
        for (size_t i = 0; i < failedCount; i++) {
            LOGE("  failed[%{public}zu]: path=%{public}s, reason=%{public}d.",
                 i, failedLists[i].pathInfo.value ? failedLists[i].pathInfo.value : "(null)",
                 failedLists[i].errorReason);
        }
    }

    // Free the memory allocated during conversion.
    if (fileSyncStates) {
        for (size_t i = 0; i < arraySize; i++) {
            free(fileSyncStates[i].filePathInfo.value);
        }
        free(fileSyncStates);
    }
    delete[] path;

    napi_value val;
    napi_create_int32(env, ret, &val);
    return val;
}
```

**Querying the Current Sync Status of Files Under the Sync Root**

When you need to query the current sync status of files under a sync root (for example, to display sync progress or troubleshoot sync exceptions), you can call **OH_CloudDisk_GetFileSyncStates()** to query the sync status of files under the sync root in batches.

> **NOTE**
>
> A maximum of 100 files can be queried per request.

<!-- @[get_file_sync_states](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value GetFileSyncStates(napi_env env, napi_callback_info info)
{
    size_t argc = 3;
    napi_value args[3] = {nullptr};
    GetArgs(env, info, argc, args);

    // Define the parameter indexes for GetFileSyncStates.
    enum ArgIndex {
        ARG_SYNC_PATH = 0,
        ARG_LENGTH = 1,
        ARG_PATH_ARRAY = 2,
    };

    // Parse the input parameters: sync root path, path count, and array of file relative paths.
    char* path = GetStringParam(env, args[ARG_SYNC_PATH]);
    if (!path) {
        LOGE("GetFileSyncStates path is empty.");
        napi_value nullVal;
        napi_get_null(env, &nullVal);
        return nullVal;
    }
    uint64_t length = static_cast<uint64_t>(GetNumberParam(env, args[ARG_LENGTH]));

    // Convert the JS path array to a C struct array (memory is allocated internally and must be released after use).
    CloudDisk_PathInfo* paths = nullptr;
    size_t arraySize = 0;
    ConvertToPathInfos(env, args[ARG_PATH_ARRAY], &paths, &arraySize);

    // Query in batches and return the status result list for each file.
    CloudDisk_ResultList* resultLists = nullptr;
    size_t resultCount = 0;
    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(path);

    // ...
    auto ret = OH_CloudDisk_GetFileSyncStates(syncFolderPath, paths, length, &resultLists, &resultCount);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_GetFileSyncStates failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_GetFileSyncStates success, resultCount: %{public}zu.", resultCount);
    }

    delete[] path;

    // Return null on failure or when there is no result.
    if (ret != CLOUD_DISK_OK || resultCount == 0 || !resultLists) {
        napi_value nullVal;
        napi_get_null(env, &nullVal);
        return nullVal;
    }

    // Convert each query result to a JS object and put it into the array to return.
    napi_value jsArray;
    napi_create_array_with_length(env, resultCount, &jsArray);
    for (size_t i = 0; i < resultCount; i++) {
        napi_value resultValue = ParseNapiResultList(env, &resultLists[i]);
        napi_set_element(env, jsArray, i, resultValue);
    }

    // Release the memory allocated during conversion.
    if (paths) {
        for (size_t i = 0; i < arraySize; i++) {
            free(paths[i].value);
        }
        free(paths);
    }

    return jsArray;
}
```

## Placeholder File Operation

Cloud files are mapped to local placeholders that store only metadata, without writing the actual file content to disk. The APIs support creating placeholder files under a sync root, distinguishing them from regular files, querying hydration status, updating metadata, reading and writing custom information, and converting between placeholder and regular files. These capabilities require a sync root registered as described in [Sync Root Management](#sync-root-management). The created placeholders are the targets of [On-Demand Hydration and Dehydration](#on-demand-hydration-and-dehydration).

### Available APIs

| Name | Description |
| -------- | -------- |
| CloudDisk_ErrorCode OH_CloudDisk_CreatePlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, const OH_CloudDisk_PlaceholderInfo placeholderInfo, const OH_CloudDisk_PlaceholderCustomInfo *customInfo) | Creates a placeholder file in the sync root and writes metadata such as the logical size, atimeMs, and mtimeMs. You can optionally write custom information through customInfo.<br>**Note:** This API is supported from API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_UpdatePlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, const OH_CloudDisk_PlaceholderInfo placeholderInfo, const OH_CloudDisk_PlaceholderCustomInfo *customInfo) | Updates the metadata information of a placeholder file (logicalSize, atimeMs, mtimeMs, and so on). When customInfo is NULL, the original custom information is retained.<br>**Note:** This API is supported from API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_IsPlaceholderFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, bool *isPlaceholder) | Determines whether a file under the sync root is a placeholder file.<br>**Note:** This API is supported from API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_GetPlaceholderState(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, OH_CloudDisk_PlaceholderState *state) | Queries the hydration state of a placeholder file (not hydrated, partially hydrated, or fully hydrated).<br>**Note:** This API is supported from API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_GetPlaceholderCustomInfo(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, uint8_t *dataBuf, size_t *inOutDataLength) | Reads the custom information of a placeholder file (up to 1024 bytes).<br>**Note:** This API is supported from API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_ConvertPlaceholderToFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo) | Converts a placeholder file into a 0-byte regular file.<br>**Note:** This API is supported from API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_MarkFileAsPlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo) | Marks a regular file as a fully hydrated placeholder file.<br>**Note:** This API is supported from API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_UnmarkPlaceholderFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo) | Restores a fully hydrated placeholder file to a regular file.<br>**Note:** This API is supported from API version 26.0.1. |

### Sample Code

**Creating a Placeholder File**

Call **OH_CloudDisk_CreatePlaceholder()** to create a local placeholder file representing actual cloud data so that cloud files can be browsed on the device. A sync root must already be registered. The placeholder is the target of subsequent hydration and dehydration operations. You can optionally pass custom information, such as a cloud file identifier, in **customInfo**. Pass **NULL** to omit it. Use **OH_CloudDisk_GetPlaceholderCustomInfo()** to read the information later.

<!-- @[create_placeholder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value CreatePlaceholderFile(napi_env env, napi_callback_info info)
{
    size_t argc = 6;
    napi_value args[6] = {nullptr};
    GetArgs(env, info, argc, args);

    // Parse the input parameters: sync root path + relative path (the relative position of the placeholder file within the sync root).
    char* syncPath = GetStringParam(env, args[0]);
    char* relativePath = GetStringParam(env, args[1]);
    if (!syncPath || !relativePath) {
        LOGE("CreatePlaceholderFile invalid params.");
        delete[] syncPath;
        delete[] relativePath;
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    // Parse the time and size parameters.
    uint64_t atimeMs = static_cast<uint64_t>(GetNumberParam(env, args[2]));  // Access time (millisecond timestamp, mapping the cloud-side file access time).
    uint64_t mtimeMs = static_cast<uint64_t>(GetNumberParam(env, args[3]));  // Modification time (millisecond timestamp, mapping the cloud-side file modification time).
    uint64_t logicalSize = static_cast<uint64_t>(GetNumberParam(env, args[4])); // Logical size of the cloud-side file (in bytes).

    // Parse the optional input parameter: custom information (set to NULL when not passed or an empty string, indicating that no custom information is written)
    char* customInfo = nullptr;
    OH_CloudDisk_PlaceholderCustomInfo customInfoValue = {};
    OH_CloudDisk_PlaceholderCustomInfo* customInfoPtr = NULL;
    if (MakeCustomInfoArg(env, args[ARG_INDEX_CUSTOM_INFO], &customInfoValue, &customInfo)) {
        customInfoPtr = &customInfoValue;  // data points to the customInfo memory, with a lifecycle covering this call
    }

    // Construct the sync root path and relative path
    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
    CloudDisk_PathInfo relativePathInfo = MakePathInfo(relativePath);

    // Define the placeholder file information
    OH_CloudDisk_PlaceholderInfo placeholderInfo = {};
    placeholderInfo.atimeMs = atimeMs;       // Access time (milliseconds)
    placeholderInfo.mtimeMs = mtimeMs;       // Modification time (milliseconds)
    placeholderInfo.logicalSize = logicalSize; // Logical size (bytes)

    // ...
    // Create the placeholder file (customInfo being NULL indicates that no custom information is written; when non-NULL, custom information is written)
    auto ret = OH_CloudDisk_CreatePlaceholder(syncFolderPath, relativePathInfo, placeholderInfo, customInfoPtr);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_CreatePlaceholder failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_CreatePlaceholder success.");
    }

    delete[] syncPath;
    delete[] relativePath;
    delete[] customInfo;

    napi_value result;
    napi_create_int32(env, ret, &result);
    return result;
}
```

**Updating the Metadata Information of a Placeholder File**

When cloud data changes, call **OH_CloudDisk_UpdatePlaceholder()** to update the corresponding local placeholder metadata, such as logical size, access time, and modification time. This API updates only placeholder files, not regular files. Passing **NULL** for **customInfo** retains the existing custom information; passing a non-**NULL** value updates it.

<!-- @[update_placeholder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value UpdatePlaceholder(napi_env env, napi_callback_info info)
{
    size_t argc = 6;
    napi_value args[6] = {nullptr};
    GetArgs(env, info, argc, args);

    char* syncPath = GetStringParam(env, args[0]);
    char* relativePath = GetStringParam(env, args[1]);
    if (!syncPath || !relativePath) {
        LOGE("UpdatePlaceholder invalid params.");
        delete[] syncPath;
        delete[] relativePath;
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    // Parse the time and size to be updated.
    uint64_t atimeMs = static_cast<uint64_t>(GetNumberParam(env, args[2]));
    uint64_t mtimeMs = static_cast<uint64_t>(GetNumberParam(env, args[3]));
    uint64_t logicalSize = static_cast<uint64_t>(GetNumberParam(env, args[4]));

    // Parse the optional input parameter: custom information (set to NULL when not passed or an empty string; the SDK semantics is to retain the original custom information).
    char* customInfo = nullptr;
    OH_CloudDisk_PlaceholderCustomInfo customInfoValue = {};
    OH_CloudDisk_PlaceholderCustomInfo* customInfoPtr = NULL;
    if (MakeCustomInfoArg(env, args[ARG_INDEX_CUSTOM_INFO], &customInfoValue, &customInfo)) {
        customInfoPtr = &customInfoValue;  // data points to the customInfo memory, whose lifetime covers this call.
    }

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
    CloudDisk_PathInfo relativePathInfo = MakePathInfo(relativePath);

    // Construct new placeholder metadata.
    OH_CloudDisk_PlaceholderInfo placeholderInfo = {};
    placeholderInfo.atimeMs = atimeMs;       // Access time (ms).
    placeholderInfo.mtimeMs = mtimeMs;       // Modification time (ms).
    placeholderInfo.logicalSize = logicalSize; // Logical size (bytes).

    // ...
    // Update the placeholder metadata (retain the original custom information when customInfo is NULL; update it when it is not NULL).
    auto ret = OH_CloudDisk_UpdatePlaceholder(syncFolderPath, relativePathInfo, placeholderInfo, customInfoPtr);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_UpdatePlaceholder failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_UpdatePlaceholder success.");
    }

    delete[] syncPath;
    delete[] relativePath;
    delete[] customInfo;

    napi_value result;
    napi_create_int32(env, ret, &result);
    return result;
}
```

**Determining Whether a File Is a Placeholder File**

To determine whether an on-device file is a regular file or a placeholder file, call the **OH_CloudDisk_IsPlaceholderFile()** API, which returns the result through an output parameter.

<!-- @[is_placeholder_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value IsPlaceholderFile(napi_env env, napi_callback_info info)
{
    size_t argc = 2;
    napi_value args[2] = {nullptr};
    GetArgs(env, info, argc, args);

    char* syncPath = GetStringParam(env, args[0]);
    char* relativePath = GetStringParam(env, args[1]);
    if (!syncPath || !relativePath) {
        // Invalid parameter: return an object with code=CLOUD_DISK_INVALID_ARG and isPlaceholder=false.
        LOGE("IsPlaceholderFile invalid params.");
        delete[] syncPath;
        delete[] relativePath;
        napi_value result;
        napi_create_object(env, &result);
        napi_value codeVal;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &codeVal);
        napi_set_named_property(env, result, "code", codeVal);
        napi_value boolVal;
        napi_get_boolean(env, false, &boolVal);
        napi_set_named_property(env, result, "isPlaceholder", boolVal);
        return result;
    }

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
    CloudDisk_PathInfo relativePathInfo = MakePathInfo(relativePath);

    // Call the SDK to query whether it is a placeholder (the result is written to isPlaceholder).
    bool isPlaceholder = false;
    // ...
    auto ret = OH_CloudDisk_IsPlaceholderFile(syncFolderPath, relativePathInfo, &isPlaceholder);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_IsPlaceholderFile failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_IsPlaceholderFile success, isPlaceholder: %{public}d.", isPlaceholder);
    }

    delete[] syncPath;
    delete[] relativePath;

    // Construct the JS return object { code, isPlaceholder }.
    napi_value result;
    napi_create_object(env, &result);
    napi_value codeVal;
    napi_create_int32(env, ret, &codeVal);
    napi_set_named_property(env, result, "code", codeVal);
    napi_value boolVal;
    napi_get_boolean(env, isPlaceholder, &boolVal);
    napi_set_named_property(env, result, "isPlaceholder", boolVal);
    return result;
}
```

**Querying the placeholder hydration state**

When the application needs to know the hydration state of a placeholder file (for example, to display the download state or determine whether the file can be dehydrated), it can call the **OH_CloudDisk_GetPlaceholderState()** API. The query result is returned through the output parameter state, whose values include: OH_CLOUD_DISK_PLACEHOLDER_STATE_NONE (not a placeholder file), OH_CLOUD_DISK_PLACEHOLDER_STATE_UNHYDRATED (not hydrated), OH_CLOUD_DISK_PLACEHOLDER_STATE_PARTIALLY_HYDRATED (partially hydrated), and OH_CLOUD_DISK_PLACEHOLDER_STATE_FULLY_HYDRATED (fully hydrated). If the storage state is invalid, the error code OH_CLOUD_DISK_INVALID_PLACEHOLDER_STATE is returned.

<!-- @[get_placeholder_state](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value GetPlaceholderState(napi_env env, napi_callback_info info)
{
    size_t argc = 2;
    napi_value args[2] = {nullptr};
    GetArgs(env, info, argc, args);

    char* syncPath = GetStringParam(env, args[0]);
    char* relativePath = GetStringParam(env, args[1]);
    if (!syncPath || !relativePath) {
        // Invalid parameter: return an object with code=CLOUD_DISK_INVALID_ARG and state=NONE.
        LOGE("GetPlaceholderState invalid params.");
        delete[] syncPath;
        delete[] relativePath;
        napi_value result;
        napi_create_object(env, &result);
        napi_value codeVal;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &codeVal);
        napi_set_named_property(env, result, "code", codeVal);
        napi_value stateVal;
        napi_create_int32(env, OH_CLOUD_DISK_PLACEHOLDER_STATE_NONE, &stateVal);
        napi_set_named_property(env, result, "state", stateVal);
        return result;
    }

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
    CloudDisk_PathInfo relativePathInfo = MakePathInfo(relativePath);

    // Call the SDK to query the placeholder hydration state (the result is written to state; on error, the SDK sets it to NONE).
    OH_CloudDisk_PlaceholderState state = OH_CLOUD_DISK_PLACEHOLDER_STATE_NONE;
    // ...
    auto ret = OH_CloudDisk_GetPlaceholderState(syncFolderPath, relativePathInfo, &state);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_GetPlaceholderState failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_GetPlaceholderState success, state: %{public}d.", static_cast<int32_t>(state));
    }

    delete[] syncPath;
    delete[] relativePath;

    // Construct the JS return object { code, state }.
    napi_value result;
    napi_create_object(env, &result);
    napi_value codeVal;
    napi_create_int32(env, ret, &codeVal);
    napi_set_named_property(env, result, "code", codeVal);
    napi_value stateVal;
    napi_create_int32(env, static_cast<int32_t>(state), &stateVal);
    napi_set_named_property(env, result, "state", stateVal);
    return result;
}
```


**Reading placeholder custom information**

Call **OH_CloudDisk_GetPlaceholderCustomInfo()** to read custom information written when a placeholder was created or updated, such as a cloud file identifier. The maximum size is 1024 bytes. Data is returned in the caller-allocated **dataBuf** buffer. On input, **inOutDataLength** specifies the allocated buffer capacity; after the call, it contains the actual number of bytes read.

<!-- @[get_placeholder_custom_info](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value GetPlaceholderCustomInfo(napi_env env, napi_callback_info info)
{
    size_t argc = 2;
    napi_value args[2] = {nullptr};
    GetArgs(env, info, argc, args);

    char* syncPath = GetStringParam(env, args[0]);
    char* relativePath = GetStringParam(env, args[1]);
    if (!syncPath || !relativePath) {
        LOGE("GetPlaceholderCustomInfo invalid params.");
        delete[] syncPath;
        delete[] relativePath;
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
    CloudDisk_PathInfo relativePathInfo = MakePathInfo(relativePath);

    // Allocate a buffer for reading custom information (custom information is limited to 1024 bytes).
    size_t dataLength = 1024;
    uint8_t *dataBuf = (uint8_t *)malloc(dataLength);
    if (!dataBuf) {
        delete[] syncPath;
        delete[] relativePath;
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    // ...
    // Read custom information (dataLength is an output parameter; the buffer capacity is passed in on input, and the actual read length is returned on output).
    CloudDisk_ErrorCode ret =
        OH_CloudDisk_GetPlaceholderCustomInfo(syncFolderPath, relativePathInfo, dataBuf, &dataLength);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_GetPlaceholderCustomInfo failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_GetPlaceholderCustomInfo success, dataLength: %{public}zu.", dataLength);
    }

    napi_value resultObj = BuildCustomInfoResult(env, ret, dataLength, dataBuf);
    free(dataBuf);
    delete[] syncPath;
    delete[] relativePath;
    return resultObj;
}
```


**Convert a placeholder file to a 0-byte regular file**

When the application needs to clear the placeholder semantics and return the file to the regular file operation policy (for example, when the file is moved out of the sync root or no longer goes through the cloud disk sync process), it can call the **OH_CloudDisk_ConvertPlaceholderToFile()** API to convert the placeholder file to a 0-byte regular file.

<!-- @[convert_placeholder_to_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value ConvertPlaceholderToFile(napi_env env, napi_callback_info info)
{
    size_t argc = 2;
    napi_value args[2] = {nullptr};
    GetArgs(env, info, argc, args);

    char* syncPath = GetStringParam(env, args[0]);
    char* relativePath = GetStringParam(env, args[1]);
    if (!syncPath || !relativePath) {
        LOGE("ConvertPlaceholderToFile invalid params.");
        delete[] syncPath;
        delete[] relativePath;
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
    CloudDisk_PathInfo relativePathInfo = MakePathInfo(relativePath);

    // ...
    // Convert a placeholder to a regular file.
    auto ret = OH_CloudDisk_ConvertPlaceholderToFile(syncFolderPath, relativePathInfo);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_ConvertPlaceholderToFile failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_ConvertPlaceholderToFile success.");
    }

    delete[] syncPath;
    delete[] relativePath;

    napi_value result;
    napi_create_int32(env, ret, &result);
    return result;
}
```

**Mark a regular file as a placeholder file**

When the application needs to bring a regular file with complete data under the sync root into placeholder management (for example, to convert it to on-demand management in conjunction with the dehydration process), it can call the **OH_CloudDisk_MarkFileAsPlaceholder()** API to mark it as a fully hydrated placeholder file. The marking process does not change the file's data or metadata. If the target is already a placeholder file, OH_CLOUD_DISK_IS_A_PLACEHOLDER is returned.

<!-- @[mark_file_as_placeholder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value MarkFileAsPlaceholder(napi_env env, napi_callback_info info)
{
    size_t argc = 2;
    napi_value args[2] = {nullptr};
    GetArgs(env, info, argc, args);

    char* syncPath = GetStringParam(env, args[0]);
    char* relativePath = GetStringParam(env, args[1]);
    if (!syncPath || !relativePath) {
        LOGE("MarkFileAsPlaceholder invalid params.");
        delete[] syncPath;
        delete[] relativePath;
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
    CloudDisk_PathInfo relativePathInfo = MakePathInfo(relativePath);

    // ...
    // Mark a regular file as a placeholder.
    auto ret = OH_CloudDisk_MarkFileAsPlaceholder(syncFolderPath, relativePathInfo);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_MarkFileAsPlaceholder failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_MarkFileAsPlaceholder success.");
    }

    delete[] syncPath;
    delete[] relativePath;

    napi_value result;
    napi_create_int32(env, ret, &result);
    return result;
}
```


**Unmark a placeholder**

When the application needs to detach a fully hydrated placeholder file from placeholder semantics and return it to the regular file operation policy, it can call the **OH_CloudDisk_UnmarkPlaceholderFile()** API to unmark the placeholder. The unmarking process does not change the file's data or metadata. If the target is not a placeholder file, OH_CLOUD_DISK_NOT_A_PLACEHOLDER is returned; if the file is not fully hydrated, OH_CLOUD_DISK_PLACEHOLDER_NOT_FULLY_HYDRATED is returned.

<!-- @[unmark_placeholder_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value UnmarkPlaceholderFile(napi_env env, napi_callback_info info)
{
    size_t argc = 2;
    napi_value args[2] = {nullptr};
    GetArgs(env, info, argc, args);

    char* syncPath = GetStringParam(env, args[0]);
    char* relativePath = GetStringParam(env, args[1]);
    if (!syncPath || !relativePath) {
        LOGE("UnmarkPlaceholderFile invalid params.");
        delete[] syncPath;
        delete[] relativePath;
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
    CloudDisk_PathInfo relativePathInfo = MakePathInfo(relativePath);

    // ...
    // Cancel the placeholder flag.
    auto ret = OH_CloudDisk_UnmarkPlaceholderFile(syncFolderPath, relativePathInfo);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_UnmarkPlaceholderFile failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_UnmarkPlaceholderFile success.");
    }

    delete[] syncPath;
    delete[] relativePath;

    napi_value result;
    napi_create_int32(env, ret, &result);
    return result;
}
```


## On-Demand Hydration and Dehydration

Cloud-side file entities are downloaded to the local device on demand, or their local data blocks are released, to avoid occupying local space through full downloads. Hydration downloads cloud-side data to the local device on demand, while dehydration releases the local data blocks of a file. This chapter depends on the sync root registered in [Sync Root Management](#sync-root-management) and the placeholder file created in [Placeholder File Operation](#placeholder-file-operation). Hydration and dehydration depend on the callback table mechanism: before triggering hydration, you must register a callback table through **OH_CloudDisk_RegisterCallbackTable()**. In the callback, you can obtain the callback type and request context, based on which the application downloads file data from the cloud side and then calls **OH_CloudDisk_Execute()** to return the data and complete the write to disk.

### Available APIs

| Name | Description |
| -------- | -------- |
| CloudDisk_ErrorCode OH_CloudDisk_RegisterCallbackTable(const CloudDisk_SyncFolderPath syncFolderPath, void (*callback)(const OH_CloudDisk_CallbackReqHead reqHead, OH_CloudDisk_CallbackContext reqContext)) | Registers a callback table. After registration, the cloud disk service foundation notifies the cloud disk access application through callbacks in scenarios such as hydration data retrieval, cancel data retrieval, and dehydration.<br>**Note:** This API is supported from API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_UnregisterCallbackTable(const CloudDisk_SyncFolderPath syncFolderPath) | Unregisters the callback table. After unregistration, related callback notifications are no longer received.<br>**Note:** This API is supported from API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_Execute(const OH_CloudDisk_CallbackReqHead reqHead, OH_CloudDisk_CallbackContext reqContext, OH_CloudDisk_CallbackResponse rsp) | The cloud disk access application responds to a hydration data retrieval or cancel data retrieval callback request. For the data retrieval callback type, the response data must be carried in the rsp parameter; for the cancel data retrieval callback type, no response data is required.<br>**Note:** This API is supported from API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_HydratePlaceholder(const CloudDisk_SyncFolderPath *syncFolderPath, const CloudDisk_PathInfo *filePath, OH_CloudDisk_CallbackType type, OH_CloudDisk_HydratePriority priority) | Triggers placeholder hydration or cancels hydration. A callback table must be registered before hydration starts.<br>**Note:** This API is supported from API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_DehydrateFile(const CloudDisk_SyncFolderPath *syncFolderPath, const CloudDisk_PathInfo *filePath) | Dehydrates a fully hydrated placeholder file into an unhydrated placeholder file. The target must not be in the process of hydration.<br>**Note:** This API is supported from API version 26.0.1. |

### Sample Code

**Registering the Callback Table**

When you need to handle callbacks in scenarios such as hydration data retrieval, cancel data retrieval, streaming read, and dehydration authorization, call the OH_CloudDisk_RegisterCallbackTable API to register a callback table for the sync root. After registration, the cloud disk service foundation delivers the corresponding requests to the application through callbacks. A sync root must already be registered, which is a prerequisite for hydration and dehydration operations.

> **NOTE**
>
> A callback table must be registered before hydration starts.

1. Implement the **OnCallbackTableCallback()** callback function, using hydration data retrieval, cancel data retrieval, and dehydration operations as examples.

   <!-- @[on_callback_table_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static void OnCallbackTableCallback(const OH_CloudDisk_CallbackReqHead reqHead,
                                       OH_CloudDisk_CallbackContext reqContext)
   {
       LOGI("OnCallbackTableCallback: callbackType=%{public}d.", reqHead.callbackType);
   
       // Save the request header using the sync root path as the key (for later queries).
       std::string syncPathKey(reqHead.syncFolderPath.value, reqHead.syncFolderPath.length);
       g_lastReqHeadMap[syncPathKey] = reqHead;
   
       // Save reqKey to the global map (from which getCallbackReqKey reads it),
       // and increment the version number so that the ETS side can poll to determine whether the new reqKey is ready.
       uint64_t reqKeyU64 = 0;
       if (reqHead.reqKey.data != nullptr && reqHead.reqKey.dataSize > 0) {
           // Deep-copy the reqKey data (the original memory may be freed after the callback returns).
           uint8_t* keyData = new uint8_t[reqHead.reqKey.dataSize];
           memcpy(keyData, reqHead.reqKey.data, reqHead.reqKey.dataSize);
   
           OH_CloudDisk_DataBuf storedKey = {};
           storedKey.data = keyData;
           storedKey.dataSize = reqHead.reqKey.dataSize;
           g_reqKeyMap[syncPathKey] = storedKey;
           g_reqKeyVersion.fetch_add(1, std::memory_order_release);
   
           // Convert the reqKey byte order to uint64 for easier log viewing (little-endian).
           const size_t uint64Size = sizeof(uint64_t);
           if (reqHead.reqKey.dataSize >= uint64Size) {
               for (size_t i = 0; i < uint64Size; ++i) {
                   reqKeyU64 |= static_cast<uint64_t>(reqHead.reqKey.data[i]) << (i * uint64Size);
               }
           }
           LOGI("OnCallbackTableCallback: stored reqKey for path=%{public}s, dataSize=%{public}llu, "
                "reqKeyU64=%{public}llu.",
                syncPathKey.c_str(), (unsigned long long)reqHead.reqKey.dataSize, (unsigned long long)reqKeyU64);
       }
   
       // Deep-copy the request context based on the callback type (the original memory may become invalid after the callback returns).
       OH_CloudDisk_CallbackContext copiedContext = CopyCallbackContext(reqHead, reqContext);
   
       // Save the deep-copied context.
       g_lastReqContextMap[syncPathKey] = copiedContext;
   
       // Manual mode: save only reqKey and the context, and let the UI trigger Execute manually.
       if (reqHead.callbackType == OH_CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA && reqContext.fetchData) {
           LOGI("OnCallbackTableCallback: FETCH_DATA stored for manual execute, "
                "syncFolder: %{public}s, file: %{public}s.",
                reqHead.syncFolderPath.value, reqContext.fetchData->filePath.value);
       }
   
       // Automatic hydration: if a "hydration data file" is specified when registering the callback table, the file is read automatically after the callback arrives,
       // and its content is returned in chunks via Execute. When g_fetchFilePath is empty, automatic execution is disabled and the manual mode above is used.
       if (reqHead.callbackType == OH_CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA && reqContext.fetchData) {
           OH_CloudDisk_CallbackReqHead *heapReqHead = DeepCopyReqHead(reqHead);
           OH_CloudDisk_CallbackContext *heapContext = DeepCopyFetchContext(copiedContext);
           std::thread([heapReqHead, heapContext]() {
               AutoHydrateFetchData(heapReqHead, heapContext);
               FreeHeapReqHead(heapReqHead);
               FreeHeapFetchContext(heapContext);
           }).detach();
       }
   }
   ```
2. Call **OH_CloudDisk_RegisterCallbackTable()** to register the callback table.

   <!-- @[register_callback_table](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static napi_value RegisterCallbackTable(napi_env env, napi_callback_info info)
   {
       size_t argc = 2;
       napi_value args[2] = {nullptr};
       GetArgs(env, info, argc, args);
   
       char* syncPath = GetStringParam(env, args[0]);
       if (!syncPath) {
           LOGE("RegisterCallbackTable syncPath is empty.");
           napi_value result;
           napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
           return result;
       }
   
       // Optional second parameter: the hydration data file name (used for automatic FETCH_DATA execution).
       char* fetchFileName = GetStringParam(env, args[1]);
       if (fetchFileName && fetchFileName[0] != '\0') {
           g_fetchFilePath = std::string("/data/storage/el2/base/haps/entry/files/") + std::string(fetchFileName);
           LOGI("RegisterCallbackTable: fetchFilePath=%{public}s.", g_fetchFilePath.c_str());
           delete[] fetchFileName;
       } else {
           // Leave it empty (nullptr) or an empty string: clear the residual path and disable automatic execution to avoid repeated Execute caused by a residual old value.
           if (fetchFileName) {
               delete[] fetchFileName;
           }
           g_fetchFilePath.clear();
           LOGW("RegisterCallbackTable: fetchFilePath cleared, auto-execute disabled.");
       }
   
       CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
   
       // ...
       // Register the callback table (the callback function is OnCallbackTableCallback).
       auto ret = OH_CloudDisk_RegisterCallbackTable(syncFolderPath, &OnCallbackTableCallback);
       if (ret != CLOUD_DISK_OK) {
           LOGE("OH_CloudDisk_RegisterCallbackTable failed, errorCode: %{public}d.", ret);
       } else {
           LOGI("OH_CloudDisk_RegisterCallbackTable success.");
       }
   
       delete[] syncPath;
   
       napi_value result;
       napi_create_int32(env, ret, &result);
       return result;
   }
   ```

**Unregistering the Callback Table**

When the application exits or no longer needs hydration or dehydration callbacks, call **OH_CloudDisk_UnregisterCallbackTable()** to unregister the callback table and avoid unnecessary callbacks and resource usage.

<!-- @[unregister_callback_table](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value UnregisterCallbackTable(napi_env env, napi_callback_info info)
{
    size_t argc = 1;
    napi_value args[1] = {nullptr};
    GetArgs(env, info, argc, args);

    char* syncPath = GetStringParam(env, args[0]);
    if (!syncPath) {
        LOGE("UnregisterCallbackTable syncPath is empty.");
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);

    // ...
    // Unregister the callback table.
    auto ret = OH_CloudDisk_UnregisterCallbackTable(syncFolderPath);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_UnregisterCallbackTable failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_UnregisterCallbackTable success.");
    }

    delete[] syncPath;

    napi_value result;
    napi_create_int32(env, ret, &result);
    return result;
}
```

**Responding to Callback Requests**

After receiving a hydration data retrieval request in the callback, the application downloads the file data from the cloud side and then calls **OH_CloudDisk_Execute()** to return the data to the cloud disk service foundation for writing to disk. When receiving a data retrieval cancellation request, it also responds through this API. This API is a unified Execute function that handles different requests based on the callback type.

> **NOTE**
>
> When data is transferred in multiple parts, call the API repeatedly until fetchDataRsp.isComplete is true.

<!-- @[execute](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value Execute(napi_env env, napi_callback_info info)
{
    ExecuteContext ctx = {};
    if (!ParseExecuteArgs(env, info, ctx)) {
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    // Construct the request header: callback type + sync root path + reqKey.
    uint8_t* reqKeyData = nullptr;
    OH_CloudDisk_CallbackReqHead reqHead = {};
    BuildReqHead(reqHead, ctx.callbackType, ctx.syncPath, ctx.reqKeyInt, reqKeyData);

    // Convert the JS string content to a byte buffer (query the length first, then copy).
    ctx.contentLen = 0;
    napi_get_value_string_utf8(env, ctx.fileContentVal, nullptr, 0, &ctx.contentLen);
    char* contentBuf = new char[ctx.contentLen + 1];
    memset(contentBuf, 0, ctx.contentLen + 1);
    napi_get_value_string_utf8(env, ctx.fileContentVal, contentBuf, ctx.contentLen + 1, &ctx.contentLen);
    ctx.contentBytes = reinterpret_cast<uint8_t*>(contentBuf);
    LOGI("Execute: fileContent len=%{public}zu, content=%{public}s.", ctx.contentLen, contentBuf);

    // Construct the request context based on the callback type (the ExecuteContext member lifetime covers the Execute call).
    OH_CloudDisk_CallbackContext reqContext = {};
    BuildReqContext(reqContext, reqHead, ctx);

    // Construct the callback response: the FETCH_DATA type requires returning file data.
    OH_CloudDisk_CallbackResponse rsp = {};
    OH_CloudDisk_FetchData fetchDataRsp = {};
    BuildCallbackResponse(rsp, fetchDataRsp, reqHead, ctx);

    // ...
    // Execute the callback response to return the content to the cloud disk SDK.
    auto ret = OH_CloudDisk_Execute(reqHead, reqContext, rsp);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_Execute failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_Execute success.");
    }

    // Release the memory allocated in this function.
    delete[] reqKeyData;
    delete[] contentBuf;
    delete[] ctx.syncPath;
    delete[] ctx.filePath;

    napi_value result;
    napi_create_int32(env, ret, &result);
    return result;
}
```

**Cancel Hydration**

When a user opens a placeholder file in File Manager, or when an application actively needs to turn a placeholder file into an accessible regular file, you can call **OH_CloudDisk_HydratePlaceholder()** to trigger hydration. When the download is no longer needed, you can cancel the hydration.

> **NOTE**
>
> Before starting hydration, register the callback table through OH_CloudDisk_RegisterCallbackTable. This API is synchronous and returns immediately after the trigger succeeds. Start downloading data only after receiving the callback.

<!-- @[hydrate_placeholder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value HydratePlaceholder(napi_env env, napi_callback_info info)
{
    LOGI("HydratePlaceholder start.");
    size_t argc = 3;
    napi_value args[3] = {nullptr};
    GetArgs(env, info, argc, args);

    // Parse the input parameters: sync root path + relative path + callback type.
    char* syncPath = GetStringParam(env, args[0]);
    char* relativePath = GetStringParam(env, args[1]);
    LOGI("HydratePlaceholder syncPath: %{public}s, relativePath: %{public}s.", syncPath, relativePath);
    if (!syncPath || !relativePath) {
        LOGE("HydratePlaceholder invalid params.");
        delete[] syncPath;
        delete[] relativePath;
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    // Callback type: FETCH_DATA (retrieve data)/CANCEL_FETCH_DATA (cancel data retrieval)/DEHYDRATE (dehydrate), etc.
    int64_t callbackType = GetNumberParam(env, args[2]);

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
    CloudDisk_PathInfo filePath = MakePathInfo(relativePath);

    // ...
    // Initiate the hydration request (asynchronous; the result is returned through the callback table).
    auto ret = OH_CloudDisk_HydratePlaceholder(&syncFolderPath, &filePath,
        static_cast<OH_CloudDisk_CallbackType>(callbackType),
        OH_CLOUD_DISK_HYDRATE_PRIORITY_NORMAL);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_HydratePlaceholder failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_HydratePlaceholder success.");
    }

    delete[] syncPath;
    delete[] relativePath;

    napi_value result;
    napi_create_int32(env, ret, &result);
    return result;
}
```

**Dehydration**

When the user or the application needs to free local storage space while the file content remains on the cloud side, call **OH_CloudDisk_DehydrateFile()** to dehydrate a fully hydrated placeholder file to the unhydrated state.

> **NOTE**
>
> The target must be a hydrated placeholder file that is not currently being hydrated; otherwise, an error code is returned.

<!-- @[dehydrate_file](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value DehydrateFile(napi_env env, napi_callback_info info)
{
    size_t argc = 2;
    napi_value args[2] = {nullptr};
    GetArgs(env, info, argc, args);

    char* syncPath = GetStringParam(env, args[0]);
    char* relativePath = GetStringParam(env, args[1]);
    if (!syncPath || !relativePath) {
        LOGE("DehydrateFile invalid params.");
        delete[] syncPath;
        delete[] relativePath;
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
    CloudDisk_PathInfo filePath = MakePathInfo(relativePath);

    // ...
    // Dehydrate the file. (Note that a structure pointer is passed here, unlike other APIs that pass by value.)
    auto ret = OH_CloudDisk_DehydrateFile(&syncFolderPath, &filePath);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_DehydrateFile failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_DehydrateFile success.");
    }

    delete[] syncPath;
    delete[] relativePath;

    napi_value result;
    napi_create_int32(env, ret, &result);
    return result;
}
```
