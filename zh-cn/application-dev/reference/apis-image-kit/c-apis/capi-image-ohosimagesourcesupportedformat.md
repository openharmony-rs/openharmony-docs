# OhosImageSourceSupportedFormat

```c
struct OhosImageSourceSupportedFormat {...}
```

## 概述

定义图像源支持的格式字符串。此选项给[OhosImageSourceSupportedFormatList](capi-image-ohosimagesourcesupportedformatlist.md)和[OH_ImageSource_GetSupportedFormats](capi-image-source-mdk-h.md#oh_imagesource_getsupportedformats)接口使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 10

**相关模块：** [Image](capi-others-image.md)

**所在头文件：** [image_source_mdk.h](capi-image-source-mdk-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char* format = nullptr | Image source supported format string head.<br>**起始版本：** 10 |
| size_t size = 0 | Image source supported format string size.<br>**起始版本：** 10 |
| char* format | Image source supported format string head.<br>**起始版本：** 10 |
| size_t size | Image source supported format string size.<br>**起始版本：** 10 |


