# Screen Capture FAQs

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=c958179c8077587660ef9f20c72543967982b782 translatedAt=2026-11-04T06:36:58.103Z pushedAt=2026-11-04T06:36:58.103Z nl=1 -->

## AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT When Starting Screen Capture

### Symptom

Setting screen capture parameters or starting screen capture fails.

### Possible Causes

1. The number of instances exceeds the current limit of two instances per data format.

2. The policy for keeping screen capture running during calls is not set, so screen capture cannot start.

3. The screen capture configuration exceeds the supported limits, so screen capture cannot start.

### Solution

1. If screen capture stops because its state changes, asynchronously release screen capture resources in [OH_AVScreenCapture_SetStateCallback()](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_setstatecallback), the state callback.

   Screen capture session limits:

   - A maximum of four client applications can coexist, such as meeting screen sharing, meeting screen projection, background music recognition, and system screen recording.

   - Each application can create up to two instances per mode (saving to a file or a stream). A typical scenario is recording an online meeting while sharing the screen.

2. From API version 20, use [OH_AVScreenCapture_StrategyForKeepCaptureDuringCall()](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforkeepcaptureduringcall) to set the policy for keeping screen capture running during cellular calls.

3. When screen capture starts in file mode, the video encoding parameters are checked against the supported limits. The video bitrate (videoBitrate) must be in the range [1, 30000000], in bits per second (bit/s). Values outside this range cause startup to fail. Check and adjust the screen capture configuration.