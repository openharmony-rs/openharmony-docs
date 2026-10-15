# Print_Resolution
 <!--Kit: Basic Services Kit-->
 <!--Subsystem: Print-->
 <!--Owner: @Zouhaifeng1-->
 <!--Designer: @baozewei-->
 <!--Tester: @baozewei-->
 <!--Adviser: @fang-jinxu-->

```cpp
typedef struct {...} Print_Resolution
```

## 概述

Print_Resolution用于表示以dpi为单位的打印分辨率，可控制打印输出的精细度与质量。

**起始版本：** 12

**相关模块：** [OH_Print](capi-oh-print.md)

**所在头文件：** [ohprint.h](capi-ohprint-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t [horizontalDpi](#horizontaldpi) | 水平方向的打印分辨率，单位为dpi。 |
| uint32_t [verticalDpi](#verticaldpi) | 垂直方向的打印分辨率，单位为dpi。 |


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

