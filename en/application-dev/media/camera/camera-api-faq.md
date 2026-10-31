# Camera API Call Sequence Issues

<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=45526eba67080b876eb51af31a33be43ae26f701 translatedAt=2026-07-13T13:20:40.435Z pushedAt=2026-07-21T06:47:08.463Z -->

## Symptom

The camera cannot be started properly. Related logs indicate that some validations fail or that certain parameters are invalid.

## Possible Causes

A normal camera startup workflow includes creating a camera manager (`cameraManager`), creating input and output streams (`input` and `output`), creating a session (`session`), configuring the session, and starting the session. These steps have dependencies on each other. If any step fails, an object is released prematurely during the workflow, or an incompatible configuration profile is used, the camera may fail to start. For example, creating an output stream before creating an input stream, or creating an output stream with capability values that do not match the input stream, may result in an incompatible input/output configuration. Possible causes include:

1. An incorrect profile is used, causing the created output stream to be incompatible with the input stream. This may result in a black screen when starting the camera.

2. A camera configuration API is called before the corresponding configuration is completed, causing the camera startup to fail.

3. A listener is registered at an incorrect time. As a result, the listener does not take effect, causing the camera startup to fail.

**Troubleshooting Steps**

Step 1: Create a camera manager ([cameraManager](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md)), select the camera to use ([getSupportedCameras](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#getsupportedcameras)), and then obtain the output stream capability profiles ([getSupportedOutputCapability](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#getsupportedoutputcapability11)) for the selected camera. Ensure that the profiles correspond to the output stream mode (photo or video recording).

Step 2: Create the corresponding input stream based on the capability profiles, call the [open](../../reference/apis-camera-kit/arkts-apis-camera-CameraInput.md#open) method of the input stream to turn on the camera, and then create the output streams (preview, photo, or video recording). You are advised to register the `photoAvailable` listener at this point to receive photos. Ensure that the output streams have the same resolution, and then create a session of the corresponding mode. Note that the mode must match the output streams.

Step 3: Call the [beginConfig](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#beginconfig11) method of the session to begin configuration. First, call the [addInput](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#addinput11) method to add the input stream; then call the [addOutput](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#addoutput11) method to add the output streams; finally, call the [commitConfig](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#commitconfig11) method to commit the session configuration, at which point the session configuration is complete. Most issues are reported during this process. If a problem occurs, the entire [commitConfig](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#commitconfig11) flow cannot be completed successfully.

Step 4: After [commitConfig](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#commitconfig11), most session listener methods can be configured at this stage, and certain effect settings, such as white balance, can also be applied.

## Solution

1. Before creating an output stream, compare the resolutions specified in the profiles of the input and output streams to ensure that they are consistent.

2. Call most `set` APIs after `commitConfig` is completed. For example, white balance related `set` APIs should be called after session configuration is complete.

3. Call most listener registration APIs after `addInput` is called to ensure that the camera is opened and added to the session before receiving data through callbacks.

For details, see [Photo Capture Practices (ArkTS)](camera-shooting-case.md).