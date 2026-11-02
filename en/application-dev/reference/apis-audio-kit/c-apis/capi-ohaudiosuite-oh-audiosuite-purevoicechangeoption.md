# OH_AudioSuite_PureVoiceChangeOption

```c
struct OH_AudioSuite_PureVoiceChangeOption {...}
```

## Overview

Define change voice option.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 23

**Related module**: [OHAudioSuite](capi-others-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_AudioSuite_PureVoiceChangeGenderOption](capi-native-audio-suite-base-h.md#oh_audiosuite_purevoicechangegenderoption) optionGender | Define speaker gender.<br>**Since**: 23 |
| [OH_AudioSuite_PureVoiceChangeType](capi-native-audio-suite-base-h.md#oh_audiosuite_purevoicechangetype) optionType | Define voice type.<br>**Since**: 23 |
| float pitch | Define voice pitch. If using default pitch in system for best effect, set to [OH_PURE_VOICE_DEFAULT_PITCH](capi-native-audio-suite-base-h.md#宏定义). For custom pitch setting, specify a value with the valid range: [0.3f, 3.0f]. If the value is out of range, the setting will fail and return [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result).<br>**Since**: 23 |


