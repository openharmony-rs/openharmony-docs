# OH_AVScreenCaptureHighlightConfig
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=7cb32cf558e3c75482fc3404f1f7c011a4ecb00a translatedAt=2026-09-15T16:54:38.105Z pushedAt=2026-09-20T03:43:56.736Z -->

```c
typedef struct OH_AVScreenCaptureHighlightConfig {...} OH_AVScreenCaptureHighlightConfig
```

## Overview

Describes the style of the highlight border shown during screen capture, including its shape, thickness, and color. This struct is used to mark the boundary of the screen capture area. By configuring the highlight border, users can clearly distinguish between the screen capture area and the non-screen capture area, improving the screen capture interaction experience. This configuration is typically used to highlight specific areas in screen capture scenarios. For example, it can be used to highlight the operation area when recording an operation tutorial, emphasize key content when recording an app demo, or mark the follow area when recording a game.

**Since**: 22

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_ScreenCaptureHighlightMode](capi-native-avscreen-capture-base-h.md#oh_screencapturehighlightmode) mode | Display modes of the highlight border. For details about the enumerated values and the mapping between the enumerated values and numbers, see [OH_ScreenCaptureHighlightMode](capi-native-avscreen-capture-base-h.md#oh_screencapturehighlightmode). **OH_HIGHLIGHT_MODE_CLOSED = 0**: applicable to common recording scenarios, with a more obvious highlight effect. **OH_HIGHLIGHT_MODE_CORNER_WRAP = 1**: applicable to scenarios where visual interference needs to be reduced. If this parameter is not specified, **OH_HIGHLIGHT_MODE_CLOSED = 0** is used by default, that is, the border completely surrounds all sides of the capture area. For other modes, select one based on the display requirements of the screen capture area. |
| uint32_t lineThickness | Width of the highlight border. If this parameter is not set, the border is invisible by default, that is, the line width is 0 or the border is not drawn. The valid value range is [1, 8], in virtual pixels (vp). If the value is out of the range, the setting does not take effect. After the setting, a highlight border with the specified width is drawn around the screen capture area. A larger width indicates a thicker border. |
| uint32_t lineColor | Color of the border line. The default value is black (0x000000). Valid values are in RGB (0x000000-0xffffff) or non-transparent ARGB (0xff000000-0xffffffff) format. If the value is out of the range, the setting does not take effect. After the setting, a highlight border with the specified color is drawn around the screen capture area. This parameter can be used to distinguish different screen capture areas or improve visibility. |