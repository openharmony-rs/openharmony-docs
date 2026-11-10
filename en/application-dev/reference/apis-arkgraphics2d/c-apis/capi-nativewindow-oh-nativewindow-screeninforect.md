# OH_NativeWindow_ScreenInfoRect

```c
struct OH_NativeWindow_ScreenInfoRect {...}
```

## Overview

Describes a rectangle with int32_t coordinates and dimensions.<br> Used by SET_SCREEN_INFO and GET_SCREEN_INFO operation codes of [OH_NativeWindow_NativeWindowHandleOpt](capi-external-window-h.md#oh_nativewindow_nativewindowhandleopt) to carry per-frame offset/size and original-in-screen offset/size.

<!--Device-struct OH_NativeWindow_ScreenInfoRect {...}--><!--Device-struct OH_NativeWindow_ScreenInfoRect {...}-End-->

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 26.1.0

**Related module**: [NativeWindow](capi-arkgraphics2d-nativewindow.md)

**Header file**: [external_window.h](capi-external-window-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t x | x offset in pixels<br>**Since**: 26.1.0 |
| int32_t y | y offset in pixels<br>**Since**: 26.1.0 |
| int32_t w | width in pixels<br>**Since**: 26.1.0 |
| int32_t h | height in pixels<br>**Since**: 26.1.0 |


