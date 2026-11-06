# DRM_OfflineMediakeyIdArray

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=22e2ea45656c6b22d0cbeef89896d28b00f5fdcf translatedAt=2026-11-03T06:45:22.809Z pushedAt=2026-11-04T03:11:19.902Z nl=1 -->

```c
typedef struct DRM_OfflineMediakeyIdArray {...} DRM_OfflineMediakeyIdArray
```

## Overview

The struct describes an array of offline media key IDs.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t idsCount | Number of offline media key IDs, that is, the number of valid elements in the idsLen and ids arrays. The value ranges from 0 to MAX_OFFLINE_MEDIA_KEY_ID_COUNT. |
| int32_t idsLen[MAX_OFFLINE_MEDIA_KEY_ID_COUNT] | Array of offline media key ID lengths. Each element indicates the number of bytes of valid data in the corresponding row of the ids array. The array length is defined by the MAX_OFFLINE_MEDIA_KEY_ID_COUNT macro. |
| uint8_t ids[MAX_OFFLINE_MEDIA_KEY_ID_COUNT][MAX_OFFLINE_MEDIA_KEY_ID_LEN] | Array of offline media key ID data, used to store the identifiers of offline media keys. Each row stores one key ID, and the valid length is specified by the corresponding element in idsLen. The array dimensions are defined by the MAX_OFFLINE_MEDIA_KEY_ID_COUNT and MAX_OFFLINE_MEDIA_KEY_ID_LEN macros. |


