# OH_AudioSuite_DownloadStatusInfo(System API)

```c
typedef struct OH_AudioSuite_DownloadStatusInfo {...} OH_AudioSuite_DownloadStatusInfo
```

## Overview

Define download status information structure.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.0.0

**System API:** This is a system API.

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

**Header file**: [native_audio_suite_download_manager.h(System API)](capi-native-audio-suite-download-manager-h-sys.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char featureName[256] | feature name.<br>**Since**: 26.0.0 |
| int32_t downloadStatus | Download status.<br>**Since**: 26.0.0 |
| int64_t size | feature size.<br>**Since**: 26.0.0 |
| char installPath[256] | Installation path.<br>**Since**: 26.0.0 |
| int32_t progress | Download progress [0-100].<br>**Since**: 26.0.0 |
| int32_t errorCode | Error code.<br>**Since**: 26.0.0 |


