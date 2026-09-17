# Region

```c
typedef struct Region {...} Region
```

## Overview

indicates a dirty region where content is updated.

**Since**: 8

**Related module**: [NativeWindow](capi-nativewindow.md)

**Header file**: [external_window.h](capi-external-window-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| struct Rect | if rects is nullptr, fill the Buffer dirty size by default |
| int32_t rectNumber | if rectNumber is 0, fill the Buffer dirty size by default |


