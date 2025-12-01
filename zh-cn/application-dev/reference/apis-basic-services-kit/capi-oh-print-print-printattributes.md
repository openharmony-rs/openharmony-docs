# Print_PrintAttributes
<!--Kit: Basic Services Kit-->	
<!--Subsystem: Print-->	
<!--Owner: @guoshengbang-->	
<!--Designer: @Q-haosu-->	
<!--Tester: @Q-haosu-->	
<!--Adviser: @fang-jinxu-->

```
typedef struct {...} Print_PrintAttributes
```

## 概述

打印属性结构体。

**起始版本：** 13

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [Print_Range](capi-oh-print-print-range.md) pageRange | 打印范围。 |
| [Print_PageSize](capi-oh-print-print-pagesize.md) pageSize | 打印尺寸。 |
| [Print_Margin](capi-oh-print-print-margin.md) pageMargin | 打印边距。 |
| uint32_t copyNumber | 打印份数。 |
| uint32_t duplexMode | 单双面。 |
| uint32_t colorMode | 彩色。 |
| bool isSequential | 顺序打印。 |
| bool isLandscape | 横纵向。 |
| bool hasOption | 打印选项标识位。 |
| char options[256] | 打印选项。 |


