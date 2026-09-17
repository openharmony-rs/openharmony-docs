# OhosImageSourceUpdateData

```c
struct OhosImageSourceUpdateData {...}
```

## 概述

定义图像源更新数据选项，由[OH_ImageSource_UpdateData](capi-image-source-mdk-h.md#oh_imagesource_updatedata)获取。

**起始版本：** 10

**相关模块：** [Image](capi-image.md)

**所在头文件：** [image_source_mdk.h](capi-image-source-mdk-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t* buffer = nullptr |  |
| size_t bufferSize = 0 |  |
| uint32_t offset = 0 |  |
| uint32_t updateLength = 0 |  |
| int8_t isCompleted = 0;
#else |  |
| uint8_t* buffer |  |
| size_t bufferSize |  |
| uint32_t offset |  |
| uint32_t updateLength |  |
| int8_t isCompleted;
#endif |  |


