# OH_NativeWindow_ScreenInfoRect

```c
typedef struct OH_NativeWindow_ScreenInfoRect {...} OH_NativeWindow_ScreenInfoRect
```

## 概述

定义一个包含坐标和尺寸信息的矩形描述屏幕信息<br> 该结构体用于 [OH_NativeWindow_NativeWindowHandleOpt](capi-external-window-h.md#oh_nativewindow_nativewindowhandleopt) 接口的 SET_SCREEN_INFO 和 GET_SCREEN_INFO 操作码， 用来承载当前帧的偏移/尺寸以及 原始内容在屏幕中的偏移/尺寸

<!--Device-struct OH_NativeWindow_ScreenInfoRect {...}--><!--Device-struct OH_NativeWindow_ScreenInfoRect {...}-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 26.1.0

**相关模块：** [NativeWindow](capi-arkgraphics2d-nativewindow.md)

**所在头文件：** [external_window.h](capi-external-window-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t x | x 偏移（单位：像素）<br>**起始版本：** 26.1.0 |
| int32_t y | y 偏移（单位：像素）<br>**起始版本：** 26.1.0 |
| int32_t w | 宽度（单位：像素）<br>**起始版本：** 26.1.0 |
| int32_t h | 高度（单位：像素）<br>**起始版本：** 26.1.0 |


