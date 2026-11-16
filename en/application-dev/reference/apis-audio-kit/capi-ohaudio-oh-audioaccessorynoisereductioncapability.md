# OH_AudioAccessoryNoiseReductionCapability
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=96f4a6288457dc7323c09f4157fef4291d5dc537 translatedAt=2026-11-09T10:26:34.403Z pushedAt=2026-11-09T11:30:18.886Z nl=1 -->

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
| uint32_t structSize | Struct size, in bytes.<br>The caller must initialize this field.<br>The system verifies the struct size through this field. |
| const [OH_AudioNoiseReductionMode](capi-native-audio-common-h.md#oh_audionoisereductionmode) *supportedModes | Array of supported noise reduction modes. |
| uint32_t supportedModeCount | Number of supported noise reduction modes. |
| [OH_AudioNoiseReductionMode](capi-native-audio-common-h.md#oh_audionoisereductionmode) currentMode | Current noise reduction mode of the device.<br>It indicates the initial state when the capability is registered. |
