# Drm

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=a9776cf91359a852d7804f0b36513c7852570375 translatedAt=2026-11-03T13:16:37.837Z pushedAt=2026-11-04T08:46:18.915Z nl=2 -->

## Overview

The Digital Rights Management (DRM) module provides APIs for digital rights protection.

You can refer to the development guide and samples based on your development requirements:

- [DRM Development (C/C++)](../../media/drm/drm-c-dev-guide.md)
- [DRM Playback with AVCodec (C/C++)](../../media/drm/drm-avcodec-integration.md)


**Since**: 11

## Files

| Name| Description|
| -- | -- |
| [native_drm_common.h](capi-native-drm-common-h.md) | Defines the DRM data types, including core data structures such as media key requests, content protection levels, and certificate status, to support the development of DRM (Digital Rights Management) capabilities and help applications implement the playback and management of copyright-protected multimedia content. |
| [native_drm_err.h](capi-native-drm-err-h.md) | Defines the DRM error codes, which are used to identify various exceptions that may occur during the running of the DRM module. Developers can perform error handling and problem locating based on the error codes to improve the stability and maintainability of DRM applications. This is applicable to scenarios where DRM capability exceptions need to be handled. |
| [native_mediakeysession.h](capi-native-mediakeysession-h.md) | Defines the DRM MediaKeySession APIs. Provides the following functions:<br>generates media key requests, processes media key responses, listens for events, obtains the content protection level, checks the media key status, deletes media keys, and so on. |
| [native_mediakeysystem.h](capi-native-mediakeysystem-h.md) | Defines the DRM MediaKeySystem APIs. Provides the following functions:<br>queries whether a specific DRM scheme is supported, creates media key sessions, obtains and sets configurations, obtains statistics, obtains the content protection level, generates provisioning requests, processes provisioning responses, listens for events, manages offline media keys, and so on. |
