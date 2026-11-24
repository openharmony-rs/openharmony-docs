# OH_AVScreenCaptureHighlightConfig

```c
typedef struct OH_AVScreenCaptureHighlightConfig {...} OH_AVScreenCaptureHighlightConfig
```

## Overview

The struct describes the style of the highlight border shown during screen capture, including its shape, thickness, and color.

<!--Device-struct OH_AVScreenCaptureHighlightConfig {...}--><!--Device-struct OH_AVScreenCaptureHighlightConfig {...}-End-->

**System capability**: SystemCapability.Multimedia.Media.AVScreenCapture

**Since**: 22

**Related module**: [AVScreenCapture](capi-media-kit-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_ScreenCaptureHighlightMode](capi-native-avscreen-capture-base-h.md#oh_screencapturehighlightmode) mode | Shape of the highlight border. If this variable is not set, a full rectangle is used by default.<br><!--Device-OH_ScreenCaptureHighlightMode mode--><!--Device-OH_ScreenCaptureHighlightMode mode-End--> |
| uint32_t lineThickness | Thickness of the border line. If this variable is not set, the border is invisible by default. The valid value range is 1 vp to 8 vp.<br><!--Device-uint32_t lineThickness--><!--Device-uint32_t lineThickness-End--> |
| uint32_t lineColor | Color of the border line. The default value is black. Valid values are in RGB (0-0xffffff) or non-transparent ARGB (0xff000000-0xffffffff) format.<br><!--Device-uint32_t lineColor--><!--Device-uint32_t lineColor-End--> |


