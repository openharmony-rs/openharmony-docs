# OH_AudioAccessoryNoiseReductionCapability

<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=fea09459a0476f095195448c2ce1ed787d76ab6a translatedAt=2026-08-31T02:32:57.042Z pushedAt=2026-08-31T08:36:50.186Z -->

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