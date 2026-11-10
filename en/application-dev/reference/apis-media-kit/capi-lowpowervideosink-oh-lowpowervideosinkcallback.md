# OH_LowPowerVideoSinkCallback
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @yangde_dy-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=4681d7d3c133f955fe79a653913b351e44f4d943 translatedAt=2026-11-10T08:39:23.454Z pushedAt=2026-11-10T10:46:27.957Z nl=1 -->

```c
typedef struct OH_LowPowerVideoSinkCallback OH_LowPowerVideoSinkCallback;
```

## Overview

Contains a set of callback function pointers for the **OH_LowPowerVideoSink**.<br> To ensure the normal running of the **OH_LowPowerVideoSink**, you must register the instance of this struct with the [OH_LowPowerVideoSink](capi-lowpowervideosink-oh-lowpowervideosink.md) instance and process the information reported by the callback functions.

**Since**: 20

**Related module**: [LowPowerVideoSink](capi-lowpowervideosink.md)

**Header file**: [lowpower_video_sink_base.h](capi-lowpower-video-sink-base-h.md)

