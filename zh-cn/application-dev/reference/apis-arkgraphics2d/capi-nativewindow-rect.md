# Rect
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @Felix-fangyang-->
<!--Designer: @conan13234-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->
```c
struct Rect { ... }
```

## 概述

定义矩形区域的结构体，包含矩形框的起始坐标和宽高信息。

**相关模块：** [NativeWindow](capi-nativewindow.md)

**所在头文件：** [external_window.h](capi-external-window-h.md)

## 汇总

### 成员变量

| 名称       | 描述              |
| ---------- | ----------------- |
| int32_t x  | 矩形框起始x坐标。 |
| int32_t y  | 矩形框起始y坐标。 |
| uint32_t w | 矩形框宽度。      |
| uint32_t h | 矩形框高度。      |

