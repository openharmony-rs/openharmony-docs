# Drm

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=2f1838c94ba23f5801be4827f23104e2625c8079 translatedAt=2026-11-03T06:47:42.779Z pushedAt=2026-11-04T03:11:19.920Z nl=2 -->

## Overview

The Digital Rights Management (DRM) module provides APIs for digital rights protection.

You can refer to the development guide and samples based on your development requirements:

- [DRM Development (C/C++)](../../media/drm/drm-c-dev-guide.md)
- [DRM Playback with AVCodec (C/C++)](../../media/drm/drm-avcodec-integration.md)


**Since**: 11

## Files

| Name| Description|
| -- | -- |
| [native_drm_common.h](capi-native-drm-common-h.md) | Defines DRM data types, including core data structures such as media key request, content protection level, and certificate status, to support the development of DRM (Digital Rights Management) features and help applications play and manage copyright-protected multimedia content. |
| [native_drm_err.h](capi-native-drm-err-h.md) | Defines DRM error codes, used to identify various exceptions that may occur during the operation of the DRM module. Developers can perform error handling and problem locating based on error codes to improve the stability and maintainability of DRM applications. This applies to scenarios where DRM feature exceptions need to be handled. |
| [native_mediakeysession.h](capi-native-mediakeysession-h.md) | Defines the DRM MediaKeySession API. Provides the following functions:<br>Generates media key requests, processes media key responses, listens for events, obtains the content protection level, checks the media key status, deletes media keys, and so on. |
| [native_mediakeysystem.h](capi-native-mediakeysystem-h.md) | Defines the DRM MediaKeySystem API. Provides the following functions:<br>Queries whether a specific DRM is supported, creates media key sessions, obtains and sets configurations, obtains statistics, obtains the content protection level, generates provisioning requests, processes provisioning responses, listens for events, manages offline media keys, and so on. |
