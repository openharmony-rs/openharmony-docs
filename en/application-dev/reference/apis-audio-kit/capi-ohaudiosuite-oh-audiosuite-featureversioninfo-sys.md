# OH_AudioSuite_FeatureVersionInfo (System API)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=96c2f543d580d0d2b2dabb53953551af3ab0252e translatedAt=2026-11-03T04:25:37.119Z pushedAt=2026-11-04T03:11:47.028Z nl=1 -->

```c
typedef struct OH_AudioSuite_FeatureVersionInfo {...} OH_AudioSuite_FeatureVersionInfo
```

## Overview

Defines the feature version information struct.

**Since:** 26.0.1

**System API:** This is a system API.

**Related module:** [OHAudioSuite](capi-ohaudiosuite.md)

**File to include:** [native_audio_suite_download_manager.h](capi-native-audio-suite-download-manager-h-sys.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| char featureName[256] | Feature name.<br>**Since:** 26.0.1 |
| int32_t downloadStatus | Current status of the feature.<br>**Since:** 26.0.1 |
| char version[128] | Feature version.<br>**Since:** 26.0.1 |
| int64_t size | Size of the space occupied by the feature module, in bytes.<br>**Since:** 26.0.1 |
| int32_t errorCode | Error code.<br>**Since:** 26.0.1 |
