# OH_AVScreenCaptureHighlightConfig
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zzs_911-->
<!--Designer: @stupig001-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

## Overview

The struct describes the style of the highlight border shown during screen capture, including its shape, thickness, and color.

**Since**: 22

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_ScreenCaptureHighlightMode](capi-native-avscreen-capture-base-h.md#oh_screencapturehighlightmode) mode | Shape of the highlight border. If this variable is not set, a full rectangle is used by default.|
| uint32_t lineThickness | Thickness of the border line. If this variable is not set, the border is invisible by default. The valid value range is 1 vp to 8 vp.|
| uint32_t lineColor | Color of the border line. The default value is black. Valid values are in RGB (0-0xffffff) or non-transparent ARGB (0xff000000-0xffffffff) format.|
