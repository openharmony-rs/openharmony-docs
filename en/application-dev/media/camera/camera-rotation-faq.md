# Camera Preview Rotation Issues

<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=45526eba67080b876eb51af31a33be43ae26f701 translatedAt=2026-07-13T13:21:05.712Z pushedAt=2026-07-21T07:29:05.886Z -->

## Symptom

The preview image is rotated incorrectly when the application opens the camera, preventing normal camera usage.

## Possible Causes

Camera preview rotation issues may occur in the following scenarios: the preview rotation APIs are called during session configuration; the camera window orientation changes, requiring the preview rotation to be adjusted. If the preview rotation is not adjusted in the corresponding scenarios, the preview image may be displayed with an incorrect rotation angle. Possible causes include:

1. The camera preview rotation APIs ([getPreviewRotation](../../reference/apis-camera-kit/arkts-apis-camera-PreviewOutput.md#getpreviewrotation12) and [setPreviewRotation](../../reference/apis-camera-kit/arkts-apis-camera-PreviewOutput.md#setpreviewrotation12)) are not properly handled during session configuration.

2. The session configuration sequence is incorrect. For example, the camera preview rotation APIs are called before [commitConfig](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#commitconfig11) is completed.

3. The camera preview rotation APIs are not handled when the camera window orientation changes.

4. Incorrect parameters are passed to `getPreviewRotation` or `setPreviewRotation`.

**Troubleshooting Steps**

Step 1: Verify that `getPreviewRotation` and `setPreviewRotation` are correctly called after `commitConfig` is completed during session configuration.

Step 2: If the following error logs are displayed, the session configuration is not completed before calling the camera preview rotation APIs.

Logs: `PreviewOutput GetPreviewOutputRotation error!`, `session is nullptr|PreviewRotation call failed. error code: 7400201`

Step 3: Verify that the application listens for `Display` object changes to detect the current window state. When the camera window orientation changes, call `getPreviewRotation` and `setPreviewRotation` to adjust the preview rotation.

Step 4: The input parameter of `getPreviewRotation` must be the current rotation angle of the camera window, which can be obtained through `display.getDefaultDisplaySync.rotation`. The `previewRotation` parameter passed to `setPreviewRotation` must be the output returned by `getPreviewRotation`. The value of `isDisplayLocked` must be consistent with the setting of `setXComponentSurfaceRotation`.

Log keywords: `GetPreviewRotation` | `SetPreviewRotation` | `session is nullptr`

## Case Study

**Symptom**

The application starts the scan function in a floating window. When switching between landscape and portrait orientations, the preview image is rotated an additional 90 degrees.

**Analysis**

When opening the camera in a floating window, the application correctly handles the camera preview rotation APIs during session configuration. The preview rotation is correct during cold start, but the preview image rotates by 90 degrees after an orientation change.

Log analysis shows that the application calls `getPreviewRotation` and `setPreviewRotation` to adjust the preview rotation before the camera window orientation changes.

**Conclusion**

The application does not adjust the preview rotation by calling `getPreviewRotation` and `setPreviewRotation` after the camera window orientation changes.

**Solution**

Call `getPreviewRotation` and `setPreviewRotation` to adjust the preview rotation when the camera window orientation changes.

Reference: [Adjusting Camera Rotation Angles (ArkTS)](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/camera-rotation-angle-adaptation#preview).

## Prevention

Use the preview rotation APIs during session configuration. It is recommended that you call them after `commitConfig` and before `start`.

When using the camera, listen for `Display` object changes to detect the current window state. When the camera window orientation changes, adjust the preview rotation accordingly. It is recommended that you create the listener immediately after configuring the preview rotation APIs during session configuration.

Reference: [Adjusting Camera Rotation Angles (ArkTS)](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/camera-rotation-angle-adaptation#preview).