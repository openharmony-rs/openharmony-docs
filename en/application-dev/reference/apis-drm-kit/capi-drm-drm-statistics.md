# DRM_Statistics

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=ba8f8ec3732f6ac3adf87c08b1dddb02b0ee3961 translatedAt=2026-11-03T06:46:01.861Z pushedAt=2026-11-04T03:11:19.907Z nl=1 -->

```c
typedef struct DRM_Statistics {...} DRM_Statistics
```

## Overview

Metric information of the MediaKeySystem.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t statisticsCount | Number of metric information items, indicating the number of valid elements in the statisticsName and statisticsDescription arrays. The value ranges from 0 to MAX_STATISTICS_COUNT. |
| char statisticsName[MAX_STATISTICS_COUNT][MAX_STATISTICS_NAME_LEN] | Array of metric information names. Each row stores the name of a metric item, such as "DecryptionOperations" (number of decryption operations) and "KeySessions" (number of key sessions). The array dimensions are defined by the MAX_STATISTICS_COUNT and MAX_STATISTICS_NAME_LEN macros. |
| char statisticsDescription[MAX_STATISTICS_COUNT][MAX_STATISTICS_BUFFER_LEN] | Array of metric information descriptions. Each row stores the metric value corresponding to statisticsName. The description content usually contains numeric values, percentages, or statistical data in other formats. The array dimensions are defined by the MAX_STATISTICS_COUNT and MAX_STATISTICS_BUFFER_LEN macros. |


