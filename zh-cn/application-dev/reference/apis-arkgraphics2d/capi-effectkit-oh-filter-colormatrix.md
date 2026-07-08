# OH_Filter_ColorMatrix

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanamaru-->
<!--Designer: @chensiyi_CE-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

```c
typedef struct OH_Filter_ColorMatrix {
    // ...
} OH_Filter_ColorMatrix;
```

## 概述

定义用于创建滤镜效果的矩阵，矩阵维度为4x5，元素取值范围为浮点数。

**使用场景**：

- 图像编辑应用中的滤镜处理（如复古、黑白、暖色调等效果）
- 视频应用的实时滤镜效果
- 相机应用的美颜、调色功能
- 需要自定义颜色变换效果的图像处理场景

颜色矩阵结构如下：

```plaintext
| R' |   | a00 a01 a02 a03 a04 |   | R |
| G' | = | a10 a11 a12 a13 a14 | * | G |
| B' |   | a20 a21 a22 a23 a24 |   | B |
| A' |   | a30 a31 a32 a33 a34 |   | A |
                                   | 1 |
```

矩阵的4行依次对应输出颜色通道R（红）、G（绿）、B（蓝）、A（透明度）；前4列依次对应输入颜色通道R、G、B、A的变换系数，第5列为常量偏移值。

**起始版本：** 12

**相关模块：** [effectKit](capi-effectkit.md)

**所在头文件：** [effect_types.h](capi-effect-types-h.md)

## 汇总

### 成员变量

| 名称          | 描述                               |
| ------------- | ---------------------------------- |
| float val[20] | 自定义颜色矩阵，用于实现图像颜色变换效果。数组包含20个float类型元素，按行优先顺序存储，组成4行5列矩阵。前4列对应R、G、B、A通道的变换系数，第5列为常量偏移值。建议元素取值为[-1, 1]，超出此范围可能导致颜色值溢出或产生非预期效果。 |
