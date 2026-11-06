# MediaKeySession

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=21259e195bf1b8fc84db30d7d959f8dc56433790 translatedAt=2026-11-03T06:46:32.836Z pushedAt=2026-11-04T03:11:19.910Z nl=1 -->

```c
typedef struct MediaKeySession MediaKeySession
```

## Overview

The MediaKeySession struct represents a media key session instance. MediaKeySession is the core component of the DRM decryption process, responsible for generating license requests, processing license responses, and managing key states. Each MediaKeySession instance corresponds to the key decryption process of a playback session.

An instance is created through the OH_MediaKeySystem_CreateMediaKeySession API and destroyed through the OH_MediaKeySession_Destroy API. Each MediaKeySystem can create multiple MediaKeySession instances to handle different playback sessions.

**Since**: 11

**Related module**: [Drm](capi-drm.md)

**Header file**: [native_drm_common.h](capi-native-drm-common-h.md)

