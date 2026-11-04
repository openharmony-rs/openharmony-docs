# Print_PrintAttributes
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->

```cpp
typedef struct {...} Print_PrintAttributes
```

## 概述

表示打印属性结构体，用于配置打印任务的各项属性（如打印范围、纸张尺寸、边距、份数、双面模式、色彩模式、打印方向及打印选项等），适用于需要对打印输出进行精细化控制的场景。

**起始版本：** 13

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 | 
| -------- | -------- |
| [Print_Range](capi-oh-print-print-range.md) [pageRange](#pagerange) | 打印范围。 | 
| [Print_PageSize](capi-oh-print-print-pagesize.md) [pageSize](#pagesize) | 打印纸张尺寸。 | 
| [Print_Margin](capi-oh-print-print-margin.md) [pageMargin](#pagemargin) | 打印边距。 | 
| uint32_t [copyNumber](#copynumber) | 份数。取值范围：大于等于1。 | 
| uint32_t [duplexMode](#duplexmode) | 双面模式。有效取值参见[Print_DuplexMode](capi-ohprint-h.md#print_duplexmode)枚举定义。 | 
| uint32_t [colorMode](#colormode) | 色彩模式。有效取值参见[Print_ColorMode](capi-ohprint-h.md#print_colormode)枚举定义。 | 
| bool [isSequential](#issequential) | 顺序打印。<br>true表示顺序打印，false表示逆序打印。 | 
| bool [isLandscape](#islandscape) | 打印方向（是否横向）。<br>true表示打印方向为横向，false表示打印方向为纵向。 | 
| bool [hasOption](#hasoption) | 打印选项标志。<br>true表示有打印选项（options字段有效），false表示没有打印选项（options字段无效）。 | 
| char [options](#options) [256] | 打印选项，用于传递额外的打印配置参数。仅在hasOption为true时生效。最大长度255个字符。 | 


## 结构体成员变量说明


### colorMode

```c
uint32_t Print_PrintAttributes::colorMode
```
**描述**

彩色。


### copyNumber

```c
uint32_t Print_PrintAttributes::copyNumber
```
**描述**

打印份数。


### duplexMode

```c
uint32_t Print_PrintAttributes::duplexMode
```
**描述**

单双面。


### hasOption

```c
bool Print_PrintAttributes::hasOption
```
**描述**

打印选项标识位。


### isLandscape

```c
bool Print_PrintAttributes::isLandscape
```
**描述**

横纵向。


### isSequential

```c
bool Print_PrintAttributes::isSequential
```
**描述**

顺序打印。


### options

```c
char Print_PrintAttributes::options[256]
```
**描述**

打印选项。


### pageMargin

```c
Print_Margin Print_PrintAttributes::pageMargin
```
**描述**

打印边距。


### pageRange

```c
Print_Range Print_PrintAttributes::pageRange
```
**描述**

打印范围。


### pageSize

```c
Print_PageSize Print_PrintAttributes::pageSize
```
**描述**

打印尺寸。