# OhosImageSourceProperty

```c
struct OhosImageSourceProperty {...}
```

## 概述

定义图像源属性键值字符串。此选项给{@link OH_ImageSource_GetImageProperty}和{@link OH_ImageSource_ModifyImageProperty}接口使用。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 10

**相关模块：** [Image](capi-image.md)

**所在头文件：** [image_source_mdk.h](capi-image-source-mdk-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char* value = nullptr |  |
| size_t size = 0;
#else |  |
| char* value |  |
| size_t size;
#endif |  |


