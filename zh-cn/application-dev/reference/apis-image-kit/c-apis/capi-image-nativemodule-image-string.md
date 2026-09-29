# Image_String

```c
typedef struct Image_String Image_String
```

## 概述

字符串结构，用于描述字符串数据地址和数据长度。Image_MimeType是Image_String的别名，用于表示MIME类型。<br>作为输入参数使用时，调用方负责保证data和size有效；作为输出参数使用时， data的分配和释放方式以具体接口说明为准。

**系统能力：** SystemCapability.Multimedia.Image.Core

**起始版本：** 12

**相关模块：** [Image_NativeModule](capi-image-nativemodule.md)

**所在头文件：** [image_common.h](capi-image-common-h.md)

