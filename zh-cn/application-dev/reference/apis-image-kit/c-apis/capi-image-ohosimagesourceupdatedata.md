# OhosImageSourceUpdateData

```c
struct OhosImageSourceUpdateData {...}
```

## 概述

定义图像源更新数据选项，由[OH_ImageSource_UpdateData](capi-image-source-mdk-h.md#oh_imagesource_updatedata)获取。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 10

**相关模块：** [Image](capi-others-image.md)

**所在头文件：** [image_source_mdk.h](capi-image-source-mdk-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t* buffer = nullptr | Image source update data buffer.<br>**起始版本：** 10 |
| size_t bufferSize = 0 | Image source update data buffer size.<br>**起始版本：** 10 |
| uint32_t offset = 0 | Image source offset of update data buffer.<br>**起始版本：** 10 |
| uint32_t updateLength = 0 | Image source update data length in update data buffer.<br>**起始版本：** 10 |
| int8_t isCompleted = 0 | Image source update data is completed in this session.<br>**起始版本：** 10 |
| uint8_t* buffer | Image source update data buffer.<br>**起始版本：** 10 |
| size_t bufferSize | Image source update data buffer size.<br>**起始版本：** 10 |
| uint32_t offset | Image source offset of update data buffer.<br>**起始版本：** 10 |
| uint32_t updateLength | Image source update data length in update data buffer.<br>**起始版本：** 10 |
| int8_t isCompleted | Image source update data is completed in this session.<br>**起始版本：** 10 |


