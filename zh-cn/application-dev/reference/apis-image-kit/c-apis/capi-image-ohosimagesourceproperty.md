# OhosImageSourceProperty

```c
struct OhosImageSourceProperty {...}
```

## 概述

定义图像源属性键值字符串。此选项给[OH_ImageSource_GetImageProperty](capi-image-source-mdk-h.md#oh_imagesource_getimageproperty)和[OH_ImageSource_ModifyImageProperty](capi-image-source-mdk-h.md#oh_imagesource_modifyimageproperty)接口使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 10

**相关模块：** [Image](capi-others-image.md)

**所在头文件：** [image_source_mdk.h](capi-image-source-mdk-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char* value = nullptr | Image source property key and value string head.<br>**起始版本：** 10 |
| size_t size = 0 | Image source property key and value string size.<br>**起始版本：** 10 |
| char* value | Image source property key and value string head.<br>**起始版本：** 10 |
| size_t size | Image source property key and value string size.<br>**起始版本：** 10 |


