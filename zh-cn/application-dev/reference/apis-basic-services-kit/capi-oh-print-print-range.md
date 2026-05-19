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

表示打印范围结构体。

**起始版本：** 13

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 | 
| -------- | -------- |
| uint32_t [startPage](#startpage) | 打印起始页。 | 
| uint32_t [endPage](#endpage) | 打印终止页。 | 
| uint32_t [pagesArrayLen](#pagesarraylen) | 打印页数组长度。 | 
| uint32_t \* [pagesArray](#pagesarray) | 打印页数组指针。 | 


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