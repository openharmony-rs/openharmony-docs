# 网盘服务底座适配指导
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @lcm_kiku-->
<!--Designer: @wangyanyue-->
<!--Tester: @zsyztt-->
<!--Adviser: @jinqiuheng-->

## 场景介绍

网盘服务底座为应用开发者提供了一套高效、安全的文件管理能力，支持对网盘同步根目录及其子目录进行状态管理，状态查询，变更监听等功能。网盘服务底座的接口由CloudDisk模块提供，详细API请参考[oh_cloud_disk_manager.h](../reference/apis-core-file-kit/capi-oh-cloud-disk-manager-h.md)。

本开发指导围绕以下四个方面展开，各项能力存在层层依赖关系：

- [同步根管理开发指导](#同步根管理开发指导)：注册/取消注册、激活/取消激活同步根，是其余三项能力的前置条件。
- [文件变更感知与同步状态管理开发指导](#文件变更感知与同步状态管理开发指导)：监听同步根下文件变更、查询历史操作记录、管理文件同步状态，依赖已注册的同步根。
- [占位符文件操作开发指导](#占位符文件操作开发指导)：在同步根下创建、更新、识别占位符文件，是水合/脱水的操作对象，依赖已注册的同步根。
- [按需水合与脱水开发指导](#按需水合与脱水开发指导)：注册回调表后触发水合/脱水，依赖已创建的占位符文件与已注册的同步根。

## 约束与限制

使用网盘服务底座能力的相关接口，需确认设备具有以下系统能力：SystemCapability.FileManagement.CloudDiskManager

## 环境准备

IDE为DevEco Studio 6.1.0 Release或更新版本（下载地址：[DevEco Studio官网](https://developer.huawei.com/consumer/cn/deveco-studio/)），SDK版本为API版本21及以上。

**添加动态链接库**

CMakeLists.txt中添加以下lib。

```txt
target_link_libraries(sample PUBLIC libohclouddiskmanager.so)
```

**添加头文件**

``` C++
#include "filemanagement/clouddiskmanager/oh_cloud_disk_manager.h"
```

## 同步根管理开发指导

支持网盘接入方应用注册/取消注册、激活/取消激活同步根，注册成功后文件管理器侧边栏展示网盘入口；支持同步根列表查询和自定义别名更新。取消注册同步根时会自动批量清理同步根下的占位符文件，普通文件保留。同步根管理是网盘服务底座各项能力的基础，文件变更监听、占位符文件操作、按需水合与脱水均依赖已注册的同步根。

### 接口说明

| 接口名称 | 描述 |
| -------- | -------- |
| CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolder(const CloudDisk_SyncFolder *syncFolder) | 应用注册同步根。<br>**说明**：从API版本21开始，支持该接口。 |
| CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath) | 应用取消注册同步根。<br>**说明**：从API版本21开始，支持该接口。 |
| CloudDisk_ErrorCode OH_CloudDisk_ActiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath) | 应用激活同步根。<br>**说明**：从API版本21开始，支持该接口。 |
| CloudDisk_ErrorCode OH_CloudDisk_DeactiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath) | 应用取消激活同步根。<br>**说明**：从API版本21开始，支持该接口。 |
| CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolders(CloudDisk_SyncFolder **syncFolders, size_t *count) | 应用获取所有已注册的同步根。<br>**说明**：从API版本21开始，支持该接口。 |
| CloudDisk_ErrorCode OH_CloudDisk_UpdateCustomAlias(const CloudDisk_SyncFolderPath syncFolderPath, const char *customAlias, size_t customAliasLength) | 应用更新同步根别名。<br>**说明**：从API版本21开始，支持该接口。 |

### 示例代码

**注册同步根**

网盘应用首次接入时，可调用OH_CloudDisk_RegisterSyncFolder()将用户授权的网盘目录注册为同步根，注册成功后文件管理器侧边栏才会展示网盘入口，系统才会开始记录该目录下的文件变更。这是接入网盘服务底座的第一步，后续的变更监听、占位符创建、水合/脱水等能力均依赖已注册的同步根。

<!-- @[register_sync_folder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value RegisterSyncFolder(napi_env env, napi_callback_info info)
{
    // 解析JS入参：同步根路径 + 显示名称（均为字符串）
    char* path = GetStringParam(env, info, 0);
    char* displayName = GetStringParam(env, info, 1);
    if (!path || !displayName) {
        // 参数非法时直接返回CLOUD_DISK_INVALID_ARG（无效参数错误码）
        LOGE("RegisterSyncFolder invalid params.");
        delete[] path;
        delete[] displayName;
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }

    // 构造同步根信息结构体
    CloudDisk_SyncFolder syncFolder = {};
    syncFolder.path = MakePathInfo(path);              // 同步根路径
    syncFolder.state = INACTIVE;                       // 初始状态：未激活（需另行激活才能开始同步）
    syncFolder.displayNameInfo.displayNameResId = 0;   // 系统资源ID名称（0表示不使用）
    syncFolder.displayNameInfo.customAlias = displayName;         // 自定义别名（用户可配置的显示名称）
    syncFolder.displayNameInfo.customAliasLength = strlen(displayName); // 自定义别名长度

    // ...
    // 调用云盘SDK注册同步根
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

**取消注册同步根**

网盘应用不再需要某个同步根，或需替换同步根目录时，可调用OH_CloudDisk_UnregisterSyncFolder()接口注销该同步根，注销后会自动批量清理同步根下的占位符文件，普通文件保留。

> **注意：**
>
> 每个应用最大注册同步根目录数量为10，超过上限时需先注销一个同步根目录才能注册新的同步根目录。

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

    // 构造同步根路径信息
    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(path);
    // ...
    // 调用云盘SDK注销同步根
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

**激活同步根**

同步根注册后默认未激活，应用启动时可调用OH_CloudDisk_ActiveSyncFolder()接口激活同步根，激活后用户才可在文件管理器界面查看该同步根下各文件的同步状态。

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
    // 调用云盘SDK激活同步根
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

**取消激活同步根**

应用退出或不需再对外展示同步根时，可调用OH_CloudDisk_DeactiveSyncFolder()接口取消激活同步根，取消激活后文件管理器不再展示该同步根的同步状态，但注册关系保留。

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
    // 调用云盘SDK去激活同步根
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

**获取所有已注册的同步根**

应用启动或配置页需要展示当前已注册的全部同步根、或判断是否已达注册上限时，可调用OH_CloudDisk_GetSyncFolders()接口查询所有已注册的同步根列表。

<!-- @[get_sync_folders](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value GetAllSyncFolder(napi_env env, napi_callback_info info)
{
    CloudDisk_SyncFolder* syncFolders = nullptr;
    size_t count = 0;
    // 查询全部同步根（SDK分配内存并返回数组指针与数量）
    auto ret = OH_CloudDisk_GetSyncFolders(&syncFolders, &count);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_GetSyncFolders failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_GetSyncFolders success, count: %{public}zu.", count);
    }
    if (ret != CLOUD_DISK_OK || count == 0) {
        // 无同步根时返回空数组，避免JS侧判空逻辑复杂化
        napi_value emptyArray;
        napi_create_array_with_length(env, 0, &emptyArray);
        return emptyArray;
    }

    // 创建JS数组，并把每个C结构体转换为JS对象放入数组
    napi_value jsArray;
    napi_create_array_with_length(env, count, &jsArray);
    for (size_t i = 0; i < count; i++) {
        napi_value syncFolderValue = ParseNapiSyncFolder(env, &syncFolders[i]);
        napi_set_element(env, jsArray, i, syncFolderValue);
    }
    return jsArray;
}
```

**更新同步根别名**

当用户在网盘应用侧修改了网盘目录的显示名称时，可调用OH_CloudDisk_UpdateCustomAlias()接口同步更新同步根的自定义别名，更新后文件管理器侧边栏将按新别名展示网盘入口。

<!-- @[update_custom_alias](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value UpdateDisplayName(napi_env env, napi_callback_info info)
{
    // 解析入参：同步根路径 + 新的显示名称
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
    // 调用云盘SDK更新别名（需要同时传入别名与长度）
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

## 文件变更感知与同步状态管理开发指导

感知同步根下文件的变化，支撑网盘接入方应用完成文件同步。包含同步根文件变更监听、历史操作记录增量查询，以及文件同步状态的设置与查询。同步根下文件增删改通过回调实时通知网盘接入方应用，应用可据此进行自身端云数据同步的流程。本章节各项能力依赖[同步根管理开发指导](#同步根管理开发指导)中已注册并激活的同步根。

### 接口说明

| 接口名称 | 描述 |
| -------- | -------- |
| CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, void (*callback)(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_ChangeData changeDatas[], size_t bufferLength)) | 应用注册一个回调函数，用于获取同步根路径下文件的变更。<br>**说明**：从API版本21开始，支持该接口。 |
| CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath) | 应用取消注册同步根路径下文件变更的回调。<br>**说明**：从API版本21开始，支持该接口。 |
| CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, uint64_t startUsn, size_t count, CloudDisk_ChangesResult **changesResult) | 获取同步根路径下的历史操作记录。<br>**说明**：从API版本21开始，支持该接口。 |
| CloudDisk_ErrorCode OH_CloudDisk_SetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_FileSyncState fileSyncStates[], size_t bufferLength, CloudDisk_FailedList **failedLists, size_t *failedCount) | 应用设置同步根路径下文件的同步状态。<br>**说明**：从API版本21开始，支持该接口。 |
| CloudDisk_ErrorCode OH_CloudDisk_GetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo paths[], size_t bufferLength, CloudDisk_ResultList **resultLists, size_t *resultCount) | 应用查询同步根路径下文件同步状态。<br>**说明**：从API版本21开始，支持该接口。 |

### 示例代码

**注册同步根变更监听**

应用需要实时感知同步根下文件的增删改以驱动自身同步逻辑时，可调用OH_CloudDisk_RegisterSyncFolderChanges()接口注册同步根变更监听，注册成功后文件变更会通过回调实时通知应用。<br>

1. OnChangeDataCallback()监听回调函数。

   <!-- @[on_change_data_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static void OnChangeDataCallback(const CloudDisk_SyncFolderPath syncFolderPath,
                                    const CloudDisk_ChangeData changeDatas[], size_t length)
   {
       LOGI("OnChangeDataCallback: path=%{public}s, length=%{public}zu.",
            syncFolderPath.value ? syncFolderPath.value : "(null)", length);
       // 逐条打印变更数据（便于调试观察变更内容）
       for (size_t i = 0; i < length; ++i) {
           auto& data = changeDatas[i];
           LOGI("  change[%{public}zu]: opType=%{public}d, relativePath=%{public}s.",
                i, data.operationType, data.relativePathInfo.value ? data.relativePathInfo.value : "(null)");
       }
       if (g_tsFn) {
           // 通过线程安全函数投递消息到JS线程（new出来的string由CallJs负责释放）
           std::string msg = "CloudDiskChange";
           napi_call_threadsafe_function(g_tsFn, new std::string(msg), napi_tsfn_blocking);
       }
   }
   ```
2. OH_CloudDisk_RegisterSyncFolderChanges()注册同步根变化监听。

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
       // 注册变更回调（C层回调为OnChangeDataCallback）
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

**取消同步根变更监听**

应用退出或不再需要接收同步根文件变更通知时，可调用OH_CloudDisk_UnregisterSyncFolderChanges()接口取消同步根变更监听，避免无效的回调与资源占用。

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
    // 取消变更订阅
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

**查询同步根下的历史操作记录**

应用启动时需补拉离线期间错过的变更、或因回调丢失需重新对齐变更进度时，可调用OH_CloudDisk_GetSyncFolderChanges()接口基于上次的变更序列号增量查询同步根下的历史操作记录。

> **注意：**
>
> 单次最大允许查询100条。

<!-- @[get_sync_folder_changes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value GetSyncFolderChanges(napi_env env, napi_callback_info info)
{
    // 解析入参：同步根路径、起始usn、拉取条数
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

    // 调用SDK增量获取变更（结果由SDK分配内存，返回结构体指针）
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

    // 失败或无数据时返回null
    if (ret != CLOUD_DISK_OK || !changesResult) {
        napi_value nullVal;
        napi_get_null(env, &nullVal);
        return nullVal;
    }
    // 把C结构体转换为JS对象（ChangesResult）返回
    return ParseNapiChangesResult(env, changesResult);
}
```

**设置同步根路径下文件的同步状态**

应用完成某文件的上行/下行同步后，可调用OH_CloudDisk_SetFileSyncStates()接口标记该文件的同步状态（如同步成功、同步失败等），供文件管理器展示同步结果。

> **注意：**
>
> 单次最大允许传入100个文件路径。

<!-- @[set_file_sync_states](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value SetFileSyncStates(napi_env env, napi_callback_info info)
{
    size_t argc = 3;
    napi_value args[3] = {nullptr};
    GetArgs(env, info, argc, args);

    // SetFileSyncStates参数索引定义
    enum ArgIndex {
        ARG_SYNC_PATH = 0,
        ARG_LENGTH = 1,
        ARG_STATE_ARRAY = 2,
    };

    // 解析入参：同步根路径、状态数组长度、文件同步状态数组
    char* path = GetStringParam(env, args[ARG_SYNC_PATH]);
    if (!path) {
        LOGE("SetFileSyncStates path is empty.");
        napi_value result;
        napi_create_int32(env, CLOUD_DISK_INVALID_ARG, &result);
        return result;
    }
    uint64_t length = static_cast<uint64_t>(GetNumberParam(env, args[ARG_LENGTH]));

    // 把JS数组转换为C结构体数组（内部new内存，用后需free）
    CloudDisk_FileSyncState* fileSyncStates = nullptr;
    size_t arraySize = 0;
    ConvertToFileSyncStates(env, args[ARG_STATE_ARRAY], &fileSyncStates, &arraySize);

    // 批量设置同步状态，失败项会写入failedLists（路径 + 失败原因）
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

    // 打印失败项（路径 + 错误原因），便于问题定位
    if (failedCount != 0 && failedLists) {
        for (size_t i = 0; i < failedCount; i++) {
            LOGE("  failed[%{public}zu]: path=%{public}s, reason=%{public}d.",
                 i, failedLists[i].pathInfo.value ? failedLists[i].pathInfo.value : "(null)",
                 failedLists[i].errorReason);
        }
    }

    // 释放转换过程中申请的内存
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

**查询同步根下文件的当前同步状态**

应用需查询同步根下文件的当前同步状态（如展示同步进度、排查同步异常）时，可调用OH_CloudDisk_GetFileSyncStates()接口批量查询同步根下文件的同步状态。

> **注意：**
>
> 单次最大允许查询100个文件。

<!-- @[get_file_sync_states](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value GetFileSyncStates(napi_env env, napi_callback_info info)
{
    size_t argc = 3;
    napi_value args[3] = {nullptr};
    GetArgs(env, info, argc, args);

    // GetFileSyncStates参数索引定义
    enum ArgIndex {
        ARG_SYNC_PATH = 0,
        ARG_LENGTH = 1,
        ARG_PATH_ARRAY = 2,
    };

    // 解析入参：同步根路径、路径数量、文件相对路径数组
    char* path = GetStringParam(env, args[ARG_SYNC_PATH]);
    if (!path) {
        LOGE("GetFileSyncStates path is empty.");
        napi_value nullVal;
        napi_get_null(env, &nullVal);
        return nullVal;
    }
    uint64_t length = static_cast<uint64_t>(GetNumberParam(env, args[ARG_LENGTH]));

    // 把JS路径数组转换为C结构体数组（内部new内存，用后需释放）
    CloudDisk_PathInfo* paths = nullptr;
    size_t arraySize = 0;
    ConvertToPathInfos(env, args[ARG_PATH_ARRAY], &paths, &arraySize);

    // 批量查询，返回每个文件的状态结果列表
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

    // 失败或无结果时返回null
    if (ret != CLOUD_DISK_OK || resultCount == 0 || !resultLists) {
        napi_value nullVal;
        napi_get_null(env, &nullVal);
        return nullVal;
    }

    // 把每个查询结果转换为JS对象并放入数组返回
    napi_value jsArray;
    napi_create_array_with_length(env, resultCount, &jsArray);
    for (size_t i = 0; i < resultCount; i++) {
        napi_value resultValue = ParseNapiResultList(env, &resultLists[i]);
        napi_set_element(env, jsArray, i, resultValue);
    }

    // 释放转换过程中申请的内存
    if (paths) {
        for (size_t i = 0; i < arraySize; i++) {
            free(paths[i].value);
        }
        free(paths);
    }

    return jsArray;
}
```

## 占位符文件操作开发指导

云侧文件以占位符形式映射到本地，本地仅保留元数据、不落盘实体数据。支持在同步根下创建占位符文件、识别占位符与普通文件、更新占位符元数据，以及将占位符文件转换为0字节普通文件。本章节各项能力依赖[同步根管理开发指导](#同步根管理开发指导)中已注册的同步根，创建的占位符文件是[按需水合与脱水开发指导](#按需水合与脱水开发指导)的操作对象。

### 接口说明

| 接口名称 | 描述 |
| -------- | -------- |
| CloudDisk_ErrorCode OH_CloudDisk_CreatePlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, const OH_CloudDisk_PlaceholderInfo placeholderInfo, const OH_CloudDisk_PlaceholderCustomInfo *customInfo) | 在同步根内创建占位符文件，写入逻辑大小、atimeMs、mtimeMs等元数据。<br>**说明**：从API版本26.0.1开始，支持该接口。 |
| CloudDisk_ErrorCode OH_CloudDisk_UpdatePlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, const OH_CloudDisk_PlaceholderInfo placeholderInfo, const OH_CloudDisk_PlaceholderCustomInfo *customInfo) | 更新占位符文件的元数据信息（logicalSize、atimeMs、mtimeMs等）。<br>**说明**：从API版本26.0.1开始，支持该接口。 |
| CloudDisk_ErrorCode OH_CloudDisk_IsPlaceholderFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, bool *isPlaceholder) | 判断同步根内文件是否为占位符文件。<br>**说明**：从API版本26.0.1开始，支持该接口。 |
| CloudDisk_ErrorCode OH_CloudDisk_ConvertPlaceholderToFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo) | 将占位符文件转换为0字节普通文件。<br>**说明**：从API版本26.0.1开始，支持该接口。 |

### 示例代码

**创建占位符文件**

调用OH_CloudDisk_CreatePlaceholder()接口，网盘应用创建一个本地的占位符文件来映射云侧的真实数据，以达到在端侧浏览云侧文件的目的。需已注册同步根，创建的占位符文件是后续水合/脱水的操作对象。

<!-- @[create_placeholder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value CreatePlaceholderFile(napi_env env, napi_callback_info info)
{
    size_t argc = 5;
    napi_value args[5] = {nullptr};
    GetArgs(env, info, argc, args);

    // 解析入参：同步根路径 + 相对路径（占位符文件在同步根内的相对位置）
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

    // 解析时间与大小参数
    uint64_t atimeMs = static_cast<uint64_t>(GetNumberParam(env, args[2]));  // 访问时间（毫秒时间戳，映射云端文件访问时间）
    uint64_t mtimeMs = static_cast<uint64_t>(GetNumberParam(env, args[3]));  // 修改时间（毫秒时间戳，映射云端文件修改时间）
    uint64_t logicalSize = static_cast<uint64_t>(GetNumberParam(env, args[4])); // 云端文件逻辑大小（字节）

    // 构造同步根路径与相对路径
    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
    CloudDisk_PathInfo relativePathInfo = MakePathInfo(relativePath);

    // 定义占位符文件信息
    OH_CloudDisk_PlaceholderInfo placeholderInfo = {};
    placeholderInfo.atimeMs = atimeMs;       // 访问时间（毫秒）
    placeholderInfo.mtimeMs = mtimeMs;       // 修改时间（毫秒）
    placeholderInfo.logicalSize = logicalSize; // 逻辑大小（字节）

    // ...
    // 创建占位符文件（customInfo传NULL，表示不写入占位符自定义信息）
    auto ret = OH_CloudDisk_CreatePlaceholder(syncFolderPath, relativePathInfo, placeholderInfo, NULL);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_CreatePlaceholder failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_CreatePlaceholder success.");
    }

    delete[] syncPath;
    delete[] relativePath;

    napi_value result;
    napi_create_int32(env, ret, &result);
    return result;
}
```

**更新占位符文件的元数据信息**

云侧的数据有更新，需要同步更新到端侧的占位符元数据，以映射最新的元数据信息，应用可调用OH_CloudDisk_UpdatePlaceholder()接口，更新占位符文件的元数据信息（逻辑大小、访问时间、修改时间等），仅支持更新占位符文件不支持更新普通文件。

<!-- @[update_placeholder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value UpdatePlaceholder(napi_env env, napi_callback_info info)
{
    size_t argc = 5;
    napi_value args[5] = {nullptr};
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

    // 解析需要更新的时间与大小
    uint64_t atimeMs = static_cast<uint64_t>(GetNumberParam(env, args[2]));
    uint64_t mtimeMs = static_cast<uint64_t>(GetNumberParam(env, args[3]));
    uint64_t logicalSize = static_cast<uint64_t>(GetNumberParam(env, args[4]));

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
    CloudDisk_PathInfo relativePathInfo = MakePathInfo(relativePath);

    // 构造新的占位符元数据
    OH_CloudDisk_PlaceholderInfo placeholderInfo = {};
    placeholderInfo.atimeMs = atimeMs;       // 访问时间（毫秒）
    placeholderInfo.mtimeMs = mtimeMs;       // 修改时间（毫秒）
    placeholderInfo.logicalSize = logicalSize; // 逻辑大小（字节）

    // ...
    // 更新占位符元数据
    auto ret = OH_CloudDisk_UpdatePlaceholder(syncFolderPath, relativePathInfo, placeholderInfo, NULL);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_UpdatePlaceholder failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_UpdatePlaceholder success.");
    }

    delete[] syncPath;
    delete[] relativePath;

    napi_value result;
    napi_create_int32(env, ret, &result);
    return result;
}
```

**判断是否为占位符文件**

应用若想要判断端侧文件是普通文件还是占位符文件，可调用OH_CloudDisk_IsPlaceholderFile()接口，结果以出参的方式带出。

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
        // 参数非法：返回code=CLOUD_DISK_INVALID_ARG, isPlaceholder=false的对象
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

    // 调用SDK查询是否为占位符（结果写入isPlaceholder）
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

    // 构造JS返回对象 { code, isPlaceholder }
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

**将占位符文件转换为0字节普通文件**

当网盘应用需要清除占位符语义、使文件回归普通文件操作策略时（如文件被移出同步根、或不再走网盘同步流程），可调用OH_CloudDisk_ConvertPlaceholderToFile()接口将占位符文件转换为0字节普通文件。

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
    // 占位符转普通文件
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

## 按需水合与脱水开发指导

云侧文件实体按需下载到本地或释放本地数据块，避免全量下载占用本地空间。水合将云侧数据按需下载到本地，脱水释放文件的本地数据块。本章节依赖[同步根管理开发指导](#同步根管理开发指导)中已注册的同步根与[占位符文件操作开发指导](#占位符文件操作开发指导)中已创建的占位符文件。水合/脱水依赖回调表机制：触发水合前需通过 `OH_CloudDisk_RegisterCallbackTable()` 注册回调表。回调中可获取回调类型与请求上下文，应用据此从云侧下载文件数据，再调用 `OH_CloudDisk_Execute()` 回传数据完成落盘。

### 接口说明

| 接口名称 | 描述 |
| -------- | -------- |
| CloudDisk_ErrorCode OH_CloudDisk_RegisterCallbackTable(const CloudDisk_SyncFolderPath syncFolderPath, void (*callback)(const OH_CloudDisk_CallbackReqHead reqHead, OH_CloudDisk_CallbackContext reqContext)) | 注册回调表。注册后，网盘服务底座在水合取数、取消取数、脱水等场景通过回调通知网盘接入方应用。<br>**说明**：从API版本26.0.1开始，支持该接口。 |
| CloudDisk_ErrorCode OH_CloudDisk_UnregisterCallbackTable(const CloudDisk_SyncFolderPath syncFolderPath) | 注销回调表，注销后不再接收相关回调通知。<br>**说明**：从API版本26.0.1开始，支持该接口。 |
| CloudDisk_ErrorCode OH_CloudDisk_Execute(const OH_CloudDisk_CallbackReqHead reqHead, OH_CloudDisk_CallbackContext reqContext, OH_CloudDisk_CallbackResponse rsp) | 网盘接入方应用响应水合取数或取消取数回调请求。取数据回调类型需在rsp参数中携带响应数据，取消取数据回调类型不需要携带响应数据。<br>**说明**：从API版本26.0.1开始，支持该接口。 |
| CloudDisk_ErrorCode OH_CloudDisk_HydratePlaceholder(const CloudDisk_SyncFolderPath *syncFolderPath, const CloudDisk_PathInfo *filePath, OH_CloudDisk_CallbackType type, OH_CloudDisk_HydratePriority priority) | 触发占位符水合或取消水合。开始水合前需已注册回调表。<br>**说明**：从API版本26.0.1开始，支持该接口。 |
| CloudDisk_ErrorCode OH_CloudDisk_DehydrateFile(const CloudDisk_SyncFolderPath *syncFolderPath, const CloudDisk_PathInfo *filePath) | 将普通文件脱水为占位符文件。目标不能是纯占位符文件且未在水合中。<br>**说明**：从API版本26.0.1开始，支持该接口。 |

### 示例代码

**注册回调表**

网盘应用需承接水合取数、取消取数、流式读取、脱水授权等场景的回调时，可调用OH_CloudDisk_RegisterCallbackTable接口为同步根注册回调表，注册后网盘服务底座会通过回调向应用下发相应请求。需已注册同步根，这是水合/脱水操作的前置条件。

> **注意：**
>
> 开始水合前必须先注册回调表。

1. OnCallbackTableCallback()回调函数，具体实现以水合取数、取消取数、去水合操作为例。

   <!-- @[on_callback_table_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static void OnCallbackTableCallback(const OH_CloudDisk_CallbackReqHead reqHead,
                                       OH_CloudDisk_CallbackContext reqContext)
   {
       LOGI("OnCallbackTableCallback: callbackType=%{public}d.", reqHead.callbackType);
   
       // 以同步根路径为key保存请求头（供后续查询）
       std::string syncPathKey(reqHead.syncFolderPath.value, reqHead.syncFolderPath.length);
       g_lastReqHeadMap[syncPathKey] = reqHead;
   
       // 保存reqKey到全局map（getCallbackReqKey从中读取），
       // 同时递增版本号，供ETS侧轮询判断"新的reqKey是否已就绪"
       uint64_t reqKeyU64 = 0;
       if (reqHead.reqKey.data != nullptr && reqHead.reqKey.dataSize > 0) {
           // 深拷贝reqKey数据（回调结束后原内存可能被释放）
           uint8_t* keyData = new uint8_t[reqHead.reqKey.dataSize];
           memcpy(keyData, reqHead.reqKey.data, reqHead.reqKey.dataSize);
   
           OH_CloudDisk_DataBuf storedKey = {};
           storedKey.data = keyData;
           storedKey.dataSize = reqHead.reqKey.dataSize;
           g_reqKeyMap[syncPathKey] = storedKey;
           g_reqKeyVersion.fetch_add(1, std::memory_order_release);
   
           // 把reqKey字节序转换为uint64便于日志查看（小端序）
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
   
       // 根据回调类型深拷贝请求上下文（原内存回调结束后可能失效）
       OH_CloudDisk_CallbackContext copiedContext = CopyCallbackContext(reqHead, reqContext);
   
       // 保存深拷贝后的上下文
       g_lastReqContextMap[syncPathKey] = copiedContext;
   
       // 手动模式：仅保存reqKey与上下文，由UI手动触发Execute。
       if (reqHead.callbackType == CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA && reqContext.fetchData) {
           LOGI("OnCallbackTableCallback: FETCH_DATA stored for manual execute, "
                "syncFolder: %{public}s, file: %{public}s.",
                reqHead.syncFolderPath.value, reqContext.fetchData->filePath.value);
       }
   
       // 自动水合：注册回调表时若填写了"水合数据文件"，回调到达后自动读取该文件
       // 内容并分块Execute回传。g_fetchFilePath为空时不自动执行，走上方手动模式。
       if (reqHead.callbackType == CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA && reqContext.fetchData) {
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
2. OH_CloudDisk_RegisterCallbackTable()注册回调表。

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
   
       // 可选第二参数：水合数据文件名（用于FETCH_DATA自动执行）
       char* fetchFileName = GetStringParam(env, args[1]);
       if (fetchFileName && fetchFileName[0] != '\0') {
           g_fetchFilePath = std::string("/data/storage/el2/base/haps/entry/files/") + std::string(fetchFileName);
           LOGI("RegisterCallbackTable: fetchFilePath=%{public}s.", g_fetchFilePath.c_str());
           delete[] fetchFileName;
       } else {
           // 不填（nullptr）或空字符串：清空残留路径，关闭自动执行，避免残留旧值导致重复Execute
           if (fetchFileName) {
               delete[] fetchFileName;
           }
           g_fetchFilePath.clear();
           LOGW("RegisterCallbackTable: fetchFilePath cleared, auto-execute disabled.");
       }
   
       CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
   
       // ...
       // 注册回调表（回调函数为OnCallbackTableCallback）
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

**注销回调表**

应用退出或不再需要承接水合/脱水回调时，可调用OH_CloudDisk_UnregisterCallbackTable()接口注销回调表，避免无效回调与资源占用。

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
    // 注销回调表
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

**响应回调请求**

应用在回调中收到水合取数请求后，从云侧下载完文件数据，可调用OH_CloudDisk_Execute()接口将数据回传给网盘服务底座完成落盘；收到取消取数请求时，也通过该接口响应。该接口为统一的Execute函数，根据不同的回调类型处理不同的请求。

> **注意：**
>
> 数据分多次传输时，需重复调用直至fetchDataRsp.isComplete为true。

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

    // 构造请求头：回调类型 + 同步根路径 + reqKey
    uint8_t* reqKeyData = nullptr;
    OH_CloudDisk_CallbackReqHead reqHead = {};
    BuildReqHead(reqHead, ctx.callbackType, ctx.syncPath, ctx.reqKeyInt, reqKeyData);

    // 把JS字符串内容转为字节缓冲区（先查长度，再拷贝）
    ctx.contentLen = 0;
    napi_get_value_string_utf8(env, ctx.fileContentVal, nullptr, 0, &ctx.contentLen);
    char* contentBuf = new char[ctx.contentLen + 1];
    memset(contentBuf, 0, ctx.contentLen + 1);
    napi_get_value_string_utf8(env, ctx.fileContentVal, contentBuf, ctx.contentLen + 1, &ctx.contentLen);
    ctx.contentBytes = reinterpret_cast<uint8_t*>(contentBuf);
    LOGI("Execute: fileContent len=%{public}zu, content=%{public}s.", ctx.contentLen, contentBuf);

    // 根据回调类型构造请求上下文（ExecuteContext成员生命周期覆盖Execute调用）
    OH_CloudDisk_CallbackContext reqContext = {};
    BuildReqContext(reqContext, reqHead, ctx);

    // 构造回调响应：FETCH_DATA / FETCH_RANGE_DATA类型需要回传文件数据
    OH_CloudDisk_CallbackResponse rsp = {};
    OH_CloudDisk_FetchData fetchDataRsp = {};
    BuildCallbackResponse(rsp, fetchDataRsp, reqHead, ctx);

    // ...
    // 执行回调响应，把内容回传给云盘SDK
    auto ret = OH_CloudDisk_Execute(reqHead, reqContext, rsp);
    if (ret != CLOUD_DISK_OK) {
        LOGE("OH_CloudDisk_Execute failed, errorCode: %{public}d.", ret);
    } else {
        LOGI("OH_CloudDisk_Execute success.");
    }

    // 释放本函数内申请的内存
    delete[] reqKeyData;
    delete[] contentBuf;
    delete[] ctx.syncPath;
    delete[] ctx.filePath;

    napi_value result;
    napi_create_int32(env, ret, &result);
    return result;
}
```

**取消水合**

用户在文件管理器打开占位符文件、或应用主动需要将占位符文件变为可访问的普通文件时，可调用OH_CloudDisk_HydratePlaceholder()接口触发水合；不再需要下载时可取消水合。

> **注意：**
>
> 开始水合前需已通过OH_CloudDisk_RegisterCallbackTable注册回调表；该接口为同步接口，触发成功后立即返回，应用收到回调后再开始下载数据。

<!-- @[hydrate_placeholder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/CoreFile/CloudDisk/entry/src/main/cpp/napi_init.cpp) -->

``` C++
static napi_value HydratePlaceholder(napi_env env, napi_callback_info info)
{
    LOGI("HydratePlaceholder start.");
    size_t argc = 3;
    napi_value args[3] = {nullptr};
    GetArgs(env, info, argc, args);

    // 解析入参：同步根路径 + 相对路径 + 回调类型
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

    // 回调类型：FETCH_DATA(取数据)/CANCEL_FETCH_DATA(取消取数据)/DEHYDRATE(去水合) 等
    int64_t callbackType = GetNumberParam(env, args[2]);

    CloudDisk_SyncFolderPath syncFolderPath = MakePathInfo(syncPath);
    CloudDisk_PathInfo filePath = MakePathInfo(relativePath);

    // ...
    // 发起水合请求（异步，结果通过回调表回调返回）
    auto ret = OH_CloudDisk_HydratePlaceholder(&syncFolderPath, &filePath,
        static_cast<OH_CloudDisk_CallbackType>(callbackType),
        CLOUD_DISK_HYDRATE_PRIORITY_NORMAL);
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

**脱水**

用户或应用需要释放本地存储空间、且文件内容仍保留在云侧时，可调用OH_CloudDisk_DehydrateFile()接口将已水合的普通文件脱水回占位符文件。

> **注意：**
>
> 目标不能是纯占位符文件且未在水合中，否则返回错误码。

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
    // 去水合（注意这里传的是结构体指针，与其它接口传值不同）
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
