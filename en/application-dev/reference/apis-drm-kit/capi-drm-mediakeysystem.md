# MediaKeySystem

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=ad59843e50284b5e122a86c5f91046ab9ac62787 translatedAt=2026-11-04T04:21:49.996Z pushedAt=2026-11-04T10:12:50.094Z nl=1 -->

```c
typedef struct MediaKeySystem MediaKeySystem
```

## Overview

The MediaKeySystem struct represents a media key system instance. MediaKeySystem provides digital rights protection capabilities and is responsible for DRM plugin configuration management, device certificate management, statistics retrieval, content protection level query, and creation of MediaKeySession instances. An instance is created through the OH_MediaKeySystem_Create API and destroyed through the OH_MediaKeySystem_Destroy API.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

