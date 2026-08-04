# Print_Range
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @guoshengbang-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->

```cpp
typedef struct {...} Print_Range
```

## 概述

表示打印范围结构体，用于指定打印任务中的页码范围。可通过 startPage 和 endPage 指定连续页码范围，或通过 pagesArray 和 pagesArrayLen 指定不连续的打印页码数组。

**起始版本：** 13

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 | 
| -------- | -------- |
| uint32_t [startPage](#startpage) | 打印起始页码（页码从 1 开始计数）。取值应为文档中的有效页码，且不大于 endPage。 | 
| uint32_t [endPage](#endpage) | 打印终止页码（页码从 1 开始计数）。取值应为文档中的有效页码，且不小于 startPage。 | 
| uint32_t [pagesArrayLen](#pagesarraylen) | 打印页码数组长度，需与 pagesArray 中实际元素一致；当 pagesArray 为 NULL 时无效。 | 
| uint32_t \* [pagesArray](#pagesarray) | 打印页码数组，每个元素表示一个需要打印的页码（从 1 开始计数）。取值应为文档中的有效页码，且数组长度由 pagesArrayLen 决定。 | 


## 结构体成员变量说明


### endPage

```c
uint32_t Print_Range::endPage
```
**描述**

打印终止页。


### pagesArray

```c
uint32_t* Print_Range::pagesArray
```
**描述**

打印页数组指针。


### pagesArrayLen

```c
uint32_t Print_Range::pagesArrayLen
```
**描述**

打印页数组长度。


### startPage

```c
uint32_t Print_Range::startPage
```
**描述**

打印起始页。