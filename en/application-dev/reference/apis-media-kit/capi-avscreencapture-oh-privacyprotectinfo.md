# OH_PrivacyProtectInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=a583afba2cef62c7b3bdd0006bc1abde317cbcc2 translatedAt=2026-11-09T06:27:39.143Z pushedAt=2026-11-09T08:39:59.595Z nl=1 -->

```c
typedef struct OH_PrivacyProtectInfo {...} OH_PrivacyProtectInfo
```

## Overview

Defines the privacy protection information.

This method is used to provide privacy protection for system windows and sensitive apps in screen recording scenarios. **systemWindowProtection** controls privacy protection at the system window level, and **sensitiveAppProtection** controls privacy protection at the sensitive app level. Both apply to scenarios where user privacy data needs to be protected during screen recording.

**Since**: 24

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| bool systemWindowProtection | Whether to enable privacy protection for system windows. The value **true** means to enable privacy protection, and **false** means to disable it. The default value is **true**. A system window is a window of a system-level app (such as an input method or notification).<br>**Since:** 24 |
| bool sensitiveAppProtection | Whether to enable privacy protection for sensitive apps. The value **true** means to enable privacy protection, and **false** means to disable it. The default value is **true**. A sensitive app (such as a financial app) is an app that contains user privacy data.<br>**Since:** 24 |
