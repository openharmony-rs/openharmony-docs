# OH_AVMetadataExtractor_FrameInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @wang-haizhou6-->
<!--Designer: @HmQQQ-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} OH_AVMetadataExtractor_FrameInfo
```

## 概述

定义从视频中提取出的帧的信息。

**起始版本：** 23

**相关模块：** [AVMetadataExtractor](capi-avmetadataextractor.md)

**所在头文件：** [avmetadata_extractor_base.h](capi-avmetadata-extractor-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| int64_t requestTimeUs | 用户传入的请求时间。 |
| int64_t actualTimeUs | 实际提取到的帧的时间；若提取失败，则为-1。 |
| [OH_PixelmapNative*](../apis-image-kit/capi-image-nativemodule-oh-pixelmapnative.md) image | 从视频中提取出的帧图像；若提取失败，则为空指针。 |
| [OH_AVMetadataExtractor_FetchState](capi-avmetadata-extractor-base-h.md#oh_avmetadataextractor_fetchstate) result | 本次帧提取操作的结果状态。 |
