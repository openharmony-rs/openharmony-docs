# OH_PrivacyProtectInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zzs_911-->
<!--Designer: @stupig001-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

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
