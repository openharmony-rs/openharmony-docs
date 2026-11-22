# swapfs_errcode.h (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=c3dac3338f135feeca4a02be08f92e9afb1fc0fc translatedAt=2026-11-03T03:55:01.051Z pushedAt=2026-11-04T03:11:33.479Z nl=1 -->

## Overview

Declares the error codes of the swapfs module, including the definitions of various error states during file system operations.

**File to include:** <filemanagement/swapfs/swapfs_errcode.h>

**Library:** libohswapfs.so

**System capability:** SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**Related module:** [Swapfs](capi-swapfs-sys.md)

## Summary

### Enums

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_Swapfs_ErrCode](#oh_swapfs_errcode) | OH_Swapfs_ErrCode | Error code of the swapfs module. |

## Enum Description

### OH_Swapfs_ErrCode

```c
enum OH_Swapfs_ErrCode
```

**Description**

Error codes of the swapfs module.

**Since**: 26.0.0

| Enum Item | Description |
| -- | -- |
| SWAPFS_E_OK = 0 | The operation is successful.<br>**Since**: 26.0.0 |
| SWAPFS_E_INVAL = 36200001 | Invalid parameter. Possible causes include a null pointer, zero length, or an invalid configuration value. Check whether the input parameters are valid.<br>**Since**: 26.0.0 |
| SWAPFS_E_DIO_ALIGN = 36200002 | The Direct I/O buffer address or length is not aligned to SWAPFS_DIO_ALIGNMENT.<br>**Since**: 26.0.0 |
| SWAPFS_E_BUFFER_TOO_SMALL = 36200003 | The swap-in buffer size is smaller than the required size (occupiedSize in Direct I/O mode, dataSize in buffered mode).<br> dataSize is the actual number of data bytes written.<br> occupiedSize is the number of physical space bytes occupied on the disk (aligned to 4096 in Direct I/O mode, equal to dataSize rounded up to a multiple of SWAPFS_DIO_ALIGNMENT).<br>**Since**: 26.0.0 |
| SWAPFS_E_KEY_NOT_FOUND = 36200004 | The specified keyId does not exist in the current manager. Check whether the keyId is correct or has been created.<br>**Since**: 26.0.0 |
| SWAPFS_E_KEY_STATE_INVALID = 36200005 | The key is in the OH_SWAPFS_KEY_STATUS_REMOVING state and cannot be operated on. Wait for the key deletion to complete or use another available key.<br>**Since**: 26.0.0 |
| SWAPFS_E_BUSY = 36200006 | A concurrency conflict is detected.<br> [OH_Swapfs_RemoveAllData](./capi-oh-swapfs-h-sys.md#oh_swapfs_removealldata) or [OH_Swapfs_DestroyManager](./capi-oh-swapfs-h-sys.md#oh_swapfs_destroymanager) detects that an active operation is in progress. Retry later or wait for the current operation to complete.<br>**Since**: 26.0.0 |
| SWAPFS_E_NOSPC = 36200007 | Insufficient device storage space. Clear the storage space and retry.<br>**Since**: 26.0.0 |
| SWAPFS_E_QUOTA_EXCEEDED = 36200008 | The swap-out space quota is exceeded. The total occupied space has reached the configured upper limit. Clear the swapped-out data or adjust the quota upper limit.<br>**Since**: 26.0.0 |
| SWAPFS_E_IO_ERROR = 36200009 | IO read or write failed. Possible causes include: the actual number of bytes read/written is less than the requested number of bytes (short read/short write), data persistence failed (fsync failed), or file rename failed.<br>**Since**: 26.0.0 |
| SWAPFS_E_FEATURE_DISABLED = 36200010 | The swap-out feature is disabled due to insufficient device storage space or control policy.<br>**Since**: 26.0.0 |
| SWAPFS_E_ACCES = 36200011 | Permission denied. Check the application permission or file access permission.<br>**Since**: 26.0.0 |
| SWAPFS_E_PATH_UNAVAILABLE = 36200012 | The swap-out root path cannot be created or is unavailable. Check the path configuration or storage device status.<br>**Since**: 26.0.0 |
| SWAPFS_E_SHUTTING_DOWN = 36200013 | The manager is shutting down.<br> New [OH_Swapfs_SwapOut](./capi-oh-swapfs-h-sys.md#oh_swapfs_swapout), [OH_Swapfs_SwapIn](./capi-oh-swapfs-h-sys.md#oh_swapfs_swapin), [OH_Swapfs_RemoveData](./capi-oh-swapfs-h-sys.md#oh_swapfs_removedata), or [OH_Swapfs_RemoveAllData](./capi-oh-swapfs-h-sys.md#oh_swapfs_removealldata) operations will be rejected.<br>**Since**: 26.0.0 |
| SWAPFS_E_NOMEM = 36200014 | Memory allocation failed.<br>**Since**: 26.0.0 |
