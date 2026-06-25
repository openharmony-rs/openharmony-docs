# OH_Camera_Rect_Ext
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_Camera_Rect_Ext {...} OH_Camera_Rect_Ext
```

## Overview

Describes the rectangle.<br> The detection point must be in the coordinate system (0-1), where the top-left corner is (0, 0) and the bottom-right corner is (1, 1).<br> The coordinate system is based on the horizontal device direction with the device's charging port on the right.<br> If the layout of the preview screen of an application is based on the vertical direction with the charging port on the lower side, the layout width and height are {w, h}, and the returned point is {x, y}, then the coordinate point after conversion is (1-y, x).

**Since:** 26.0.0

**Related module:** [OH_Camera](capi-oh-camera.md)

**Header file:** [camera.h](capi-camera-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| double topLeftX | X coordinate of the top-left corner of the rectangle, in the range of [0, 1].<br>**Since:** 26.0.0|
| double topLeftY | Y coordinate of the top-left corner of the rectangle, in the range of [0, 1].<br>**Since:** 26.0.0|
| double width | Width of the rectangle, in the range of [0, 1].<br>**Since:** 26.0.0|
| double height | Height of the rectangle, in the range of [0, 1].<br>**Since:** 26.0.0|
