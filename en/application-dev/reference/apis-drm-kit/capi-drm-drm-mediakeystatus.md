# DRM_MediaKeyStatus

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=6dec6b14cb206fe02a5ddd5033caa3930c0dd80f translatedAt=2026-11-04T04:19:22.862Z pushedAt=2026-11-04T10:12:50.083Z nl=1 -->

```c
typedef struct DRM_MediaKeyStatus {...} DRM_MediaKeyStatus
```

## Overview

The struct describes the media key status.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t statusCount | Number of media key status items, indicating the number of valid elements in the statusName and statusValue arrays. The value range is [0, MAX_MEDIA_KEY_STATUS_COUNT]. |
| char statusName[MAX_MEDIA_KEY_STATUS_COUNT][MAX_MEDIA_KEY_STATUS_NAME_LEN] | Array of media key status names, with each row storing the name of a status. Common status names include "Usable", "Expired", "OutputRestricted", and so on, which are defined by the DRM solution. The array dimensions are defined by the MAX_MEDIA_KEY_STATUS_COUNT and MAX_MEDIA_KEY_STATUS_NAME_LEN macros. |
| char statusValue[MAX_MEDIA_KEY_STATUS_COUNT][MAX_MEDIA_KEY_STATUS_VALUE_LEN] | Array of media key status values, with each row storing the status value corresponding to statusName. The status value format is defined by the DRM solution and may contain information such as timestamps and levels. The array dimensions are defined by the MAX_MEDIA_KEY_STATUS_COUNT and MAX_MEDIA_KEY_STATUS_VALUE_LEN macros. |


