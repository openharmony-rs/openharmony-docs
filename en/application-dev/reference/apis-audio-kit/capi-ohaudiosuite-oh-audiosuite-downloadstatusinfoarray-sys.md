# OH_AudioSuite_DownloadStatusInfoArray (System API)

<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=b9233046c3f90e6ca45044fd6224c6d08e2aa256 translatedAt=2026-08-31T02:33:22.258Z pushedAt=2026-08-31T08:33:44.984Z -->

```c
typedef struct OH_AudioSuite_DownloadStatusInfoArray {...} OH_AudioSuite_DownloadStatusInfoArray
```

## Overview

Defines the download status information array structure.

**Since:** 26.0.0

**System API:** This is a system API.

**Related module:** [OHAudioSuite](capi-ohaudiosuite.md)

**File to include:** [native_audio_suite_download_manager.h](capi-native-audio-suite-download-manager-h-sys.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint32_t size | Size of the download status information pointer array.<br>**Since:** 26.0.0 |
| [OH_AudioSuite_DownloadStatusInfo](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfo-sys.md) **downloadStatusInfo | Pointer array of download status information.<br>**Since:** 26.0.0 |