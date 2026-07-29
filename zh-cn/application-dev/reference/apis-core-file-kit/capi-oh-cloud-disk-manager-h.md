# oh_cloud_disk_manager.h
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

## 概述

云盘管理模块的接口定义，提供云盘同步根路径的注册、激活、监听和查询能力，支持监听文件变更、设置和查询文件同步状态，适用于需要在应用内实现云盘文件同步和变更监听的场景。

**引用文件：** `<filemanagement/clouddiskmanager/oh_cloud_disk_manager.h>`

**库：** libohclouddiskmanager.so

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**起始版本：** 21

**相关模块：** [CloudDisk](capi-clouddisk.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) | CloudDisk_PathInfo/CloudDisk_FileIdInfo/CloudDisk_SyncFolderPath | CloudDisk_PathInfo：文件路径信息。<br> CloudDisk_FileIdInfo：定义的文件ID。<br> CloudDisk_SyncFolderPath：定义的同步根路径。 |
| [CloudDisk_FileSyncState](capi-clouddisk-clouddisk-filesyncstate.md) | CloudDisk_FileSyncState | 文件的同步状态。 |
| [CloudDisk_ChangeData](capi-clouddisk-clouddisk-changedata.md) | CloudDisk_ChangeData | 定义同步根路径下单个文件变更事件的数据结构，包含更新序列号、文件ID、父目录ID、相对路径、变更类型、文件大小和时间信息。 |
| [CloudDisk_ChangesResult](capi-clouddisk-clouddisk-changesresult.md) | CloudDisk_ChangesResult | 查询同步根路径中文件变更的结果，包含下一次可查询的更新序列号、结尾标志以及变更数据项数组。 |
| [CloudDisk_FailedList](capi-clouddisk-clouddisk-failedlist.md) | CloudDisk_FailedList | 同步操作中失败的文件列表信息。该结构包含文件路径信息以及失败的具体错误原因。 |
| [CloudDisk_ResultList](capi-clouddisk-clouddisk-resultlist.md) | CloudDisk_ResultList | 表示一个文件同步操作的结果，包含文件路径信息、操作结果、同步状态或失败原因。 |
| [CloudDisk_DisplayNameInfo](capi-clouddisk-clouddisk-displaynameinfo.md) | CloudDisk_DisplayNameInfo | 定义同步根路径的显示名称信息。 |
| [CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md) | CloudDisk_SyncFolder | 同步根路径属性信息。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [CloudDisk_SyncState](#clouddisk_syncstate) | CloudDisk_SyncState | 文件同步状态的枚举值。 |
| [CloudDisk_OperationType](#clouddisk_operationtype) | CloudDisk_OperationType | 文件变更类型枚举值。 |
| [CloudDisk_ErrorReason](#clouddisk_errorreason) | CloudDisk_ErrorReason | 文件同步失败原因的枚举值。 |
| [CloudDisk_SyncFolderState](#clouddisk_syncfolderstate) | CloudDisk_SyncFolderState | 同步根路径状态的枚举值。 |

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

## 枚举类型说明

### CloudDisk_SyncState

```c
enum CloudDisk_SyncState
```

**描述**

文件同步状态的枚举值。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| IDLE = 0 | 目前处于空闲状态，未执行任何同步操作。 |
| SYNCING = 1 | 文件正在同步。 |
| SYNC_SUCCEEDED = 2 | 文件同步成功。 |
| SYNC_FAILED = 3 | 文件同步失败。 |
| SYNC_CANCELED = 4 | 文件同步取消。 |
| SYNC_CONFLICTED = 5 | 文件同步冲突。 |

### CloudDisk_OperationType

```c
enum CloudDisk_OperationType
```

**描述**

文件变更类型枚举值。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| CREATE = 0 | 创建文件或目录。 |
| DELETE = 1 | 删除文件或目录。 |
| MOVE_FROM = 2 | 文件或目录被移出。 |
| MOVE_TO = 3 | 文件或目录被移入。 |
| CLOSE_WRITE = 4 | 在写入操作后关闭文件。 |
| SYNC_FOLDER_INVALID = 5 | 同步根路径无效。 |

### CloudDisk_ErrorReason

```c
enum CloudDisk_ErrorReason
```

**描述**

文件同步失败原因的枚举值。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| INVALID_ARGUMENT = 0 | 输入的参数无效。 |
| NO_SUCH_FILE = 1 | 操作的文件或目录不存在。 |
| NO_SPACE_LEFT = 2 | 设备上的剩余空间不足。 |
| OUT_OF_RANGE = 3 | 超出有效范围。 |
| NO_SYNC_STATE = 4 | 同步状态未设置。 |

### CloudDisk_SyncFolderState

```c
enum CloudDisk_SyncFolderState
```

**描述**

同步根路径状态的枚举值。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| INACTIVE = 0 | 表示同步根路径的状态是未激活的。 |
| ACTIVE = 1 | 表示同步根路径的状态是激活的。 |


## 函数说明

### OH_CloudDisk_RegisterSyncFolderChanges()

```c
CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, void (*callback)(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_ChangeData changeDatas[], size_t bufferLength))
```

**描述**

应用注册一个回调函数，用于获取同步根路径下文件的变更，适用于需要实时监听同步根路径下文件创建、删除、修改等变更事件的场景。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 表示同步根路径，参考：[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)。 |
| void (*callback)(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_ChangeData changeDatas[], size_t bufferLength) | 注册的回调函数。当同步根路径下文件发生变更时触发。syncFolderPath表示同步根路径，changeDatas表示文件变更数据数组，bufferLength表示数组长度。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_UnregisterSyncFolderChanges()

```c
CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath)
```

**描述**

应用取消注册同步根路径下文件变更的回调，适用于应用不再需要监听文件变更、切换账号或释放监听资源的场景。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 表示同步根路径，参考：[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_GetSyncFolderChanges()

```c
CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolderChanges(const CloudDisk_SyncFolderPath syncFolderPath, uint64_t startUsn, size_t count, CloudDisk_ChangesResult **changesResult)
```

**描述**

应用获取同步根路径下的历史操作记录，适用于按需查询文件变更历史、断线重连后恢复同步进度或排查同步问题的场景。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 查询的同步根路径，参考：[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)。 |
| uint64_t startUsn | 查询起始的变更序列号，用于指定从哪个变更记录开始查询。首次查询可设为0，后续查询可使用上次返回结果中的下一个序列号。取值范围：[0, 2^64 - 1]。 |
| size_t count | 查询文件变更的数量，取值范围：[1, 100]。 |
| [CloudDisk_ChangesResult](capi-clouddisk-clouddisk-changesresult.md) **changesResult | 输出参数，表示查询文件变更的结果。详情请参阅[CloudDisk_ChangesResult](capi-clouddisk-clouddisk-changesresult.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_SetFileSyncStates()

```c
CloudDisk_ErrorCode OH_CloudDisk_SetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_FileSyncState fileSyncStates[], size_t bufferLength, CloudDisk_FailedList **failedLists, size_t *failedCount)
```

**描述**

应用设置同步根路径下文件的同步状态，适用于需要手动控制文件同步行为的场景。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 待设置的同步根路径，参考：[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)。 |
| [const CloudDisk_FileSyncState](capi-clouddisk-clouddisk-filesyncstate.md) fileSyncStates[] | 指定文件路径及其目标同步状态的[CloudDisk_FileSyncState](capi-clouddisk-clouddisk-filesyncstate.md)数组。 |
| size_t bufferLength | 待设置同步状态数组的长度，取值范围：[1, 100]。 |
| [CloudDisk_FailedList](capi-clouddisk-clouddisk-failedlist.md) **failedLists | 输出参数。返回一个指向[CloudDisk_FailedList](capi-clouddisk-clouddisk-failedlist.md)数组的指针，该数组包含设置失败的文件。 |
| size_t *failedCount | 输出参数。返回设置同步状态失败的文件数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_GetFileSyncStates()

```c
CloudDisk_ErrorCode OH_CloudDisk_GetFileSyncStates(const CloudDisk_SyncFolderPath syncFolderPath, const CloudDisk_PathInfo paths[], size_t bufferLength, CloudDisk_ResultList **resultLists, size_t *resultCount)
```

**描述**

应用查询同步根路径下文件同步状态，适用于需要在界面显示同步状态、判断文件是否已完成同步或检查文件同步是否失败的场景。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 待查询的同步根路径，参考：[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)。 |
| [const CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) paths[] | 待查询同步状态[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)的数组。 |
| size_t bufferLength | 待查询同步状态的数组的长度，取值范围：[1, 100]。 |
| [CloudDisk_ResultList](capi-clouddisk-clouddisk-resultlist.md) **resultLists | 输出参数。返回一个查询到的文件同步操作结果，详情可参考：[CloudDisk_ResultList](capi-clouddisk-clouddisk-resultlist.md)。 |
| size_t *resultCount | 输出参数。返回查询结果的数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_RegisterSyncFolder()

```c
CloudDisk_ErrorCode OH_CloudDisk_RegisterSyncFolder(const CloudDisk_SyncFolder *syncFolder)
```

**描述**

应用注册同步根，适用于需要将本地目录设置为云盘同步目录的场景。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md) *syncFolder | 待注册的同步根路径，参考：[CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_UnregisterSyncFolder()

```c
CloudDisk_ErrorCode OH_CloudDisk_UnregisterSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)
```

**描述**

应用取消注册同步根，适用于需要移除云盘同步目录的场景。通常在取消激活同步根后调用。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 需要取消注册的同步根路径，参考：[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_ActiveSyncFolder()

```c
CloudDisk_ErrorCode OH_CloudDisk_ActiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)
```

**描述**

应用激活同步根，适用于需要开始或恢复同步文件的场景。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 需要激活监听的同步根路径，参考：[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_DeactiveSyncFolder()

```c
CloudDisk_ErrorCode OH_CloudDisk_DeactiveSyncFolder(const CloudDisk_SyncFolderPath syncFolderPath)
```

**描述**

应用取消激活同步根，适用于需要暂停同步文件或释放同步资源的场景。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 取消激活监听的同步根路径，参考：[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_GetSyncFolders()

```c
CloudDisk_ErrorCode OH_CloudDisk_GetSyncFolders(CloudDisk_SyncFolder **syncFolders, size_t *count)
```

**描述**

应用获取所有同步根，适用于查询当前已注册的同步目录、展示同步目录列表或恢复同步状态的场景。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md) **syncFolders | 输出参数。返回同步根路径数组[CloudDisk_SyncFolder](capi-clouddisk-clouddisk-syncfolder.md)。 |
| size_t *count | 输出参数。当前应用注册的同步根数量。当没有同步根时为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |

### OH_CloudDisk_UpdateCustomAlias()

```c
CloudDisk_ErrorCode OH_CloudDisk_UpdateCustomAlias(const CloudDisk_SyncFolderPath syncFolderPath, const char *customAlias, size_t customAliasLength)
```

**描述**

应用更新同步根别名，适用于需要为同步目录设置自定义显示名称、区分多个同步目录或在界面显示友好目录名称的场景。

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const CloudDisk_SyncFolderPath syncFolderPath | 待更新别名的同步根路径，参考：[CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md)。 |
| const char *customAlias | 用户自定义的同步根别名，用于在界面上显示和标识不同的同步根，便于用户识别和管理。别名不能包含以下字符：\\\/\*\?\<\>\|\:\"。名称不能为"."、".."或纯空格。 |
| size_t customAliasLength | 用户定义的别名长度，取值范围：[0, 255]。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode) | 如果接口调用成功，返回[CLOUD_DISK_OK](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)；否则返回云盘管理模块的错误码[CloudDisk_ErrorCode](capi-cloud-disk-error-code-h.md#clouddisk_errorcode)。 |


