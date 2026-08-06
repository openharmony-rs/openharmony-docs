# Print_PropertyList

```c
typedef struct Print_PropertyList {...} Print_PropertyList
```

## 概述

打印机属性列表。

**起始版本：** 12

**相关模块：** [Print](capi-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t count | 属性数量。 |
| [Print_Property](capi-print-print-property.md) *list | 属性指针数组。 |


