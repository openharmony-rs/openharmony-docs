# Cloud Disk Foundation Adaptation
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @lcm_kiku-->
<!--Designer: @wangyanyue-->
<!--Tester: @zsyztt-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=788623e0eb18ba08c52aadb7d2814c255c7a1e4d translatedAt=2026-11-05T00:54:18.359Z nl=1 -->

## When to Use

Cloud Disk Foundation provides efficient and secure file management capabilities, including state management, state queries, and change monitoring for cloud disk sync roots and their subdirectories. Its APIs are provided by the CloudDisk module. For details, see [oh_cloud_disk_manager.h](../reference/apis-core-file-kit/capi-oh-cloud-disk-manager-h.md).

This guide covers the following four areas, whose capabilities have successive dependencies:

- [Sync Root Management](#sync-root-management): registering/unregistering and activating/deactivating sync roots, which are prerequisites for the other three capabilities.
- [File Change Monitoring and Synchronization State Management](#file-change-monitoring-and-synchronization-state-management): monitoring file changes, querying historical operations, and managing file synchronization states under a registered sync root.
- [Placeholder File Operations](#placeholder-file-operations): creating, updating, and identifying placeholder files, querying hydration states, and reading/writing custom information under a registered sync root. These files are the targets of hydration/dehydration.
- [On-Demand Hydration and Dehydration](#on-demand-hydration-and-dehydration): triggering hydration/dehydration after registering a callback table. This requires existing placeholder files and a registered sync root.

## Constraints

Before using Cloud Disk Foundation APIs, ensure that the device supports the following system capability: `SystemCapability.FileManagement.CloudDiskManager`.

## Environment Setup

The IDE and SDK requirements vary by capability. Select the appropriate versions:

- [Sync Root Management](#sync-root-management) and [File Change Monitoring and Synchronization State Management](#file-change-monitoring-and-synchronization-state-management): DevEco Studio 6.0.0 Release or later and SDK API version 21 or later.
- [Placeholder File Operations](#placeholder-file-operations) and [On-Demand Hydration and Dehydration](#on-demand-hydration-and-dehydration): DevEco Studio 26.0.0 Release or later and SDK API version 26.0.1 or later.

To use all Cloud Disk Foundation capabilities, use DevEco Studio 26.0.0 Release or later and SDK API version 26.0.1 or later. Download the IDE from the [DevEco Studio website](https://developer.huawei.com/consumer/en/deveco-studio/).

**Adding Dynamic Libraries**

Add the following library to `CMakeLists.txt`.

```txt
target_link_libraries(sample PUBLIC libohclouddiskmanager.so)
```

**Adding Header Files**

``` C++
#include "filemanagement/clouddiskmanager/oh_cloud_disk_manager.h"
```

## Sync Root Management

Cloud disk provider applications can register/unregister and activate/deactivate sync roots. After registration, the cloud disk entry appears in the file manager sidebar. Applications can also query the sync root list and update custom aliases. Unregistering a sync root automatically removes its placeholder files in batches, but retains ordinary files. Sync root management underpins all Cloud Disk Foundation capabilities: file change monitoring, placeholder operations, and on-demand hydration/dehydration require a registered sync root.

### Available APIs

| Name | Description |
| -------- | -------- |
| CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolder(const CloudDisk_SyncFolder *syncFolder) | Registers a sync root.<br>**Note:** This API is supported since API version 21. |
| CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath) | Unregisters a sync root.<br>**Note:** This API is supported since API version 21. |
| CloudDisk_ErrorCode OH_CloudDisk_ActiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath) | Activates a sync root.<br>**Note:** This API is supported since API version 21. |
| CloudDisk_ErrorCode OH_CloudDisk_DeactiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath) | Deactivates a sync root.<br>**Note:** This API is supported since API version 21. |
| CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolders(CloudDisk_SyncFolder **syncFolders, size_t *count) | Obtains all registered sync roots.<br>**Note:** This API is supported since API version 21. |
| CloudDisk_ErrorCode OH_CloudDisk_UpdateCustomAlias(const CloudDisk_SyncFolderPath syncFolderPath, const char *customAlias, size_t customAliasLength) | Updates the custom alias of a sync root.<br>**Note:** This API is supported since API version 21. |

### Code Example

**Registering a Sync Root**

When integrating for the first time, call `OH_CloudDisk_RegisterSyncFolder()` to register a user-authorized cloud disk directory as a sync root. Only after registration does the cloud disk entry appear in the file manager sidebar and the system start recording file changes in the directory. This is the first step in integrating Cloud Disk Foundation; subsequent change monitoring, placeholder creation, and hydration/dehydration require a registered sync root.

<!-- @[register_sync_folder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value RegisterSyncFolder(napi_env env, napi_callback_info info)
{
    // Parse the JS arguments: sync root path and display name (both strings).
    char* path = GetStringParam(env, info, 0);
    char* displayName = GetStringParam(env, info, 1);
    if (!path || !displayName) {
        // Return CLOUD_DISK_INVALID_ARG (invalid argument error code) for invalid arguments.
        LOGE("RegisterSyncFolder invalid params.");
        delete[] path;
        delete[] displayName;
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    // Construct the sync root information structure.
    CloudDisk_SyncFolder syncFolder = {};
    syncFolder.path = MakePathInfo(path);              // Sync root path.
    syncFolder.state = INACTIVE;                       // Initial state: inactive (activate separately to start synchronization).
    syncFolder.displayNameInfo.displayNameResId = 0;   // System resource ID for the name (0 means not used).
    syncFolder.displayNameInfo.customAlias = displayName;         // Custom alias (user-configurable display name).
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

When a sync root is no longer needed or its directory needs to be replaced, call `OH_CloudDisk_UnregisterSyncFolder()` to unregister it. This automatically removes its placeholder files in batches, but retains ordinary files.

> **NOTE**
>
> Each application can register up to 10 sync roots. At this limit, unregister an existing sync root before registering a new one.

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

A newly registered sync root is inactive by default. Call `OH_CloudDisk_ActiveSyncFolder()` when the application starts to activate it. Only after activation can users view the synchronization states of its files in the file manager.

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

**Deactivating a Sync Root**

When the application exits or no longer needs to display a sync root, call `OH_CloudDisk_DeactiveSyncFolder()` to deactivate it. The file manager stops displaying its synchronization states, but the registration is retained.

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

**Obtaining All Registered Sync Roots**

Call `OH_CloudDisk_GetSyncFolders()` when the application starts or its settings page needs to display all registered sync roots or check whether the registration limit has been reached.

<!-- @[get_sync_folders](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value GetAllSyncFolder(napi_env env, napi_callback_info info)
{
    CloudDisk_SyncFolder* syncFolders = nullptr;
    size_t count = 0;
    // Query all sync roots (the SDK allocates memory and returns an array pointer and count).
    auto ret = OH_CloudDisk_GetSyncFolders(&syncFolders, &count);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_GetSyncFolders failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_GetSyncFolders success, count: %{public}zu.", count);
    }
    if (ret != CLOUD_DISK_OK || count == 0) {
        // Return an empty array if there are no sync roots, simplifying JS null checks.
        napi_value emptyArray;
        napi_create_array_with_length(env, 0, &emptyArray);
        return emptyArray;
    }

    // Create a JS array and convert each C structure into a JS object in the array.
    napi_value jsArray;
    napi_create_array_with_length(env, count, &jsArray);
    for (size_t i = 0; i < count; i++) {
        napi_value syncFolderValue = ParseNapiSyncFolder(env, &syncFolders[i]);
        napi_set_element(env, jsArray, i, syncFolderValue);
    }
    return jsArray;
}
```

**Updating a Sync Root Alias**

When a user changes a cloud disk directory display name in the application, call `OH_CloudDisk_UpdateCustomAlias()` to update the custom alias. The file manager sidebar then displays the new alias.

<!-- @[update_custom_alias](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value UpdateDisplayName(napi_env env, napi_callback_info info)
{
    // Parse the arguments: sync root path and new display name.
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

## File Change Monitoring and Synchronization State Management

Monitor file changes under a sync root to support file synchronization, including file change monitoring, incremental queries of historical operations, and setting/querying file synchronization states. File additions, deletions, and modifications are reported to the cloud disk provider application in real time through callbacks, enabling its own device-cloud synchronization workflow. These capabilities require a sync root that is registered and activated as described in [Sync Root Management](#sync-root-management).

### Available APIs

| Name | Description |
| -------- | -------- |
| CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, void (*callback)(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_ChangeData changeDatas[], size_t bufferLength)) | Registers a callback to obtain file changes under a sync root.<br>**Note:** This API is supported since API version 21. |
| CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath) | Unregisters the file change callback for a sync root.<br>**Note:** This API is supported since API version 21. |
| CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, uint64_t startUsn, size_t count, CloudDisk_ChangesResult **changesResult) | Obtains historical operations under a sync root.<br>**Note:** This API is supported since API version 21. |
| CloudDisk_ErrorCode OH_CloudDisk_SetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_FileSyncState fileSyncStates[], size_t bufferLength, CloudDisk_FailedList **failedLists, size_t *failedCount) | Sets file synchronization states under a sync root.<br>**Note:** This API is supported since API version 21. |
| CloudDisk_ErrorCode OH_CloudDisk_GetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo paths[], size_t bufferLength, CloudDisk_ResultList **resultLists, size_t *resultCount) | Queries file synchronization states under a sync root.<br>**Note:** This API is supported since API version 21. |

### Code Example

**Registering Sync Root Change Monitoring**

Call `OH_CloudDisk_RegisterSyncFolderChanges()` to monitor file additions, deletions, and modifications under a sync root in real time and drive application synchronization logic. After registration, file changes are reported in real time through callbacks.<br>

1. Implement the `OnChangeDataCallback()` callback.

   <!-- @[on_change_data_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static void OnChangeDataCallback(const CloudDisk_SyncFolderPath syncFolderPath,
                                    const CloudDisk_ChangeData changeDatas[], size_t length)
   {
       LOGI("OnChangeDataCallback: path=%{public}s, length=%{public}zu.",
            syncFolderPath.value ? syncFolderPath.value : "(null)", length);
       // Print each change record for debugging.
       for (size_t i = 0; i < length; ++i) {
           auto& data = changeDatas[i];
           LOGI("  change[%{public}zu]: opType=%{public}d, relativePath=%{public}s.",
                i, data.operationType, data.relativePathInfo.value ? data.relativePathInfo.value : "(null)");
       }
       if (g_tsFn) {
           // Send a message to the JS thread through a thread-safe function (CallJs releases the string allocated with new).
           std::string msg = "CloudDiskChange";
           napi_call_threadsafe_function(g_tsFn, new std::string(msg), napi_tsfn_blocking);
       }
   }
   ```
2. Call `OH_CloudDisk_RegisterSyncFolderChanges()` to register sync root change monitoring.

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
       // Register the change callback (the C callback is OnChangeDataCallback).
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

**Unregistering Sync Root Change Monitoring**

When the application exits or no longer needs file change notifications, call `OH_CloudDisk_UnregisterSyncFolderChanges()` to unregister monitoring and avoid unnecessary callbacks and resource usage.

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
    // Unsubscribe from changes.
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

**Querying Historical Operations Under a Sync Root**

Call `OH_CloudDisk_GetSyncFolderChanges()` to incrementally query historical operations from the last change sequence number when the application starts and needs changes missed while offline, or needs to realign progress after missed callbacks.

> **NOTE**
>
> A maximum of 100 records can be queried per call.

<!-- @[get_sync_folder_changes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value GetSyncFolderChanges(napi_env env, napi_callback_info info)
{
    // Parse the arguments: sync root path, starting USN, and number of records.
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

    // Call the SDK to obtain incremental changes (the SDK allocates memory and returns a structure pointer).
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

    // Return null on failure or if no data is available.
    if (ret != CLOUD_DISK_OK || !changesResult) {
        napi_value nullVal;
        napi_get_null(env, &nullVal);
        return nullVal;
    }
    // Convert the C structure into a JS object (ChangesResult) and return it.
    return ParseNapiChangesResult(env, changesResult);
}
```

**Setting File Synchronization States Under a Sync Root**

After uploading or downloading a file, call `OH_CloudDisk_SetFileSyncStates()` to mark its synchronization state (for example, success or failure) for the file manager to display.

> **NOTE**
>
> A maximum of 100 file paths can be passed per call.

<!-- @[set_file_sync_states](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value SetFileSyncStates(napi_env env, napi_callback_info info)
{
    size_t argc = 3;
    napi_value args[3] = {nullptr};
    GetArgs(env, info, argc, args);

    // Define SetFileSyncStates argument indexes.
    enum ArgIndex {
        ARG_SYNC_PATH = 0,
        ARG_LENGTH = 1,
        ARG_STATE_ARRAY = 2,
    };

    // Parse the arguments: sync root path, state array length, and file synchronization state array.
    char* path = GetStringParam(env, args[ARG_SYNC_PATH]);
    if (!path) {
        LOGE("SetFileSyncStates path is empty.");
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }
    uint64_t length = static_cast<uint64_t>(GetNumberParam(env, args[ARG_LENGTH]));

    // Convert the JS array into a C structure array (memory allocated with new internally must be freed after use).
    CloudDisk_FileSyncState* fileSyncStates = nullptr;
    size_t arraySize = 0;
    ConvertToFileSyncStates(env, args[ARG_STATE_ARRAY], &fileSyncStates, &arraySize);

    // Set synchronization states in batches; failedLists receives failed items (path and failure reason).
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

    // Print failed items (path and error reason) for troubleshooting.
    if (failedCount != 0 && failedLists) {
        for (size_t i = 0; i < failedCount; i++) {
            LOGE("  failed[%{public}zu]: path=%{public}s, reason=%{public}d.",
                 i, failedLists[i].pathInfo.value ? failedLists[i].pathInfo.value : "(null)",
                 failedLists[i].errorReason);
        }
    }

    // Release memory allocated during conversion.
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

**Querying Current File Synchronization States Under a Sync Root**

Call `OH_CloudDisk_GetFileSyncStates()` to query file synchronization states under a sync root in batches, for example, to display progress or troubleshoot synchronization failures.

> **NOTE**
>
> A maximum of 100 files can be queried per call.

<!-- @[get_file_sync_states](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value GetFileSyncStates(napi_env env, napi_callback_info info)
{
    size_t argc = 3;
    napi_value args[3] = {nullptr};
    GetArgs(env, info, argc, args);

    // Define GetFileSyncStates argument indexes.
    enum ArgIndex {
        ARG_SYNC_PATH = 0,
        ARG_LENGTH = 1,
        ARG_PATH_ARRAY = 2,
    };

    // Parse the arguments: sync root path, path count, and array of relative file paths.
    char* path = GetStringParam(env, args[ARG_SYNC_PATH]);
    if (!path) {
        LOGE("GetFileSyncStates path is empty.");
        napi_value nullVal;
        napi_get_null(env, &nullVal);
        return nullVal;
    }
    uint64_t length = static_cast<uint64_t>(GetNumberParam(env, args[ARG_LENGTH]));

    // Convert the JS path array into a C structure array (release memory allocated with new internally after use).
    CloudDisk_PathInfo* paths = nullptr;
    size_t arraySize = 0;
    ConvertToPathInfos(env, args[ARG_PATH_ARRAY], &paths, &arraySize);

    // Query in batches and return a state result list for each file.
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

    // Return null on failure or if there are no results.
    if (ret != CLOUD_DISK_OK || resultCount == 0 || !resultLists) {
        napi_value nullVal;
        napi_get_null(env, &nullVal);
        return nullVal;
    }

    // Convert each result into a JS object and return them in an array.
    napi_value jsArray;
    napi_create_array_with_length(env, resultCount, &jsArray);
    for (size_t i = 0; i < resultCount; i++) {
        napi_value resultValue = ParseNapiResultList(env, &resultLists[i]);
        napi_set_element(env, jsArray, i, resultValue);
    }

    // Release memory allocated during conversion.
    if (paths) {
        for (size_t i = 0; i < arraySize; i++) {
            free(paths[i].value);
        }
        free(paths);
    }

    return jsArray;
}
```

## Placeholder File Operations

Cloud files are mapped to local placeholder files, which retain only metadata without storing actual file data. You can create placeholders under a sync root, distinguish them from ordinary files, query hydration states, update metadata, read/write custom information, and convert between placeholder and ordinary files. These capabilities require a registered sync root as described in [Sync Root Management](#sync-root-management). The placeholders are the targets of [On-Demand Hydration and Dehydration](#on-demand-hydration-and-dehydration).

### Available APIs

| Name | Description |
| -------- | -------- |
| CloudDisk_ErrorCode OH_CloudDisk_CreatePlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, const OH_CloudDisk_PlaceholderInfo placeholderInfo, const OH_CloudDisk_PlaceholderCustomInfo *customInfo) | Creates a placeholder file under a sync root, setting metadata such as logical size, atimeMs, and mtimeMs. Optionally writes custom information through customInfo.<br>**Note:** This API is supported since API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_UpdatePlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, const OH_CloudDisk_PlaceholderInfo placeholderInfo, const OH_CloudDisk_PlaceholderCustomInfo *customInfo) | Updates placeholder metadata (logicalSize, atimeMs, mtimeMs, and so on). Retains existing custom information if customInfo is NULL.<br>**Note:** This API is supported since API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_IsPlaceholderFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, bool *isPlaceholder) | Checks whether a file under a sync root is a placeholder.<br>**Note:** This API is supported since API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_GetPlaceholderState(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, OH_CloudDisk_PlaceholderState *state) | Queries the hydration state of a placeholder (unhydrated, partially hydrated, or fully hydrated).<br>**Note:** This API is supported since API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_GetPlaceholderCustomInfo(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, uint8_t *dataBuf, size_t *inOutDataLength) | Reads placeholder custom information (up to 1024 bytes).<br>**Note:** This API is supported since API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_ConvertPlaceholderToFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo) | Converts a placeholder into a 0-byte ordinary file.<br>**Note:** This API is supported since API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_MarkFileAsPlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo) | Marks an ordinary file as a fully hydrated placeholder.<br>**Note:** This API is supported since API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_UnmarkPlaceholderFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo) | Converts a fully hydrated placeholder back into an ordinary file.<br>**Note:** This API is supported since API version 26.0.1. |

### Code Example

**Creating a Placeholder File**

Call `OH_CloudDisk_CreatePlaceholder()` to create a local placeholder that maps to actual cloud data, allowing cloud files to be browsed on the device. A sync root must already be registered. The placeholder is the target of subsequent hydration/dehydration. Optionally pass custom information (such as a cloud file identifier) through `customInfo`, or pass `NULL` to omit it. Use `OH_CloudDisk_GetPlaceholderCustomInfo()` to read it back.

<!-- @[create_placeholder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value CreatePlaceholderFile(napi_env env, napi_callback_info info)
{
    size_t argc = 6;
    napi_value args[6] = {nullptr};
    GetArgs(env, info, argc, args);

    // Parse the arguments: sync root path and relative path (placeholder location within the sync root).
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

    // Parse the time and size arguments.
    uint64_t atimeMs = static_cast<uint64_t>(GetNumberParam(env, args[2]));  // Access time (millisecond timestamp mapped from the cloud file access time).
    uint64_t mtimeMs = static_cast<uint64_t>(GetNumberParam(env, args[3]));  // Modification time (millisecond timestamp mapped from the cloud file modification time).
    uint64_t logicalSize = static_cast<uint64_t>(GetNumberParam(env, args[4])); // Logical size of the cloud file (bytes).

    // Parse optional custom information (NULL for an omitted or empty string, meaning no custom information is written).
    char* customInfo = nullptr;
    OH_CloudDisk_PlaceholderCustomInfo customInfoValue = {};
    OH_CloudDisk_PlaceholderCustomInfo* customInfoPtr = NULL;
    if (MakeCustomInfoArg(env, args[ARG_INDEX_CUSTOM_INFO], &customInfoValue, &customInfo)) {
        customInfoPtr = &customInfoValue;  // data points to customInfo memory, whose lifetime covers this call.
    }

    // Construct the sync root path and relative path.
    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
    CloudDisk_PathInfo relativePathInfo = MakePathInfo(relativePath);

    // Define placeholder file information.
    OH_CloudDisk_PlaceholderInfo placeholderInfo = {};
    placeholderInfo.atimeMs = atimeMs;       // Access time (milliseconds).
    placeholderInfo.mtimeMs = mtimeMs;       // Modification time (milliseconds).
    placeholderInfo.logicalSize = logicalSize; // Logical size (bytes).

    // ...
    // Create the placeholder (NULL customInfo omits custom information; non-NULL writes it).
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

**Updating Placeholder Metadata**

When cloud data changes, call `OH_CloudDisk_UpdatePlaceholder()` to update local placeholder metadata (logical size, access time, modification time, and so on) to reflect the latest cloud metadata. Only placeholders can be updated; ordinary files are not supported. A `NULL` customInfo retains existing custom information; a non-NULL value updates it.

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

    // Parse the time and size to update.
    uint64_t atimeMs = static_cast<uint64_t>(GetNumberParam(env, args[2]));
    uint64_t mtimeMs = static_cast<uint64_t>(GetNumberParam(env, args[3]));
    uint64_t logicalSize = static_cast<uint64_t>(GetNumberParam(env, args[4]));

    // Parse optional custom information (NULL for an omitted or empty string, which retains existing custom information in the SDK).
    char* customInfo = nullptr;
    OH_CloudDisk_PlaceholderCustomInfo customInfoValue = {};
    OH_CloudDisk_PlaceholderCustomInfo* customInfoPtr = NULL;
    if (MakeCustomInfoArg(env, args[ARG_INDEX_CUSTOM_INFO], &customInfoValue, &customInfo)) {
        customInfoPtr = &customInfoValue;  // data points to customInfo memory, whose lifetime covers this call.
    }

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
    CloudDisk_PathInfo relativePathInfo = MakePathInfo(relativePath);

    // Construct new placeholder metadata.
    OH_CloudDisk_PlaceholderInfo placeholderInfo = {};
    placeholderInfo.atimeMs = atimeMs;       // Access time (milliseconds).
    placeholderInfo.mtimeMs = mtimeMs;       // Modification time (milliseconds).
    placeholderInfo.logicalSize = logicalSize; // Logical size (bytes).

    // ...
    // Update placeholder metadata (NULL customInfo retains existing custom information; non-NULL updates it).
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

**Checking Whether a File Is a Placeholder**

Call `OH_CloudDisk_IsPlaceholderFile()` to determine whether a local file is an ordinary file or a placeholder. The result is returned through an output parameter.

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
        // Invalid arguments: return an object with code=CLOUD_DISK_INVALID_ARG and isPlaceholder=false.
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

    // Call the SDK to check for a placeholder (the result is written to isPlaceholder).
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

**Querying Placeholder Hydration State**

Call `OH_CloudDisk_GetPlaceholderState()` to query hydration state, for example, to display download status or determine whether a file can be dehydrated. The output parameter `state` can be `OH_CLOUD_DISK_PLACEHOLDER_STATE_NONE` (not a placeholder), `OH_CLOUD_DISK_PLACEHOLDER_STATE_UNHYDRATED` (unhydrated), `OH_CLOUD_DISK_PLACEHOLDER_STATE_PARTIALLY_HYDRATED` (partially hydrated), or `OH_CLOUD_DISK_PLACEHOLDER_STATE_FULLY_HYDRATED` (fully hydrated). An invalid stored state returns `OH_CLOUD_DISK_INVALID_PLACEHOLDER_STATE`.

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
        // Invalid arguments: return an object with code=CLOUD_DISK_INVALID_ARG and state=NONE.
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

    // Query placeholder hydration state (the SDK writes state and sets it to NONE on error).
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


**Reading Placeholder Custom Information**

Call `OH_CloudDisk_GetPlaceholderCustomInfo()` to read custom information written when creating or updating a placeholder, such as a cloud file identifier (up to 1024 bytes). Data is returned in the caller-allocated `dataBuf`. On input, `inOutDataLength` specifies the allocated buffer capacity; on return, it contains the actual length read.

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

    // Allocate a custom information buffer (up to 1024 bytes).
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
    // Read custom information (dataLength is an output parameter: pass buffer capacity on input; it returns the actual length read).
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


**Converting a Placeholder into a 0-Byte Ordinary File**

Call `OH_CloudDisk_ConvertPlaceholderToFile()` to convert a placeholder into a 0-byte ordinary file when removing placeholder semantics and restoring ordinary file operations, for example, when a file leaves the sync root or no longer participates in cloud disk synchronization.

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
    // Convert the placeholder into an ordinary file.
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

**Marking an Ordinary File as a Placeholder**

Call `OH_CloudDisk_MarkFileAsPlaceholder()` to include an ordinary file with complete data under a sync root in placeholder management, for example, for on-demand management through dehydration. This marks it as a fully hydrated placeholder without changing its data or metadata. If the target is already a placeholder, `OH_CLOUD_DISK_IS_A_PLACEHOLDER` is returned.

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
    // Mark the ordinary file as a placeholder.
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


**Removing the Placeholder Mark**

Call `OH_CloudDisk_UnmarkPlaceholderFile()` to remove placeholder semantics from a fully hydrated placeholder and restore ordinary file operations, without changing data or metadata. If the target is not a placeholder, `OH_CLOUD_DISK_NOT_A_PLACEHOLDER` is returned; if it is not fully hydrated, `OH_CLOUD_DISK_PLACEHOLDER_NOT_FULLY_HYDRATED` is returned.

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
    // Remove the placeholder mark.
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

Cloud file data is downloaded locally on demand or local data blocks are released, avoiding full downloads that consume local space. Hydration downloads cloud data locally on demand; dehydration releases local file data blocks. This section requires a registered sync root from [Sync Root Management](#sync-root-management) and existing placeholders from [Placeholder File Operations](#placeholder-file-operations). Hydration/dehydration uses a callback table: register it through `OH_CloudDisk_RegisterCallbackTable()` before triggering hydration. The callback provides the callback type and request context. The application downloads cloud data accordingly and calls `OH_CloudDisk_Execute()` to return the data for storage.

### Available APIs

| Name | Description |
| -------- | -------- |
| CloudDisk_ErrorCode OH_CloudDisk_RegisterCallbackTable(const CloudDisk_SyncFolderPath syncFolderPath, void (*callback)(const OH_CloudDisk_CallbackReqHead reqHead, OH_CloudDisk_CallbackContext reqContext)) | Registers a callback table. Cloud Disk Foundation then notifies the cloud disk provider application through callbacks for hydration data retrieval, cancellation, and dehydration.<br>**Note:** This API is supported since API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_UnregisterCallbackTable(const CloudDisk_SyncFolderPath syncFolderPath) | Unregisters the callback table, stopping related callback notifications.<br>**Note:** This API is supported since API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_Execute(const OH_CloudDisk_CallbackReqHead reqHead, OH_CloudDisk_CallbackContext reqContext, OH_CloudDisk_CallbackResponse rsp) | Responds to hydration data retrieval or cancellation callback requests. For data retrieval, rsp must carry response data; cancellation does not require response data.<br>**Note:** This API is supported since API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_HydratePlaceholder(const CloudDisk_SyncFolderPath *syncFolderPath, const CloudDisk_PathInfo *filePath, OH_CloudDisk_CallbackType type, OH_CloudDisk_HydratePriority priority) | Triggers or cancels placeholder hydration. A callback table must be registered before hydration starts.<br>**Note:** This API is supported since API version 26.0.1. |
| CloudDisk_ErrorCode OH_CloudDisk_DehydrateFile(const CloudDisk_SyncFolderPath *syncFolderPath, const CloudDisk_PathInfo *filePath) | Dehydrates a fully hydrated placeholder into an unhydrated placeholder. The target must not be undergoing hydration.<br>**Note:** This API is supported since API version 26.0.1. |

### Code Example

**Registering a Callback Table**

Call `OH_CloudDisk_RegisterCallbackTable` to register a callback table for a sync root to handle hydration data retrieval, cancellation, streaming reads, and dehydration authorization. Cloud Disk Foundation then sends requests through callbacks. A sync root must already be registered; this is a prerequisite for hydration/dehydration.

> **NOTE**
>
> You must register a callback table before starting hydration.

1. Implement `OnCallbackTableCallback()`, using hydration data retrieval, cancellation, and dehydration as examples.

   <!-- @[on_callback_table_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static void OnCallbackTableCallback(const OH_CloudDisk_CallbackReqHead reqHead,
                                       OH_CloudDisk_CallbackContext reqContext)
   {
       LOGI("OnCallbackTableCallback: callbackType=%{public}d.", reqHead.callbackType);
   
       // Save the request header keyed by the sync root path for later queries.
       std::string syncPathKey(reqHead.syncFolderPath.value, reqHead.syncFolderPath.length);
       g_lastReqHeadMap[syncPathKey] = reqHead;
   
       // Save reqKey in the global map (read by getCallbackReqKey),
       // and increment the version for ETS polling to check whether a new reqKey is ready.
       uint64_t reqKeyU64 = 0;
       if (reqHead.reqKey.data != nullptr && reqHead.reqKey.dataSize > 0) {
           // Deep-copy reqKey data (the original memory may be released after the callback).
           uint8_t* keyData = new uint8_t[reqHead.reqKey.dataSize];
           memcpy(keyData, reqHead.reqKey.data, reqHead.reqKey.dataSize);
   
           OH_CloudDisk_DataBuf storedKey = {};
           storedKey.data = keyData;
           storedKey.dataSize = reqHead.reqKey.dataSize;
           g_reqKeyMap[syncPathKey] = storedKey;
           g_reqKeyVersion.fetch_add(1, std::memory_order_release);
   
           // Convert reqKey bytes to uint64 for logging (little-endian).
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
   
       // Deep-copy the request context by callback type (original memory may become invalid after the callback).
       OH_CloudDisk_CallbackContext copiedContext = CopyCallbackContext(reqHead, reqContext);
   
       // Save the deep-copied context.
       g_lastReqContextMap[syncPathKey] = copiedContext;
   
       // Manual mode: save only reqKey and context; the UI triggers Execute manually.
       if (reqHead.callbackType == OH_CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA && reqContext.fetchData) {
           LOGI("OnCallbackTableCallback: FETCH_DATA stored for manual execute, "
                "syncFolder: %{public}s, file: %{public}s.",
                reqHead.syncFolderPath.value, reqContext.fetchData->filePath.value);
       }
   
       // Automatic hydration: if a hydration data file was specified during callback table registration, read its
       // contents automatically on callback arrival and return chunks through Execute. If g_fetchFilePath is empty, use manual mode above.
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
2. Call `OH_CloudDisk_RegisterCallbackTable()` to register the callback table.

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
   
       // Optional second argument: hydration data file name (for automatic FETCH_DATA execution).
       char* fetchFileName = GetStringParam(env, args[1]);
       if (fetchFileName && fetchFileName[0] != '\0') {
           g_fetchFilePath = std::string("/data/storage/el2/base/haps/entry/files/") + std::string(fetchFileName);
           LOGI("RegisterCallbackTable: fetchFilePath=%{public}s.", g_fetchFilePath.c_str());
           delete[] fetchFileName;
       } else {
           // For nullptr or an empty string, clear the residual path and disable automatic execution to avoid duplicate Execute calls from stale values.
           if (fetchFileName) {
               delete[] fetchFileName;
           }
           g_fetchFilePath.clear();
           LOGW("RegisterCallbackTable: fetchFilePath cleared, auto-execute disabled.");
       }
   
       CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
   
       // ...
       // Register the callback table (callback: OnCallbackTableCallback).
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

**Unregistering a Callback Table**

When the application exits or no longer handles hydration/dehydration callbacks, call `OH_CloudDisk_UnregisterCallbackTable()` to avoid unnecessary callbacks and resource usage.

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

After receiving a hydration data retrieval callback and downloading cloud file data, call `OH_CloudDisk_Execute()` to return the data to Cloud Disk Foundation for storage. Use the same API to respond to cancellation requests. This unified Execute function handles requests according to callback type.

> **NOTE**
>
> For multiple data transfers, repeat the call until `fetchDataRsp.isComplete` is `true`.

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

    // Construct the request header: callback type, sync root path, and reqKey.
    uint8_t* reqKeyData = nullptr;
    OH_CloudDisk_CallbackReqHead reqHead = {};
    BuildReqHead(reqHead, ctx.callbackType, ctx.syncPath, ctx.reqKeyInt, reqKeyData);

    // Convert JS string contents into a byte buffer (query the length, then copy).
    ctx.contentLen = 0;
    napi_get_value_string_utf8(env, ctx.fileContentVal, nullptr, 0, &ctx.contentLen);
    char* contentBuf = new char[ctx.contentLen + 1];
    memset(contentBuf, 0, ctx.contentLen + 1);
    napi_get_value_string_utf8(env, ctx.fileContentVal, contentBuf, ctx.contentLen + 1, &ctx.contentLen);
    ctx.contentBytes = reinterpret_cast<uint8_t*>(contentBuf);
    LOGI("Execute: fileContent len=%{public}zu, content=%{public}s.", ctx.contentLen, contentBuf);

    // Construct the request context by callback type (ExecuteContext members remain valid throughout Execute).
    OH_CloudDisk_CallbackContext reqContext = {};
    BuildReqContext(reqContext, reqHead, ctx);

    // Construct the callback response: FETCH_DATA requires file data.
    OH_CloudDisk_CallbackResponse rsp = {};
    OH_CloudDisk_FetchData fetchDataRsp = {};
    BuildCallbackResponse(rsp, fetchDataRsp, reqHead, ctx);

    // ...
    // Execute the callback response and return contents to the cloud disk SDK.
    auto ret = OH_CloudDisk_Execute(reqHead, reqContext, rsp);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_Execute failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_Execute success.");
    }

    // Release memory allocated in this function.
    delete[] reqKeyData;
    delete[] contentBuf;
    delete[] ctx.syncPath;
    delete[] ctx.filePath;

    napi_value result;
    napi_create_int32(env, ret, &result);
    return result;
}
```

**Canceling Hydration**

Call `OH_CloudDisk_HydratePlaceholder()` to trigger hydration when a user opens a placeholder in the file manager or the application needs to make it accessible as an ordinary file. Cancel hydration when downloading is no longer needed.

> **NOTE**
>
> Before hydration, register a callback table through `OH_CloudDisk_RegisterCallbackTable`. This API is synchronous and returns immediately after successfully triggering hydration. The application starts downloading data after receiving the callback.

<!-- @[hydrate_placeholder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value HydratePlaceholder(napi_env env, napi_callback_info info)
{
    LOGI("HydratePlaceholder start.");
    size_t argc = 3;
    napi_value args[3] = {nullptr};
    GetArgs(env, info, argc, args);

    // Parse the arguments: sync root path, relative path, and callback type.
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

    // Callback types include FETCH_DATA (retrieve data), CANCEL_FETCH_DATA (cancel retrieval), and DEHYDRATE.
    int64_t callbackType = GetNumberParam(env, args[2]);

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
    CloudDisk_PathInfo filePath = MakePathInfo(relativePath);

    // ...
    // Initiate hydration (asynchronous; results arrive through the callback table).
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

**Dehydrating a File**

Call `OH_CloudDisk_DehydrateFile()` to change a fully hydrated placeholder into an unhydrated one when the user or application needs to release local storage while retaining the file contents in the cloud.

> **NOTE**
>
> The target must be a hydrated placeholder and must not be undergoing hydration; otherwise, an error code is returned.

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
    // Dehydrate (pass structure pointers here, unlike other APIs that pass values).
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
