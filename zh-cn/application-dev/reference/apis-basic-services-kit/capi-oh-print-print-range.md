# Print_Range
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->

```cpp
typedef struct {...} Print_Range
```

## 概述

表示打印范围结构体，用于指定打印任务中的页码范围。可通过startPage和endPage指定连续页码范围，或通过pagesArray和pagesArrayLen指定不连续的打印页码数组。

**起始版本：** 13

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称                   | 描述             |
| ---------------------- | ---------------- |
| uint32_t startPage     | 打印起始页，页码从1开始计数，取值应为文档中的有效页码且需小于等于endPage。     |
| uint32_t endPage       | 打印结束页，页码从1开始计数，取值应为文档中的有效页码且需大于等于startPage。     |
| uint32_t pagesArrayLen | 打印页码数组长度，须与pagesArray数组实际元素数一致，仅在pagesArray不为NULL时有效。 |
| uint32_t* pagesArray   | 打印页码数组，每个元素表示一个需要打印的页码，页码从1开始计数，取值应为文档中的有效页码，数组长度由pagesArrayLen决定。 |

