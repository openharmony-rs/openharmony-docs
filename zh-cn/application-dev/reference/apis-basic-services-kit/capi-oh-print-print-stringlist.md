# Print_StringList
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->

```cpp
typedef struct {...} Print_StringList;
```

## 概述

表示字符串列表，用于在打印模块中传递多个字符串数据。相关接口请参见[OH_Print](capi-oh-print.md)。

**起始版本：** 12

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t count | 字符串数量，表示list数组中的元素个数，需与list数组实际元素数一致。 |
| `char **list` | 指向字符串数组的指针，数组元素数量须与count值一致。 |


