# DRM_MediaKeyRequest

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=6dec6b14cb206fe02a5ddd5033caa3930c0dd80f translatedAt=2026-11-04T04:16:52.657Z pushedAt=2026-11-04T10:12:50.079Z nl=1 -->

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
| [DRM_MediaKeyRequestType](capi-native-drm-common-h.md#drm_mediakeyrequesttype) type | Media key request type, indicating the purpose of the request. Common types include **DRM_MEDIA_KEY_REQUEST_TYPE_INITIAL** (initial request), DRM_MEDIA_KEY_REQUEST_TYPE_RENEWAL (renewal request), and so on. The specific type is determined by the DRM Solution. |
| int32_t dataLen | Length of the media key request data, indicating the number of valid data bytes in the data array. The unit is byte, and the value ranges from 0 to MAX_MEDIA_KEY_REQUEST_DATA_LEN. |
| uint8_t data[MAX_MEDIA_KEY_REQUEST_DATA_LEN] | Media key request data to be sent to the license server. The data format is defined by the DRM Solution, typically binary data in a specific format or JSON format. The array length is defined by the MAX_MEDIA_KEY_REQUEST_DATA_LEN macro. |
| char defaultUrl[MAX_DEFAULT_URL_LEN] | Default URL of the license server, used to obtain the media key. This URL is provided by the DRM Solution. The application can use this URL or a custom URL to send requests. The array length is defined by the MAX_DEFAULT_URL_LEN macro. |


