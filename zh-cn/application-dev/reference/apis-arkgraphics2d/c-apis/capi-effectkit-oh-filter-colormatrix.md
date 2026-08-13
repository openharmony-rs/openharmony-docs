# OH_Filter_ColorMatrix

```c
struct OH_Filter_ColorMatrix {...}
```

## 概述

定义用于创建滤镜效果的矩阵，矩阵维度为4x5，元素取值范围为浮点数。

**起始版本：** 12

**相关模块：** [effectKit](capi-effectkit.md)

**所在头文件：** [effect_types.h](capi-effect-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| float val[20] | 自定义颜色矩阵，用于实现图像颜色变换效果。数组包含20个float类型元素，按行优先顺序存储，组成4行5列矩阵。前4列对应R、G、B、A通道的变换系数，第5列为常量偏移值。建议元素取值为[-1, 1]，超出此范围可能导致颜色值溢出或产生非预期效果。 |


