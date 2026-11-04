# oh_swapfs.h (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=e24188be42371510a5430ef99fce8749325dfd13 translatedAt=2026-11-03T03:53:16.738Z pushedAt=2026-11-04T05:39:44.119Z nl=1 -->

## Overview

Defines the native APIs of swapfs (swap file system), providing operation interfaces for creating, mounting, and unmounting file system swap space.<br> The swapfs module is used to manage and monitor the swap partition usage of applications.<br> This module supports operations such as creating, mounting, and unmounting swap space, and is suitable for scenarios that require optimizing memory management and improving application runtime performance.<br> It supports swapping data out to disk and managing it, and swapping it back in when it needs to be retrieved later, thereby achieving flexible memory management and performance improvement.<br> This module helps developers effectively utilize system swap resources and improve the application experience when memory is insufficient.

**Header file:** <filemanagement/swapfs/oh_swapfs.h>

**Library:** libohswapfs.so

**System capability:** SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**Related module:** [Swapfs](capi-swapfs-sys.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_SwapfsConfig](capi-swapfs-oh-swapfsconfig-sys.md) | OH_SwapfsConfig | Used to configure the initialization parameters of the swapfs manager, including the data storage path, space limit, and I/O mode. |
| [OH_SwapfsSwapOutRequest](capi-swapfs-oh-swapfsswapoutrequest-sys.md) | OH_SwapfsSwapOutRequest | Request parameters for the swap-out operation. Used in scenarios where an application needs to release memory and actively triggers data swap-out to the swap partition, for example, temporarily swapping out part of the data when memory is tight. |
| [OH_SwapfsSwapInRequest](capi-swapfs-oh-swapfsswapinrequest-sys.md) | OH_SwapfsSwapInRequest | Request parameters for the swap-in operation. This structure is used to describe the parameters required for the swap-in operation, including the keyId returned during swap-out, the buffer that receives the swapped-in data, and the buffer size.<br> Developers need to obtain the keyId through [OH_Swapfs_SwapOut()](#oh_swapfs_swapout), and then use the parameters in this structure to call the swap-in interface to swap the data into memory. |
| [OH_SwapfsDataInfo](capi-swapfs-oh-swapfsdatainfo-sys.md) | OH_SwapfsDataInfo | Information of a single key. Used when an application needs to precisely manage the metadata of swapped-out data entries (such as querying swap-out status and monitoring swap-out size). |
| [OH_SwapfsStats](capi-swapfs-oh-swapfsstats-sys.md) | OH_SwapfsStats | OH_SwapfsStats is used to obtain the statistics information of the swapfs manager, including the number of active keys, data size, space usage, and so on.<br> It is suitable for scenarios that require monitoring the swapfs status and analyzing storage usage, helping developers understand the system swap space usage. |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) | OH_SwapfsManager | This structure is used to perform operations related to interacting with the swapfs manager. Before use, a valid manager instance must be created through the [OH_Swapfs_CreateManager()](#oh_swapfs_createmanager) function.<br> This structure is used to manage the lifecycle and configuration of swapfs, providing management capabilities such as creating, destroying, and expanding the swap partition. |

### Enums

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_SwapfsKeyStatus](#oh_swapfskeystatus) | OH_SwapfsKeyStatus | Data swapped out by swapfs is managed by swapfs in the form of keys (swap-out data exchange units). This enum defines the status of keys that have been swapped out by swapfs. |
| [OH_SwapfsDisableReason](#oh_swapfsdisablereason) | OH_SwapfsDisableReason | Defines the reason why the swap-out function is disabled. It is valid only when featureEnabled is false. |

### Macros

| Name | Description |
| -- | -- |
| SWAPFS_DIO_ALIGNMENT 4096U | Minimum alignment requirement for the Direct I/O buffer.<br>**Since Version:** 26.0.0 |

### Functions

| Name | Description |
| -- | -- |
| [`OH_Swapfs_ErrCode`](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) [`OH_Swapfs_CreateManager(const OH_SwapfsConfig *config, OH_SwapfsManager **manager)`](#oh_swapfs_createmanager) | Creates a swapfs manager. |
| [`OH_Swapfs_ErrCode`](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) [`OH_Swapfs_DestroyManager(OH_SwapfsManager *manager)`](#oh_swapfs_destroymanager) | Destroys the swapfs manager and releases all resources.<br> Waits up to 5s for operations to complete. If all operations complete within the waiting time, all swap data owned by the manager is automatically deleted and the manager is destroyed.<br> If the wait times out, this function cancels the closing state and returns [SWAPFS_E_BUSY](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode); the caller can retry later.<br> After the operation completes, this function enters the closing state and rejects new [OH_Swapfs_SwapOut](capi-oh-swapfs-h-sys.md#oh_swapfs_swapout), [OH_Swapfs_SwapIn](capi-oh-swapfs-h-sys.md#oh_swapfs_swapin), [OH_Swapfs_RemoveData](capi-oh-swapfs-h-sys.md#oh_swapfs_removedata), and [OH_Swapfs_RemoveAllData](capi-oh-swapfs-h-sys.md#oh_swapfs_removealldata) operations. |
| [`OH_Swapfs_ErrCode`](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) [`OH_Swapfs_SwapOut(OH_SwapfsManager *manager, const OH_SwapfsSwapOutRequest *request, uint64_t *keyId)`](#oh_swapfs_swapout) | Swaps data out from memory to disk.<br> When useDirectIo in [OH_SwapfsConfig](capi-swapfs-oh-swapfsconfig-sys.md) is false, buffered I/O is used. When it is true, Direct I/O is required, and an unaligned buffer will cause an error.<br> In Direct I/O mode, the swap-out file size is padded to SWAPFS_DIO_ALIGNMENT (occupiedSize is greater than or equal to dataSize). |
| [`OH_Swapfs_ErrCode`](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) [`OH_Swapfs_SwapIn(OH_SwapfsManager *manager, const OH_SwapfsSwapInRequest *request, uint64_t *readSize)`](#oh_swapfs_swapin) | Swaps data in from disk to memory.<br> In Direct I/O mode, the buffer address and size must be aligned to SWAPFS_DIO_ALIGNMENT, and bufferSize must be greater than or equal to occupiedSize.<br> In buffered mode, bufferSize must be greater than or equal to dataSize.<br> On success, readSize receives the raw dataSize (not occupiedSize). |
| [`OH_Swapfs_ErrCode`](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) [`OH_Swapfs_QueryData(OH_SwapfsManager *manager, uint64_t keyId, OH_SwapfsDataInfo *info)`](#oh_swapfs_querydata) | Queries the information of a specific swapfs key, including the key status, data size, and so on. |
| [`OH_Swapfs_ErrCode`](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) [`OH_Swapfs_GetStats(OH_SwapfsManager *manager, OH_SwapfsStats *stats)`](#oh_swapfs_getstats) | Obtains the statistics information of the current swapfs manager. |
| [`OH_Swapfs_ErrCode`](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) [`OH_Swapfs_RemoveData(OH_SwapfsManager *manager, uint64_t keyId)`](#oh_swapfs_removedata) | Logically deletes the specified swapfs key. After being triggered, the key is immediately marked with the OH_SWAPFS_KEY_STATUS_REMOVING status.<br> If an [OH_Swapfs_SwapIn](capi-oh-swapfs-h-sys.md#oh_swapfs_swapin) operation already exists when triggered, the swap-in can still complete, and deletion starts after completion.<br> After deletion starts, new [OH_Swapfs_SwapIn](capi-oh-swapfs-h-sys.md#oh_swapfs_swapin) or [OH_Swapfs_QueryData](capi-oh-swapfs-h-sys.md#oh_swapfs_querydata) operations on this key will return [SWAPFS_E_KEY_STATE_INVALID](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode). |
| [`OH_Swapfs_ErrCode`](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) [`OH_Swapfs_RemoveAllData(OH_SwapfsManager *manager)`](#oh_swapfs_removealldata) | Deletes all swapfs keys in the manager.<br> If there is an operation in progress ([OH_Swapfs_SwapOut](capi-oh-swapfs-h-sys.md#oh_swapfs_swapout) or [OH_Swapfs_SwapIn](capi-oh-swapfs-h-sys.md#oh_swapfs_swapin)), or any key is in the OH_SWAPFS_KEY_STATUS_REMOVING status,<br> this function returns [SWAPFS_E_BUSY](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) without starting any deletion operation. |

## Enum Description

### OH_SwapfsKeyStatus

```c
enum OH_SwapfsKeyStatus
```

**Description**

Data swapped out by swapfs is managed by swapfs in the form of keys (swap-out data exchange units). This enum defines the status of keys that have been swapped out by swapfs.

**Since**: 26.0.0

| Enum Item | Description |
| -- | -- |
| OH_SWAPFS_KEY_STATUS_ACTIVE = 0 | The key is in the active state and can be used for swap-in, query, or deletion operations.<br>**Since Version:** 26.0.0 |
| OH_SWAPFS_KEY_STATUS_REMOVING = 1 | The key has been deleted. New swap-in or query operations will be rejected.<br>**Since Version:** 26.0.0 |

### OH_SwapfsDisableReason

```c
enum OH_SwapfsDisableReason
```

**Description**

Defines the reason why the swap-out feature is disabled. It is valid only when featureEnabled is false.

**Since**: 26.0.0

| Enum Item | Description |
| -- | -- |
| OH_SWAPFS_DISABLE_REASON_NONE = 0 | The swap-out feature is enabled.<br>**Since Version:** 26.0.0 |
| OH_SWAPFS_DISABLE_REASON_NOSPC = 1 | Insufficient device storage space.<br>**Since Version:** 26.0.0 |

## Function Description

### OH_Swapfs_CreateManager()

```c
OH_Swapfs_ErrCode OH_Swapfs_CreateManager(const OH_SwapfsConfig *config, OH_SwapfsManager **manager)
```

**Description**

Creates a swapfs manager.

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| const [OH_SwapfsConfig](capi-swapfs-oh-swapfsconfig-sys.md) *config | Pointer to the configuration. If it is a null pointer, config uses the temporary directory by default, spaceLimitBytes is limited to 1GB, and useDirectIo is false. |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) **manager | Double pointer used to receive the created [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) handle. Must not be a null pointer. On failure, the value it points to is set to a null pointer. |

**Return:**

| Type | Description |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) | Returns the error code of the execution.<br>         <ul><br>         <li>SWAPFS_E_OK: Execution successful.</li><br>         <li>SWAPFS_E_INVAL: manager is a null pointer.</li><br>         <li>SWAPFS_E_NOMEM: Memory allocation failed.</li><br>         <li>SWAPFS_E_ACCES: Permission for the swap-out root path is denied.</li><br>         <li>SWAPFS_E_PATH_UNAVAILABLE: The swap-out root path cannot be created.</li><br>         <li>202: A non-system application calls this system API. Ensure that it is a system application.</li><br>         </ul> |

**See also**

[OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)


### OH_Swapfs_DestroyManager()

```c
OH_Swapfs_ErrCode OH_Swapfs_DestroyManager(OH_SwapfsManager *manager)
```

**Description**

Destroys the swapfs manager and releases all resources.<br> Waits up to 5s for the operation to complete. If all operations complete within the waiting time, all swap data owned by the manager is automatically deleted, and the manager is destroyed.<br> If the wait times out, this function cancels the closing state and returns [SWAPFS_E_BUSY](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode); the caller can retry later.<br> After the operation completes, this function enters the closing state and rejects new [OH_Swapfs_SwapOut](capi-oh-swapfs-h-sys.md#oh_swapfs_swapout), [OH_Swapfs_SwapIn](capi-oh-swapfs-h-sys.md#oh_swapfs_swapin), [OH_Swapfs_RemoveData](capi-oh-swapfs-h-sys.md#oh_swapfs_removedata), and [OH_Swapfs_RemoveAllData](capi-oh-swapfs-h-sys.md#oh_swapfs_removealldata) operations.

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | Pointer to the OH_SwapfsManager object to be destroyed. Must not be a null pointer. |

**Return:**

| Type | Description |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) | Returns the error code of the execution.<br>         <ul><br>         <li>SWAPFS_E_OK: Execution successful.</li><br>         <li>SWAPFS_E_INVAL: manager is a null pointer.</li><br>         <li>SWAPFS_E_BUSY: There are active operations in progress.</li><br>         <li>202: A non-system application calls this system API. Ensure that it is a system application.</li><br>         </ul> |

**See also**

[OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)


### OH_Swapfs_SwapOut()

```c
OH_Swapfs_ErrCode OH_Swapfs_SwapOut(OH_SwapfsManager *manager, const OH_SwapfsSwapOutRequest *request, uint64_t *keyId)
```

**Description**

Swaps data from memory out to disk.<br> When useDirectIo in [OH_SwapfsConfig](capi-swapfs-oh-swapfsconfig-sys.md) is false, buffered I/O is used. When it is true, Direct I/O is required, and an unaligned buffer will cause an error.<br> In Direct I/O mode, the swapped-out file size is padded to SWAPFS_DIO_ALIGNMENT (occupiedSize is greater than or equal to dataSize).

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | Pointer to an OH_SwapfsManager object. Must not be a null pointer. |
| const [OH_SwapfsSwapOutRequest](capi-swapfs-oh-swapfsswapoutrequest-sys.md) *request | Pointer to the swap-out request, which contains the data buffer and its size. Must not be a null pointer. |
| uint64_t *keyId | Pointer used for receiving the keyId generated for this swapped-out data. Must not be a null pointer. On failure, the value pointed to remains unchanged. |

**Return:**

| Type | Description |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) | Returns the error code of the execution.<br>         <ul><br>         <li>SWAPFS_E_OK: Execution successful.</li><br>         <li>SWAPFS_E_INVAL: manager is a null pointer, request is a null pointer, keyId is a null pointer, buffer is a null pointer, or bufferSize is 0.</li><br>         <li>SWAPFS_E_DIO_ALIGN: useDirectIo is true and buffer is not aligned to SWAPFS_DIO_ALIGNMENT.</li><br>         <li>SWAPFS_E_NOSPC: Insufficient device storage space.</li><br>         <li>SWAPFS_E_QUOTA_EXCEEDED: Swap-out space quota exceeded.</li><br>         <li>SWAPFS_E_FEATURE_DISABLED: Swap-out feature is disabled due to insufficient space or policy.</li><br>         <li>SWAPFS_E_IO_ERROR: I/O write failed.</li><br>         <li>SWAPFS_E_NOMEM: Memory allocation failed.</li><br>         <li>SWAPFS_E_ACCES: Permission denied.</li><br>         <li>SWAPFS_E_BUSY: [OH_Swapfs_RemoveAllData](capi-oh-swapfs-h-sys.md#oh_swapfs_removealldata) is in progress or there are too many concurrent operations.</li><br>         <li>SWAPFS_E_SHUTTING_DOWN: The manager is shutting down.</li><br>         <li>202: A non-system application calls this system API. Ensure that it is a system application.</li><br>         </ul> |

**See also**

[OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)


### OH_Swapfs_SwapIn()

```c
OH_Swapfs_ErrCode OH_Swapfs_SwapIn(OH_SwapfsManager *manager, const OH_SwapfsSwapInRequest *request, uint64_t *readSize)
```

**Description**

Swaps data from the disk into memory.<br> In Direct I/O mode, the buffer address and size must be aligned to SWAPFS_DIO_ALIGNMENT, and bufferSize must be greater than or equal to occupiedSize.<br> In buffered mode, bufferSize must be greater than or equal to dataSize.<br> On success, readSize receives the raw dataSize (not occupiedSize).

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | Pointer to the OH_SwapfsManager object. Must not be a null pointer. |
| const [OH_SwapfsSwapInRequest](capi-swapfs-oh-swapfsswapinrequest-sys.md) *request | Pointer to the swap-in request, containing keyId, buffer, and bufferSize. Must not be a null pointer. |
| uint64_t *readSize | Pointer used for receiving the raw data size (raw data size unit: Byte). May be a null pointer if the caller does not need it. On success, receives the raw dataSize. On failure, the value pointed to remains unchanged. |

**Return:**

| Type | Description |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) | Returns the error code of the execution.<br>         <ul><br>         <li>SWAPFS_E_OK: Execution successful.</li><br>         <li>SWAPFS_E_INVAL: manager is a null pointer, request is a null pointer, keyId is 0, buffer is a null pointer, or bufferSize is 0.</li><br>         <li>SWAPFS_E_DIO_ALIGN: The buffer address or size is not aligned to SWAPFS_DIO_ALIGNMENT.</li><br>         <li>SWAPFS_E_BUFFER_TOO_SMALL: bufferSize is smaller than the required size.</li><br>         <li>SWAPFS_E_KEY_NOT_FOUND: keyId does not exist.</li><br>         <li>SWAPFS_E_KEY_STATE_INVALID: The key is in the OH_SWAPFS_KEY_STATUS_REMOVING state.</li><br>         <li>SWAPFS_E_IO_ERROR: IO read failed.</li><br>         <li>SWAPFS_E_NOMEM: Memory allocation failed.</li><br>         <li>SWAPFS_E_ACCES: Permission denied.</li><br>         <li>SWAPFS_E_BUSY: Too many concurrent operations.</li><br>         <li>SWAPFS_E_SHUTTING_DOWN: The manager is shutting down.</li><br>         <li>202: Non-system application calls this system API. Ensure that it is a system application.</li><br>         </ul> |

**See also**

[OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)


### OH_Swapfs_QueryData()

```c
OH_Swapfs_ErrCode OH_Swapfs_QueryData(OH_SwapfsManager *manager, uint64_t keyId, OH_SwapfsDataInfo *info)
```

**Description**

Queries the information of a specific swapfs key, including the key status, data size, and so on.

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | Pointer to the OH_SwapfsManager object. Must not be a null pointer. |
| uint64_t keyId | keyId to be queried. |
| [OH_SwapfsDataInfo](capi-swapfs-oh-swapfsdatainfo-sys.md) *info | Pointer used for receiving the [OH_SwapfsDataInfo](capi-swapfs-oh-swapfsdatainfo-sys.md) structure of the key information. Must not be a null pointer. On failure, the content remains unchanged. |

**Return:**

| Type | Description |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) | Returns the error code of the execution.<br>         <ul><br>         <li>SWAPFS_E_OK: Execution successful.</li><br>         <li>SWAPFS_E_INVAL: manager is a null pointer, keyId is 0, or info is a null pointer.</li><br>         <li>SWAPFS_E_KEY_NOT_FOUND: keyId does not exist.</li><br>         <li>SWAPFS_E_KEY_STATE_INVALID: The key is in the OH_SWAPFS_KEY_STATUS_REMOVING state.</li><br>         <li>202: A non-system application calls this system API. Ensure that it is a system application.</li><br>         </ul> |

**See also**

[OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)


### OH_Swapfs_GetStats()

```c
OH_Swapfs_ErrCode OH_Swapfs_GetStats(OH_SwapfsManager *manager, OH_SwapfsStats *stats)
```

**Description**

Obtains the statistics information of the current swapfs manager.

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | Pointer to the OH_SwapfsManager object. Must not be a null pointer. |
| [OH_SwapfsStats](capi-swapfs-oh-swapfsstats-sys.md) *stats | Pointer used for receiving the [OH_SwapfsStats](capi-swapfs-oh-swapfsstats-sys.md) structure of statistics information. Must not be a null pointer. On failure, the content remains unchanged. |

**Return:**

| Type | Description |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) | Returns the error code of the execution.<br>         <ul><br>         <li>SWAPFS_E_OK: Execution successful.</li><br>         <li>SWAPFS_E_INVAL: manager is a null pointer, or stats is a null pointer.</li><br>         <li>202: A non-system application calls this system API. Ensure that it is a system application.</li><br>         </ul> |

**See also**

[OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)


### OH_Swapfs_RemoveData()

```c
OH_Swapfs_ErrCode OH_Swapfs_RemoveData(OH_SwapfsManager *manager, uint64_t keyId)
```

**Description**

Logically deletes the specified swapfs key. After triggering, the key is immediately marked with the OH_SWAPFS_KEY_STATUS_REMOVING status.<br> If an [OH_Swapfs_SwapIn](capi-oh-swapfs-h-sys.md#oh_swapfs_swapin) operation already exists when triggered, the swapin can still be completed, and deletion starts after completion.<br> After deletion starts, new [OH_Swapfs_SwapIn](capi-oh-swapfs-h-sys.md#oh_swapfs_swapin) or [OH_Swapfs_QueryData](capi-oh-swapfs-h-sys.md#oh_swapfs_querydata) operations on this key will return [SWAPFS_E_KEY_STATE_INVALID](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode).

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | Pointer to the OH_SwapfsManager object. Must not be a null pointer. |
| uint64_t keyId | The keyId to be deleted. |

**Return:**

| Type | Description |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) | Returns the error code of the execution.<br>         <ul><br>         <li>SWAPFS_E_OK: Execution successful.</li><br>         <li>SWAPFS_E_INVAL: manager is a null pointer or keyId is 0.</li><br>         <li>SWAPFS_E_KEY_NOT_FOUND: keyId does not exist.</li><br>         <li>SWAPFS_E_KEY_STATE_INVALID: The key is already in the OH_SWAPFS_KEY_STATUS_REMOVING state.</li><br>         <li>SWAPFS_E_NOMEM: Memory allocation failed.</li><br>         <li>SWAPFS_E_BUSY: Too many concurrent operations.</li><br>         <li>SWAPFS_E_SHUTTING_DOWN: The manager is shutting down.</li><br>         <li>202: A non-system application calls this system API. Ensure that it is a system application.</li><br>         </ul> |

**See also**

[OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)


### OH_Swapfs_RemoveAllData()

```c
OH_Swapfs_ErrCode OH_Swapfs_RemoveAllData(OH_SwapfsManager *manager)
```

**Description**

Deletes all swapfs keys in the manager.<br> If there is an operation in progress ([OH_Swapfs_SwapOut](capi-oh-swapfs-h-sys.md#oh_swapfs_swapout) or [OH_Swapfs_SwapIn](capi-oh-swapfs-h-sys.md#oh_swapfs_swapin)), or any key is in the OH_SWAPFS_KEY_STATUS_REMOVING state,<br> this function returns [SWAPFS_E_BUSY](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) without starting any deletion operation.

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | Pointer to the OH_SwapfsManager object. Must not be a null pointer. |

**Returns:**

| Type | Description |
| -- | -- |
| [OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) | Returns the error code of the execution.<br>         <ul><br>         <li>SWAPFS_E_OK: Execution successful.</li><br>         <li>SWAPFS_E_INVAL: manager is a null pointer.</li><br>         <li>SWAPFS_E_NOMEM: Memory allocation failed.</li><br>         <li>SWAPFS_E_BUSY: There is an active operation in progress or a key is in the OH_SWAPFS_KEY_STATUS_REMOVING state.</li><br>         <li>SWAPFS_E_SHUTTING_DOWN: The manager is shutting down.</li><br>         <li>202: A non-system application calls this system API. Ensure that it is a system application.</li><br>         </ul> |

**See also**

[OH_Swapfs_ErrCode](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode)



