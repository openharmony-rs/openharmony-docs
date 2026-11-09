# OH_AudioSuite_DownloadStatusInfoArray (System API)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=a306395a78cd7ac89b1bdc20446e826350df2c3a translatedAt=2026-11-03T04:25:27.108Z pushedAt=2026-11-04T03:11:47.031Z nl=1 -->

```c
typedef struct OH_AudioSuite_DownloadStatusInfoArray {...} OH_AudioSuite_DownloadStatusInfoArray
```

## Overview

Defines the download status information array structure.

**Since:** 26.0.0

**System API:** This is a system API.

**Related Module:** [OHAudioSuite](capi-ohaudiosuite.md)

**File to include:** [native_audio_suite_download_manager.h](capi-native-audio-suite-download-manager-h-sys.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint32_t size | Size of the pointer array of download status information.<br>**Since:** 26.0.0 |
| [OH_AudioSuite_DownloadStatusInfo](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfo-sys.md) **downloadStatusInfo | Pointer array of download status information.<br>**Since:** 26.0.0 |


