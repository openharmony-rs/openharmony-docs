# OH_VideoProcessing
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @liziliang-->
<!--Designer: @dev_ZUT-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=562a7078212c9b28d8dc43b038a6724f5b49ce15 translatedAt=2026-11-09T06:31:29.807Z pushedAt=2026-11-09T08:46:36.392Z nl=1 -->

```c
typedef struct OH_VideoProcessing OH_VideoProcessing
```

## Overview

The struct describes an object for video processing.
 
You should define a null pointer for **OH_VideoProcessing** and use [OH_VideoProcessing_Create](capi-video-processing-h.md#oh_videoprocessing_create) to create a video processing instance. Before creation, ensure that the pointer is null. You can create different video processing instances with different processing types.

**Since**: 12

**Related module**: [VideoProcessing](capi-videoprocessing.md)

**Header file**: [video_processing_types.h](capi-video-processing-types-h.md)

