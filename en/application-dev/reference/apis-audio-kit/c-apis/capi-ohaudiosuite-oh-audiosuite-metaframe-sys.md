# OH_AudioSuite_MetaFrame(System API)

```c
typedef struct OH_AudioSuite_MetaFrame {...} OH_AudioSuite_MetaFrame
```

## Overview

Define the audio meta data frame structure. This structure is used to pass audio data and meta data together.

<!--Device-struct OH_AudioSuite_MetaFrame {...}--><!--Device-struct OH_AudioSuite_MetaFrame {...}-End-->

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.0.0

**System API:** This is a system API.

**Related module**: [OHAudioSuite](capi-audio-kit-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h(System API)](capi-native-audio-suite-base-h-sys.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| void* audioData | Audio data pointer.<br>**Since**: 26.0.0<br><!--Device-void* audioData--><!--Device-void* audioData-End--> |
| int32_t audioDataSize | Audio data size.<br>**Since**: 26.0.0<br><!--Device-int32_t audioDataSize--><!--Device-int32_t audioDataSize-End--> |
| void* metaData | Meta data pointer.<br>**Since**: 26.0.0<br><!--Device-void* metaData--><!--Device-void* metaData-End--> |
| int32_t metaDataSize | Meta data size.<br>**Since**: 26.0.0<br><!--Device-int32_t metaDataSize--><!--Device-int32_t metaDataSize-End--> |


