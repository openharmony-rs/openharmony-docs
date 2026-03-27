# OH_Camera_ZoomRange
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_Camera_ZoomRange {...} OH_Camera_ZoomRange
```

## 概述

变焦范围配置。

**起始版本：** 24

**相关模块：** [OH_Camera](capi-oh-camera.md)

**所在头文件：** [camera.h](capi-camera-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| float minZoom | 最小变焦值。 |
| float maxZoom | 最大变焦值。 |