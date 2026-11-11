# OH_SwapfsSwapInRequest (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=c3dac3338f135feeca4a02be08f92e9afb1fc0fc translatedAt=2026-11-03T03:59:40.214Z pushedAt=2026-11-04T03:11:33.489Z nl=1 -->

```c
typedef struct OH_SwapfsSwapInRequest {...} OH_SwapfsSwapInRequest
```

## Overview

Request parameters for a swap-in operation. This structure is used to describe the parameters required for a swap-in operation, including the keyId returned during swap-out, the buffer that receives the swapped-in data, and its size.<br> Developers need to obtain the keyId through [OH_Swapfs_SwapOut](capi-oh-swapfs-h-sys.md#oh_swapfs_swapout), and then use the parameters in this structure to call the swap-in API to swap the data into memory.

**Since**: 26.0.0

**Related module:** [Swapfs](capi-swapfs-sys.md)

**Header file:** [oh_swapfs.h (System API)](capi-oh-swapfs-h-sys.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint64_t keyId | The keyId returned by a previous [OH_Swapfs_SwapOut](capi-oh-swapfs-h-sys.md#oh_swapfs_swapout). It is used to uniquely identify the data to be swapped in.<br>**Since:** 26.0.0 |
| void *buffer | Pointer to the buffer that receives the swapped-in data. It cannot be a null pointer.<br> In Direct I/O mode, the buffer address and size must be aligned to SWAPFS_DIO_ALIGNMENT, and bufferSize must be greater than or equal to occupiedSize.<br> In buffered mode, bufferSize must be greater than or equal to dataSize.<br> Direct I/O mode reads from and writes to the disk directly without going through the system cache; buffered mode uses the system cache. occupiedSize indicates the actual storage size occupied by the data, and dataSize indicates the logical size of the data.<br>**Since:** 26.0.0 |
| uint64_t bufferSize | Size of the receiving buffer, in bytes.<br> In Direct I/O mode, it must be greater than or equal to occupiedSize and aligned to SWAPFS_DIO_ALIGNMENT.<br> In buffered mode, it must be greater than or equal to dataSize. It is recommended to set an appropriate buffer size based on the actual data size to improve performance.<br> Value range: greater than or equal to the size of the data to be swapped in, and must be greater than 0. If the value is out of range or invalid, the API returns an error.<br>**Since:** 26.0.0 |


