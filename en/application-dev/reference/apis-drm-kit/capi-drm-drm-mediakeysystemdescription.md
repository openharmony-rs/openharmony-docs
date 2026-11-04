# DRM_MediaKeySystemDescription

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=21259e195bf1b8fc84db30d7d959f8dc56433790 translatedAt=2026-11-03T06:44:37.319Z pushedAt=2026-11-04T03:11:19.899Z nl=1 -->

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
| char name[MAX_MEDIA_KEY_SYSTEM_NAME_LEN] | Name of the DRM plugin, used to uniquely identify a DRM solution. The name format is defined by the DRM solution, for example, "com.widevine.alpha" and "com.microsoft.playready". The array length is defined by the MAX_MEDIA_KEY_SYSTEM_NAME_LEN macro. |
| uint8_t uuid[DRM_UUID_LEN] | UUID (universally unique identifier) of the DRM system, used to uniquely identify a DRM content protection system. The UUID is 16 bytes long (DRM_UUID_LEN) and is assigned by the DRM solution provider. The UUID and name are different representations of the same DRM solution. |


