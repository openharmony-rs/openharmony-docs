# Print_PageSize
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->

```cpp
typedef struct {...} Print_PageSize
```

## 概述

Print_PageSize用于表示打印任务中的纸张尺寸信息，包含纸张ID、名称、宽度与高度等关键属性，适用于需要在打印配置流程中指定或查询纸张规格的场景。

**起始版本：** 12

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 | 
| -------- | -------- |
| char \* [id](#id) | 纸张尺寸的唯一标识ID，用于区分不同标准纸张规格。 | 
| char \* [name](#name) | 纸张尺寸的名称，如"A4"、"Letter"等标准纸张规格。 | 
| uint32_t [width](#width) | 纸张宽度，单位：密尔（千分之一英寸）。取值原则：大于0。 | 
| uint32_t [height](#height) | 纸张高度，单位：密尔（千分之一英寸）。取值原则：大于0。 | 


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