# Image_String
<!--Kit: Image Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @aulight02-->
<!--Designer: @XiaoYao555-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
struct Image_String {...}
typedef struct Image_String Image_MimeType
typedef struct Image_String Image_String
```

## 概述

字符串结构，用于描述字符串数据地址和数据长度。Image_MimeType是Image_String的别名，用于表示MIME类型。

作为输入参数使用时，调用方负责保证data和size有效；作为输出参数使用时，data的分配和释放方式以具体接口说明为准。

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_common.h](capi-image-common-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char *data = nullptr | 指向字符串数据首地址的指针。 |
| size_t size = 0 | 字符串数据长度。 |

