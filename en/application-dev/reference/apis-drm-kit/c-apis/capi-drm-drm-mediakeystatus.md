# DRM_MediaKeyStatus

```c
typedef struct DRM_MediaKeyStatus {...} DRM_MediaKeyStatus
```

## Overview

The struct describes the media key status.

<!--Device-struct DRM_MediaKeyStatus {...}--><!--Device-struct DRM_MediaKeyStatus {...}-End-->

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Related module**: [Drm](capi-drm-kit-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t statusCount | Status count.<br><!--Device-uint32_t statusCount--><!--Device-uint32_t statusCount-End--> |
| char statusName[MAX_MEDIA_KEY_STATUS_COUNT][MAX_MEDIA_KEY_STATUS_NAME_LEN] | Status name.<br><!--Device-char statusName[MAX_MEDIA_KEY_STATUS_COUNT][MAX_MEDIA_KEY_STATUS_NAME_LEN]--><!--Device-char statusName[MAX_MEDIA_KEY_STATUS_COUNT][MAX_MEDIA_KEY_STATUS_NAME_LEN]-End--> |
| char statusValue[MAX_MEDIA_KEY_STATUS_COUNT][MAX_MEDIA_KEY_STATUS_VALUE_LEN] | Status value.<br><!--Device-char statusValue[MAX_MEDIA_KEY_STATUS_COUNT][MAX_MEDIA_KEY_STATUS_VALUE_LEN]--><!--Device-char statusValue[MAX_MEDIA_KEY_STATUS_COUNT][MAX_MEDIA_KEY_STATUS_VALUE_LEN]-End--> |


