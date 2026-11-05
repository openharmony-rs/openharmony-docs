# Region
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=1f370dd3425411b659f906071e53860b94f0e2f1 translatedAt=2026-11-04T10:33:45.826Z pushedAt=2026-11-04T10:35:39.131Z nl=2 -->

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
| [Rect](capi-nativewindow-rect.md)* rects            | If **rects** is a null pointer, the buffer size is the same as the size of the dirty region by default. |
| int32_t rectNumber | If **rectNumber** is **0**, the buffer size is the same as the size of the dirty region by default.       |

