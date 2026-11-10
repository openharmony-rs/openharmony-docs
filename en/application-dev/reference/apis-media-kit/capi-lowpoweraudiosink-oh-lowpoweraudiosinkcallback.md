# OH_LowPowerAudioSinkCallback
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @yangde_dy-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=4681d7d3c133f955fe79a653913b351e44f4d943 translatedAt=2026-11-10T08:39:09.603Z pushedAt=2026-11-10T10:46:20.586Z nl=1 -->

```c
typedef struct OH_LowPowerAudioSinkCallback OH_LowPowerAudioSinkCallback;
```

## Overview

Contains a set of callback function pointers for the **OH_LowPowerAudioSink**.<br> To ensure the normal running of the **OH_LowPowerAudioSink**, you must register the instance of this struct with the [OH_LowPowerAudioSink](capi-lowpoweraudiosink-oh-lowpoweraudiosink.md) instance and process the information reported by the callback functions.

**Since**: 20

**Related module**: [LowPowerAudioSink](capi-lowpoweraudiosink.md)

**Header file**: [lowpower_audio_sink_base.h](capi-lowpower-audio-sink-base-h.md)

