# Camera_Rect

```c
typedef struct Camera_Rect {...} Camera_Rect
```

## Overview

The struct describes a rectangle. The coordinate system for the returned detection points is based on the landscape device orientation, with the charging port on the right. In this coordinate system, the top-left corner is (0, 0), and the bottom-right corner corresponds to the pixel dimensions of the camera preview output stream. All member values are integer pixel values. Here, **topLeftX** and **topLeftY** represent the coordinates of the top-left corner of the rectangle, whereas **width** and **height** represent the width and height of the rectangle, respectively.

**Since**: 11

**Related module**: [OH_Camera](capi-oh-camera.md)

**Header file**: [camera.h](capi-camera-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t topLeftX |  |
| int32_t topLeftY |  |
| int32_t width |  |
| int32_t height |  |


