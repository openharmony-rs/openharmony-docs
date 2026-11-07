# Screen Capture FAQs

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @chenkun613227-->
<!--Designer: @yxc2-->
<!--Tester: @xdlinc-->
<!--Adviser: @zzs911-->
<!-- md-trans-meta sourceCommit=5a8c55e6b1f303fae33c03815f70c538de49d46c translatedAt=2026-11-05T06:16:33.956Z pushedAt=2026-08-22T06:48:20.456Z nl=1 -->

## Error Code AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT Is Reported When Starting Screen Capture

### Symptom

Screen capture parameter configuration or startup fails.

### Possible Causes

1. The number of instances exceeds the current limit of two instances per data format.

2. The strategy for keeping screen capture active during a call is not set, so screen capture cannot start.

3. The screen capture configuration exceeds the supported limits, so screen capture cannot start.

### Solution

1. If screen capture stops due to a state change, asynchronously release the screen capture resources in [OH_AVScreenCapture_SetStateCallback()](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_setstatecallback) (state callback).

   Screen capture session limit policy:

   - A maximum of four client applications are allowed. Examples include simultaneous use of screen sharing in a meeting, screen casting, background music recognition, and system screen capture.

   - Each application can create up to two instances per operational mode (saving to files or saving as streams). A typical use case is simultaneously recording meeting content while sharing the screen during an online meeting.

2. Starting from API version 20, to keep screen capture active during a call, call [OH_AVScreenCapture_StrategyForKeepCaptureDuringCall()](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforkeepcaptureduringcall) to set the strategy for keeping screen capture during cellular calls.

3. When screen capture starts in file-saving mode, video encoding parameters are checked against the supported limits. The video bit rate (videoBitrate) must be in the range [1, 30000000], in bits per second (bit/s). Values outside this range cause startup to fail. Check and adjust the screen capture configuration parameters.
