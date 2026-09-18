# DRM_Statistics

```c
typedef struct DRM_Statistics {...} DRM_Statistics
```

## Overview

The struct describes the metrics for a media key system.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t statisticsCount | Statistics count. |
| char statisticsName[MAX_STATISTICS_COUNT][MAX_STATISTICS_NAME_LEN] | Statistics name. |
| char statisticsDescription[MAX_STATISTICS_COUNT][MAX_STATISTICS_BUFFER_LEN] | Statistics description. |


