# DRM_MediaKeyRequestInfo

```c
typedef struct DRM_MediaKeyRequestInfo {...} DRM_MediaKeyRequestInfo
```

## Overview

The struct describes the information about a media key request.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [DRM_MediaKeyType](capi-native-drm-common-h.md#drm_mediakeytype) type | Type of the media key request. |
| int32_t initDataLen | Length of the initialization data. |
| uint8_t initData[MAX_INIT_DATA_LEN] | PSSH info. |
| char mimeType[MAX_MIMETYPE_LEN] | Media content mime type. |
| uint32_t optionsCount | Number of options. |
| char optionName[MAX_MEDIA_KEY_REQUEST_OPTION_COUNT][MAX_MEDIA_KEY_REQUEST_OPTION_NAME_LEN] | Options name the application set to drm framework. |
| char optionData[MAX_MEDIA_KEY_REQUEST_OPTION_COUNT][MAX_MEDIA_KEY_REQUEST_OPTION_DATA_LEN] | Options data the application set to drm framework. |


