# OH_EqualizerFrequencyBandGains

```c
struct OH_EqualizerFrequencyBandGains {...}
```

## Overview

Specify equalizer frequency band gains.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

**Related module**: [OHAudioSuite](capi-others-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t gains[EQUALIZER_BAND_NUM] | The equalizer supports gain adjustment for 10 specific frequencies. Frequencies: 31 Hz, 62 Hz, 125 Hz, 250 Hz, 500 Hz, 1 kHz, 2 kHz, 4 kHz, 8 kHz, 16 kHz.<br>**Since**: 22 |


