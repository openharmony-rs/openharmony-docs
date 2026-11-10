# OH_EqualizerFrequencyBandGains
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=e9ec8701c87cf0327fd7aa17be40e1c4aeed0156 translatedAt=2026-11-10T03:10:00.475Z pushedAt=2026-11-10T04:48:23.326Z nl=1 -->

```c
typedef struct OH_EqualizerFrequencyBandGains {...} OH_EqualizerFrequencyBandGains
```

## Overview

The struct describes the configuration parameters for the equalizer effect node used in audio creation.

**Since**: 22

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| int32_t gains[EQUALIZER_BAND_NUM] | Equalizer band gain configuration. The array length EQUALIZER_BAND_NUM is 10, and the gain input range is [-10, 10] in dB (decibel).<br> Bands: 31Hz, 62Hz, 125Hz, 250Hz, 500Hz, 1kHz, 2kHz, 4kHz, 8kHz, 16kHz.<br>**Since:** 22 |
