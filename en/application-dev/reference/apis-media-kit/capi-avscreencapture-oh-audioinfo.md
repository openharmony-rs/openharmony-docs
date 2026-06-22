# OH_AudioInfo
<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=320793da1b58e6a20565f5e582fc3e50f69572ee translatedAt=2026-06-22T03:37:40.044Z pushedAt=2026-06-22T09:23:26.583Z -->

```c
typedef struct OH_AudioInfo {...} OH_AudioInfo
```

## Overview

The struct describes the audio information.

To perform both external capture (using microphones) and internal capture, **audioSampleRate** and **audioChannels** must be the same for both audio channels.

**Since**: 10

**Related module**: [AVScreenCapture](capi-avscreencapture.md)

**Header file**: [native_avscreen_capture_base.h](capi-native-avscreen-capture-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_AudioCaptureInfo](capi-avscreencapture-oh-audiocaptureinfo.md) micCapInfo | External audio capture information.|
| [OH_AudioCaptureInfo](capi-avscreencapture-oh-audiocaptureinfo.md) innerCapInfo | Internal audio capture information.|
| [OH_AudioEncInfo](capi-avscreencapture-oh-audioencinfo.md) audioEncInfo | Audio encoding information, which is not required for raw streams.|