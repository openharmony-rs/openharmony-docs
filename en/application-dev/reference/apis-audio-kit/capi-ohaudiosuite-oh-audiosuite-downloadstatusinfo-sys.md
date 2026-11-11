# OH_AudioSuite_DownloadStatusInfo (System API)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=a306395a78cd7ac89b1bdc20446e826350df2c3a translatedAt=2026-11-03T04:25:33.894Z pushedAt=2026-11-04T03:11:47.026Z nl=1 -->

```c
typedef struct OH_AudioSuite_DownloadStatusInfo {...} OH_AudioSuite_DownloadStatusInfo
```

## Overview

Defines the download status information struct.

**Since:** 26.0.0

**System API:** This is a system API.

**Related module:** [OHAudioSuite](capi-ohaudiosuite.md)

**File to include:** [native_audio_suite_download_manager.h](capi-native-audio-suite-download-manager-h-sys.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| char featureName[256] | Name of the cloud file.<br>**Since:** 26.0.0 |
| int32_t downloadStatus | Current download status of the cloud file.<br>**Since:** 26.0.0 |
| int64_t size | Size of the cloud file.<br>**Since:** 26.0.0 |
| char installPath[256] | Local installation path of the cloud file.<br>**Since:** 26.0.0 |
| int32_t progress | Current download progress of the cloud file [0-100].<br>**Since:** 26.0.0 |
| int32_t errorCode | Error code.<br>**Since:** 26.0.0 |


