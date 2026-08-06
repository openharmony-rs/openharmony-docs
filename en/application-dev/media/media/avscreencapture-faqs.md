# Screen Capture FAQs

<!--Kit: Media Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @zzs_911-->
<!--Designer: @stupig001-->
<!--Tester: @xdlinc-->
<!--Adviser: @w_Machine_cc-->

## Error Code AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT Is Reported When Starting Screen Capture

This error occurs when the number of instances exceeds the system limit. The current specification allows a maximum of two instances per data format. You are advised to release any extra instances before creating new ones.

Possible cause: During screen capture, the resources are not released after you reject the screen capture, stop screen capture in the notification bar, or the recording is interrupted by a call.

Solution: If the screen capture stops due to status change, you need to asynchronously release the screen recording resources via [OH_AVScreenCapture_SetStateCallback()](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_setstatecallback) (state callback).

Screen capture session limit policy:

1. A maximum of four client applications are allowed. Examples include simultaneous use of screen sharing in a meeting, screen casting, background music recognition, and system screen capture.

2. Each application can create up to two instances per operational mode (saving to files or saving as streams). A typical use case is simultaneously recording meeting content while sharing the screen during an online meeting.

## Error Code AV_SCREEN_CAPTURE_ERR_OPERATE_NOT_PERMIT Is Reported When Starting Screen Capture During a Call

Starting from API version 20, you can call [OH_AVScreenCapture_StrategyForKeepCaptureDuringCall()](../../reference/apis-media-kit/capi-native-avscreen-capture-h.md#oh_avscreencapture_strategyforkeepcaptureduringcall) to keep screen capture during a cellular call.
