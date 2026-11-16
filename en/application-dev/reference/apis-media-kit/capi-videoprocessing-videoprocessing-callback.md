# VideoProcessing_Callback
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @liziliang-->
<!--Designer: @dev_ZUT-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=562a7078212c9b28d8dc43b038a6724f5b49ce15 translatedAt=2026-11-09T06:31:44.061Z pushedAt=2026-11-09T08:46:39.806Z nl=1 -->

```c
typedef struct VideoProcessing_Callback VideoProcessing_Callback
```

## Overview

The struct describes a callback object for handling video processing events.

You should define a null pointer for **VideoProcessing_Callback** and use [OH_VideoProcessingCallback_Create](capi-video-processing-h.md#oh_videoprocessingcallback_create) to create a callback object. Before creation, ensure that the pointer is null. After creating the callback object, call [OH_VideoProcessing_RegisterCallback](capi-video-processing-h.md#oh_videoprocessing_registercallback) to register it with the video processing instance.

**Since**: 12

**Related module**: [VideoProcessing](capi-videoprocessing.md)

**Header file**: [video_processing_types.h](capi-video-processing-types-h.md)

