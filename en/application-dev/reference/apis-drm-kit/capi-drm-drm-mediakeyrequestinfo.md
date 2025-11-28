# DRM_MediaKeyRequestInfo

## Overview

The struct describes the information about a media key request.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [DRM_MediaKeyType](capi-native-drm-common-h.md#drm_mediakeytype) type | Type of the media key request.|
| int32_t initDataLen | Length of the initialization data.|
| uint8_t initData[MAX_INIT_DATA_LEN] | Initialization data in PSSH format (Base64-decoded).|
| char mimeType[MAX_MIMETYPE_LEN] | MIME type of the media content.|
| uint32_t optionsCount | Number of options.|
| char optionName[MAX_MEDIA_KEY_REQUEST_OPTION_COUNT][MAX_MEDIA_KEY_REQUEST_OPTION_NAME_LEN] | Array of option names.|
| char optionData[MAX_MEDIA_KEY_REQUEST_OPTION_COUNT][MAX_MEDIA_KEY_REQUEST_OPTION_DATA_LEN] | Array of option values.|
