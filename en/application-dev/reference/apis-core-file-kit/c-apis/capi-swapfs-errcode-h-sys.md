# swapfs_errcode.h(System API)

## Overview

Declare the error codes of swapfs module.

**Library**: libohswapfs.so

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**System API:** This is a system API.

**Related module**: [Swapfs](capi-swapfs.md)

## Summary

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_Swapfs_ErrCode(System API)](#oh_swapfs_errcode) | OH_Swapfs_ErrCode | Error codes of swapfs module.<br>**System API:** This is a system API. |

## Enum type description

### OH_Swapfs_ErrCode

```c
enum OH_Swapfs_ErrCode
```

**Description**

Error codes of swapfs module.

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**System API:** This is a system API.

| Enum item | Description |
| -- | -- |
| SWAPFS_E_OK = 0 | Operation successful.<br>**Since**: 26.0.0 |
| SWAPFS_E_INVAL = 36200001 | Invalid parameter. Possible causes a null pointer, zero length, or an invalid configuration value.<br>**Since**: 26.0.0 |
| SWAPFS_E_DIO_ALIGN = 36200002 | DIO buffer address or length is not aligned to SWAPFS_DIO_ALIGNMENT.<br>**Since**: 26.0.0 |
| SWAPFS_E_BUFFER_TOO_SMALL = 36200003 | SwapIn buffer size is smaller than the required size (occupiedSize for DIO mode and dataSize for buffered mode).<br>**Since**: 26.0.0 |
| SWAPFS_E_KEY_NOT_FOUND = 36200004 | The specified keyId does not exist in the current manager.<br>**Since**: 26.0.0 |
| SWAPFS_E_KEY_STATE_INVALID = 36200005 | The key is in the REMOVING state and cannot be operated on.<br>**Since**: 26.0.0 |
| SWAPFS_E_BUSY = 36200006 | Concurrent conflict detected. RemoveAllData or DestroyManager detected active operations in progress.<br>**Since**: 26.0.0 |
| SWAPFS_E_NOSPC = 36200007 | Insufficient device storage space.<br>**Since**: 26.0.0 |
| SWAPFS_E_QUOTA_EXCEEDED = 36200008 | Swap space quota exceeded. The total occupied space has reached the configured limit.<br>**Since**: 26.0.0 |
| SWAPFS_E_IO_ERROR = 36200009 | I/O read or write failure, including a short read, short write, fsync failure, or rename failure.<br>**Since**: 26.0.0 |
| SWAPFS_E_FEATURE_DISABLED = 36200010 | The SwapOut feature is disabled due to insufficient device storage space or control policy.<br>**Since**: 26.0.0 |
| SWAPFS_E_ACCES = 36200011 | Permission denied.<br>**Since**: 26.0.0 |
| SWAPFS_E_PATH_UNAVAILABLE = 36200012 | Swap root path cannot be created or is unavailable.<br>**Since**: 26.0.0 |
| SWAPFS_E_SHUTTING_DOWN = 36200013 | The manager is shutting down. New swap-out, swap-in, remove, or remove-all operations will be rejected.<br>**Since**: 26.0.0 |
| SWAPFS_E_NOMEM = 36200014 | Memory allocation failed.<br>**Since**: 26.0.0 |


