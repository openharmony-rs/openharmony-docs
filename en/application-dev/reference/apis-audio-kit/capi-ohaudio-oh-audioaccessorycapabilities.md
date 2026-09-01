# OH_AudioAccessoryCapabilities

<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=fea09459a0476f095195448c2ce1ed787d76ab6a translatedAt=2026-08-31T02:32:04.228Z pushedAt=2026-08-31T08:42:45.687Z -->

```c
typedef struct OH_AudioAccessoryCapabilities {...} OH_AudioAccessoryCapabilities
```

## Overview

Defines the capabilities of an audio accessory.

The caller must set **structSize** to sizeof(OH_AudioAccessoryCapabilities).

**Since:** 26.0.0

**Related module:** [OHAudio](capi-ohaudio.md)

**File to include:** [native_audio_accessory_common.h](capi-native-audio-accessory-common-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint32_t structSize | Size of the struct, in bytes.<br>The caller must initialize this field. |
| const [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamProperties | Array of supported audio stream configurations.<br>Each entry represents a valid combination of sampling rate, sampling format, and channel count.<br>The system performs a deep copy of this array. |
| uint32_t streamPropertyCount | Number of supported audio stream configurations. |