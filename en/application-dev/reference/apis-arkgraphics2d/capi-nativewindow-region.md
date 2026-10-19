# Region

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=094ced2c1714888f81b48ee277d1e52615f35dc2 translatedAt=2026-08-24T09:17:40.077Z pushedAt=2026-08-31T11:57:33.282Z -->

```c
typedef struct Region {...} Region
```

## Overview

The **Region** struct describes the rectangle (dirty region) where the content is to be updated in the local **OHNativeWindow**.

**Since**: 8

**Related module**: [NativeWindow](capi-nativewindow.md)

**Header file**: [external_window.h](capi-external-window-h.md)

## Summary

### Member Variables

| Name              | Description                                            |
| ------------------ | ------------------------------------------------ |
| [Rect](capi-nativewindow-rect.md)* rects            | If rects is a null pointer (nullptr), the default buffer size is the dirty region. |
| int32_t rectNumber | If **rectNumber** is **0**, the buffer size is the same as the size of the dirty region by default.       |