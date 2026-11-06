# OH_Rect
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=7cb32cf558e3c75482fc3404f1f7c011a4ecb00a translatedAt=2026-09-15T16:57:16.881Z pushedAt=2026-09-20T07:28:06.504Z -->

```c
typedef struct OH_Rect {...} OH_Rect
```

## Overview

Defines the position and size of the screen capture area, including the position coordinates and size information. This struct can be used to precisely control the screen capture scope, supporting scenarios such as customizing an area for screen capture and partial screen capture.

This method is applicable to scenarios such as recording only the key operation area during teaching/demo recording, recording only the presentation area during conference recording, and recording only the game screen during game recording.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t x | X coordinate of the screen capture rectangle, relative to the upper left corner of the screen. The value must be greater than or equal to 0, in pixels. |
| int32_t y | Y coordinate of the screen capture rectangle, relative to the upper left corner of the screen. The value must be greater than or equal to 0, in pixels. |
| int32_t width | Width of the screen capture rectangle. The value must be greater than 0, in pixels. If **0** or a negative number is passed, screen capture does not take effect. |
| int32_t height | Height of the screen capture rectangle. The value must be greater than 0, in pixels. If **0** or a negative number is passed, screen capture does not take effect. |


