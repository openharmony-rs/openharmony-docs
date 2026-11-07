# DRM_MediaKeyRequestInfo

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=142c2eda94ab15437220607a462d17616dde4d9f translatedAt=2026-11-04T04:19:04.408Z pushedAt=2026-11-04T10:12:50.077Z nl=1 -->

```c
typedef struct DRM_MediaKeyRequestInfo {...} DRM_MediaKeyRequestInfo
```

## Overview

The struct describes the information about a media key request.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [DRM_MediaKeyType](capi-native-drm-common-h.md#drm_mediakeytype) type | Media key type, which specifies the purpose of the requested key. The value is MEDIA_KEY_TYPE_ONLINE (online streaming) or MEDIA_KEY_TYPE_OFFLINE (offline playback). |
| int32_t initDataLen | Length of the initialization data, indicating the number of valid data bytes in the initData array. The unit is byte, and the value range is [1, MAX_INIT_DATA_LEN]. |
| uint8_t initData[MAX_INIT_DATA_LEN] | Initialization data, which contains data in the Protection System Specific Header (PSSH) format of the DRM content protection system. It is usually extracted from the PSSH box of the media content and must be base64-decoded before being passed in. The array length is defined by the MAX_INIT_DATA_LEN macro. |
| char mimeType[MAX_MIMETYPE_LEN] | MIME type of the media content, used to identify the format of the media content. Common values include "video/mp4" and "video/webm". The specific supported types are determined by the DRM solution. The array length is defined by the MAX_MIMETYPE_LEN macro. |
| uint32_t optionsCount | Number of option data entries, indicating the number of valid elements in the optionName and optionData arrays. The value range is [0, MAX_MEDIA_KEY_REQUEST_OPTION_COUNT]. |
| char optionName[MAX_MEDIA_KEY_REQUEST_OPTION_COUNT][MAX_MEDIA_KEY_REQUEST_OPTION_NAME_LEN] | Array of option names, where each row stores the name of an option. The option names are defined by the DRM solution and are used to pass specific request parameters. The array dimensions are defined by the MAX_MEDIA_KEY_REQUEST_OPTION_COUNT and MAX_MEDIA_KEY_REQUEST_OPTION_NAME_LEN macros. |
| char optionData[MAX_MEDIA_KEY_REQUEST_OPTION_COUNT][MAX_MEDIA_KEY_REQUEST_OPTION_DATA_LEN] | Array of option data, where each row stores the option value corresponding to optionName. The array dimensions are defined by the MAX_MEDIA_KEY_REQUEST_OPTION_COUNT and MAX_MEDIA_KEY_REQUEST_OPTION_DATA_LEN macros. |


