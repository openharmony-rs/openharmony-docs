# OH_PrivacyProtectInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=320793da1b58e6a20565f5e582fc3e50f69572ee translatedAt=2026-06-22T03:38:22.603Z pushedAt=2026-06-22T09:23:26.595Z -->

```c
typedef struct {...} OH_PrivacyProtectInfo
```

## Overview

Defines the privacy protection information.

**Since**: 24

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| bool systemWindowProtection | Whether to enable privacy protection for system windows. The value **true** means to enable privacy protection, and **false** means the opposite.<br>**Since**: 24|
| bool sensitiveAppProtection | Whether to enable privacy protection for sensitive applications. The value **true** means to enable privacy protection, and **false** means the opposite.<br>**Since**: 24|