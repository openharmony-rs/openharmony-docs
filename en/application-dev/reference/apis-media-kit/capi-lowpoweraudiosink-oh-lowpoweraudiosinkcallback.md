# OH_LowPowerAudioSinkCallback
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @yangde_dy-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=6b885b838ace79912222a91118f2a6346fb31954 translatedAt=2026-09-16T03:50:27.646Z pushedAt=2026-09-21T08:30:03.239Z -->

```c
typedef struct OH_LowPowerAudioSinkCallback OH_LowPowerAudioSinkCallback;
```

## Overview

Contains a set of callback function pointers for the **OH_LowPowerAudioSink**.<br> To ensure the normal running of the **OH_LowPowerAudioSink**, you must register the instance of this struct with the [OH_LowPowerAudioSink](capi-lowpoweraudiosink-oh-lowpoweraudiosink.md) instance and process the information reported by the callback functions.

**Since**: 20

**Related module**: [LowPowerAudioSink](capi-lowpoweraudiosink.md)

**Header file**: [lowpower_audio_sink_base.h](capi-lowpower-audio-sink-base-h.md)

