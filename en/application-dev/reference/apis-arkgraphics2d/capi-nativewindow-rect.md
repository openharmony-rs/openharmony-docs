# Rect

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=c9742d4d4a757fbb6f0510281af0e732af135c64 translatedAt=2026-08-24T09:17:33.279Z pushedAt=2026-08-25T07:19:41.332Z -->

```c
struct Rect { ... }
```

## Overview

If **rects** is a null pointer, the buffer size is the same as the size of the dirty region by default.

**Related module**: [NativeWindow](capi-nativewindow.md)

**Header file**: [external_window.h](capi-external-window-h.md)

## Summary

### Member Variables

| Name      | Description             |
| ---------- | ----------------- |
| int32_t x  | Start X coordinate of the rectangle.|
| int32_t y  | Start Y coordinate of the rectangle.|
| uint32_t w | Width of the rectangle.     |
| uint32_t h | Height of the rectangle.     |