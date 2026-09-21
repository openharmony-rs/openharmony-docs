# OH_LowPowerVideoSinkCallback
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @yangde_dy-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=6b885b838ace79912222a91118f2a6346fb31954 translatedAt=2026-09-16T03:51:06.932Z pushedAt=2026-09-21T08:33:52.667Z -->

```c
typedef struct OH_LowPowerVideoSinkCallback OH_LowPowerVideoSinkCallback;
```

## Overview

Contains a set of callback function pointers for the **OH_LowPowerVideoSink**.<br> To ensure the normal running of the **OH_LowPowerVideoSink**, you must register the instance of this struct with the [OH_LowPowerVideoSink](capi-lowpowervideosink-oh-lowpowervideosink.md) instance and process the information reported by the callback functions.

**Since**: 20

**Related module**: [LowPowerVideoSink](capi-lowpowervideosink.md)

**Header file**: [lowpower_video_sink_base.h](capi-lowpower-video-sink-base-h.md)

