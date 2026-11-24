# OH_AVMetadataExtractor_FrameInfo

```c
typedef struct OH_AVMetadataExtractor_FrameInfo {...} OH_AVMetadataExtractor_FrameInfo
```

## 概述

定义从视频中提取出的帧的信息。

<!--Device-struct OH_AVMetadataExtractor_FrameInfo {...}--><!--Device-struct OH_AVMetadataExtractor_FrameInfo {...}-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

**起始版本：** 23

**相关模块：** [AVMetadataExtractor](capi-media-kit-avmetadataextractor.md)

**所在头文件：** [avmetadata_extractor_base.h](capi-avmetadata-extractor-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int64_t requestTimeUs | 用户传入的请求时间。<br><!--Device-int64_t requestTimeUs--><!--Device-int64_t requestTimeUs-End--> |
| int64_t actualTimeUs | 实际提取到的帧的时间；若提取失败，则为-1。<br><!--Device-int64_t actualTimeUs--><!--Device-int64_t actualTimeUs-End--> |
| OH_PixelmapNative* image | 从视频中提取出的帧图像；若提取失败，则为空指针。<br><!--Device-OH_PixelmapNative* image--><!--Device-OH_PixelmapNative* image-End--> |
| [OH_AVMetadataExtractor_FetchState](capi-avmetadata-extractor-base-h.md#oh_avmetadataextractor_fetchstate) result | 本次帧提取操作的结果状态。<br><!--Device-OH_AVMetadataExtractor_FetchState result--><!--Device-OH_AVMetadataExtractor_FetchState result-End--> |


