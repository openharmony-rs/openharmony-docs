---
kits: ["Media Kit / Media Services"]
description: "Summarizes common AVScreenCapture issues and solutions, including exceeding the instance limit and being unable to start screen capture during a call."
keywords: [AVScreenCapture, screen capture during calls, state callbacks]
doctype: faq
status: active
---

# Screen Capture FAQs

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=c569c5cc1f327da4a0ad09bb8d59b653d244c83e translatedAt=2026-11-02T02:33:31.187Z pushedAt=2026-11-02T02:33:31.187Z nl=1 -->

## Error Code AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT Is Reported When Starting Screen Capture

### Symptom

Screen capture parameter configuration or startup fails.

### Possible Causes

1. The number of instances exceeds the current limit of two instances per data format.

2. Screen capture cannot start because the policy for keeping capture active during calls has not been set.

3. Screen capture cannot start because its parameters exceed the supported limits.

### Solution

1. If screen capture stops due to a state change, release capture resources asynchronously in the [OH_AVScreenCapture_SetStateCallback()](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_setstatecallback) state callback.

   Screen capture session limits:

   - Up to four client apps can run concurrently, for example, meeting screen sharing, meeting screen projection, background music recognition, and system screen recording.

   - Each app can create up to two instances per mode (file output or bitstream output). A typical scenario is sharing the screen in an online meeting while recording the meeting.

2. Starting from API version 20, use [OH_AVScreenCapture_StrategyForKeepCaptureDuringCall()](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforkeepcaptureduringcall) to keep screen capture active during cellular calls.

3. Video encoding parameters are validated when starting screen capture in file output mode. videoBitrate must be in the range [1, 30000000], in bits per second (bit/s). Values outside this range cause startup to fail. Check and adjust the capture configuration.
