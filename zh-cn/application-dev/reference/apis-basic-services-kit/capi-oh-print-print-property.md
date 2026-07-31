# Print_Property
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->

```cpp
typedef struct {...} Print_Property
```

## 概述

Print_Property表示打印机属性，以键值对形式描述打印机的各类属性信息，开发者可通过该结构体获取或设置打印机的属性参数。

**起始版本：** 12

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char *key | 属性键，用于标识打印机属性的类型，取值须为[OH_Print](capi-oh-print.md)模块定义的有效属性名称。 |
| char *value | 属性值，与属性键key对应的值内容，其格式和有效范围取决于对应的属性键。 |


