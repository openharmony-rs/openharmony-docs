# OH_SwapfsSwapOutRequest(System API)

```c
typedef struct OH_SwapfsSwapOutRequest {...} OH_SwapfsSwapOutRequest
```

## Overview

Request parameters for swap-out operation.

**Since**: 26.0.0

**System API:** This is a system API.

**Related module**: [Swapfs](capi-swapfs.md)

**Header file**: [oh_swapfs.h(System API)](capi-oh-swapfs-h-sys.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const void *buffer | Pointer to the data buffer to be swapped out. Must not be NULL.<br>**Since**: 26.0.0 |
| uint64_t bufferSize | Size of the data buffer in bytes. Must be greater than 0.<br>**Since**: 26.0.0 |


