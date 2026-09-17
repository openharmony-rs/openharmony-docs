# DRM_OfflineMediakeyIdArray

```c
typedef struct DRM_OfflineMediakeyIdArray {...} DRM_OfflineMediakeyIdArray
```

## Overview

The struct describes an array of offline media key IDs.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t idsCount | Ids count. |
| int32_t idsLen[MAX_OFFLINE_MEDIA_KEY_ID_COUNT] | Ids len. |
| uint8_t ids[MAX_OFFLINE_MEDIA_KEY_ID_COUNT][MAX_OFFLINE_MEDIA_KEY_ID_LEN] | Ids. |


