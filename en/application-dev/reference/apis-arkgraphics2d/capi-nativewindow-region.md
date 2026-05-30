# Region
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang; @BruceXu; @dingpy-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
```
typedef struct {...} Region
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
| * rects            | If **rects** is a null pointer, the buffer size is the same as the size of the dirty region by default.|
| int32_t rectNumber | If **rectNumber** is **0**, the buffer size is the same as the size of the dirty region by default.       |
