# OH_SwapfsStats (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=c3dac3338f135feeca4a02be08f92e9afb1fc0fc translatedAt=2026-11-03T03:58:51.540Z pushedAt=2026-11-04T03:11:33.487Z nl=1 -->

```c
typedef struct OH_SwapfsStats {...} OH_SwapfsStats
```

## Overview

OH_SwapfsStats is used to obtain statistics of the swapfs manager, including the number of active keys, data size, space usage, and so on.<br> It is applicable to scenarios where the swapfs status needs to be monitored and storage usage needs to be analyzed, helping developers understand the swap space usage of the system.

**Since**: 26.0.0

**Related module:** [Swapfs](capi-swapfs-sys.md)

**Header file:** [oh_swapfs.h (System API)](capi-oh-swapfs-h-sys.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint64_t totalKeys | Total number of active keys in the manager.<br>**Since version:** 26.0.0 |
| uint64_t totalDataSize | Total size of the original data of all keys, in bytes.<br>**Since version:** 26.0.0 |
| uint64_t totalOccupiedSize | Total size of the aligned files of all keys, in bytes.<br>**Since version:** 26.0.0 |
| uint64_t spaceLimitBytes | Configured upper limit of the swap space, in bytes.<br>**Since version:** 26.0.0 |
| bool featureEnabled | Whether the swap-out feature is enabled. The value is false when the device space is less than 5 GB or the control policy disables the feature.<br>**Since version:** 26.0.0 |
| [OH_SwapfsDisableReason](capi-oh-swapfs-h-sys.md#oh_swapfsdisablereason) disableReason | Reason why the swap-out feature is disabled. It is valid only when featureEnabled is false.<br>**Since version:** 26.0.0 |
| uint64_t accumulatedWriteBytes | Accumulated amount of data written by successful swap-out operations, in bytes.<br>**Since version:** 26.0.0 |
| int64_t lastSpaceCheckTime | Timestamp of the most recent device space check (Unix epoch, in ms).<br>**Since version:** 26.0.0 |
| uint64_t availableDeviceSpace | Available storage space of the cached device at the most recent check, in bytes.<br>**Since version:** 26.0.0 |


