# OH_SwapfsConfig (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=c3dac3338f135feeca4a02be08f92e9afb1fc0fc translatedAt=2026-11-03T03:55:26.605Z pushedAt=2026-11-04T03:11:33.480Z nl=1 -->

```c
typedef struct OH_SwapfsConfig {...} OH_SwapfsConfig
```

## Overview

Used to configure the initialization parameters of the swapfs manager, including the data storage path, space limit, and I/O mode.

**Since**: 26.0.0

**Related module:** [Swapfs](capi-swapfs-sys.md)

**Header file:** [oh_swapfs.h (System API)](capi-oh-swapfs-h-sys.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| const char *swapRootPath | Root path for storing swapped-out data. Setting different root paths affects the storage location and access performance of swapfs data. Ensure that the path has sufficient storage space and read/write permissions.<br> swapfs uses the fixed "swapfs" subdirectory. When this is a null pointer or an empty string, the default temporary root path "/data/storage/el2/base/temp/swapfs" under the application sandbox is used.<br>**Since:** 26.0.0 |
| uint64_t spaceLimitBytes | Maximum swap-out space, in bytes. When spaceLimitBytes is 0, the default limit is 1,073,741,824 Bytes (that is, 1 GB).<br>**Since:** 26.0.0 |
| bool useDirectIo | Whether to force Direct I/O for swap-out operations. When false, buffered I/O is used; when true, Direct I/O is used, and the buffer is forcibly aligned. An unaligned buffer will cause an error.<br>**Since:** 26.0.0 |


