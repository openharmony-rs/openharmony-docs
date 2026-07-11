# OH_Rect
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=4b1a2f751fcd33c52248528ed8c23a9b2935126b translatedAt=2026-06-23T01:06:38.455Z pushedAt=2026-06-23T06:12:23.715Z -->

```c
typedef struct OH_Rect {...} OH_Rect
```

## Overview

The struct describes the width, height, and image information of the rectangle used for screen capture.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t x | X coordinate of the screen capture rectangle.|
| int32_t y | Y coordinate of the screen capture rectangle.|
| int32_t width | Width of the screen capture rectangle, in px.|
| int32_t height | Height of the screen capture rectangle, in px.|