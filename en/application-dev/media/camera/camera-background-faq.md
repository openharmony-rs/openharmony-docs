# Black Preview After Returning from the Background
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=e476139de9ed15b53d382eea5c559d854f9a7593 translatedAt=2026-11-02T02:33:31.187Z pushedAt=2026-11-02T02:33:31.187Z nl=1 -->

## Symptom

A third-party app displays a black camera preview that does not recover after switching to the background and then returning to the foreground.

## Possible Causes

When a third-party app moves to the background, the system may close its camera session for privacy protection or resource preemption, invalidating the session. The preview remains black if the app does not handle this correctly when returning to the foreground. Possible causes are as follows:

1. The system closes the camera session under its privacy protection policy when the app moves to the background, preventing preview recovery when the app returns to the foreground.

2. An app with higher privileges, such as the system camera, preempts camera resources while the third-party app is in the background, making its camera unavailable.

   - ArkTS: The system notifies the app through the CameraInput [on('error')](../../reference/apis-camera-kit/arkts-apis-camera-CameraInput.md#onerror) callback with error code [7400109 Camera Preempted](../../reference/apis-camera-kit/errorcode-camera.md#7400109-camera-preempted).
   - C/C++: The system notifies the app through the [OH_CameraInput_OnError](../../reference/apis-camera-kit/capi-camera-input-h.md#oh_camerainput_onerror) callback with CAMERA_DEVICE_PREEMPTED in [Camera_ErrorCode](../../reference/apis-camera-kit/capi-camera-h.md#camera_errorcode).

3. The app has not registered CameraInput [on('error')](../../reference/apis-camera-kit/arkts-apis-camera-CameraInput.md#onerror) or [OH_CameraInput_RegisterCallback](../../reference/apis-camera-kit/capi-camera-input-h.md#oh_camerainput_registercallback) callbacks and cannot detect camera preemption.

## Solution

1. Listen for foreground/background lifecycle events, such as onBackground/onForeground of the ability. In onBackground, stop the session and release related resources, including session, output, and input. In onForeground, rebuild the complete camera pipeline: create CameraInput, create Output, create Session, then call beginConfig, addInput, addOutput, commitConfig, and start.

2. Register CameraInput [on('error')](../../reference/apis-camera-kit/arkts-apis-camera-CameraInput.md#onerror) or [OH_CameraInput_RegisterCallback](../../reference/apis-camera-kit/capi-camera-input-h.md#oh_camerainput_registercallback) callbacks to detect camera preemption.

3. On receiving error code [7400109 Camera Preempted](../../reference/apis-camera-kit/errorcode-camera.md#7400109-camera-preempted) or CAMERA_DEVICE_PREEMPTED in [Camera_ErrorCode](../../reference/apis-camera-kit/capi-camera-h.md#camera_errorcode), release the current session and CameraInput resources and reopen the camera after returning to the foreground.

For sample code, see [Photo Capture Practices (ArkTS)](camera-shooting-case.md).
