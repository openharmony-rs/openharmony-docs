# OH_AudioSuite_FeatureVersionInfo(System API)

```c
struct OH_AudioSuite_FeatureVersionInfo {...}
```

## Overview

Define feature version information structure.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.0.1

**System API:** This is a system API.

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

**Header file**: [native_audio_suite_download_manager.h(System API)](capi-native-audio-suite-download-manager-h-sys.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char featureName[256] | Feature name.<br>**Since**: 26.0.1 |
| int32_t downloadStatus | Download status.<br>**Since**: 26.0.1 |
| char version[128] | Feature version.<br>**Since**: 26.0.1 |
| int64_t size | Feature size in bytes, unit is byte.<br>**Since**: 26.0.1 |
| int32_t errorCode | Error code.<br>**Since**: 26.0.1 |


