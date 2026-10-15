# Region

```c
struct Region {...}
```

## 概述

表示本地窗口OHNativeWindow需要更新内容的矩形区域（脏区）。

**系统能力：** SystemCapability.Graphic.Graphic2D.NativeWindow

**起始版本：** 8

**相关模块：** [NativeWindow](capi-nativewindow.md)

**所在头文件：** [external_window.h](capi-external-window-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| rects.x |  |
| rects.y |  |
| rects.w |  |
| rects.h |  |
| int32_t rectNumber | 如果rectNumber是0，默认Buffer大小为脏区 |


