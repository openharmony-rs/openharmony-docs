# OH_AudioAccessoryNoiseReductionCapability
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=231a0f852838e757ab03536e79d2ff209c5f5457 translatedAt=2026-10-08T12:40:24.259Z pushedAt=2026-10-13T05:57:32.107Z -->

```c
typedef struct OH_AudioAccessoryNoiseReductionCapability {...} OH_AudioAccessoryNoiseReductionCapability
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
| uint32_t structSize | Struct size, in bytes.<br>The caller must initialize this field.<br>The system verifies the struct size through this field. |
| const [OH_AudioNoiseReductionMode](capi-native-audio-common-h.md#oh_audionoisereductionmode) *supportedModes | Array of supported noise reduction modes. |
| uint32_t supportedModeCount | Number of supported noise reduction modes. |
| [OH_AudioNoiseReductionMode](capi-native-audio-common-h.md#oh_audionoisereductionmode) currentMode | Current noise reduction mode of the device.<br>It indicates the initial state when the capability is registered. |
