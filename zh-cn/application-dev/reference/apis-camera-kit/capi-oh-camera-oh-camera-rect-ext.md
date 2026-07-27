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

## 概述

矩形定义。<br> 检测点应在0-1坐标系内，该坐标系左上角为(0，0)，右下角为(1，1)。<br> 此坐标系以设备充电口在右侧时的横向设备方向为基准。<br> 例如应用的预览界面布局以设备充电口在下侧时的竖向方向为基准，布局宽高为(w，h)，返回点为(x，y)，则转换后的坐标点为(1-y，x)。

**起始版本：** 26.0.0

**相关模块：** [OH_Camera](capi-oh-camera.md)

**所在头文件：** [camera.h](capi-camera-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| double topLeftX | 矩形左上角的X坐标，范围[0, 1]。<br>**起始版本：** 26.0.0 |
| double topLeftY | 矩形左上角的Y坐标，范围[0, 1]。<br>**起始版本：** 26.0.0 |
| double width | 矩形宽度，范围[0, 1]。<br>**起始版本：** 26.0.0 |
| double height | 矩形高度，范围[0, 1]。<br>**起始版本：** 26.0.0 |


