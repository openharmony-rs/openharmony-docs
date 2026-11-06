# OH_NativeWindow_ScreenInfoRect
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
```c
typedef struct OH_NativeWindow_ScreenInfoRect {...} OH_NativeWindow_ScreenInfoRect
```

## 概述

定义一个矩形对象，包含坐标和尺寸信息，用于描述屏幕区域。

**起始版本：** 26.1.0

**相关模块：** [NativeWindow](capi-nativewindow.md)

**所在头文件：** [external_window.h](capi-external-window-h.md)

## 汇总

### 成员变量

| 名称       | 描述              |
| ---------- | ----------------- |
| int32_t x  | 矩形对象的X轴坐标。 |
| int32_t y  | 矩形对象的Y轴坐标。 |
| int32_t w | 矩形对象的宽度。      |
| int32_t h | 矩形对象的高度。      |