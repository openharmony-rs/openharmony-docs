# Scan_ScannerOptions
<!--Kit: Basic Services Kit-->
<!--Subsystem: Print-->
<!--Owner: @guoshengbang-->
<!--Designer: @Q-haosu-->
<!--Tester: @Q-haosu-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} Scan_ScannerOptions
```

## 概述

表示一个扫描仪的所有参数选项

**起始版本：** 12

**相关模块：** [OH_Scan](capi-oh-scan.md)

**所在头文件：** [ohscan.h](capi-ohscan-h.md)

## 汇总

### 成员变量

| 名称 | 描述 | 
| -------- | -------- |
| char** [titles](#titles) | 选项标题 | 
| char** [descriptions](#descriptions) | 选项描述 | 
| char** [ranges](#ranges) | 选项可设置的范围 | 
| int32_t [optionCount](#optioncount) | 可设置的参数选项数量 | 


## 结构体成员变量说明


### titles

```
char** Scan_ScannerOptions::titles
```
**描述**

选项标题。


### descriptions

```
char** Scan_ScannerOptions::descriptions
```
**描述**

选项描述信息。


### ranges

```
char** Scan_ScannerOptions::ranges
```
**描述**

选项范围。


### optionCount

```
int32_t Scan_ScannerOptions::optionCount
```
**描述**

选项个数。