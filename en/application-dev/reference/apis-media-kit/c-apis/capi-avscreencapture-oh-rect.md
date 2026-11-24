# OH_Rect

```c
typedef struct OH_Rect {...} OH_Rect
```

## Overview

The struct describes the width, height, and image information of the rectangle used for screen capture.

<!--Device-struct OH_Rect {...}--><!--Device-struct OH_Rect {...}-End-->

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 10

**Related module**: [AVScreenCapture](capi-media-kit-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t x | X-coordinate of screen recording<br><!--Device-int32_t x--><!--Device-int32_t x-End--> |
| int32_t y | y-coordinate of screen recording<br><!--Device-int32_t y--><!--Device-int32_t y-End--> |
| int32_t width | Width of screen recording, in px<br><!--Device-int32_t width--><!--Device-int32_t width-End--> |
| int32_t height | Height of screen recording, in px<br><!--Device-int32_t height--><!--Device-int32_t height-End--> |


