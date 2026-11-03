# Camera_Rect

```c
struct Camera_Rect {...}
```

## Overview

The struct describes a rectangle. The coordinate system for the returned detection points is based on the landscape device orientation, with the charging port on the right. In this coordinate system, the top-left corner is (0, 0), and the bottom-right corner corresponds to the pixel dimensions of the camera preview output stream. All member values are integer pixel values. Here, **topLeftX** and **topLeftY** represent the coordinates of the top-left corner of the rectangle, whereas **width** and **height** represent the width and height of the rectangle, respectively.

**System capability**: SystemCapability.Multimedia.Camera.Core

**Since**: 11

**Related module**: [OH_Camera](capi-others-oh-camera.md)

**Header file**: [camera.h](capi-camera-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t topLeftX | X coordinate of the top-left corner of the rectangle. Value range: [0, preview stream width], e.g. 0 to 1920 for a 1920*1440 preview stream.<br>**Since**: 11 |
| int32_t topLeftY | Y coordinate of the top-left corner of the rectangle. Value range: [0, preview stream height], e.g. 0 to 1440 for a 1920*1440 preview stream.<br>**Since**: 11 |
| int32_t width | Width of the rectangle. Value does not exceed the X-axis upper limit of the coordinate system.<br>**Since**: 11 |
| int32_t height | Height of the rectangle. Value does not exceed the Y-axis upper limit of the coordinate system.<br>**Since**: 11 |


