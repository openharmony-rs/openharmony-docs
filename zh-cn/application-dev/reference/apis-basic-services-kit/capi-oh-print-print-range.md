# Print_Range
<!--Kit: Basic Services Kit-->	
<!--Subsystem: Print-->	
<!--Owner: @guoshengbang-->	
<!--Designer: @Q-haosu-->	
<!--Tester: @Q-haosu-->	
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} Print_Range
```

## 概述

打印范围。

**起始版本：** 13

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t startPage | 打印起始页。 |
| uint32_t endPage | 打印终止页。 |
| uint32_t pagesArrayLen | 打印队列长度。 |
| uint32_t* pagesArray | 打印队列指针。 |


