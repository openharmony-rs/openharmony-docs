# OH_PrivacyProtectInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=4b1a2f751fcd33c52248528ed8c23a9b2935126b translatedAt=2026-06-23T01:06:29.024Z pushedAt=2026-06-23T06:12:23.713Z -->

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