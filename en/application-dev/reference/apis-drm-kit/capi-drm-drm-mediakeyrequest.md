# DRM_MediaKeyRequest
<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qin_wei_jie-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct DRM_MediaKeyRequest {...} DRM_MediaKeyRequest
```

## Overview

The struct describes a media key request.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [DRM_MediaKeyRequestType](capi-native-drm-common-h.md#drm_mediakeyrequesttype) type | Type of the media key request.|
| int32_t dataLen | Length of data in the media key request.|
| uint8_t data[MAX_MEDIA_KEY_REQUEST_DATA_LEN] | Data in the media key request.|
| char defaultUrl[MAX_DEFAULT_URL_LEN] | URL of the media key server to which the media key request is sent.|
