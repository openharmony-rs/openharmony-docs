# OH_AudioSuite_PureVoiceChangeOption
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=e9ec8701c87cf0327fd7aa17be40e1c4aeed0156 translatedAt=2026-11-10T03:09:34.383Z pushedAt=2026-11-10T04:48:13.022Z nl=1 -->

```c
typedef struct OH_AudioSuite_PureVoiceChangeOption {...} OH_AudioSuite_PureVoiceChangeOption
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
| [OH_AudioSuite_PureVoiceChangeGenderOption](capi-native-audio-suite-base-h.md#oh_audiosuite_purevoicechangegenderoption) optionGender | Specifies the gender for traditional voice change. |
| [OH_AudioSuite_PureVoiceChangeType](capi-native-audio-suite-base-h.md#oh_audiosuite_purevoicechangetype) optionType | Specifies the type of traditional voice change. |
| float pitch | Specifies the pitch for traditional voice change. To use the default pitch in the system for the best effect, set this parameter to OH_PURE_VOICE_DEFAULT_PITCH in [macros](capi-native-audio-suite-base-h.md#macros).<br> The value range for a custom pitch is [0.3f, 3.0f]. |
