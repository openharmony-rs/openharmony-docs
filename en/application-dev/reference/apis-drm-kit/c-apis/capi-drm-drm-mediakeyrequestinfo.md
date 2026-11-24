# DRM_MediaKeyRequestInfo

```c
typedef struct DRM_MediaKeyRequestInfo {...} DRM_MediaKeyRequestInfo
```

## Overview

The struct describes the information about a media key request.

<!--Device-struct DRM_MediaKeyRequestInfo {...}--><!--Device-struct DRM_MediaKeyRequestInfo {...}-End-->

**System capability**: SystemCapability.Multimedia.Drm.Core

**Since**: 11

**Related module**: [Drm](capi-drm-kit-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [DRM_MediaKeyType](capi-native-drm-common-h.md#drm_mediakeytype) type | Type of the media key request.<br><!--Device-DRM_MediaKeyType type--><!--Device-DRM_MediaKeyType type-End--> |
| int32_t initDataLen | Length of the initialization data.<br><!--Device-int32_t initDataLen--><!--Device-int32_t initDataLen-End--> |
| uint8_t initData[MAX_INIT_DATA_LEN] | PSSH info.<br><!--Device-uint8_t initData[MAX_INIT_DATA_LEN]--><!--Device-uint8_t initData[MAX_INIT_DATA_LEN]-End--> |
| char mimeType[MAX_MIMETYPE_LEN] | Media content mime type.<br><!--Device-char mimeType[MAX_MIMETYPE_LEN]--><!--Device-char mimeType[MAX_MIMETYPE_LEN]-End--> |
| uint32_t optionsCount | Number of options.<br><!--Device-uint32_t optionsCount--><!--Device-uint32_t optionsCount-End--> |
| char optionName[MAX_MEDIA_KEY_REQUEST_OPTION_COUNT][MAX_MEDIA_KEY_REQUEST_OPTION_NAME_LEN] | Options name the application set to drm framework.<br><!--Device-char optionName[MAX_MEDIA_KEY_REQUEST_OPTION_COUNT][MAX_MEDIA_KEY_REQUEST_OPTION_NAME_LEN]--><!--Device-char optionName[MAX_MEDIA_KEY_REQUEST_OPTION_COUNT][MAX_MEDIA_KEY_REQUEST_OPTION_NAME_LEN]-End--> |
| char optionData[MAX_MEDIA_KEY_REQUEST_OPTION_COUNT][MAX_MEDIA_KEY_REQUEST_OPTION_DATA_LEN] | Options data the application set to drm framework.<br><!--Device-char optionData[MAX_MEDIA_KEY_REQUEST_OPTION_COUNT][MAX_MEDIA_KEY_REQUEST_OPTION_DATA_LEN]--><!--Device-char optionData[MAX_MEDIA_KEY_REQUEST_OPTION_COUNT][MAX_MEDIA_KEY_REQUEST_OPTION_DATA_LEN]-End--> |


