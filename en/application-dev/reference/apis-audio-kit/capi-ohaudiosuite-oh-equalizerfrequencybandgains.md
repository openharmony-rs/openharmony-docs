# OH_EqualizerFrequencyBandGains
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} OH_EqualizerFrequencyBandGains
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
| int32_t gains[EQUALIZER_BAND_NUM] | Settings for the equalizer band gains. The value of **EQUALIZER_BAND_NUM** is **10**, with each gain value ranging from -10 to 10 dB.<br> Frequency bands: 31 Hz, 62 Hz, 125 Hz, 250 Hz, 500 Hz, 1 kHz, 2 kHz, 4 kHz, 8 kHz, and 16 kHz.<br>**Since**: 22|
