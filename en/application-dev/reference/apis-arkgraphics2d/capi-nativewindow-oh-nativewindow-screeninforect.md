# OH_NativeWindow_ScreenInfoRect
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=a100856430377b9a5ee0bd89073e8514d4ec7990 translatedAt=2026-11-14T08:10:39.173Z pushedAt=2026-11-14T08:14:20.064Z nl=2 -->

```c
typedef struct OH_NativeWindow_ScreenInfoRect {...} OH_NativeWindow_ScreenInfoRect
```

## Overview

Defines a rectangle object that contains coordinate and dimension information, used to describe a screen area.

**Since:** 26.1.0

**Related module**: [NativeWindow](capi-nativewindow.md)

**Header file**: [external_window.h](capi-external-window-h.md)

## Summary

### Member Variables

| Name       | Description              |
| ---------- | ----------------- |
| int32_t x  | X-axis coordinate of the rectangle object. |
| int32_t y  | Y-axis coordinate of the rectangle object. |
| int32_t w | Width of the rectangle object.      |
| int32_t h | Height of the rectangle object.      |
