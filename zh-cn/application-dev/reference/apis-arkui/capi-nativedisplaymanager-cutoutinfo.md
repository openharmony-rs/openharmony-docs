# NativeDisplayManager_CutoutInfo
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk; @logn-->
<!--Designer: @hejunfei1991-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## 概述

挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息。

**起始版本：** 12

**相关模块：** [OH_DisplayManager](capi-oh-displaymanager.md)

**所在头文件：** [oh_display_info.h](capi-oh-display-info-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t boundingRectsLength | 挖孔屏、刘海屏不可用屏幕区域长度。 |
| [NativeDisplayManager_Rect](capi-nativedisplaymanager-rect.md)* boundingRects | 挖孔屏、刘海屏等区域的边界矩形。 |
| [NativeDisplayManager_WaterfallDisplayAreaRects](capi-nativedisplaymanager-waterfalldisplayarearects.md) waterfallDisplayAreaRects | 瀑布屏曲面部分显示区域。 |


