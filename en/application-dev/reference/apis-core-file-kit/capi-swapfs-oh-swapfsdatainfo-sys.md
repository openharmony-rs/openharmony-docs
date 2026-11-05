# OH_SwapfsDataInfo (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=c3dac3338f135feeca4a02be08f92e9afb1fc0fc translatedAt=2026-11-03T03:57:11.656Z pushedAt=2026-11-04T03:11:33.482Z nl=1 -->

```c
typedef struct OH_SwapfsDataInfo {...} OH_SwapfsDataInfo
```

## Overview

Information about a single key. It is used when an application needs to precisely manage the metadata of swapped-out data entries (for example, querying the swap-out status or monitoring the swap-out size).

**Since**: 26.0.0

**Related module:** [Swapfs](capi-swapfs-sys.md)

**Header file:** [oh_swapfs.h (System API)](capi-oh-swapfs-h-sys.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint64_t keyId | Identifier of the swap data entry, used to uniquely identify the swap data. Different keyId values correspond to different data entries.<br>**Since version:** 26.0.0 |
| uint64_t dataSize | Original data size provided by the caller during swap-out, in bytes. This size determines the space occupied by the data and the read performance.<br>**Since version:** 26.0.0 |
| uint64_t occupiedSize | File size occupied on the disk, in bytes.<br> In Direct I/O mode, this is the value of dataSize aligned upward to SWAPFS_DIO_ALIGNMENT; in buffered mode, it equals dataSize.<br>**Since version:** 26.0.0 |
| int64_t createTime | Timestamp when the key was created (Unix epoch, in ms). This timestamp records the data creation time and can be used for data sorting, expiration policy determination, and so on.<br>**Since version:** 26.0.0 |
| [OH_SwapfsKeyStatus](capi-oh-swapfs-h-sys.md#oh_swapfskeystatus) status | Current status of the key. Different status values indicate different usage stages of the key, such as whether it is available, whether it is being swapped, whether it has been deleted, and so on.<br>**Since version:** 26.0.0 |
| bool canSwapIn | Whether the key can be swapped in.<br> If the [OH_SwapfsKeyStatus](capi-oh-swapfs-h-sys.md#oh_swapfskeystatus) status of the key is OH_SWAPFS_KEY_STATUS_REMOVING, the value is false; if the key is active and has not been cleaned up, the value is true.<br>**Since version:** 26.0.0 |


