# DRM_MediaKeyRequest

```c
typedef struct DRM_MediaKeyRequest {...} DRM_MediaKeyRequest
```

## Overview

The struct describes a media key request.

<!--Device-struct DRM_MediaKeyRequest {...}--><!--Device-struct DRM_MediaKeyRequest {...}-End-->

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Related module**: [Drm](capi-drm-kit-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [DRM_MediaKeyRequestType](capi-native-drm-common-h.md#drm_mediakeyrequesttype) type | Type of the media key request.<br><!--Device-DRM_MediaKeyRequestType type--><!--Device-DRM_MediaKeyRequestType type-End--> |
| int32_t dataLen | Length of data in the media key request.<br><!--Device-int32_t dataLen--><!--Device-int32_t dataLen-End--> |
| uint8_t data[MAX_MEDIA_KEY_REQUEST_DATA_LEN] | Media key request data sent to media key server.<br><!--Device-uint8_t data[MAX_MEDIA_KEY_REQUEST_DATA_LEN]--><!--Device-uint8_t data[MAX_MEDIA_KEY_REQUEST_DATA_LEN]-End--> |
| char defaultUrl[MAX_DEFAULT_URL_LEN] | Media key server URL.<br><!--Device-char defaultUrl[MAX_DEFAULT_URL_LEN]--><!--Device-char defaultUrl[MAX_DEFAULT_URL_LEN]-End--> |


