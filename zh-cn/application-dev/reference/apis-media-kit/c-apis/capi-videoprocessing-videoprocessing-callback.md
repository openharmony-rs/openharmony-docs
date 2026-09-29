# VideoProcessing_Callback

```c
typedef struct VideoProcessing_Callback VideoProcessing_Callback
```

## 概述

视频处理回调对象类型。 <br>定义一个VideoProcessing_Callback空指针，调用OH_VideoProcessingCallback_Create来创建一个回调对象。 创建之前该指针必须为空。通过调用OH_VideoProcessing_RegisterCallback来向视频处理实例注册回调对象。

**系统能力：** SystemCapability.Multimedia.VideoProcessingEngine

**起始版本：** 12

**相关模块：** [VideoProcessing](capi-videoprocessing.md)

**所在头文件：** [video_processing_types.h](capi-video-processing-types-h.md)

