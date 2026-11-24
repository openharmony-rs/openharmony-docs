# DRM_OfflineMediakeyIdArray

```c
typedef struct DRM_OfflineMediakeyIdArray {...} DRM_OfflineMediakeyIdArray
```

## Overview

The struct describes an array of offline media key IDs.

<!--Device-struct DRM_OfflineMediakeyIdArray {...}--><!--Device-struct DRM_OfflineMediakeyIdArray {...}-End-->

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Related module**: [Drm](capi-drm-kit-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t idsCount | Ids count.<br><!--Device-uint32_t idsCount--><!--Device-uint32_t idsCount-End--> |
| int32_t idsLen[MAX_OFFLINE_MEDIA_KEY_ID_COUNT] | Ids len.<br><!--Device-int32_t idsLen[MAX_OFFLINE_MEDIA_KEY_ID_COUNT]--><!--Device-int32_t idsLen[MAX_OFFLINE_MEDIA_KEY_ID_COUNT]-End--> |
| uint8_t ids[MAX_OFFLINE_MEDIA_KEY_ID_COUNT][MAX_OFFLINE_MEDIA_KEY_ID_LEN] | Ids.<br><!--Device-uint8_t ids[MAX_OFFLINE_MEDIA_KEY_ID_COUNT][MAX_OFFLINE_MEDIA_KEY_ID_LEN]--><!--Device-uint8_t ids[MAX_OFFLINE_MEDIA_KEY_ID_COUNT][MAX_OFFLINE_MEDIA_KEY_ID_LEN]-End--> |


