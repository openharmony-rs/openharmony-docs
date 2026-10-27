# OH_NativeWindow_ScreenInfoRect
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
```c
typedef struct OH_NativeWindow_ScreenInfoRect OH_NativeWindow_ScreenInfoRect
```

## 概述

定义一个包含坐标和尺寸信息的矩阵描述屏幕信息。

**起始版本：** 26.2.0

**相关模块：** [NativeWindow](capi-nativewindow.md)

**所在头文件：** [external_window.h](capi-external-window-h.md)

## 汇总

### 成员变量

| 名称       | 描述              |
| ---------- | ----------------- |
| int32_t x  | 矩形框起始x坐标。 |
| int32_t y  | 矩形框起始y坐标。 |
| int32_t w | 矩形框宽度。      |
| int32_t h | 矩形框高度。      |
