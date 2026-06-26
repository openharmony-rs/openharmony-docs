# ColorSpacePrimaries
<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @xubo233-->
<!--Designer: @dizuo1-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

```c
typedef struct {...} ColorSpacePrimaries
```

## 概述

提供色彩原色结构体声明，用于定义色彩空间的红绿蓝三原色和白点的色度坐标。ColorSpacePrimaries结构体用于存储色彩空间的红绿蓝三原色及白点坐标信息，支持色彩空间转换、色彩校正和色彩管理等场景，适用于需要对图像或视频进行精确色彩处理的开发场景。

**起始版本：** 13

**相关模块：** [NativeColorSpaceManager](capi-nativecolorspacemanager.md)

**所在头文件：** [native_color_space_manager.h](capi-native-color-space-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| float rX | 红色的x轴坐标值。 |
| float rY | 红色的y轴坐标值。 |
| float gX | 绿色的x轴坐标值。 |
| float gY | 绿色的y轴坐标值。 |
| float bX | 蓝色的x轴坐标值。 |
| float bY | 蓝色的y轴坐标值。 |
| float wX | 白点的x轴坐标值。 |
| float wY | 白点的y轴坐标值。 |


