# Print_Resolution
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->

```cpp
typedef struct {...} Print_Resolution;
```

## 概述

Print_Resolution用于表示以 dpi 为单位的打印分辨率，可控制打印输出的精细度与质量。

**起始版本：** 12

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t horizontalDpi | 水平方向的打印分辨率，单位为 dpi。 |
| uint32_t verticalDpi | 垂直方向的打印分辨率，单位为 dpi。 |
