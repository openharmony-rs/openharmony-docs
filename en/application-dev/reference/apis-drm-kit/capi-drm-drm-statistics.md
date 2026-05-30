# DRM_Statistics
<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qin_wei_jie-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct DRM_Statistics {...} DRM_Statistics
```

## Overview

The struct describes the metrics for a media key system.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t statisticsCount | Number of metrics.|
| char statisticsName[MAX_STATISTICS_COUNT][MAX_STATISTICS_NAME_LEN] | Array of metric names.|
| char statisticsDescription[MAX_STATISTICS_COUNT][MAX_STATISTICS_BUFFER_LEN] | Array of metric descriptions.|
