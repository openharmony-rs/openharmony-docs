# oh_swapfs.h

## 概述

Defines the native APIs for swapfs.

**库：** libohswapfs.so

**系统能力：** SystemCapability.FileManagement.File.Swapfs

**起始版本：** 26.0.0

**相关模块：** [Swapfs](capi-swapfs.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_SwapfsConfig](capi-swapfs-oh-swapfsconfig.md) | OH_SwapfsConfig | 创建swapfs管理器的配置。 |
| [OH_SwapfsSwapOutRequest](capi-swapfs-oh-swapfsswapoutrequest.md) | OH_SwapfsSwapOutRequest | 换出操作请求参数。 |
| [OH_SwapfsSwapInRequest](capi-swapfs-oh-swapfsswapinrequest.md) | OH_SwapfsSwapInRequest | 换入操作的请求参数。 |
| [OH_SwapfsDataInfo](capi-swapfs-oh-swapfsdatainfo.md) | OH_SwapfsDataInfo | 单个swap key的信息。 |
| [OH_SwapfsStats](capi-swapfs-oh-swapfsstats.md) | OH_SwapfsStats | 当前swapfs管理器的统计信息。 |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager.md) | OH_SwapfsManager | 该结构体用于执行swapfs manager的相关操作。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_SwapfsKeyStatus](#oh_swapfskeystatus) | OH_SwapfsKeyStatus | 定义swap key的状态。 |
| [OH_SwapfsDisableReason](#oh_swapfsdisablereason) | OH_SwapfsDisableReason | 定义了禁用换出特性的原因。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| SWAPFS_DIO_ALIGNMENT 4096U | Direct IO缓冲区的最低对齐要求。<br>**起始版本：** 26.0.0 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_Swapfs_ErrCode OH_Swapfs_CreateManager(const OH_SwapfsConfig *config, OH_SwapfsManager **manager)](#oh_swapfs_createmanager) | 创建swapfs管理器。 |
| [OH_Swapfs_ErrCode OH_Swapfs_DestroyManager(OH_SwapfsManager *manager)](#oh_swapfs_destroymanager) | 销毁swapfs管理器并释放所有资源。该功能进入关闭状态，拒绝新的换出、换入、移除、和remove-all操作。它最多等待5秒，以便活动操作完成。如果所有操作在超时时间内完成，则管理器拥有的所有交换数据自动删除，管理器被销毁。如果等待超时，此函数取消关闭状态并返回SWAPFS_E_BUSY；调用者可以稍后重试。 |
| [OH_Swapfs_ErrCode OH_Swapfs_SwapOut(OH_SwapfsManager *manager, const OH_SwapfsSwapOutRequest *request, uint64_t *keyId)](#oh_swapfs_swapout) | 将数据从内存交换到磁盘。当config.useDirectIo为false时，使用缓冲IO。如果为true，则需要直接IO和未对齐的缓冲区会导致错误。在DIO模式下，交换文件的大小被填充为SWAPFS_DIO_ALIGNMENT（大于等于dataSize）。 |
| [OH_Swapfs_ErrCode OH_Swapfs_SwapIn(OH_SwapfsManager *manager, const OH_SwapfsSwapInRequest *request, uint64_t *readSize)](#oh_swapfs_swapin) | 将数据从磁盘交换回内存。在DIO模式下，缓冲区地址和大小必须对齐SWAPFS_DIO_ALIGNMENT。bufferSize必须大于或等于占用的大小。在缓冲模式下，bufferSize必须大于或等于dataSize。成功后，readSize会收到原dataSize（不占用）。 |
| [OH_Swapfs_ErrCode OH_Swapfs_QueryData(OH_SwapfsManager *manager, uint64_t keyId, OH_SwapfsDataInfo *info)](#oh_swapfs_querydata) | 查询指定swap key的信息。 |
| [OH_Swapfs_ErrCode OH_Swapfs_GetStats(OH_SwapfsManager *manager, OH_SwapfsStats *stats)](#oh_swapfs_getstats) | 获取当前swapfs管理器的统计信息。 |
| [OH_Swapfs_ErrCode OH_Swapfs_RemoveData(OH_SwapfsManager *manager, uint64_t keyId)](#oh_swapfs_removedata) | 逻辑删除指定的swap key。键被标记为立即删除状态。现有的换入操作仍然可以完成。在此密钥上进行新的换入或查询操作将返回SWAPFS_E_KEY_STATE_INVALID。对于并发的swap-in操作，该函数不会返回SWAPFS_E_BUSY。 |
| [OH_Swapfs_ErrCode OH_Swapfs_RemoveAllData(OH_SwapfsManager *manager)](#oh_swapfs_removealldata) | 删除管理器中的所有交换密钥。如果有正在进行的活动操作（换出或换入），或者有任何键在状态，此函数返回SWAPFS_E_BUSY，而不启动任何删除。 |

## 枚举类型说明

### OH_SwapfsKeyStatus

```c
enum OH_SwapfsKeyStatus
```

**描述**

定义swap key的状态。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_SWAPFS_KEY_STATUS_ACTIVE = 0 | key处于活动状态，可用于换入、查询或删除。<br>**起始版本：** 26.0.0 |
| OH_SWAPFS_KEY_STATUS_REMOVING = 1 | key被逻辑删除。新的换入或查询操作将被拒绝。<br>**起始版本：** 26.0.0 |

### OH_SwapfsDisableReason

```c
enum OH_SwapfsDisableReason
```

**描述**

定义了禁用换出特性的原因。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_SWAPFS_DISABLE_REASON_NONE = 0 | 功能已启用（无禁用原因）。<br>**起始版本：** 26.0.0 |
| OH_SWAPFS_DISABLE_REASON_NOSPC = 1 | 设备存储空间不足。<br>**起始版本：** 26.0.0 |


## 函数说明

### OH_Swapfs_CreateManager()

```c
OH_Swapfs_ErrCode OH_Swapfs_CreateManager(const OH_SwapfsConfig *config, OH_SwapfsManager **manager)
```

**描述**

创建swapfs管理器。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [const OH_SwapfsConfig](capi-swapfs-oh-swapfsconfig.md) *config | 【in】指向配置的指针，若为NULL则使用默认配置（默认临时目录，1GB限制，useDirectIo=false）。 |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager.md) **manager | 【out】接收创建的OH_SwapfsManager句柄的指针。不能为NULL。失败时，指向的值被设置为NULL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h.md#oh_swapfs_errcode) | 返回执行的错误代码。<br> <ul><br> <li>[SWAPFS_E_OK](capi-swapfs-errcode-h.md#oh_swapfs_errcode)执行成功</li><br> <li>[SWAPFS_E_INVAL](capi-swapfs-errcode-h.md#oh_swapfs_errcode)管理器为空。</li><br> <li>[SWAPFS_E_IO_ERROR](capi-swapfs-errcode-h.md#oh_swapfs_errcode)内存分配失败。</li><br> 交换根路径的<li>[SWAPFS_E_ACCES](capi-swapfs-errcode-h.md#oh_swapfs_errcode)权限被拒绝。</li><br> <li>[SWAPFS_E_PATH_UNAVAILABLE](capi-swapfs-errcode-h.md#oh_swapfs_errcode)交换根路径无法创建。</li><br> <li>202如果非系统应用程序调用此系统API。</li><br> </ul> |

### OH_Swapfs_DestroyManager()

```c
OH_Swapfs_ErrCode OH_Swapfs_DestroyManager(OH_SwapfsManager *manager)
```

**描述**

销毁swapfs管理器并释放所有资源。该功能进入关闭状态，拒绝新的换出、换入、移除、和remove-all操作。它最多等待5秒，以便活动操作完成。如果所有操作在超时时间内完成，则管理器拥有的所有交换数据自动删除，管理器被销毁。如果等待超时，此函数取消关闭状态并返回SWAPFS_E_BUSY；调用者可以稍后重试。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager.md) *manager | 【in】指向要销毁的OH_SwapfsManager对象的指针。不能为NULL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h.md#oh_swapfs_errcode) | 返回执行的错误码。<br> <ul><br> <li>[SWAPFS_E_OK](capi-swapfs-errcode-h.md#oh_swapfs_errcode)执行成功</li><br> <li>[SWAPFS_E_INVAL](capi-swapfs-errcode-h.md#oh_swapfs_errcode)管理器为空。</li><br> <li>[SWAPFS_E_BUSY](capi-swapfs-errcode-h.md#oh_swapfs_errcode)有正在进行的活动操作。</li><br> <li>202如果非系统应用程序调用此系统API。</li><br> </ul> |

### OH_Swapfs_SwapOut()

```c
OH_Swapfs_ErrCode OH_Swapfs_SwapOut(OH_SwapfsManager *manager, const OH_SwapfsSwapOutRequest *request, uint64_t *keyId)
```

**描述**

将数据从内存交换到磁盘。当config.useDirectIo为false时，使用缓冲IO。如果为true，则需要直接IO和未对齐的缓冲区会导致错误。在DIO模式下，交换文件的大小被填充为SWAPFS_DIO_ALIGNMENT（大于等于dataSize）。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager.md) *manager | 【in】指向OH_SwapfsManager对象的指针。不能为NULL。 |
| [const OH_SwapfsSwapOutRequest](capi-swapfs-oh-swapfsswapoutrequest.md) *request | 【in】指针，指向换出请求，包含数据缓冲区及其大小。不能为NULL。 |
| uint64_t *keyId | 【out】接收此交换数据生成的keyId的指针。不能为NULL。失败时，指向的值不变。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h.md#oh_swapfs_errcode) | 返回执行的错误代码。<br> <ul><br> <li>[SWAPFS_E_OK](capi-swapfs-errcode-h.md#oh_swapfs_errcode)执行成功</li><br> <li>[SWAPFS_E_INVAL](capi-swapfs-errcode-h.md#oh_swapfs_errcode)管理器为nullptr，请求为nullptr, keyId为nullptr。<br> buffer为nullptr，或者bufferSize为0。</li><br> <li>[SWAPFS_E_DIO_ALIGN](capi-swapfs-errcode-h.md#oh_swapfs_errcode) useDirectIo为真且缓冲区未对齐。</li><br> <li>[SWAPFS_E_NOSPC](capi-swapfs-errcode-h.md#oh_swapfs_errcode)设备存储空间不足。</li><br> <li>[SWAPFS_E_QUOTA_EXCEEDED](capi-swapfs-errcode-h.md#oh_swapfs_errcode)超出交换空间配额。</li><br> <li>[SWAPFS_E_FEATURE_DISABLED](capi-swapfs-errcode-h.md#oh_swapfs_errcode)由于空间或策略不足而禁用了换出。</li><br> <li>[SWAPFS_E_IO_ERROR](capi-swapfs-errcode-h.md#oh_swapfs_errcode) IO写入失败。</li><br> <li>[SWAPFS_E_ACCES](capi-swapfs-errcode-h.md#oh_swapfs_errcode)权限被拒绝。</li><br> <li>[SWAPFS_E_BUSY](capi-swapfs-errcode-h.md#oh_swapfs_errcode) RemoveAllData正在进行或并发操作太多。</li><br> <li>{@link SWAPFS_E_SHUTING_DOWN}管理器正在关闭。</li><br> <li>202如果非系统应用程序调用此系统API。</li><br> </ul> |

### OH_Swapfs_SwapIn()

```c
OH_Swapfs_ErrCode OH_Swapfs_SwapIn(OH_SwapfsManager *manager, const OH_SwapfsSwapInRequest *request, uint64_t *readSize)
```

**描述**

将数据从磁盘交换回内存。在DIO模式下，缓冲区地址和大小必须对齐SWAPFS_DIO_ALIGNMENT。bufferSize必须大于或等于占用的大小。在缓冲模式下，bufferSize必须大于或等于dataSize。成功后，readSize会收到原dataSize（不占用）。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager.md) *manager | 【in】指向OH_SwapfsManager对象的指针。不能为NULL。 |
| [const OH_SwapfsSwapInRequest](capi-swapfs-oh-swapfsswapinrequest.md) *request | 【in】指针类型，指向swap-in请求，包含keyId、buffer和bufferSize。不能为NULL。 |
| uint64_t *readSize | 【out】以字节为单位接收原始数据大小的指针，如果调用者不需要它，则为NULL。成功时，接收原始的dataSize。失败时，指向的值不变。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h.md#oh_swapfs_errcode) | 返回执行的错误代码。<br> <ul><br> <li>[SWAPFS_E_OK](capi-swapfs-errcode-h.md#oh_swapfs_errcode)执行成功</li><br> <li>[SWAPFS_E_INVAL](capi-swapfs-errcode-h.md#oh_swapfs_errcode)管理器为nullptr，请求为nullptr, keyId为0，<br> buffer为nullptr，或者bufferSize为0。</li><br> <li>[SWAPFS_E_DIO_ALIGN](capi-swapfs-errcode-h.md#oh_swapfs_errcode)缓冲区地址或大小未与SWAPFS_DIO_ALIGNMENT对齐。</li><br> <li>[SWAPFS_E_BUFFER_TOO_SMALL](capi-swapfs-errcode-h.md#oh_swapfs_errcode) bufferSize小于所需的大小。</li><br> <li>[SWAPFS_E_KEY_NOT_FOUND](capi-swapfs-errcode-h.md#oh_swapfs_errcode) keyId不存在。</li><br> <li>[SWAPFS_E_KEY_STATE_INVALID](capi-swapfs-errcode-h.md#oh_swapfs_errcode)项处于删除状态。</li><br> <li>[SWAPFS_E_IO_ERROR](capi-swapfs-errcode-h.md#oh_swapfs_errcode) IO读取失败。</li><br> <li>[SWAPFS_E_ACCES](capi-swapfs-errcode-h.md#oh_swapfs_errcode)权限被拒绝。</li><br> <li>[SWAPFS_E_BUSY](capi-swapfs-errcode-h.md#oh_swapfs_errcode)并发操作过多。</li><br> <li>{@link SWAPFS_E_SHUTING_DOWN}管理器正在关闭。</li><br> <li>202如果非系统应用程序调用此系统API。</li><br> </ul> |

### OH_Swapfs_QueryData()

```c
OH_Swapfs_ErrCode OH_Swapfs_QueryData(OH_SwapfsManager *manager, uint64_t keyId, OH_SwapfsDataInfo *info)
```

**描述**

查询指定swap key的信息。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager.md) *manager | 【in】指向OH_SwapfsManager对象的指针。不能为NULL。 |
| uint64_t keyId | 【in】要查询的keyId。 |
| [OH_SwapfsDataInfo](capi-swapfs-oh-swapfsdatainfo.md) *info | 【out】指向OH_SwapfsDataInfo结构体的指针，用于接收key信息。不能为NULL。失败时，内容不变。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h.md#oh_swapfs_errcode) | 返回执行的错误码。<br> <ul><br> <li>[SWAPFS_E_OK](capi-swapfs-errcode-h.md#oh_swapfs_errcode)执行成功</li><br> <li>[SWAPFS_E_INVAL](capi-swapfs-errcode-h.md#oh_swapfs_errcode)管理器为nullptr, keyId为0，或者info为nullptr。</li><br> <li>[SWAPFS_E_KEY_NOT_FOUND](capi-swapfs-errcode-h.md#oh_swapfs_errcode) keyId不存在。</li><br> <li>[SWAPFS_E_KEY_STATE_INVALID](capi-swapfs-errcode-h.md#oh_swapfs_errcode)项处于删除状态。</li><br> <li>202如果非系统应用程序调用此系统API。</li><br> </ul> |

### OH_Swapfs_GetStats()

```c
OH_Swapfs_ErrCode OH_Swapfs_GetStats(OH_SwapfsManager *manager, OH_SwapfsStats *stats)
```

**描述**

获取当前swapfs管理器的统计信息。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager.md) *manager | 【in】指向OH_SwapfsManager对象的指针。不能为NULL。 |
| [OH_SwapfsStats](capi-swapfs-oh-swapfsstats.md) *stats | 【out】指向OH_SwapfsStats结构体的指针，用于接收统计信息。不能为NULL。失败时，内容不变。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h.md#oh_swapfs_errcode) | 返回执行的错误码。<br> <ul><br> <li>[SWAPFS_E_OK](capi-swapfs-errcode-h.md#oh_swapfs_errcode)执行成功</li><br> <li>[SWAPFS_E_INVAL](capi-swapfs-errcode-h.md#oh_swapfs_errcode)管理器为nullptr，或者stats为nullptr。</li><br> <li>202如果非系统应用程序调用此系统API。</li><br> </ul> |

### OH_Swapfs_RemoveData()

```c
OH_Swapfs_ErrCode OH_Swapfs_RemoveData(OH_SwapfsManager *manager, uint64_t keyId)
```

**描述**

逻辑删除指定的swap key。键被标记为立即删除状态。现有的换入操作仍然可以完成。在此密钥上进行新的换入或查询操作将返回SWAPFS_E_KEY_STATE_INVALID。对于并发的swap-in操作，该函数不会返回SWAPFS_E_BUSY。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager.md) *manager | 【in】指向OH_SwapfsManager对象的指针。不能为NULL。 |
| uint64_t keyId | 【in】要删除的keyId。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h.md#oh_swapfs_errcode) | 返回执行的错误码。<br> <ul><br> <li>[SWAPFS_E_OK](capi-swapfs-errcode-h.md#oh_swapfs_errcode)如果执行成功</li><br> <li>[SWAPFS_E_INVAL](capi-swapfs-errcode-h.md#oh_swapfs_errcode)管理器为nullptr或keyId为0。</li><br> <li>[SWAPFS_E_KEY_NOT_FOUND](capi-swapfs-errcode-h.md#oh_swapfs_errcode) keyId不存在。</li><br> <li>[SWAPFS_E_KEY_STATE_INVALID](capi-swapfs-errcode-h.md#oh_swapfs_errcode)项已处于删除状态。</li><br> <li>[SWAPFS_E_BUSY](capi-swapfs-errcode-h.md#oh_swapfs_errcode)并发操作过多。</li><br> <li>{@link SWAPFS_E_SHUTING_DOWN}管理器正在关闭。</li><br> <li>202如果非系统应用程序调用此系统API。</li><br> </ul> |

### OH_Swapfs_RemoveAllData()

```c
OH_Swapfs_ErrCode OH_Swapfs_RemoveAllData(OH_SwapfsManager *manager)
```

**描述**

删除管理器中的所有交换密钥。如果有正在进行的活动操作（换出或换入），或者有任何键在状态，此函数返回SWAPFS_E_BUSY，而不启动任何删除。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager.md) *manager | 【in】指向OH_SwapfsManager对象的指针。不能为NULL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h.md#oh_swapfs_errcode) | 返回执行的错误码。<br> <ul><br> <li>[SWAPFS_E_OK](capi-swapfs-errcode-h.md#oh_swapfs_errcode)执行成功</li><br> <li>[SWAPFS_E_INVAL](capi-swapfs-errcode-h.md#oh_swapfs_errcode)管理器为空。</li><br> <li>[SWAPFS_E_BUSY](capi-swapfs-errcode-h.md#oh_swapfs_errcode)存在正在进行的活动操作或处于删除状态的挂起密钥。</li><br> <li>{@link SWAPFS_E_SHUTING_DOWN}管理器正在关闭。</li><br> <li>202如果非系统应用程序调用此系统API。</li><br> </ul> |


