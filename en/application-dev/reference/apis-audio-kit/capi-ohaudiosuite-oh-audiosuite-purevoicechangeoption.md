# OH_AudioSuite_PureVoiceChangeOption
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} OH_AudioSuite_PureVoiceChangeOption
```

## Overview

Defines pure voice change options for audio creation.

**Since**: 23

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_AudioSuite_PureVoiceChangeGenderOption](capi-native-audio-suite-base-h.md#oh_audiosuite_purevoicechangegenderoption) optionGender | Defines the gender for pure voice change.|
| [OH_AudioSuite_PureVoiceChangeType](capi-native-audio-suite-base-h.md#oh_audiosuite_purevoicechangetype) optionType | Defines the type for pure voice change.|
| float pitch | Defines the pitch for pure voice change. If the default pitch in the system is used for the optimal effect, set this parameter to [OH_PURE_VOICE_DEFAULT_PITCH](capi-native-audio-suite-base-h.md#macros).<br> The value range of the custom pitch is [0.3f, 3.0f].|
