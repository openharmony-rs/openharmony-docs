# OhosImageSourceDelayTimeList

```c
struct OhosImageSourceDelayTimeList {...}
```

## 概述

定义图像源延迟时间列表。由{@link OH_ImageSource_GetDelayTime}获取。

**系统能力：** SystemCapability.Multimedia.Image.ImageSource

**起始版本：** 10

**相关模块：** [Image](capi-image.md)

**所在头文件：** [image_source_mdk.h](capi-image-source-mdk-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t* delayTimeList |  |
| size_t size = 0;
#else |  |
| int32_t* delayTimeList |  |
| size_t size;
#endif |  |


