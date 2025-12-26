# DRM_MediaKeySystemDescription
<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qin_wei_jie-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct DRM_MediaKeySystemDescription {...} DRM_MediaKeySystemDescription
```

## Overview

The struct describes the DRM solution name and UUID list.

**Since**: 12

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| char name[MAX_MEDIA_KEY_SYSTEM_NAME_LEN] | Name of the DRM plugin.|
| uint8_t uuid[DRM_UUID_LEN] | UUID of the DRM plugin.|
