# ColorSpacePrimaries
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @xiaojianfeng_jeffery-->
<!--Designer: @dizuo1-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

```c
typedef struct {...} ColorSpacePrimaries
```

## Overview

Provides the declaration for the color primary structure, which is used to store the coordinates of the red, green, and blue primary colors and white point in the color space.

**Since**: 13

**Related module**: [NativeColorSpaceManager](capi-nativecolorspacemanager.md)

**Header file**: [native_color_space_manager.h](capi-native-color-space-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| float rX | X-coordinate of the red color.|
| float rY | Y-coordinate of the red color.|
| float gX | X-coordinate of the green color.|
| float gY | Y-coordinate of the green color.|
| float bX | X-coordinate of the blue color.|
| float bY | Y-coordinate of the blue color.|
| float wX | X-coordinate of the white point.|
| float wY | Y-coordinate of the white point.|
