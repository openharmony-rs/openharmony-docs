# oh_swapfs.h(System API)

## Overview

Defines the native APIs for swapfs.

**Library**: libohswapfs.so

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**System API:** This is a system API.

**Related module**: [Swapfs](capi-swapfs.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_SwapfsConfig(System API)](capi-swapfs-oh-swapfsconfig-sys.md) | OH_SwapfsConfig | Configuration for creating a swapfs manager.<br>**System API:** This is a system API. |
| [OH_SwapfsSwapOutRequest(System API)](capi-swapfs-oh-swapfsswapoutrequest-sys.md) | OH_SwapfsSwapOutRequest | Request parameters for swap-out operation.<br>**System API:** This is a system API. |
| [OH_SwapfsSwapInRequest(System API)](capi-swapfs-oh-swapfsswapinrequest-sys.md) | OH_SwapfsSwapInRequest | Request parameters for swap-in operation.<br>**System API:** This is a system API. |
| [OH_SwapfsDataInfo(System API)](capi-swapfs-oh-swapfsdatainfo-sys.md) | OH_SwapfsDataInfo | Information about a single swap key.<br>**System API:** This is a system API. |
| [OH_SwapfsStats(System API)](capi-swapfs-oh-swapfsstats-sys.md) | OH_SwapfsStats | Statistics of the current swapfs manager.<br>**System API:** This is a system API. |
| [OH_SwapfsManager(System API)](capi-swapfs-oh-swapfsmanager-sys.md) | OH_SwapfsManager | The struct is used to perform operations related to swapfs manager.<br>**System API:** This is a system API. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_SwapfsKeyStatus(System API)](#oh_swapfskeystatus) | OH_SwapfsKeyStatus | Defines the status of a swap key.<br>**System API:** This is a system API. |
| [OH_SwapfsDisableReason(System API)](#oh_swapfsdisablereason) | OH_SwapfsDisableReason | Defines the reason why the swap-out feature is disabled.<br>**System API:** This is a system API. |

### Macro

| Name | Description |
| -- | -- |
| SWAPFS_DIO_ALIGNMENT 4096U(System API) | Minimum alignment requirement for Direct IO buffers.<br>**Since**: 26.0.0<br>**System API:** This is a system API. |

### Function

| Name | Description |
| -- | -- |
| [OH_Swapfs_ErrCode OH_Swapfs_CreateManager(const OH_SwapfsConfig *config, OH_SwapfsManager **manager)(System API)](#oh_swapfs_createmanager) | Creates a swapfs manager.<br>**System API:** This is a system API. |
| [OH_Swapfs_ErrCode OH_Swapfs_DestroyManager(OH_SwapfsManager *manager)(System API)](#oh_swapfs_destroymanager) | Destroys a swapfs manager and releases all resources.<br> This function enters the shutting-down state and rejects new swap-out, swap-in, remove, and remove-all operations. It waits up to 5 seconds for active operations to complete. If all operations complete within the timeout, all swap data owned by the manager is automatically removed and the manager is destroyed. If the wait times out, this function cancels the shutting-down state and returns SWAPFS_E_BUSY; the caller can retry later.<br>**System API:** This is a system API. |
| [OH_Swapfs_ErrCode OH_Swapfs_SwapOut(OH_SwapfsManager *manager, const OH_SwapfsSwapOutRequest *request, uint64_t *keyId)(System API)](#oh_swapfs_swapout) | Swaps out data from memory to disk.<br> When config.useDirectIo is false, buffered IO is used. When true, Direct IO is required and misaligned buffers cause an error. In DIO mode, the swap file size is padded to SWAPFS_DIO_ALIGNMENT (occupiedSize is greater than or equal to dataSize).<br>**System API:** This is a system API. |
| [OH_Swapfs_ErrCode OH_Swapfs_SwapIn(OH_SwapfsManager *manager, const OH_SwapfsSwapInRequest *request, uint64_t *readSize)(System API)](#oh_swapfs_swapin) | Swaps in data from disk back to memory.<br> In DIO mode, the buffer address and size must be aligned to SWAPFS_DIO_ALIGNMENT, and bufferSize must be greater than or equal to occupiedSize. In buffered mode, bufferSize must be greater than or equal to dataSize. On success, readSize receives the original dataSize (not occupiedSize).<br>**System API:** This is a system API. |
| [OH_Swapfs_ErrCode OH_Swapfs_QueryData(OH_SwapfsManager *manager, uint64_t keyId, OH_SwapfsDataInfo *info)(System API)](#oh_swapfs_querydata) | Queries information about a specific swap key.<br>**System API:** This is a system API. |
| [OH_Swapfs_ErrCode OH_Swapfs_GetStats(OH_SwapfsManager *manager, OH_SwapfsStats *stats)(System API)](#oh_swapfs_getstats) | Obtains statistics of the current swapfs manager.<br>**System API:** This is a system API. |
| [OH_Swapfs_ErrCode OH_Swapfs_RemoveData(OH_SwapfsManager *manager, uint64_t keyId)(System API)](#oh_swapfs_removedata) | Logically deletes a specific swap key.<br> The key is marked as REMOVING state immediately. Existing swap-in operations can still complete. New swap-in or query operations on this key will return SWAPFS_E_KEY_STATE_INVALID. This function does not return SWAPFS_E_BUSY for concurrent swap-in operations.<br>**System API:** This is a system API. |
| [OH_Swapfs_ErrCode OH_Swapfs_RemoveAllData(OH_SwapfsManager *manager)(System API)](#oh_swapfs_removealldata) | Removes all swap keys in the manager.<br> If there are active operations in progress (swap-out or swap-in), or any key is in REMOVING state, this function returns SWAPFS_E_BUSY without starting any removal.<br>**System API:** This is a system API. |

## Enum type description

### OH_SwapfsKeyStatus

```c
enum OH_SwapfsKeyStatus
```

**Description**

Defines the status of a swap key.

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**System API:** This is a system API.

| Enum item | Description |
| -- | -- |
| OH_SWAPFS_KEY_STATUS_ACTIVE = 0 | The key is active and available for swap-in, query, or removal.<br>**Since**: 26.0.0 |
| OH_SWAPFS_KEY_STATUS_REMOVING = 1 | The key is logically deleted. New swap-in or query operations will be rejected.<br>**Since**: 26.0.0 |

### OH_SwapfsDisableReason

```c
enum OH_SwapfsDisableReason
```

**Description**

Defines the reason why the swap-out feature is disabled.

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**System API:** This is a system API.

| Enum item | Description |
| -- | -- |
| OH_SWAPFS_DISABLE_REASON_NONE = 0 | The feature is enabled (no disable reason).<br>**Since**: 26.0.0 |
| OH_SWAPFS_DISABLE_REASON_NOSPC = 1 | Device storage space is insufficient.<br>**Since**: 26.0.0 |


## Function description

### OH_Swapfs_CreateManager()

```c
OH_Swapfs_ErrCode OH_Swapfs_CreateManager(const OH_SwapfsConfig *config, OH_SwapfsManager **manager)
```

**Description**

Creates a swapfs manager.

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_SwapfsConfig](capi-swapfs-oh-swapfsconfig-sys.md) *config | [in] Pointer to the configuration, or NULL to use the default configuration (default temporary directory, 1GB limit, useDirectIo=false). |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) **manager | [out] Double pointer to receive the created OH_SwapfsManager handle. Must not be NULL. On failure, the pointed value is set to NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Swapfs_ErrCode | Returns the error code of the execution.          <ul>          <li>[SWAPFS_E_OK](capi-swapfs-errcode-h.md#oh_swapfs_errcode) if the execution is successful.</li>          <li>[SWAPFS_E_INVAL](capi-swapfs-errcode-h.md#oh_swapfs_errcode) manager is nullptr.</li>          <li>[SWAPFS_E_NOMEM](capi-swapfs-errcode-h.md#oh_swapfs_errcode) memory allocation failed.</li>          <li>[SWAPFS_E_ACCES](capi-swapfs-errcode-h.md#oh_swapfs_errcode) permission denied for the swap root path.</li>          <li>[SWAPFS_E_PATH_UNAVAILABLE](capi-swapfs-errcode-h.md#oh_swapfs_errcode) swap root path cannot be created.</li>          <li>202 if a non-system application calls this system API.</li>          </ul> |

### OH_Swapfs_DestroyManager()

```c
OH_Swapfs_ErrCode OH_Swapfs_DestroyManager(OH_SwapfsManager *manager)
```

**Description**

Destroys a swapfs manager and releases all resources.<br> This function enters the shutting-down state and rejects new swap-out, swap-in, remove, and remove-all operations. It waits up to 5 seconds for active operations to complete. If all operations complete within the timeout, all swap data owned by the manager is automatically removed and the manager is destroyed. If the wait times out, this function cancels the shutting-down state and returns SWAPFS_E_BUSY; the caller can retry later.

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | [in] Pointer to the OH_SwapfsManager object to destroy. Must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Swapfs_ErrCode | Returns the error code of the execution.          <ul>          <li>[SWAPFS_E_OK](capi-swapfs-errcode-h.md#oh_swapfs_errcode) if the execution is successful.</li>          <li>[SWAPFS_E_INVAL](capi-swapfs-errcode-h.md#oh_swapfs_errcode) manager is nullptr.</li>          <li>[SWAPFS_E_BUSY](capi-swapfs-errcode-h.md#oh_swapfs_errcode) there are active operations in progress.</li>          <li>202 if a non-system application calls this system API.</li>          </ul> |

### OH_Swapfs_SwapOut()

```c
OH_Swapfs_ErrCode OH_Swapfs_SwapOut(OH_SwapfsManager *manager, const OH_SwapfsSwapOutRequest *request, uint64_t *keyId)
```

**Description**

Swaps out data from memory to disk.<br> When config.useDirectIo is false, buffered IO is used. When true, Direct IO is required and misaligned buffers cause an error. In DIO mode, the swap file size is padded to SWAPFS_DIO_ALIGNMENT (occupiedSize is greater than or equal to dataSize).

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | [in] Pointer to the OH_SwapfsManager object. Must not be NULL. |
| [const OH_SwapfsSwapOutRequest](capi-swapfs-oh-swapfsswapoutrequest-sys.md) *request | [in] Pointer to the swap-out request containing the data buffer and its size. Must not be NULL. |
| uint64_t *keyId | [out] Pointer to receive the generated keyId for this swap data. Must not be NULL. On failure, the pointed value is unchanged. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Swapfs_ErrCode | Returns the error code of the execution.          <ul>          <li>[SWAPFS_E_OK](capi-swapfs-errcode-h.md#oh_swapfs_errcode) if the execution is successful.</li>          <li>[SWAPFS_E_INVAL](capi-swapfs-errcode-h.md#oh_swapfs_errcode) manager is nullptr, request is nullptr, keyId is nullptr,              buffer is nullptr, or bufferSize is 0.</li>          <li>[SWAPFS_E_DIO_ALIGN](capi-swapfs-errcode-h.md#oh_swapfs_errcode) useDirectIo is true and buffer is not aligned.</li>          <li>[SWAPFS_E_NOSPC](capi-swapfs-errcode-h.md#oh_swapfs_errcode) insufficient device storage space.</li>          <li>[SWAPFS_E_QUOTA_EXCEEDED](capi-swapfs-errcode-h.md#oh_swapfs_errcode) swap space quota exceeded.</li>          <li>[SWAPFS_E_FEATURE_DISABLED](capi-swapfs-errcode-h.md#oh_swapfs_errcode) swap-out is disabled due to low space or policy.</li>          <li>[SWAPFS_E_IO_ERROR](capi-swapfs-errcode-h.md#oh_swapfs_errcode) IO write failure.</li>          <li>[SWAPFS_E_NOMEM](capi-swapfs-errcode-h.md#oh_swapfs_errcode) memory allocation failed.</li>          <li>[SWAPFS_E_ACCES](capi-swapfs-errcode-h.md#oh_swapfs_errcode) permission denied.</li>          <li>[SWAPFS_E_BUSY](capi-swapfs-errcode-h.md#oh_swapfs_errcode) RemoveAllData is in progress or too many concurrent operations.</li>          <li>[SWAPFS_E_SHUTTING_DOWN](capi-swapfs-errcode-h.md#oh_swapfs_errcode) manager is shutting down.</li>          <li>202 if a non-system application calls this system API.</li>          </ul> |

### OH_Swapfs_SwapIn()

```c
OH_Swapfs_ErrCode OH_Swapfs_SwapIn(OH_SwapfsManager *manager, const OH_SwapfsSwapInRequest *request, uint64_t *readSize)
```

**Description**

Swaps in data from disk back to memory.<br> In DIO mode, the buffer address and size must be aligned to SWAPFS_DIO_ALIGNMENT, and bufferSize must be greater than or equal to occupiedSize. In buffered mode, bufferSize must be greater than or equal to dataSize. On success, readSize receives the original dataSize (not occupiedSize).

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | [in] Pointer to the OH_SwapfsManager object. Must not be NULL. |
| [const OH_SwapfsSwapInRequest](capi-swapfs-oh-swapfsswapinrequest-sys.md) *request | [in] Pointer to the swap-in request containing keyId, buffer, and bufferSize. Must not be NULL. |
| uint64_t *readSize | [out] Pointer to receive the original data size in bytes, or NULL if the caller does not need it. On success, receives the original dataSize. On failure, the pointed value is unchanged. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Swapfs_ErrCode | Returns the error code of the execution.          <ul>          <li>[SWAPFS_E_OK](capi-swapfs-errcode-h.md#oh_swapfs_errcode) if the execution is successful.</li>          <li>[SWAPFS_E_INVAL](capi-swapfs-errcode-h.md#oh_swapfs_errcode) manager is nullptr, request is nullptr, keyId is 0,              buffer is nullptr, or bufferSize is 0.</li>          <li>[SWAPFS_E_DIO_ALIGN](capi-swapfs-errcode-h.md#oh_swapfs_errcode) buffer address or size is not aligned to SWAPFS_DIO_ALIGNMENT.</li>          <li>[SWAPFS_E_BUFFER_TOO_SMALL](capi-swapfs-errcode-h.md#oh_swapfs_errcode) bufferSize is smaller than the required size.</li>          <li>[SWAPFS_E_KEY_NOT_FOUND](capi-swapfs-errcode-h.md#oh_swapfs_errcode) keyId does not exist.</li>          <li>[SWAPFS_E_KEY_STATE_INVALID](capi-swapfs-errcode-h.md#oh_swapfs_errcode) key is in REMOVING state.</li>          <li>[SWAPFS_E_IO_ERROR](capi-swapfs-errcode-h.md#oh_swapfs_errcode) IO read failure.</li>          <li>[SWAPFS_E_NOMEM](capi-swapfs-errcode-h.md#oh_swapfs_errcode) memory allocation failed.</li>          <li>[SWAPFS_E_ACCES](capi-swapfs-errcode-h.md#oh_swapfs_errcode) permission denied.</li>          <li>[SWAPFS_E_BUSY](capi-swapfs-errcode-h.md#oh_swapfs_errcode) too many concurrent operations.</li>          <li>[SWAPFS_E_SHUTTING_DOWN](capi-swapfs-errcode-h.md#oh_swapfs_errcode) manager is shutting down.</li>          <li>202 if a non-system application calls this system API.</li>          </ul> |

### OH_Swapfs_QueryData()

```c
OH_Swapfs_ErrCode OH_Swapfs_QueryData(OH_SwapfsManager *manager, uint64_t keyId, OH_SwapfsDataInfo *info)
```

**Description**

Queries information about a specific swap key.

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | [in] Pointer to the OH_SwapfsManager object. Must not be NULL. |
| uint64_t keyId | [in] The keyId to query. |
| [OH_SwapfsDataInfo](capi-swapfs-oh-swapfsdatainfo-sys.md) *info | [out] Pointer to the OH_SwapfsDataInfo structure to receive the key information. Must not be NULL. On failure, the content is unchanged. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Swapfs_ErrCode | Returns the error code of the execution.          <ul>          <li>[SWAPFS_E_OK](capi-swapfs-errcode-h.md#oh_swapfs_errcode) if the execution is successful.</li>          <li>[SWAPFS_E_INVAL](capi-swapfs-errcode-h.md#oh_swapfs_errcode) manager is nullptr, keyId is 0, or info is nullptr.</li>          <li>[SWAPFS_E_KEY_NOT_FOUND](capi-swapfs-errcode-h.md#oh_swapfs_errcode) keyId does not exist.</li>          <li>[SWAPFS_E_KEY_STATE_INVALID](capi-swapfs-errcode-h.md#oh_swapfs_errcode) key is in REMOVING state.</li>          <li>202 if a non-system application calls this system API.</li>          </ul> |

### OH_Swapfs_GetStats()

```c
OH_Swapfs_ErrCode OH_Swapfs_GetStats(OH_SwapfsManager *manager, OH_SwapfsStats *stats)
```

**Description**

Obtains statistics of the current swapfs manager.

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | [in] Pointer to the OH_SwapfsManager object. Must not be NULL. |
| [OH_SwapfsStats](capi-swapfs-oh-swapfsstats-sys.md) *stats | [out] Pointer to the OH_SwapfsStats structure to receive the statistics. Must not be NULL. On failure, the content is unchanged. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Swapfs_ErrCode | Returns the error code of the execution.          <ul>          <li>[SWAPFS_E_OK](capi-swapfs-errcode-h.md#oh_swapfs_errcode) if the execution is successful.</li>          <li>[SWAPFS_E_INVAL](capi-swapfs-errcode-h.md#oh_swapfs_errcode) manager is nullptr, or stats is nullptr.</li>          <li>202 if a non-system application calls this system API.</li>          </ul> |

### OH_Swapfs_RemoveData()

```c
OH_Swapfs_ErrCode OH_Swapfs_RemoveData(OH_SwapfsManager *manager, uint64_t keyId)
```

**Description**

Logically deletes a specific swap key.<br> The key is marked as REMOVING state immediately. Existing swap-in operations can still complete. New swap-in or query operations on this key will return SWAPFS_E_KEY_STATE_INVALID. This function does not return SWAPFS_E_BUSY for concurrent swap-in operations.

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | [in] Pointer to the OH_SwapfsManager object. Must not be NULL. |
| uint64_t keyId | [in] The keyId to remove. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Swapfs_ErrCode | Returns the error code of the execution.          <ul>          <li>[SWAPFS_E_OK](capi-swapfs-errcode-h.md#oh_swapfs_errcode) if the execution is successful.</li>          <li>[SWAPFS_E_INVAL](capi-swapfs-errcode-h.md#oh_swapfs_errcode) manager is nullptr or keyId is 0.</li>          <li>[SWAPFS_E_KEY_NOT_FOUND](capi-swapfs-errcode-h.md#oh_swapfs_errcode) keyId does not exist.</li>          <li>[SWAPFS_E_KEY_STATE_INVALID](capi-swapfs-errcode-h.md#oh_swapfs_errcode) key is already in REMOVING state.</li>          <li>[SWAPFS_E_NOMEM](capi-swapfs-errcode-h.md#oh_swapfs_errcode) memory allocation failed.</li>          <li>[SWAPFS_E_BUSY](capi-swapfs-errcode-h.md#oh_swapfs_errcode) too many concurrent operations.</li>          <li>[SWAPFS_E_SHUTTING_DOWN](capi-swapfs-errcode-h.md#oh_swapfs_errcode) manager is shutting down.</li>          <li>202 if a non-system application calls this system API.</li>          </ul> |

### OH_Swapfs_RemoveAllData()

```c
OH_Swapfs_ErrCode OH_Swapfs_RemoveAllData(OH_SwapfsManager *manager)
```

**Description**

Removes all swap keys in the manager.<br> If there are active operations in progress (swap-out or swap-in), or any key is in REMOVING state, this function returns SWAPFS_E_BUSY without starting any removal.

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_SwapfsManager](capi-swapfs-oh-swapfsmanager-sys.md) *manager | [in] Pointer to the OH_SwapfsManager object. Must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| OH_Swapfs_ErrCode | Returns the error code of the execution.          <ul>          <li>[SWAPFS_E_OK](capi-swapfs-errcode-h.md#oh_swapfs_errcode) if the execution is successful.</li>          <li>[SWAPFS_E_INVAL](capi-swapfs-errcode-h.md#oh_swapfs_errcode) manager is nullptr.</li>          <li>[SWAPFS_E_NOMEM](capi-swapfs-errcode-h.md#oh_swapfs_errcode) memory allocation failed.</li>          <li>[SWAPFS_E_BUSY](capi-swapfs-errcode-h.md#oh_swapfs_errcode) there are active operations in progress or pending keys in REMOVING state.</li>          <li>[SWAPFS_E_SHUTTING_DOWN](capi-swapfs-errcode-h.md#oh_swapfs_errcode) manager is shutting down.</li>          <li>202 if a non-system application calls this system API.</li>          </ul> |


