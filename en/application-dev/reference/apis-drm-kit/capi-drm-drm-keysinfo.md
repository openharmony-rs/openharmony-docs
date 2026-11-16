# DRM_KeysInfo

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=6dec6b14cb206fe02a5ddd5033caa3930c0dd80f translatedAt=2026-11-04T04:16:21.483Z pushedAt=2026-11-04T10:12:50.075Z nl=1 -->

```c
typedef struct DRM_KeysInfo {...} DRM_KeysInfo
```

## Overview

The struct describes the information about media keys.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t keysInfoCount | Number of Media Key information entries, indicating the number of valid elements in the keyId and statusValue arrays. The value ranges from 0 to MAX_KEY_INFO_COUNT. |
| uint8_t keyId[MAX_KEY_INFO_COUNT][MAX_KEY_ID_LEN] | Media Key ID array, where each row stores the identifier of a key. A key ID is used to identify a unique Media Key. The array dimensions are defined by the MAX_KEY_INFO_COUNT and MAX_KEY_ID_LEN macros. |
| char statusValue[MAX_KEY_INFO_COUNT][MAX_KEY_STATUS_VALUE_LEN] | Media Key status value array, where each row stores the key status corresponding to the keyId. The status values are defined by the DRM solution. Common statuses include "usable" (available) and "expired" (expired). The array dimensions are defined by the MAX_KEY_INFO_COUNT and MAX_KEY_STATUS_VALUE_LEN macros. |


