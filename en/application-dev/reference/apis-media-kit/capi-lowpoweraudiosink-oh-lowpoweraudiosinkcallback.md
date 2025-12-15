# OH_LowPowerAudioSinkCallback
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @wang-haizhou6-->
<!--Designer: @HmQQQ-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_LowPowerAudioSinkCallback OH_LowPowerAudioSinkCallback
```

## Overview

The struct contains a set of callback function pointers for the LowPowerAudioSink.

To ensure the normal running of the LowPowerAudioSink, you must register the instance of this struct with the [OH_LowPowerAudioSink](capi-lowpoweraudiosink-oh-lowpoweraudiosink.md) instance and process the information reported by the callback functions.

**Since**: 20

**Related module**: [LowPowerAudioSink](capi-lowpoweraudiosink.md)

**Header file**: [lowpower_audio_sink_base.h](capi-lowpower-audio-sink-base-h.md)
