# OH_MultiDisplayCapability
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=320793da1b58e6a20565f5e582fc3e50f69572ee translatedAt=2026-06-22T03:38:13.068Z pushedAt=2026-06-22T09:23:26.594Z -->

```c
typedef struct OH_MultiDisplayCapability {...} OH_MultiDisplayCapability
```

## Overview

Defines a struct for the multi-screen recording capability. It includes whether the multi-screen supports joint recording and the width and height of the screen for joint recording.

**Since**: 24

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| bool isMultiDisplaySupport | Whether multi-screen recording is supported. **true**: yes; **false**: no.|
| uint32_t width | Width of the screen area that can be recorded, in pixels.|
| uint32_t height | Height of the screen area that can be recorded, in pixels.|