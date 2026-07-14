# WhitePointArray
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @xiaojianfeng_jeffery-->
<!--Designer: @dizuo1-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

```c
typedef struct WhitePointArray {...} WhitePointArray
```

## Overview

Provides a white point array structure. The white point is the coordinate that represents white in the current color space.

**Since**: 13

**Related module**: [NativeColorSpaceManager](capi-nativecolorspacemanager.md)

**Header file**: [native_color_space_manager.h](capi-native-color-space-manager-h.md)

## Summary

### Member Variables

| Name        | Description              |
| ------------ | ------------------ |
| float arr[2] | White point coordinate array. arr[0] indicates the x-coordinate, and arr[1] indicates the y-coordinate. They are used to accurately define the white reference point in the color space, which affects the display effect and color accuracy of the color space.|
