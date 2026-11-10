# OH_SwapfsSwapOutRequest (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=c3dac3338f135feeca4a02be08f92e9afb1fc0fc translatedAt=2026-11-03T04:00:05.014Z pushedAt=2026-11-04T03:11:33.491Z nl=1 -->

```c
typedef struct OH_SwapfsSwapOutRequest {...} OH_SwapfsSwapOutRequest
```

## Overview

Request parameters for a swap-out operation. Used in scenarios where an application needs to proactively trigger data swap-out to the swap partition when releasing memory, for example, temporarily swapping out part of the data when memory is tight.

**Since**: 26.0.0

**Related module:** [Swapfs](capi-swapfs-sys.md)

**Header file:** [oh_swapfs.h (System API)](capi-oh-swapfs-h-sys.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| const void *buffer | Pointer to the buffer of the data to be swapped out. Must not be a null pointer. If a null pointer is passed, the error code [SWAPFS_E_INVAL](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) is returned.<br>**Since:** 26.0.0 |
| uint64_t bufferSize | Size of the buffer of the data to be swapped out, in bytes. Must be greater than 0. If 0 is passed, the error code [SWAPFS_E_INVAL](capi-swapfs-errcode-h-sys.md#oh_swapfs_errcode) is returned.<br>**Since:** 26.0.0 |


