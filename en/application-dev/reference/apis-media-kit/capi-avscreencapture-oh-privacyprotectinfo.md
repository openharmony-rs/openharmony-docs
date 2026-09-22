# OH_PrivacyProtectInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=9f1115d2ccd3978a08359533e231af3da6050977 translatedAt=2026-09-15T16:56:13.148Z pushedAt=2026-09-20T07:03:19.287Z -->

```c
typedef struct OH_PrivacyProtectInfo {...} OH_PrivacyProtectInfo
```

## Overview

Defines the privacy protection information.

This struct is used to protect the privacy of system windows and sensitive apps in screen capture scenarios. By setting the member variables of this struct, you can control whether to enable privacy protection for system windows and sensitive apps, preventing privacy information disclosure during screen capture. The **systemWindowProtection** parameter controls privacy protection for system windows, and the **sensitiveAppProtection** parameter controls privacy protection for sensitive apps. This method is applicable to scenarios where user privacy data needs to be protected during screen capture. For example, during screen capture or screenshot capture, sensitive windows (such as banking apps and chat windows) need to be protected from being captured. Financial apps need to protect sensitive information entered by users. Video conferencing apps need to protect privacy content on the shared screen.

**Since**: 24

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| bool systemWindowProtection | Whether to enable privacy protection for system windows. The value **true** means to enable privacy protection, and **false** means the opposite. The default value is **true**. System windows refer to the windows of system appss (such as Settings and Notifications). This parameter must be configured before screen capture is started. After privacy protection is enabled, the content of such windows will be protected during screen capture. Typical scenarios: During screen capture or sharing, enabling privacy protection can protect privacy information in system windows, such as the notification bar and pop-up windows, from being recorded or shared.<br>**Since:** 24 |
| bool sensitiveAppProtection | Whether to enable privacy protection for sensitive apps. The value **true** means to enable privacy protection, and **false** means the opposite. The default value is **true**. Sensitive apps refer to those that contain user privacy data. This parameter must be configured before screen capture is started. After privacy protection is enabled, the content of such app windows will be protected during screen capture. Typical scenarios: During screen capture or sharing, enabling privacy protection can protect the content of sensitive apps, such as banking and social media apps, from being recorded or shared.<br>**Since:** 24 |
