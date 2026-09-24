# OH_SwapfsConfig(System API)

```c
typedef struct OH_SwapfsConfig {...} OH_SwapfsConfig
```

## Overview

Configuration for creating a swapfs manager.

**System capability**: SystemCapability.FileManagement.File.Swapfs

**Since**: 26.0.0

**System API:** This is a system API.

**Related module**: [Swapfs](capi-swapfs.md)

**Header file**: [oh_swapfs.h(System API)](capi-oh-swapfs-h-sys.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char *swapRootPath | Base path for swap data storage. Swapfs uses the fixed "swapfs" child directory. When NULL or empty, a default temporary base path under the application sandbox is used.<br>**Since**: 26.0.0 |
| uint64_t spaceLimitBytes | Maximum swap space in bytes. When 0, the default limit is 1GB (1073741824).<br>**Since**: 26.0.0 |
| bool useDirectIo | Whether to enforce Direct IO for swap-out operations. When false, buffered IO is used; when true, Direct IO is required and misaligned buffers will cause an error.<br>**Since**: 26.0.0 |


