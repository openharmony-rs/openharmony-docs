# Region

```c
struct Region {...}
```

## Overview

indicates a dirty region where content is updated.

**System capability**: SystemCapability.Graphic.Graphic2D.NativeWindow

**Since**: 8

**Related module**: [NativeWindow](capi-others-nativewindow.md)

**Header file**: [external_window.h](capi-external-window-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| rects | if rects is nullptr, fill the Buffer dirty size by default |
| rects.x |  |
| rects.y |  |
| rects.w |  |
| rects.h |  |
| int32_t rectNumber | if rectNumber is 0, fill the Buffer dirty size by default |


