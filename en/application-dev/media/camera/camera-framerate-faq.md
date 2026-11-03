# Frame Rate Settings Do Not Take Effect
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=4262000117456ea7ec773fc4d641408e0631b8d6 translatedAt=2026-11-02T02:33:31.187Z pushedAt=2026-11-02T02:33:31.187Z nl=1 -->

## Symptom

Frame rate settings do not take effect in video recording mode.

## Possible Causes

The frame rate APIs have requirements for call timing, supported modes, and consistency with the recording stream frame rate. Settings do not take effect if these requirements are not met. Possible causes are as follows:

1. [setFrameRate](../../reference/apis-camera-kit/arkts-apis-camera-PreviewOutput.md#setframerate12) (ArkTS) and [OH_PreviewOutput_SetFrameRate](../../reference/apis-camera-kit/capi-preview-output-h.md#oh_previewoutput_setframerate) (C/C++) support NORMAL_PHOTO and NORMAL_VIDEO modes only. Calling them in other modes returns [7400101 Invalid Parameter](../../reference/apis-camera-kit/errorcode-camera.md#7400101-invalid-parameter) in ArkTS or CAMERA_INVALID_ARGUMENT in [Camera_ErrorCode](../../reference/apis-camera-kit/capi-camera-h.md#camera_errorcode) in C/C++.

2. [setFrameRate](../../reference/apis-camera-kit/arkts-apis-camera-PreviewOutput.md#setframerate12) or [OH_PreviewOutput_SetFrameRate](../../reference/apis-camera-kit/capi-preview-output-h.md#oh_previewoutput_setframerate) is called before the session completes stream configuration through [commitConfig](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#commitconfig11) (ArkTS) or [OH_CaptureSession_CommitConfig](../../reference/apis-camera-kit/capi-capture-session-h.md#oh_capturesession_commitconfig) (C/C++).

3. After setting a variable frame rate, the app calls [setFrameRate](../../reference/apis-camera-kit/arkts-apis-camera-PreviewOutput.md#setframerate12) or [OH_PreviewOutput_SetFrameRate](../../reference/apis-camera-kit/capi-preview-output-h.md#oh_previewoutput_setframerate) again to change it. This operation is not supported.

4. When changing a fixed frame rate, the new and existing rates do not have an integer-multiple relationship. The API returns [7400110 Configuration Conflicts](../../reference/apis-camera-kit/errorcode-camera.md#7400110-configuration-conflicts) in ArkTS or CAMERA_UNRESOLVED_CONFLICTS_WITH_CURRENT_CONFIGURATIONS in [Camera_ErrorCode](../../reference/apis-camera-kit/capi-camera-h.md#camera_errorcode) in C/C++.

5. Preview and recording stream frame rate constraints are inconsistent.
   - The recording stream uses a frame rate range, but the preview stream does not use the same range.
   - The recording stream uses a fixed frame rate, but the preview frame rate is not a divisor of the recording frame rate.

## Solution

1. Specify NORMAL_PHOTO or NORMAL_VIDEO when creating the session through [createSession](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#createsession11) (ArkTS) or [OH_CameraManager_CreateCaptureSession](../../reference/apis-camera-kit/capi-camera-manager-h.md#oh_cameramanager_createcapturesession) (C/C++).

2. Call [setFrameRate](../../reference/apis-camera-kit/arkts-apis-camera-PreviewOutput.md#setframerate12) or [OH_PreviewOutput_SetFrameRate](../../reference/apis-camera-kit/capi-preview-output-h.md#oh_previewoutput_setframerate) after the session completes [commitConfig](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#commitconfig11) or [OH_CaptureSession_CommitConfig](../../reference/apis-camera-kit/capi-capture-session-h.md#oh_capturesession_commitconfig).

3. Do not call [setFrameRate](../../reference/apis-camera-kit/arkts-apis-camera-PreviewOutput.md#setframerate12) or [OH_PreviewOutput_SetFrameRate](../../reference/apis-camera-kit/capi-preview-output-h.md#oh_previewoutput_setframerate) repeatedly for a variable frame rate. When changing a fixed frame rate, ensure that the new and existing rates have an integer-multiple relationship. Otherwise, the API returns [7400110 Configuration Conflicts](../../reference/apis-camera-kit/errorcode-camera.md#7400110-configuration-conflicts) or CAMERA_UNRESOLVED_CONFLICTS_WITH_CURRENT_CONFIGURATIONS in [Camera_ErrorCode](../../reference/apis-camera-kit/capi-camera-h.md#camera_errorcode).

4. Keep the preview stream frame rate consistent with the recording stream constraints.
   - If the recording stream uses a frame rate range, set the same range for the preview stream.
   - If the recording stream uses a fixed frame rate, set a fixed preview frame rate that is a divisor of the recording frame rate.

   Select a recording output stream that meets your requirements through [CameraOutputCapability](../../reference/apis-camera-kit/arkts-apis-camera-i.md#cameraoutputcapability) (ArkTS) or [OH_CameraManager_GetSupportedCameraOutputCapability](../../reference/apis-camera-kit/capi-camera-manager-h.md#oh_cameramanager_getsupportedcameraoutputcapability).videoProfiles (C/C++) to obtain the expected frame rate.
