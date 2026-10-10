# OH_PrivacyProtectInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->

```c
typedef struct OH_PrivacyProtectInfo {...} OH_PrivacyProtectInfo
```

## Overview

Defines the privacy protection information.

This struct is used to protect the privacy of system windows and sensitive apps in screen capture scenarios. The **systemWindowProtection** parameter controls privacy protection for system windows, and the **sensitiveAppProtection** parameter controls privacy protection for sensitive apps. Both methods are applicable to scenarios where user privacy data needs to be protected during screen capture.

**Since**: 24

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| bool systemWindowProtection | Whether to enable privacy protection for system windows. The value **true** means to enable privacy protection, and **false** means the opposite. The default value is **true**. System windows refer to the windows of system-level apps (such as the input method and notification).<br>**Since**: 24|
| bool sensitiveAppProtection | Whether to enable privacy protection for sensitive apps. The value **true** means to enable privacy protection, and **false** means the opposite. The default value is **true**. Sensitive apps (such as financial apps) refer to apps that contain users' private data.<br>**Since**: 24|
