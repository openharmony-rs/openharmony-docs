# Region

```c
typedef struct Region {...} Region
```

## 概述

表示本地窗口OHNativeWindow需要更新内容的矩形区域（脏区）。

<!--Device-struct Region {...}--><!--Device-struct Region {...}-End-->

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 8

**相关模块：** [NativeWindow](capi-arkgraphics2d-nativewindow.md)

**所在头文件：** [external_window.h](capi-external-window-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| rects.x | <!--Device-rects.x--><!--Device-rects.x-End--> |
| rects.y | <!--Device-rects.y--><!--Device-rects.y-End--> |
| rects.w | <!--Device-rects.w--><!--Device-rects.w-End--> |
| rects.h | <!--Device-rects.h--><!--Device-rects.h-End--> |
| int32_t rectNumber | 如果rectNumber是0，默认Buffer大小为脏区<br><!--Device-int32_t rectNumber--><!--Device-int32_t rectNumber-End--> |


