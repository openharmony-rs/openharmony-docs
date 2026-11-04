# DRM_MediaKeySystemInfo

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=6dec6b14cb206fe02a5ddd5033caa3930c0dd80f translatedAt=2026-11-03T13:13:37.066Z pushedAt=2026-11-04T08:45:42.827Z nl=1 -->

```c
typedef struct DRM_MediaKeySystemInfo {...} DRM_MediaKeySystemInfo
```

## Overview

The struct describes the DRM information for encrypted content.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t psshCount | Number of PSSH entries, indicating the number of valid elements in the psshInfo array. A media file may contain PSSH entries of multiple DRM systems. The value ranges from 0 to MAX_PSSH_INFO_COUNT. |
| [DRM_PsshInfo](capi-drm-drm-psshinfo.md) psshInfo[MAX_PSSH_INFO_COUNT] | Array of PSSH entries. Each entry contains the information of a DRM content protection system-specific header. The array length is defined by the MAX_PSSH_INFO_COUNT macro. Each entry contains the DRM system UUID and initialization data. |


