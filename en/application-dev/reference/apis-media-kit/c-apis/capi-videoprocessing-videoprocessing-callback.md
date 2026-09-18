# VideoProcessing_Callback

```c
typedef struct VideoProcessing_Callback VideoProcessing_Callback
```

## Overview

Video processing asynchronous callback object type.<br> Define a null pointer of VideoProcessing_Callback and call {@link OH_VideoProcessingCallback_Create} to create a<br>callback object. The pointer should be null before creating the callback object.<br>Register the callback to a video processing instance by calling {@link OH_VideoProcessing_RegisterCallback}.

**Since**: 12

**Related module**: [VideoProcessing](capi-videoprocessing.md)

**Header file**: [video_processing_types.h](capi-video-processing-types-h.md)

