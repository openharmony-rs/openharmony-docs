# OH_SwapfsStats(System API)

```c
typedef struct OH_SwapfsStats {...} OH_SwapfsStats
```

## Overview

Statistics of the current swapfs manager.

**Since**: 26.0.0

**System API:** This is a system API.

**Related module**: [Swapfs](capi-swapfs.md)

**Header file**: [oh_swapfs.h(System API)](capi-oh-swapfs-h-sys.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t totalKeys | Total number of active keys in the manager.<br>**Since**: 26.0.0 |
| uint64_t totalDataSize | Total original data size of all keys in bytes.<br>**Since**: 26.0.0 |
| uint64_t totalOccupiedSize | Total aligned file size of all keys in bytes.<br>**Since**: 26.0.0 |
| uint64_t spaceLimitBytes | Configured swap space limit in bytes.<br>**Since**: 26.0.0 |
| bool featureEnabled | Whether swap-out is currently enabled. False when device space is below 5GB or control policy disables the feature.<br>**Since**: 26.0.0 |
| [OH_SwapfsDisableReason](capi-oh-swapfs-h.md#oh_swapfsdisablereason) disableReason | Reason for feature disablement.<br>**Since**: 26.0.0 |
| uint64_t accumulatedWriteBytes | Accumulated bytes written by successful swap-out operations.<br>**Since**: 26.0.0 |
| int64_t lastSpaceCheckTime | Timestamp of the last device space check (Unix epoch in milliseconds).<br>**Since**: 26.0.0 |
| uint64_t availableDeviceSpace | Cached available device storage space in bytes at the last check time.<br>**Since**: 26.0.0 |


