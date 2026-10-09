# Session Configuration Issues

<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=45526eba67080b876eb51af31a33be43ae26f701 translatedAt=2026-07-13T13:21:05.769Z pushedAt=2026-07-21T07:36:03.646Z -->

## Symptom

The camera fails to start normally, and errors are reported in session-related processes.

## Possible Causes

The session configuration process consists of four main steps: `beginConfig`, `addInput`, `addOutput`, and `commitConfig`. The calling order of these steps cannot be changed, and all four steps must be configured successfully for the camera to function properly. The specific causes may include the following:

1. [beginConfig](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#beginconfig11) fails.

2. [addInput](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#addinput11) fails.

3. [addOutput](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#addoutput11) fails.

4. [commitConfig](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#commitconfig11) fails.

**Troubleshooting Steps**

Step 1: `beginConfig` may fail if the API is called when the session is already in the `commitConfig` state, or when the session object does not exist, which results in a null pointer error.

Step 2: `addInput` can only be called after the session calls `beginConfig`, and cannot be modified after `commitConfig`. Each session can be configured with only one `input`, and null value detection is performed.

Step 3: `addOutput` can only be called when the session is in the `beginConfig` state, after `addInput` has been called and before `commitConfig` is called. The API checks the current profile to verify whether it matches the input configuration. You can use `ValidateOutputProfile` to check the profile information of the corresponding output. The API also performs null value checks.

Step 4: After the preceding configurations are confirmed, call `commitConfig` to submit the configuration to the underlying system. This connects the input and output streams, allowing image data to be delivered back to the application.

Log keywords: `beginConfig` | `addInput` | `addOutput` | `commitConfig`

## Solution

1. If `beginConfig` fails, check whether the session has been released or whether the session is currently performing a `commitConfig` operation.

2. Before calling the `addInput` API, you can first call the `canAddInput` API to verify whether the current session can add an `input`.

3. Before calling the `addOutput` API, you can first call the `canAddOutput` API to verify whether the current session can add an `output`.

4. During `commitConfig`, ensure that none of the preceding steps have failed and that the session has not been released or subjected to other operations.

For a normal session configuration, refer to [Photo Capture (ArkTS)](camera-shooting.md).