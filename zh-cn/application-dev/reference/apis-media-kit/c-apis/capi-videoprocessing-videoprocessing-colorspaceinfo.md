# VideoProcessing_ColorSpaceInfo

```c
typedef struct VideoProcessing_ColorSpaceInfo {...} VideoProcessing_ColorSpaceInfo
```

## 概述

视频颜色空间信息数据结构。

<!--Device-struct VideoProcessing_ColorSpaceInfo {...}--><!--Device-struct VideoProcessing_ColorSpaceInfo {...}-End-->

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

**起始版本：** 12

**相关模块：** [VideoProcessing](capi-media-kit-videoprocessing.md)

**所在头文件：** [video_processing_types.h](capi-video-processing-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int32_t metadataType | 视频元数据类型，参考[OH_NativeBuffer_MetadataType](../../apis-arkgraphics2d/c-apis/capi-buffer-common-h.md#oh_nativebuffer_metadatatype)。<br><!--Device-int32_t metadataType--><!--Device-int32_t metadataType-End--> |
| int32_t colorSpace | 视频颜色空间类型，参考[OH_NativeBuffer_ColorSpace](../../apis-arkgraphics2d/c-apis/capi-buffer-common-h.md#oh_nativebuffer_colorspace)。<br><!--Device-int32_t colorSpace--><!--Device-int32_t colorSpace-End--> |
| int32_t pixelFormat | 视频像素格式，参考[OH_NativeBuffer_Format](../../apis-arkgraphics2d/c-apis/capi-buffer-common-h.md#oh_nativebuffer_format)。<br><!--Device-int32_t pixelFormat--><!--Device-int32_t pixelFormat-End--> |


