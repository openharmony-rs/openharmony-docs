# Print_Margin
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->

```cpp
typedef struct {...} Print_Margin;
```

## 概述

Print_Margin用于表示打印页面的边距信息，支持设置左、上、右、下四个方向的边距，控制可打印内容区域。适用于需要在打印时精确控制内容与纸张边缘距离的场景，通过合理配置边距可以避免内容溢出或被裁剪。

**起始版本：** 12

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称                  | 描述     |
| --------------------- | -------- |
| uint32_t leftMargin   | 左边距，单位：毫米。取值原则：大于0。 |
| uint32_t topMargin    | 上边距，单位：毫米。取值原则：大于0。 |
| uint32_t rightMargin  | 右边距，单位：毫米。取值原则：大于0。 |
| uint32_t bottomMargin | 下边距，单位：毫米。取值原则：大于0。 |

