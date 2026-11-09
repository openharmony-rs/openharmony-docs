# OH_AudioAccessoryCapabilities
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=96f4a6288457dc7323c09f4157fef4291d5dc537 translatedAt=2026-11-09T10:26:31.667Z pushedAt=2026-11-09T11:28:41.518Z nl=1 -->

```c
typedef struct {...} OH_AudioAccessoryCapabilities
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