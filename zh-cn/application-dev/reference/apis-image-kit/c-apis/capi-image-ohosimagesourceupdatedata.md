# OhosImageSourceUpdateData

```c
struct OhosImageSourceUpdateData {...}
```

## 概述

定义图像源更新数据选项，由[OH_ImageSource_UpdateData](capi-image-source-mdk-h.md#oh_imagesource_updatedata)获取。

<!--Device-struct OhosImageSourceUpdateData {...}--><!--Device-struct OhosImageSourceUpdateData {...}-End-->

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 10

**相关模块：** [Image](capi-image-kit-image.md)

**所在头文件：** [image_source_mdk.h](capi-image-source-mdk-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t* buffer = nullptr | Image source update data buffer.<br>**起始版本：** 10<br><!--Device-uint8_t* buffer = nullptr--><!--Device-uint8_t* buffer = nullptr-End--> |
| size_t bufferSize = 0 | Image source update data buffer size.<br>**起始版本：** 10<br><!--Device-size_t bufferSize = 0--><!--Device-size_t bufferSize = 0-End--> |
| uint32_t offset = 0 | Image source offset of update data buffer.<br>**起始版本：** 10<br><!--Device-uint32_t offset = 0--><!--Device-uint32_t offset = 0-End--> |
| uint32_t updateLength = 0 | Image source update data length in update data buffer.<br>**起始版本：** 10<br><!--Device-uint32_t updateLength = 0--><!--Device-uint32_t updateLength = 0-End--> |
| int8_t isCompleted = 0 | Image source update data is completed in this session.<br>**起始版本：** 10<br><!--Device-int8_t isCompleted = 0--><!--Device-int8_t isCompleted = 0-End--> |
| uint8_t* buffer | Image source update data buffer.<br>**起始版本：** 10<br><!--Device-uint8_t* buffer--><!--Device-uint8_t* buffer-End--> |
| size_t bufferSize | Image source update data buffer size.<br>**起始版本：** 10<br><!--Device-size_t bufferSize--><!--Device-size_t bufferSize-End--> |
| uint32_t offset | Image source offset of update data buffer.<br>**起始版本：** 10<br><!--Device-uint32_t offset--><!--Device-uint32_t offset-End--> |
| uint32_t updateLength | Image source update data length in update data buffer.<br>**起始版本：** 10<br><!--Device-uint32_t updateLength--><!--Device-uint32_t updateLength-End--> |
| int8_t isCompleted | Image source update data is completed in this session.<br>**起始版本：** 10<br><!--Device-int8_t isCompleted--><!--Device-int8_t isCompleted-End--> |


