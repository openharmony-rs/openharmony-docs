# Print_PageSize
 <!--Kit: Basic Services Kit-->   
 <!--Subsystem: Print-->  
 <!--Owner: @guoshengbang-->  
 <!--Designer: @Q-haosu-->    
 <!--Tester: @Q-haosu-->  
 <!--Adviser: @fang-jinxu-->

```c
typedef struct {...} Print_PageSize
```

## 概述

表示纸张尺寸信息。

**起始版本：** 12

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 | 
| -------- | -------- |
| char \* [id](#id) | 纸张 ID。 | 
| char \* [name](#name) | 纸张名称。 | 
| uint32_t [width](#width) | 纸张宽度，单位：毫米。 | 
| uint32_t [height](#height) | 纸张高度，单位：毫米。 | 


## 结构体成员变量说明


### height

```c
uint32_t Print_PageSize::height
```
**描述**

纸张高度。


### id

```c
char* Print_PageSize::id
```
**描述**

纸张 ID。


### name

```c
char* Print_PageSize::name
```
**描述**

纸张名称。


### width

```c
uint32_t Print_PageSize::width
```
**描述**

纸张宽度。