# NativeDisplayManager_CutoutInfo

```c
typedef struct NativeDisplayManager_CutoutInfo {...} NativeDisplayManager_CutoutInfo
```

## 概述

挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息。

**起始版本：** 12

**相关模块：** [OH_DisplayManager](capi-oh-displaymanager.md)

**所在头文件：** [oh_display_info.h](capi-oh-display-info-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t boundingRectsLength | boundingRects length |
| [NativeDisplayManager_Rect](capi-oh-displaymanager-nativedisplaymanager-rect.md) *boundingRects | boundingRects info pointer |
| [NativeDisplayManager_WaterfallDisplayAreaRects](capi-oh-displaymanager-nativedisplaymanager-waterfalldisplayarearects.md) waterfallDisplayAreaRects | waterfallDisplayAreaRects info |


