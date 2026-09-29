# oh_cloud_disk_manager.h

## 概述

云盘管理模块的接口定义。

**库：** libohclouddiskmanager.so

**起始版本：** 21

**相关模块：** [CloudDisk](capi-clouddisk.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) | - | 文件路径信息。 |
| [CloudDisk_FileSyncState](capi-clouddisk-clouddisk-filesyncstate.md) | - | 文件的同步状态。 |
| [CloudDisk_ChangeData](capi-clouddisk-clouddisk-changedata.md) | - | 定义了同步根路径下单个文件变更事件的数据结构。该结构包含有关文件变更的详细信息，包括唯一ID、父目录的唯一ID、相对路径、变更类型、文件大小和时间戳。 |
| [CloudDisk_ChangesResult](capi-clouddisk-clouddisk-changesresult.md) | - | 查询同步根路径中文件变更的结果。该结构体包含同步根路径中文件的变更数据，包括下一个更新序列号、结尾标志以及变更数据项数组。 |
| [CloudDisk_FailedList](capi-clouddisk-clouddisk-failedlist.md) | - | 同步操作中失败的文件列表信息。该结构包含文件路径信息以及失败的具体错误原因。 |
| [CloudDisk_ResultList](capi-clouddisk-clouddisk-resultlist.md) | - | 表示一个文件同步操作的结果。该结构体包含文件的绝对路径、同步结果，以及同步状态或失败原因。 |
| [CloudDisk_DisplayNameInfo](capi-clouddisk-clouddisk-displaynameinfo.md) | - | 定义同步根路径的显示名称信息。 |
| [CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md) | - | 同步根属性信息。 |
| [OH_CloudDisk_SyncFolderEx](capi-clouddisk-oh-clouddisk-syncfolderex.md) | - | 定义带占位符支持的云盘同步文件夹。 必须将版本字段设置为有效的版本宏(例如[OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1](capi-oh-cloud-disk-manager-h.md#宏定义))，然后才能传递结构到任何API。 运行时使用版本来确定字段有效；当指定低版本时，在较高版本中引入的字段将被忽略。 |
| [OH_CloudDisk_PlaceholderInfo](capi-clouddisk-oh-clouddisk-placeholderinfo.md) | - | 占位符文件的元数据信息。 |
| [OH_CloudDisk_DataBuf](capi-clouddisk-oh-clouddisk-databuf.md) | - | 云盘数据缓冲区信息。 |
| [OH_CloudDisk_CallbackReqHead](capi-clouddisk-oh-clouddisk-callbackreqhead.md) | - | 云盘回调请求头信息。 |
| [OH_CloudDisk_DehydrateInfo](capi-clouddisk-oh-clouddisk-dehydrateinfo.md) | - | 脱水授权信息。 |
| [OH_CloudDisk_FetchRangeDataRequest](capi-clouddisk-oh-clouddisk-fetchrangedatarequest.md) | - | 获取范围数据请求信息。 |
| [OH_CloudDisk_FetchDataRequest](capi-clouddisk-oh-clouddisk-fetchdatarequest.md) | - | 获取数据请求信息。 |
| [OH_CloudDisk_CallbackContext](capi-clouddisk-oh-clouddisk-callbackcontext.md) | - | 回调请求上下文信息联合体。 |
| [OH_CloudDisk_FetchData](capi-clouddisk-oh-clouddisk-fetchdata.md) | - | 云端文件数据获取结果。 |
| [OH_CloudDisk_CallbackResponse](capi-clouddisk-oh-clouddisk-callbackresponse.md) | - | 回调响应信息联合体。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [CloudDisk_SyncState](#clouddisk_syncstate) | CloudDisk_SyncState | 文件同步状态的枚举值。 |
| [CloudDisk_OperationType](#clouddisk_operationtype) | CloudDisk_OperationType | 文件变更类型枚举值。 |
| [CloudDisk_ErrorReason](#clouddisk_errorreason) | CloudDisk_ErrorReason | 文件同步失败原因的枚举值。 |
| [CloudDisk_SyncFolderState](#clouddisk_syncfolderstate) | CloudDisk_SyncFolderState | 同步根路径状态的枚举值。 |
| [OH_CloudDisk_CallbackType](#oh_clouddisk_callbacktype) | OH_CloudDisk_CallbackType | 云盘回调类型枚举值。 |
| [OH_CloudDisk_HydratePriority](#oh_clouddisk_hydratepriority) | OH_CloudDisk_HydratePriority | 水合优先级枚举值。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1 1 | OH_CloudDisk_SyncFolderEx服务的版本1。 当结构体被扩展时，将定义新的版本宏。 运行库使用版本字段确定哪些字段有效。<br>**起始版本：** 26.0.1 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, void (\*callback)(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_ChangeData changeDatas[], size_t bufferLength))](#oh_clouddisk_registersyncfolderchanges) | 应用注册一个回调函数，用于获取同步根路径下文件的变更。 |
| [CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath)](#oh_clouddisk_unregistersyncfolderchanges) | 应用取消注册同步根路径下文件变更的回调。 |
| [CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, uint64_t startUsn, size_t count, CloudDisk_ChangesResult **changesResult)](#oh_clouddisk_getsyncfolderchanges) | 获取同步根路径下的历史操作记录。 |
| [CloudDisk_ErrorCode OH_CloudDisk_SetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_FileSyncState fileSyncStates[], size_t bufferLength, CloudDisk_FailedList **failedLists, size_t *failedCount)](#oh_clouddisk_setfilesyncstates) | 应用设置同步根路径下文件的同步状态。 |
| [CloudDisk_ErrorCode OH_CloudDisk_GetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo paths[], size_t bufferLength, CloudDisk_ResultList **resultLists, size_t *resultCount)](#oh_clouddisk_getfilesyncstates) | 应用查询同步根路径下文件同步状态。 |
| [CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolder(const CloudDisk_SyncFolder *syncFolder)](#oh_clouddisk_registersyncfolder) | 应用注册同步根。 |
| [CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)](#oh_clouddisk_unregistersyncfolder) | 应用取消注册同步根。 |
| [CloudDisk_ErrorCode OH_CloudDisk_ActiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)](#oh_clouddisk_activesyncfolder) | 应用激活同步根。 |
| [CloudDisk_ErrorCode OH_CloudDisk_DeactiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)](#oh_clouddisk_deactivesyncfolder) | 应用取消激活同步根。 |
| [CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolders(CloudDisk_SyncFolder **syncFolders, size_t *count)](#oh_clouddisk_getsyncfolders) | 应用获取所有同步根。 |
| [CloudDisk_ErrorCode OH_CloudDisk_UpdateCustomAlias(const CloudDisk_SyncFolderPath syncFolderPath, const char *customAlias, size_t customAliasLength)](#oh_clouddisk_updatecustomalias) | 应用更新同步根别名。 |
| [CloudDisk_ErrorCode OH_CloudDisk_CreatePlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, const OH_CloudDisk_PlaceholderInfo placeholderInfo)](#oh_clouddisk_createplaceholder) | 在已注册的同步文件夹中创建占位符。 |
| [CloudDisk_ErrorCode OH_CloudDisk_IsPlaceholderFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, bool *isPlaceholder)](#oh_clouddisk_isplaceholderfile) | 检查同步根中的文件是否为占位符文件。 |
| [CloudDisk_ErrorCode OH_CloudDisk_ConvertPlaceholderToFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo)](#oh_clouddisk_convertplaceholdertofile) | 将占位符文件转换为0字节普通文件。 |
| [CloudDisk_ErrorCode OH_CloudDisk_UpdatePlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, const OH_CloudDisk_PlaceholderInfo placeholderInfo)](#oh_clouddisk_updateplaceholder) | 更新文件元数据（支持占位符和普通文件）。 |
| [CloudDisk_ErrorCode OH_CloudDisk_RegisterCallbackTable(const CloudDisk_SyncFolderPath syncFolderPath, void (\*callback)(const OH_CloudDisk_CallbackReqHead reqHead, OH_CloudDisk_CallbackContext reqContext))](#oh_clouddisk_registercallbacktable) | 注册用于水合和脱水请求的回调表。 |
| [CloudDisk_ErrorCode OH_CloudDisk_UnregisterCallbackTable(const CloudDisk_SyncFolderPath syncFolderPath)](#oh_clouddisk_unregistercallbacktable) | 取消注册用于水合和脱水请求的回调表。 |
| [CloudDisk_ErrorCode OH_CloudDisk_Execute(const OH_CloudDisk_CallbackReqHead reqHead, OH_CloudDisk_CallbackContext reqContext, OH_CloudDisk_CallbackResponse rsp)](#oh_clouddisk_execute) | 响应回调请求。 |
| [CloudDisk_ErrorCode OH_CloudDisk_HydratePlaceholder(const CloudDisk_SyncFolderPath *syncFolderPath, const CloudDisk_PathInfo *filePath, OH_CloudDisk_CallbackType type, OH_CloudDisk_HydratePriority priority)](#oh_clouddisk_hydrateplaceholder) | 主动水合占位符文件或取消水合。 |
| [CloudDisk_ErrorCode OH_CloudDisk_DehydrateFile(const CloudDisk_SyncFolderPath *syncFolderPath, const CloudDisk_PathInfo *filePath)](#oh_clouddisk_dehydratefile) | 对完全水合的占位符文件执行脱水。 |
| [CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolderEx(const OH_CloudDisk_SyncFolderEx *syncFolder)](#oh_clouddisk_registersyncfolderex) | 使用占位符支持信息注册同步文件夹。 |
| [CloudDisk_ErrorCode OH_CloudDisk_GetSyncFoldersEx(OH_CloudDisk_SyncFolderEx **syncFolders, size_t *count)](#oh_clouddisk_getsyncfoldersex) | 获取具有占位符支持信息的同步文件夹。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| CloudDisk_PathInfo CloudDisk_FileIdInfo | 定义的文件ID。<br>**起始版本：** 21<br>**系统能力：** SystemCapability.FileManagement.CloudDiskManager |
| CloudDisk_PathInfo CloudDisk_SyncFolderPath | 定义的同步根路径。<br>**起始版本：** 21<br>**系统能力：** SystemCapability.FileManagement.CloudDiskManager |

## 枚举类型说明

### CloudDisk_SyncState

```c
enum CloudDisk_SyncState
```

**描述：**

文件同步状态的枚举值。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| IDLE = 0 | 目前处于空闲状态，未执行任何同步操作。<br>**起始版本：** 21 |
| SYNCING = 1 | 文件正在同步。<br>**起始版本：** 21 |
| SYNC_SUCCEEDED = 2 | 文件同步成功。<br>**起始版本：** 21 |
| SYNC_FAILED = 3 |  文件同步失败。<br>**起始版本：** 21 |
| SYNC_CANCELED = 4 | 文件同步取消。<br>**起始版本：** 21 |
| SYNC_CONFLICTED = 5 | 文件同步冲突。<br>**起始版本：** 21 |

### CloudDisk_OperationType

```c
enum CloudDisk_OperationType
```

**描述：**

文件变更类型枚举值。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| CREATE = 0 | 创建文件或目录。<br>**起始版本：** 21 |
| DELETE = 1 | 删除文件或目录。<br>**起始版本：** 21 |
| MOVE_FROM = 2 | 移动此文件或目录。<br>**起始版本：** 21 |
| MOVE_TO = 3 | 移动到此文件或目录。<br>**起始版本：** 21 |
| CLOSE_WRITE = 4 | 在写入操作后关闭文件。<br>**起始版本：** 21 |
| SYNC_FOLDER_INVALID = 5 | 同步根路径无效。<br>**起始版本：** 21 |
| OH_CLOUD_DISK_CLOSE_MODIFY = 6 | 修改内容后关闭文件。<br>**起始版本：** 26.0.1 |

### CloudDisk_ErrorReason

```c
enum CloudDisk_ErrorReason
```

**描述：**

文件同步失败原因的枚举值。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| INVALID_ARGUMENT = 0 | 输入的参数无效。<br>**起始版本：** 21 |
| NO_SUCH_FILE = 1 | 操作的文件或目录不存在。<br>**起始版本：** 21 |
| NO_SPACE_LEFT = 2 | 设备上的剩余空间不足。<br>**起始版本：** 21 |
| OUT_OF_RANGE = 3 | 超出有效范围。<br>**起始版本：** 21 |
| NO_SYNC_STATE = 4 | 同步状态未设置。<br>**起始版本：** 21 |

### CloudDisk_SyncFolderState

```c
enum CloudDisk_SyncFolderState
```

**描述：**

同步根路径状态的枚举值。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| INACTIVE = 0 | 表示同步根路径的状态是未激活的。<br>**起始版本：** 21 |
| ACTIVE = 1 | 表示同步根路径的状态是激活的。<br>**起始版本：** 21 |

### OH_CloudDisk_CallbackType

```c
enum OH_CloudDisk_CallbackType
```

**描述：**

云盘回调类型枚举值。

**起始版本：** 26.0.1

| 枚举项 | 描述 |
| -- | -- |
| OH_CLOUD_DISK_CALLBACK_TYPE_FETCH_DATA = 0 | 获取云端文件数据，用于水合。<br>**起始版本：** 26.0.1 |
| OH_CLOUD_DISK_CALLBACK_TYPE_CANCEL_FETCH_DATA = 1 | 取消获取云端文件数据。<br>**起始版本：** 26.0.1 |
| OH_CLOUD_DISK_CALLBACK_TYPE_DEHYDRATE = 2 | 请求脱水授权。<br>**起始版本：** 26.0.1 |
| OH_CLOUD_DISK_CALLBACK_TYPE_FETCH_RANGE_DATA = 3 | 获取指定范围数据，用于读取。<br>**起始版本：** 26.2.0 |

### OH_CloudDisk_HydratePriority

```c
enum OH_CloudDisk_HydratePriority
```

**描述：**

水合优先级枚举值。

**起始版本：** 26.0.1

| 枚举项 | 描述 |
| -- | -- |
| OH_CLOUD_DISK_HYDRATE_PRIORITY_LOW = 0 | 低优先级。<br>**起始版本：** 26.0.1 |
| OH_CLOUD_DISK_HYDRATE_PRIORITY_NORMAL = 1 | 常规优先级。<br>**起始版本：** 26.0.1 |
| OH_CLOUD_DISK_HYDRATE_PRIORITY_HIGH = 2 | 高优先级。<br>**起始版本：** 26.0.1 |


## 函数说明

### OH_CloudDisk_RegisterSyncFolderChanges()

```c
CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, void (*callback)(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_ChangeData changeDatas[], size_t bufferLength))
```

**描述：**

应用注册一个回调函数，用于获取同步根路径下文件的变更。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| onst CloudDisk_SyncFolderPath syncFolderPath | 表示同步根路径，参考：[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)。 |
| void (*callback)(const CloudDisk_SyncFolderPath syncFolderPath | 注册的回调函数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_UnregisterSyncFolderChanges()

```c
CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath)
```

**描述：**

应用取消注册同步根路径下文件变更的回调。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 表示同步根路径，参考：[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_GetSyncFolderChanges()

```c
CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, uint64_t startUsn, size_t count, CloudDisk_ChangesResult **changesResult)
```

**描述：**

获取同步根路径下的历史操作记录。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 查询的同步根路径，参考：[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)。 |
| uint64_t startUsn | 查询起始的变更序列，范围：[0, 2^64 - 1]。 |
| size_t count | 查询文件变更的数量，范围：[1, 100]。 |
| [CloudDisk_ChangesResult](capi-clouddisk-clouddisk-changesresult.md) **changesResult | 表示查询文件变更的结果。详情请参阅[CloudDisk_ChangesResult](capi-clouddisk-clouddisk-changesresult.md)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_SetFileSyncStates()

```c
CloudDisk_ErrorCode OH_CloudDisk_SetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_FileSyncState fileSyncStates[], size_t bufferLength, CloudDisk_FailedList **failedLists, size_t *failedCount)
```

**描述：**

应用设置同步根路径下文件的同步状态。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 待设置的同步根路径，参考：[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)。 |
| [const CloudDisk_FileSyncState](capi-clouddisk-clouddisk-filesyncstate.md) fileSyncStates[] | The array of [CloudDisk_FileSyncState](capi-clouddisk-clouddisk-filesyncstate.md) specifying the file paths and their target sync states. |
| size_t bufferLength | 待设置同步状态数组的长度，范围：[1, 100]。 |
| [CloudDisk_FailedList](capi-clouddisk-clouddisk-failedlist.md) **failedLists | 输出参数。返回一个指向[CloudDisk_FailedList](capi-clouddisk-clouddisk-failedlist.md)数组的指针，该数组包含设置失败的文件。 |
| size_t *failedCount | 输出参数。设置同步状态失败的文件列表数组长度。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_GetFileSyncStates()

```c
CloudDisk_ErrorCode OH_CloudDisk_GetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo paths[], size_t bufferLength, CloudDisk_ResultList **resultLists, size_t *resultCount)
```

**描述：**

应用查询同步根路径下文件同步状态。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 待查询的同步根路径，参考：[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)。 |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) paths[] | The array of file paths to query. |
| size_t bufferLength | 待查询同步状态的数组的长度，范围：[1, 100]。 |
| [CloudDisk_ResultList](capi-clouddisk-clouddisk-resultlist.md) **resultLists | 输出参数。返回一个查询到的文件同步操作结果，详情可参考：[CloudDisk_ResultList](capi-clouddisk-clouddisk-resultlist.md)。 |
| size_t *resultCount | 输出参数。返回失败的文件数量。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_RegisterSyncFolder()

```c
CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolder(const CloudDisk_SyncFolder *syncFolder)
```

**描述：**

应用注册同步根。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md) *syncFolder | 待注册的同步根路径，参考：[CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_UnregisterSyncFolder()

```c
CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)
```

**描述：**

应用取消注册同步根。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 需要取消注册的同步根路径，参考：[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_ActiveSyncFolder()

```c
CloudDisk_ErrorCode OH_CloudDisk_ActiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)
```

**描述：**

应用激活同步根。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 需要激活监听的同步根路径，参考：[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_DeactiveSyncFolder()

```c
CloudDisk_ErrorCode OH_CloudDisk_DeactiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)
```

**描述：**

应用取消激活同步根。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 取消激活监听的同步根路径，参考：[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_GetSyncFolders()

```c
CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolders(CloudDisk_SyncFolder **syncFolders, size_t *count)
```

**描述：**

应用获取所有同步根。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md) **syncFolders | 输出参数。返回同步根路径数组[CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md)。 |
| size_t *count | 输出参数。当前网盘注册的所有同步根的数量。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_UpdateCustomAlias()

```c
CloudDisk_ErrorCode OH_CloudDisk_UpdateCustomAlias(const CloudDisk_SyncFolderPath syncFolderPath, const char *customAlias, size_t customAliasLength)
```

**描述：**

应用更新同步根别名。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 待更新别名的同步根路径，参考：[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)。 |
| const char *customAlias | 用户定义的别名，不能包含字符：\\\/\*\?\<\>\|\:\"，以及不能以"."、".."和纯空格作为完整名称。 |
| size_t customAliasLength | 用户定义的别名长度，范围：[0, 255]。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_CreatePlaceholder()

```c
CloudDisk_ErrorCode OH_CloudDisk_CreatePlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, const OH_CloudDisk_PlaceholderInfo placeholderInfo)
```

**描述：**

在已注册的同步文件夹中创建占位符。

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 已注册同步根路径。 |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | 同步根内相对路径。 |
| [const OH_CloudDisk_PlaceholderInfo](capi-clouddisk-oh-clouddisk-placeholderinfo.md) placeholderInfo | 占位符文件元数据信息。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，则返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；<br>否则返回[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_IsPlaceholderFile()

```c
CloudDisk_ErrorCode OH_CloudDisk_IsPlaceholderFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, bool *isPlaceholder)
```

**描述：**

检查同步根中的文件是否为占位符文件。

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 已注册同步根路径。 |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | 同步根内相对路径。 |
| bool *isPlaceholder | 输出参数。仅当返回值为[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)时有效。 如果文件是占位符文件，则返回true；否则返回false。错误时设置为false。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，则返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；<br>否则返回[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_ConvertPlaceholderToFile()

```c
CloudDisk_ErrorCode OH_CloudDisk_ConvertPlaceholderToFile(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo)
```

**描述：**

将占位符文件转换为0字节普通文件。

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 已注册同步根路径。 |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | 同步根内相对路径。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，则返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；<br>否则返回[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_UpdatePlaceholder()

```c
CloudDisk_ErrorCode OH_CloudDisk_UpdatePlaceholder(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo relativePathInfo, const OH_CloudDisk_PlaceholderInfo placeholderInfo)
```

**描述：**

更新文件元数据（支持占位符和普通文件）。

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 已注册同步根路径。 |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | 同步根内相对路径。 |
| [const OH_CloudDisk_PlaceholderInfo](capi-clouddisk-oh-clouddisk-placeholderinfo.md) placeholderInfo | 占位符文件元数据信息。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，则返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；<br>否则返回[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_RegisterCallbackTable()

```c
CloudDisk_ErrorCode OH_CloudDisk_RegisterCallbackTable(const CloudDisk_SyncFolderPath syncFolderPath, void (*callback)(const OH_CloudDisk_CallbackReqHead reqHead, OH_CloudDisk_CallbackContext reqContext))
```

**描述：**

注册用于水合和脱水请求的回调表。

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| onst CloudDisk_SyncFolderPath syncFolderPath | [in] 已注册同步根路径。 |
| void (*callback)(const OH_CloudDisk_CallbackReqHead reqHead | [in] 注册的回调函数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，则返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；<br>否则返回[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

**参考：**

[OH_CloudDisk_UnregisterCallbackTable](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_unregistercallbacktable)


### OH_CloudDisk_UnregisterCallbackTable()

```c
CloudDisk_ErrorCode OH_CloudDisk_UnregisterCallbackTable(const CloudDisk_SyncFolderPath syncFolderPath)
```

**描述：**

取消注册用于水合和脱水请求的回调表。

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | [in] 已注册同步根路径。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，则返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；<br>否则返回[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_Execute()

```c
CloudDisk_ErrorCode OH_CloudDisk_Execute(const OH_CloudDisk_CallbackReqHead reqHead, OH_CloudDisk_CallbackContext reqContext, OH_CloudDisk_CallbackResponse rsp)
```

**描述：**

响应回调请求。

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_CloudDisk_CallbackReqHead](capi-clouddisk-oh-clouddisk-callbackreqhead.md) reqHead | [in] 回调请求头。 |
| [OH_CloudDisk_CallbackContext](capi-clouddisk-oh-clouddisk-callbackcontext.md) reqContext | [in] 回调请求上下文。 |
| [OH_CloudDisk_CallbackResponse](capi-clouddisk-oh-clouddisk-callbackresponse.md) rsp | [in] 回调响应。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，则返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；<br>否则返回[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_HydratePlaceholder()

```c
CloudDisk_ErrorCode OH_CloudDisk_HydratePlaceholder(const CloudDisk_SyncFolderPath *syncFolderPath, const CloudDisk_PathInfo *filePath, OH_CloudDisk_CallbackType type, OH_CloudDisk_HydratePriority priority)
```

**描述：**

主动水合占位符文件或取消水合。

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath *syncFolderPath | [in] 已注册同步根路径。 |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) *filePath | [in] 同步根内相对路径。 |
| [OH_CloudDisk_CallbackType](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_callbacktype) type | [in] 水合或取消水合的回调类型。 |
| [OH_CloudDisk_HydratePriority](capi-oh-cloud-disk-manager-h.md#oh_clouddisk_hydratepriority) priority | [in] 水合优先级。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，则返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；<br>否则返回[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_DehydrateFile()

```c
CloudDisk_ErrorCode OH_CloudDisk_DehydrateFile(const CloudDisk_SyncFolderPath *syncFolderPath, const CloudDisk_PathInfo *filePath)
```

**描述：**

对完全水合的占位符文件执行脱水。

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath *syncFolderPath | [in] 已注册同步根路径。 |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) *filePath | [in] 同步根内相对路径。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，则返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；<br>否则返回[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_RegisterSyncFolderEx()

```c
CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolderEx(const OH_CloudDisk_SyncFolderEx *syncFolder)
```

**描述：**

使用占位符支持信息注册同步文件夹。

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_CloudDisk_SyncFolderEx](capi-clouddisk-oh-clouddisk-syncfolderex.md) *syncFolder | 指示具有占位符支持的同步文件夹。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果操作成功，则返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；<br> 否则返回[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)中定义的错误代码。 |

### OH_CloudDisk_GetSyncFoldersEx()

```c
CloudDisk_ErrorCode OH_CloudDisk_GetSyncFoldersEx(OH_CloudDisk_SyncFolderEx **syncFolders, size_t *count)
```

**描述：**

获取具有占位符支持信息的同步文件夹。

**起始版本：** 26.0.1

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_CloudDisk_SyncFolderEx](capi-clouddisk-oh-clouddisk-syncfolderex.md) **syncFolders | 输出参数。 <br> 返回[OH_CloudDisk_SyncFolderEx](capi-clouddisk-oh-clouddisk-syncfolderex.md)的数组，用于存储同步文件夹。 |
| size_t *count | 输出参数。返回同步文件夹的数量。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果操作成功，则返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；<br> 否则返回[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)中定义的错误代码。 |


