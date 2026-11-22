# OH_AudioAccessoryNoiseReductionCapability
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=03e07731f28ea3c4338c42628096ca0f42c1efd0 translatedAt=2026-11-03T04:18:06.113Z pushedAt=2026-11-04T03:11:46.984Z nl=1 -->

```c
typedef struct {...} OH_AudioAccessoryNoiseReductionCapability
```

## Overview

Defines the noise reduction capability of an audio accessory.

**Since:** 26.0.0

**Related module:** [OHAudio](capi-ohaudio.md)

**File to include:** [native_audio_accessory_common.h](capi-native-audio-accessory-common-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint32_t structSize | Size of the struct, in bytes.<br>The caller must initialize this field.<br>The system uses this field to verify the struct size. |
| const [OH_AudioNoiseReductionMode](capi-native-audio-common-h.md#oh_audionoisereductionmode) *supportedModes | Array of supported noise reduction modes. |
| uint32_t supportedModeCount | Number of supported noise reduction modes. |
| [OH_AudioNoiseReductionMode](capi-native-audio-common-h.md#oh_audionoisereductionmode) currentMode | Current noise reduction mode of the device.<br>Indicates the initial state when the capability is registered. |
