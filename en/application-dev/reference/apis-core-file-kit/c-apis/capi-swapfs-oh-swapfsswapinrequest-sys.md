# OH_SwapfsSwapInRequest(System API)

```c
typedef struct OH_SwapfsSwapInRequest {...} OH_SwapfsSwapInRequest
```

## Overview

Request parameters for swap-in operation.

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**System API:** This is a system API.

**Related module**: [Swapfs](capi-swapfs.md)

**Header file**: [oh_swapfs.h(System API)](capi-oh-swapfs-h-sys.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t keyId | The keyId returned by a previous swap-out operation.<br>**Since**: 26.0.0 |
| void *buffer | Pointer to the buffer for receiving swapped-in data. Must not be NULL. In DIO mode, the buffer address and size must be aligned to SWAPFS_DIO_ALIGNMENT, and bufferSize must be greater than or equal to occupiedSize. In buffered mode, bufferSize must be greater than or equal to dataSize.<br>**Since**: 26.0.0 |
| uint64_t bufferSize | Size of the receiving buffer in bytes.<br>**Since**: 26.0.0 |


