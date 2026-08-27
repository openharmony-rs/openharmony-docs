# ImageProcessing_ColorSpaceInfo

```c
typedef struct ImageProcessing_ColorSpaceInfo {...} ImageProcessing_ColorSpaceInfo
```

## 概述

色彩空间信息，用于色彩空间转换能力查询。

**起始版本：** 13

**相关模块：** [ImageProcessing](capi-imageprocessing.md)

**所在头文件：** [image_processing_types.h](capi-image-processing-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t metadataType | 定义元数据类型，参考{@link OH_Pixelmap_HdrMetadataKey}。 |
| int32_t colorSpace | 定义色彩空间，参考{@link ColorSpaceName}。 |
| int32_t pixelFormat | 定义像素格式，参考{@link PIXEL_FORMAT}。 |


