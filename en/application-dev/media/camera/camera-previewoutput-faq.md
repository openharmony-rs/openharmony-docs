# Camera Preview Stream Startup Issues
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=c363c4134c11bcec868cc8b279dc8af0b7551cf3 translatedAt=2026-11-02T02:33:31.187Z pushedAt=2026-11-02T02:33:31.187Z nl=1 -->

## Symptom

The application displays a black screen or distorted images when opening the camera, preventing normal camera usage.

## Possible Causes

The preview stream (`previewOutput`) in the camera process consists of three stages: creation, addition, and startup. Dependencies exist between these stages. If a previous stage fails, subsequent stages will also fail, resulting in a black screen on the camera. Possible causes include the following:

1. The `SurfaceId` is not passed correctly, preventing images from being displayed properly.

2. [createPreviewOutput](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#createpreviewoutput) fails, or the profile used does not match the `cameraDevice`.

3. [addOutput](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#addoutput11) fails, causing the output to not be successfully configured in the session.

4. The aspect ratio of `previewOutput` is inconsistent with that of `photoOutput`/`videoOutput`.

**Troubleshooting Steps**

Step 1: Print the `SurfaceId` in the application and compare it with internal logs to verify that the `SurfaceId` is correct. You can also search for logs related to the preview output surface to confirm whether the `SurfaceId` is valid. When creating preview, photo, and video outputs, use profiles with the same aspect ratio.

Step 2: If the profile configuration is incorrect, logs containing `ValidCreateOutputStream` are generated. If the width and height of the camera profile do not match those of the display component (such as XComponent), the displayed image may be distorted.

Step 3: When calling [addOutput](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#addoutput11), the system performs sequence validation. Configure outputs only when the session is in the `beginConfig` state, after `addInput` has been called and before `commitConfig` is called. You can use `ValidateOutputProfile` to check the profile information of the corresponding `previewOutput`.

Log keywords: `CreatePreviewOutput` | `ValidCreateOutputStream` | `CanAddOutput` | `ValidateOutputProfile`

## Solution

1. Check whether the input `SurfaceId` is null and valid to ensure that images can be displayed correctly.

2. If a profile is passed as a parameter, use `getSupportedOutputCapability` to obtain the supported profiles for the corresponding input. Ensure that the selected mode (`mode`) and camera device (`cameraDevice`) match the profile.

3. Before calling `addOutput`, call `canAddOutput` to verify that the output can be added to the session. If validation fails, recreate the output and add it again.

4. Before configuring `previewOutput` with `photoOutput` or `videoOutput`, compare their profiles to ensure that they use the same aspect ratio.