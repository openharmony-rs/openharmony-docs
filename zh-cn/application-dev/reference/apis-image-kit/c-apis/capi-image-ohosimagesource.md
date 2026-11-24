# OhosImageSource

```c
struct OhosImageSource {...}
```

## 概述

定义图像源输入资源，每次仅接收一种类型。由[OH_ImageSource_CreateFromUri](capi-image-source-mdk-h.md#oh_imagesource_createfromuri)、[OH_ImageSource_CreateFromFd](capi-image-source-mdk-h.md#oh_imagesource_createfromfd)和 [OH_ImageSource_CreateFromData](capi-image-source-mdk-h.md#oh_imagesource_createfromdata)获取。

<!--Device-struct OhosImageSource {...}--><!--Device-struct OhosImageSource {...}-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 10

**废弃版本：** 11

**相关模块：** [Image](capi-image-kit-image.md)

**所在头文件：** [image_source_mdk.h](capi-image-source-mdk-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| char* uri = nullptr | Pointer to the image source URI. Only a file URI or Base64 URI is accepted.<br>**起始版本：** 10<br><!--Device-char* uri = nullptr--><!--Device-char* uri = nullptr-End--> |
| size_t uriSize = 0 | Length of the image source URI.<br>**起始版本：** 10<br><!--Device-size_t uriSize = 0--><!--Device-size_t uriSize = 0-End--> |
| int32_t fd = -1 | Descriptor of the image source.<br>**起始版本：** 10<br><!--Device-int32_t fd = -1--><!--Device-int32_t fd = -1-End--> |
| uint8_t* buffer = nullptr | Pointer to the image source buffer. Only a formatted packet buffer or Base64 buffer is accepted.<br>**起始版本：** 10<br><!--Device-uint8_t* buffer = nullptr--><!--Device-uint8_t* buffer = nullptr-End--> |
| size_t bufferSize = 0 | Size of the image source buffer.<br>**起始版本：** 10<br><!--Device-size_t bufferSize = 0--><!--Device-size_t bufferSize = 0-End--> |
| char* uri | Pointer to the image source URI. Only a file URI or Base64 URI is accepted.<br>**起始版本：** 10<br><!--Device-char* uri--><!--Device-char* uri-End--> |
| size_t uriSize | Length of the image source URI.<br>**起始版本：** 10<br><!--Device-size_t uriSize--><!--Device-size_t uriSize-End--> |
| int32_t fd | Descriptor of the image source.<br>**起始版本：** 10<br><!--Device-int32_t fd--><!--Device-int32_t fd-End--> |
| uint8_t* buffer | Pointer to the image source buffer. Only a formatted packet buffer or Base64 buffer is accepted.<br>**起始版本：** 10<br><!--Device-uint8_t* buffer--><!--Device-uint8_t* buffer-End--> |
| size_t bufferSize | Size of the image source buffer.<br>**起始版本：** 10<br><!--Device-size_t bufferSize--><!--Device-size_t bufferSize-End--> |


