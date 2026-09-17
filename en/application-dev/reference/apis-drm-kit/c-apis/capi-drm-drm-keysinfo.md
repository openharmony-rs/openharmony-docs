# DRM_KeysInfo

```c
typedef struct DRM_KeysInfo {...} DRM_KeysInfo
```

## Overview

The struct describes the information about media keys.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t keysInfoCount | Keys count. |
| uint8_t keyId[MAX_KEY_INFO_COUNT][MAX_KEY_ID_LEN] | Key id. |
| char statusValue[MAX_KEY_INFO_COUNT][MAX_KEY_STATUS_VALUE_LEN] | Key status value. |


