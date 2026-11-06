# MediaKeySystem

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=5a524fc5f898cdc9aaa2066d0f83d9a63c748249 translatedAt=2026-11-03T06:46:55.682Z pushedAt=2026-11-04T03:11:19.912Z nl=1 -->

```c
typedef struct MediaKeySystem MediaKeySystem
```

## Overview

The MediaKeySystem struct represents a media key system instance. MediaKeySystem provides digital rights protection capabilities and is responsible for DRM plugin configuration management, device certificate management, statistics retrieval, content protection level query, and creation of MediaKeySession instances. An instance is created through the OH_MediaKeySystem_Create API and destroyed through the OH_MediaKeySystem_Destroy API.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

