# Print_Resolution
 <!--Kit: Basic Services Kit-->   
 <!--Subsystem: Print-->  
 <!--Owner: @guoshengbang-->  
 <!--Designer: @Q-haosu-->    
 <!--Tester: @Q-haosu-->  
 <!--Adviser: @fang-jinxu-->

```c
typedef struct {...} Print_Resolution
```

## 概述

表示以 dpi 为单位的打印分辨率。

**起始版本：** 12

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t [horizontalDpi](#horizontaldpi) | 水平分辨率，单位：dpi。 |
| uint32_t [verticalDpi](#verticaldpi) | 垂直分辨率，单位：dpi。 |


## 结构体成员变量说明


### horizontalDpi

```c
uint32_t Print_Resolution::horizontalDpi
```
**描述**

水平分辨率，单位：dpi。


### verticalDpi

```c
uint32_t Print_Resolution::verticalDpi
```
**描述**

垂直分辨率，单位：dpi。

