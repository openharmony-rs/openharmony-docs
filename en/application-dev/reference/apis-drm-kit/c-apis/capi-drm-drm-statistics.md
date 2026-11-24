# DRM_Statistics

```c
typedef struct DRM_Statistics {...} DRM_Statistics
```

## Overview

The struct describes the metrics for a media key system.

<!--Device-struct DRM_Statistics {...}--><!--Device-struct DRM_Statistics {...}-End-->

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Related module**: [Drm](capi-drm-kit-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t statisticsCount | Statistics count.<br><!--Device-uint32_t statisticsCount--><!--Device-uint32_t statisticsCount-End--> |
| char statisticsName[MAX_STATISTICS_COUNT][MAX_STATISTICS_NAME_LEN] | Statistics name.<br><!--Device-char statisticsName[MAX_STATISTICS_COUNT][MAX_STATISTICS_NAME_LEN]--><!--Device-char statisticsName[MAX_STATISTICS_COUNT][MAX_STATISTICS_NAME_LEN]-End--> |
| char statisticsDescription[MAX_STATISTICS_COUNT][MAX_STATISTICS_BUFFER_LEN] | Statistics description.<br><!--Device-char statisticsDescription[MAX_STATISTICS_COUNT][MAX_STATISTICS_BUFFER_LEN]--><!--Device-char statisticsDescription[MAX_STATISTICS_COUNT][MAX_STATISTICS_BUFFER_LEN]-End--> |


