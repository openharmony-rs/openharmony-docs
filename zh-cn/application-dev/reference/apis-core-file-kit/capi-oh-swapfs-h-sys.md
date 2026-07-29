# oh_swapfs.h (系统接口)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->

## 概述

定义swapfs（交换文件系统）的native API，提供文件系统交换空间的创建、挂载、卸载等操作接口。<br> swapfs模块用于管理和监控应用的swap分区使用情况。<br> 该模块支持交换空间的创建、挂载、卸载等操作，适用于需要优化内存管理、提升应用运行性能的场景。<br> 支持将数据换出到磁盘并进行管理，在后续需要取回时换入，来实现对内存的灵活管理与性能提升。<br> 该模块能够帮助开发者有效利用系统swap资源，改善内存不足情况下的应用体验。

**引用文件：** <filemanagement/swapfs/oh_swapfs.h>

**库：** libohswapfs.so

**系统能力：** SystemCapability.FileManagement.File.Swapfs

**起始版本：** 26.0.0

**相关模块：** [Swapfs](capi-swapfs-sys.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_SwapfsConfig](capi-swapfs-oh-swapfsconfig-sys.md) | OH_SwapfsConfig | 用于配置swapfs管理器的初始化参数，包括数据存储路径、空间限制和IO方式等。 |
| [OH_SwapfsSwapOutRequest](capi-swapfs-oh-swapfsswapoutrequest-sys.md) | OH_SwapfsSwapOutRequest | 换出操作的请求参数。用于在应用需要释放内存时，主动触发数据换出到交换分区的场景，例如内存紧张时将部分数据临时换出。 |
| [OH_SwapfsSwapInRequest](capi-swapfs-oh-swapfsswapinrequest-sys.md) | OH_SwapfsSwapInRequest | 换入操作的请求参数。该结构体用于描述换入操作所需的参数，包括换出时返回的keyId、接收换入数据的缓冲区及其大小。<br> 开发者需通过[OH_Swapfs_SwapOut](#oh_swapfs_swapout)获取keyId，再使用本结构体中的参数调用换入接口将数据换入内存。 |
| [OH_SwapfsDataInfo](capi-swapfs-oh-swapfsdatainfo-sys.md) | OH_SwapfsDataInfo | 单个key的信息。用于在应用需要精确管理换出数据条目的元信息时（如查询换出状态、监控换出大小等）。 |
| [OH_SwapfsStats](capi-swapfs-oh-swapfsstats-sys.md) | OH_SwapfsStats | OH_SwapfsStats用于获取swapfs管理器的统计信息，包括活跃key数量、数据大小、空间使用情况等。<br> 适用于需要监控swapfs状态、分析存储使用情况的场景，帮助开发者了解系统的交换空间使用情况。 |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) | OH_SwapfsManager | 该结构体用于执行与swapfs管理器交互相关的操作。使用前需通过[OH_Swapfs_CreateManager](#oh_swapfs_createmanager)函数创建有效的管理器实例。<br> 该结构体用于管理swapfs的生命周期和配置，提供交换分区的创建、销毁、扩展等管理能力。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_SwapfsKeyStatus](#oh_swapfskeystatus) | OH_SwapfsKeyStatus | 被swapfs换出的数据将以key（换出数据交换单元）的形式被swapfs管理，该枚举定义已经被swapfs换出的key的状态。 |
| [OH_SwapfsDisableReason](#oh_swapfsdisablereason) | OH_SwapfsDisableReason | 定义换出功能被禁用的原因。仅在featureEnabled为false时有效。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| SWAPFS_DIO_ALIGNMENT 4096U | Direct I/O（直接I/O）缓冲区的最小对齐要求。<br>**起始版本：** 26.0.0 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [`OH_Swapfs_ErrCode`](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) [`OH_Swapfs_CreateManager(const OH_SwapfsConfig *config, OH_SwapfsManager **manager)`](#oh_swapfs_createmanager) | 创建swapfs管理器 |
| [`OH_Swapfs_ErrCode`](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) [`OH_Swapfs_DestroyManager(OH_SwapfsManager *manager)`](#oh_swapfs_destroymanager) | 销毁swapfs管理器并释放所有资源。<br> 等待最多5s以使操作完成。如果所有操作在等待时间内完成，管理器拥有的所有交换数据将被自动删除，管理器将被销毁。<br> 如果等待超时，此函数取消关闭状态并返回[SWAPFS_E_BUSY](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)；调用方可稍后重试。<br> 操作完成后，该功能进入关闭状态，拒绝新的[OH_Swapfs_SwapOut](capi-oh-swapfs-h-sys.md#oh_swapfs_swapout)、[OH_Swapfs_SwapIn](capi-oh-swapfs-h-sys.md#oh_swapfs_swapin)、[OH_Swapfs_RemoveData](capi-oh-swapfs-h-sys.md#oh_swapfs_removedata)和[OH_Swapfs_RemoveAllData](capi-oh-swapfs-h-sys.md#oh_swapfs_removealldata)操作。 |
| [`OH_Swapfs_ErrCode`](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) [`OH_Swapfs_SwapOut(OH_SwapfsManager *manager, const OH_SwapfsSwapOutRequest *request, uint64_t *keyId)`](#oh_swapfs_swapout) | 将数据从内存换出到磁盘。<br> 当[OH_SwapfsConfig](capi-swapfs-oh-swapfsconfig-sys.md)中的useDirectIo为false时，使用缓冲IO。为true时，要求使用Direct I/O，未对齐的缓冲区将导致错误。<br> 在Direct I/O模式下，换出文件大小会被填充到SWAPFS_DIO_ALIGNMENT（occupiedSize大于等于dataSize）。 |
| [`OH_Swapfs_ErrCode`](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) [`OH_Swapfs_SwapIn(OH_SwapfsManager *manager, const OH_SwapfsSwapInRequest *request, uint64_t *readSize)`](#oh_swapfs_swapin) | 将数据从磁盘换入内存。<br> 在Direct I/O模式下，缓冲区地址和大小必须对齐到SWAPFS_DIO_ALIGNMENT，且bufferSize必须大于等于occupiedSize。<br> 在缓冲模式下，bufferSize必须大于等于dataSize。<br> 成功时，readSize接收原始dataSize（非occupiedSize）。 |
| [`OH_Swapfs_ErrCode`](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) [`OH_Swapfs_QueryData(OH_SwapfsManager *manager, uint64_t keyId, OH_SwapfsDataInfo *info)`](#oh_swapfs_querydata) | 查询特定swapfs key的信息，包括key的状态、数据大小等。 |
| [`OH_Swapfs_ErrCode`](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) [`OH_Swapfs_GetStats(OH_SwapfsManager *manager, OH_SwapfsStats *stats)`](#oh_swapfs_getstats) | 获取当前swapfs管理器的统计信息。 |
| [`OH_Swapfs_ErrCode`](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) [`OH_Swapfs_RemoveData(OH_SwapfsManager *manager, uint64_t keyId)`](#oh_swapfs_removedata) | 逻辑删除指定的swapfs key。触发后key立即被标记OH_SWAPFS_KEY_STATUS_REMOVING状态。<br> 触发时若已有[OH_Swapfs_SwapIn](capi-oh-swapfs-h-sys.md#oh_swapfs_swapin)操作则仍可完成swapin，完成后开始删除。<br> 开始删除后，对该key的新[OH_Swapfs_SwapIn](capi-oh-swapfs-h-sys.md#oh_swapfs_swapin)或[OH_Swapfs_QueryData](capi-oh-swapfs-h-sys.md#oh_swapfs_querydata)操作将返回[SWAPFS_E_KEY_STATE_INVALID](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)。 |
| [`OH_Swapfs_ErrCode`](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) [`OH_Swapfs_RemoveAllData(OH_SwapfsManager *manager)`](#oh_swapfs_removealldata) | 删除管理器中的所有swapfs key。<br> 如果存在进行中的操作（[OH_Swapfs_SwapOut](capi-oh-swapfs-h-sys.md#oh_swapfs_swapout)或[OH_Swapfs_SwapIn](capi-oh-swapfs-h-sys.md#oh_swapfs_swapin)），或任何key处于OH_SWAPFS_KEY_STATUS_REMOVING状态,<br> 此函数返回[SWAPFS_E_BUSY](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)而不开始任何删除操作。 |

## 枚举类型说明

### OH_SwapfsKeyStatus

```c
enum OH_SwapfsKeyStatus
```

**描述**

被swapfs换出的数据将以key（换出数据交换单元）的形式被swapfs管理，该枚举定义已经被swapfs换出的key的状态。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_SWAPFS_KEY_STATUS_ACTIVE = 0 | key处于活跃状态，可用于换入、查询或删除操作。<br>**起始版本：** 26.0.0 |
| OH_SWAPFS_KEY_STATUS_REMOVING = 1 | key已被删除。新的换入或查询操作将被拒绝。<br>**起始版本：** 26.0.0 |

### OH_SwapfsDisableReason

```c
enum OH_SwapfsDisableReason
```

**描述**

定义换出功能被禁用的原因。仅在featureEnabled为false时有效。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_SWAPFS_DISABLE_REASON_NONE = 0 | 换出功能已启用。<br>**起始版本：** 26.0.0 |
| OH_SWAPFS_DISABLE_REASON_NOSPC = 1 | 设备存储空间不足。<br>**起始版本：** 26.0.0 |

## 函数说明

### OH_Swapfs_CreateManager()

```c
OH_Swapfs_ErrCode OH_Swapfs_CreateManager(const OH_SwapfsConfig *config, OH_SwapfsManager **manager)
```

**描述**

创建swapfs管理器。

**系统能力：** SystemCapability.FileManagement.File.Swapfs

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| const [OH_SwapfsConfig](capi-swapfs-oh-swapfsconfig-sys.md) *config | 指向配置的指针，若为空指针，则config默认使用临时目录，spaceLimitBytes限制为1GB，useDirectIo为false。 |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) **manager | 双指针，用于接收创建的[OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md)句柄。不可为空指针。失败时，所指向的值被设置为空指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) | 返回执行的错误码。<br>         <ul><br>         <li>SWAPFS_E_OK：执行成功。</li><br>         <li>SWAPFS_E_INVAL：manager为空指针。</li><br>         <li>SWAPFS_E_NOMEM：内存分配失败。</li><br>         <li>SWAPFS_E_ACCES：换出根路径权限被拒绝。</li><br>         <li>SWAPFS_E_PATH_UNAVAILABLE：换出根路径无法创建。</li><br>         <li>202：非系统应用调用此系统API。请确保为系统应用。</li><br>         </ul> |

**参考：**

[OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)


### OH_Swapfs_DestroyManager()

```c
OH_Swapfs_ErrCode OH_Swapfs_DestroyManager(OH_SwapfsManager *manager)
```

**描述**

销毁swapfs管理器并释放所有资源。<br> 等待最多5s以使操作完成。如果所有操作在等待时间内完成，管理器拥有的所有交换数据将被自动删除，管理器将被销毁。<br> 如果等待超时，此函数取消关闭状态并返回[SWAPFS_E_BUSY](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)；调用方可稍后重试。<br> 操作完成后，该功能进入关闭状态，拒绝新的[OH_Swapfs_SwapOut](capi-oh-swapfs-h-sys.md#oh_swapfs_swapout)、[OH_Swapfs_SwapIn](capi-oh-swapfs-h-sys.md#oh_swapfs_swapin)、[OH_Swapfs_RemoveData](capi-oh-swapfs-h-sys.md#oh_swapfs_removedata)和[OH_Swapfs_RemoveAllData](capi-oh-swapfs-h-sys.md#oh_swapfs_removealldata)操作。

**系统能力：** SystemCapability.FileManagement.File.Swapfs

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | 指向待销毁的OH_SwapfsManager对象的指针。不可为空指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) | 返回执行的错误码。<br>         <ul><br>         <li>SWAPFS_E_OK：执行成功。</li><br>         <li>SWAPFS_E_INVAL：manager为空指针。</li><br>         <li>SWAPFS_E_BUSY：存在进行中的活跃操作。</li><br>         <li>202：非系统应用调用此系统API。请确保为系统应用。</li><br>         </ul> |

**参考：**

[OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)


### OH_Swapfs_SwapOut()

```c
OH_Swapfs_ErrCode OH_Swapfs_SwapOut(OH_SwapfsManager *manager, const OH_SwapfsSwapOutRequest *request, uint64_t *keyId)
```

**描述**

将数据从内存换出到磁盘。<br> 当[OH_SwapfsConfig](capi-swapfs-oh-swapfsconfig-sys.md)中的useDirectIo为false时，使用缓冲IO。为true时，要求使用Direct I/O，未对齐的缓冲区将导致错误。<br> 在Direct I/O模式下，换出文件大小会被填充到SWAPFS_DIO_ALIGNMENT（occupiedSize大于等于dataSize）。

**系统能力：** SystemCapability.FileManagement.File.Swapfs

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | 指向OH_SwapfsManager对象的指针。不可为空指针。 |
| const [OH_SwapfsSwapOutRequest](capi-swapfs-oh-swapfsswapoutrequest-sys.md) *request | 指向换出请求的指针，包含数据缓冲区及其大小。不可为空指针。 |
| uint64_t *keyId | 指向用于接收此换出数据生成的keyId的指针。不可为空指针。失败时，所指向的值不变。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) | 返回执行的错误码。<br>         <ul><br>         <li>SWAPFS_E_OK：执行成功。</li><br>         <li>SWAPFS_E_INVAL：manager为空指针、request为空指针、keyId为空指针、buffer为空指针，或bufferSize为0。</li><br>         <li>SWAPFS_E_Direct_IO_ALIGN：useDirectIo为true且buffer未对齐到SWAPFS_DIO_ALIGNMENT。</li><br>         <li>SWAPFS_E_NOSPC：设备存储空间不足。</li><br>         <li>SWAPFS_E_QUOTA_EXCEEDED：换出空间配额超限。</li><br>         <li>SWAPFS_E_FEATURE_DISABLED：换出功能因空间不足或策略被禁用。</li><br>         <li>SWAPFS_E_IO_ERROR：IO写入失败。</li><br>         <li>SWAPFS_E_NOMEM：内存分配失败。</li><br>         <li>SWAPFS_E_ACCES：权限被拒绝。</li><br>         <li>SWAPFS_E_BUSY：[OH_Swapfs_RemoveAllData](capi-oh-swapfs-h-sys.md#oh_swapfs_removealldata)正在进行或并发操作过多。</li><br>         <li>SWAPFS_E_SHUTTING_DOWN：管理器正在关闭。</li><br>         <li>202：非系统应用调用此系统API。请确保为系统应用。</li><br>         </ul> |

**参考：**

[OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)


### OH_Swapfs_SwapIn()

```c
OH_Swapfs_ErrCode OH_Swapfs_SwapIn(OH_SwapfsManager *manager, const OH_SwapfsSwapInRequest *request, uint64_t *readSize)
```

**描述**

将数据从磁盘换入内存。<br> 在Direct I/O模式下，缓冲区地址和大小必须对齐到SWAPFS_DIO_ALIGNMENT，且bufferSize必须大于等于occupiedSize。<br> 在缓冲模式下，bufferSize必须大于等于dataSize。<br> 成功时，readSize接收原始dataSize（非occupiedSize）。

**系统能力：** SystemCapability.FileManagement.File.Swapfs

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | 指向OH_SwapfsManager对象的指针。不可为空指针。 |
| const [OH_SwapfsSwapInRequest](capi-swapfs-oh-swapfsswapinrequest-sys.md) *request | 指向换入请求的指针，包含keyId、buffer和bufferSize。不可为空指针。 |
| uint64_t *readSize | 指向用于接收原始数据大小（原始数据大小单位：Byte）的指针，如调用方不需要可为空指针。成功时接收原始dataSize。失败时所指向的值不变。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) | 返回执行的错误码。<br>         <ul><br>         <li>SWAPFS_E_OK：执行成功。</li><br>         <li>SWAPFS_E_INVAL：manager为空指针、request为空指针、keyId为0、buffer为空指针，或bufferSize为0。</li><br>         <li>SWAPFS_E_DIO_ALIGN：缓冲区地址或大小未对齐到SWAPFS_DIO_ALIGNMENT。</li><br>         <li>SWAPFS_E_BUFFER_TOO_SMALL：bufferSize小于所需大小。</li><br>         <li>SWAPFS_E_KEY_NOT_FOUND：keyId不存在。</li><br>         <li>SWAPFS_E_KEY_STATE_INVALID：key处于 OH_SWAPFS_KEY_STATUS_REMOVING 状态。</li><br>         <li>SWAPFS_E_IO_ERROR：IO读取失败。</li><br>         <li>SWAPFS_E_NOMEM：内存分配失败。</li><br>         <li>SWAPFS_E_ACCES：权限被拒绝。</li><br>         <li>SWAPFS_E_BUSY：并发操作过多。</li><br>         <li>SWAPFS_E_SHUTTING_DOWN：管理器正在关闭。</li><br>         <li>202：非系统应用调用此系统API。请确保为系统应用。</li><br>         </ul> |

**参考：**

[OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)


### OH_Swapfs_QueryData()

```c
OH_Swapfs_ErrCode OH_Swapfs_QueryData(OH_SwapfsManager *manager, uint64_t keyId, OH_SwapfsDataInfo *info)
```

**描述**

查询特定swapfs key的信息，包括key的状态、数据大小等。

**系统能力：** SystemCapability.FileManagement.File.Swapfs

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | 指向OH_SwapfsManager对象的指针。不可为空指针。 |
| uint64_t keyId | 待查询的keyId。 |
| [OH_SwapfsDataInfo](capi-swapfs-oh-swapfsdatainfo-sys.md) *info | 指向用于接收key信息的[OH_SwapfsDataInfo](capi-swapfs-oh-swapfsdatainfo-sys.md)结构体的指针。不可为空指针。失败时，内容不变。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) | 返回执行的错误码。<br>         <ul><br>         <li>SWAPFS_E_OK：执行成功。</li><br>         <li>SWAPFS_E_INVAL：manager为空指针、keyId为0，或info为空指针。</li><br>         <li>SWAPFS_E_KEY_NOT_FOUND：keyId不存在。</li><br>         <li>SWAPFS_E_KEY_STATE_INVALID：key处于 OH_SWAPFS_KEY_STATUS_REMOVING 状态。</li><br>         <li>202：非系统应用调用此系统API。</li><br>         </ul> |

**参考：**

[OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)


### OH_Swapfs_GetStats()

```c
OH_Swapfs_ErrCode OH_Swapfs_GetStats(OH_SwapfsManager *manager, OH_SwapfsStats *stats)
```

**描述**

获取当前swapfs管理器的统计信息。

**系统能力：** SystemCapability.FileManagement.File.Swapfs

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | 指向OH_SwapfsManager对象的指针。不可为空指针。 |
| [OH_SwapfsStats](capi-swapfs-oh-swapfsstats-sys.md) *stats | 指向用于接收统计信息的[OH_SwapfsStats](capi-swapfs-oh-swapfsstats-sys.md)结构体的指针。不可为空指针。失败时，内容不变。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) | 返回执行的错误码。<br>         <ul><br>         <li>SWAPFS_E_OK：执行成功。</li><br>         <li>SWAPFS_E_INVAL：manager为空指针，或stats为空指针。</li><br>         <li>202：非系统应用调用此系统API。请确保为系统应用。</li><br>         </ul> |

**参考：**

[OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)


### OH_Swapfs_RemoveData()

```c
OH_Swapfs_ErrCode OH_Swapfs_RemoveData(OH_SwapfsManager *manager, uint64_t keyId)
```

**描述**

逻辑删除指定的swapfs key。触发后key立即被标记OH_SWAPFS_KEY_STATUS_REMOVING状态。<br> 触发时若已有[OH_Swapfs_SwapIn](capi-oh-swapfs-h-sys.md#oh_swapfs_swapin)操作则仍可完成swapin，完成后开始删除。<br> 开始删除后，对该key的新[OH_Swapfs_SwapIn](capi-oh-swapfs-h-sys.md#oh_swapfs_swapin)或[OH_Swapfs_QueryData](capi-oh-swapfs-h-sys.md#oh_swapfs_querydata)操作将返回[SWAPFS_E_KEY_STATE_INVALID](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)。

**系统能力：** SystemCapability.FileManagement.File.Swapfs

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | 指向OH_SwapfsManager对象的指针。不可为空指针。 |
| uint64_t keyId | 待删除的keyId。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) | 返回执行的错误码。<br>         <ul><br>         <li>SWAPFS_E_OK：执行成功。</li><br>         <li>SWAPFS_E_INVAL：manager为空指针或keyId为0。</li><br>         <li>SWAPFS_E_KEY_NOT_FOUND：keyId不存在。</li><br>         <li>SWAPFS_E_KEY_STATE_INVALID：key已处于OH_SWAPFS_KEY_STATUS_REMOVING状态。</li><br>         <li>SWAPFS_E_NOMEM：内存分配失败。</li><br>         <li>SWAPFS_E_BUSY：并发操作过多。</li><br>         <li>SWAPFS_E_SHUTTING_DOWN：管理器正在关闭。</li><br>         <li>202：非系统应用调用此系统API。请确保为系统应用。</li><br>         </ul> |

**参考：**

[OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)


### OH_Swapfs_RemoveAllData()

```c
OH_Swapfs_ErrCode OH_Swapfs_RemoveAllData(OH_SwapfsManager *manager)
```

**描述**

删除管理器中的所有swapfs key。<br> 如果存在进行中的操作（[OH_Swapfs_SwapOut](capi-oh-swapfs-h-sys.md#oh_swapfs_swapout)或[OH_Swapfs_SwapIn](capi-oh-swapfs-h-sys.md#oh_swapfs_swapin)），或任何key处于OH_SWAPFS_KEY_STATUS_REMOVING状态,<br> 此函数返回[SWAPFS_E_BUSY](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)而不开始任何删除操作。

**系统能力：** SystemCapability.FileManagement.File.Swapfs

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | 指向OH_SwapfsManager对象的指针。不可为空指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) | 返回执行的错误码。<br>         <ul><br>         <li>SWAPFS_E_OK：执行成功。</li><br>         <li>SWAPFS_E_INVAL：manager为空指针。</li><br>         <li>SWAPFS_E_NOMEM：内存分配失败。</li><br>         <li>SWAPFS_E_BUSY：存在进行中的活跃操作或有key处于OH_SWAPFS_KEY_STATUS_REMOVING状态。</li><br>         <li>SWAPFS_E_SHUTTING_DOWN：管理器正在关闭。</li><br>         <li>202：非系统应用调用此系统API。请确保为系统应用。</li><br>         </ul> |

**参考：**

[OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)



