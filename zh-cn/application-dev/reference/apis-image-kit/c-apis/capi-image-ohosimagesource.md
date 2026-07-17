# OhosImageSource

```c
struct OhosImageSource {...}
```

## 概述

定义图像源输入资源，每次仅接收一种类型。由[OH_ImageSource_CreateFromUri](capi-image-source-mdk-h.md#oh_imagesource_createfromuri)、[OH_ImageSource_CreateFromFd](capi-image-source-mdk-h.md#oh_imagesource_createfromfd)和[OH_ImageSource_CreateFromData](capi-image-source-mdk-h.md#oh_imagesource_createfromdata)获取。

**起始版本：** 10

**废弃版本：** 11

**相关模块：** [Image](capi-image.md)

**所在头文件：** [image_source_mdk.h](capi-image-source-mdk-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char* uri = nullptr |  |
| size_t uriSize = 0 |  |
| int32_t fd = -1 |  |
| uint8_t* buffer = nullptr |  |
| size_t bufferSize = 0;
#else |  |
| char* uri |  |
| size_t uriSize |  |
| int32_t fd |  |
| uint8_t* buffer |  |
| size_t bufferSize;
#endif |  |


