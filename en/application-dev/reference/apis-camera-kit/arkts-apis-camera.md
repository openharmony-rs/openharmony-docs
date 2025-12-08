# Module Description
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

The module provides a set of easy-to-use camera service APIs. With these APIs, you can create camera applications that access and control camera hardware to achieve basic functions like previewing, taking photos, and recording videos. In addition, you can combine these APIs to perform advanced operations, such as controlling the flash, exposure time, and focus.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.

This module contains the following classes:

- [AutoDeviceSwitch](arkts-apis-camera-AutoDeviceSwitch.md) class, which provides the capabilities of checking the support for automatic camera switching and enabling or disabling automatic camera switching.
- [AutoExposure](arkts-apis-camera-AutoExposure.md) class, which provides the capabilities related to the device's automatic exposure feature, including setting or querying the exposure value, metering point, and exposure compensation.
- [CameraInput](arkts-apis-camera-CameraInput.md) class, which provides the capabilities of enabling or disabling the camera switch and listening for input stream exceptions.
- [CameraManager](arkts-apis-camera-CameraManager.md) class, which provides the capabilities of obtaining camera device objects, creating input/output streams and sessions, and registering or unregistering listeners for camera states.
- [ColorManagement](arkts-apis-camera-ColorManagement.md) class, which provides the capabilities of checking the support for the color space and setting or querying color space parameters.
- [ControlCenter](arkts-apis-camera-ControlCenter.md) class, which provides the capabilities of checking the support for the camera controller and enabling the camera controller.
- [Flash](arkts-apis-camera-Flash.md) class, which provides the capabilities of checking the support for flash functionality and manipulating the flash device.
- [Focus](arkts-apis-camera-Focus.md) class, which provides the capabilities of checking the support for focus modes on the device and setting focus-related functionalities.
- [Macro](arkts-apis-camera-Macro.md) class, which provides the capabilities of checking the support for macro photography and enabling macro photography.
- [MetadataOutput](arkts-apis-camera-MetadataOutput.md) class, which provides the capabilities of registering or unregistering listeners for metadata and starting or stopping metadata streams.
- [Photo](arkts-apis-camera-Photo.md) class, which is a full-quality image object containing complete information about a photo.
- [PhotoOutput](arkts-apis-camera-PhotoOutput.md) class, which is used in photo sessions to provide photo-related capabilities, such as taking photos, enabling moving-photo capture, and obtaining photo rotation angles.
- [PhotoSession](arkts-apis-camera-PhotoSession.md) class, which is a regular photo mode session class and provides the capabilities for pre-configuration and session state monitoring.
- [PreviewOutput](arkts-apis-camera-PreviewOutput.md) class, which provides the capabilities of setting the preview stream frame rate and preview rotation angle, and querying the current configuration.
- [SecureSession](arkts-apis-camera-SecureSession.md) class, which is a secure mode session class and provides the capabilities of checking the support for secure mode and listening for session states.
- [Session](arkts-apis-camera-Session.md) class, which is the base class for sessions and provides a range of APIs from starting to stopping preview streams.
- [Stabilization](arkts-apis-camera-Stabilization.md) class, which provides the capabilities of checking the support for stabilization and obtaining or setting the device's stabilization types.
- [VideoOutput](arkts-apis-camera-VideoOutput.md) class, which provides the capabilities of starting or stopping video streams, and configuring the frame rate and mirroring of video streams.
- [VideoSession](arkts-apis-camera-VideoSession.md) class, which is a regular video mode session class and provides the capabilities for pre-configuration and session state monitoring.
- [WhiteBalance](arkts-apis-camera-WhiteBalance.md) class, which provides the capabilities of checking the support for white balance modes and setting WB-related parameters.
- [Zoom](arkts-apis-camera-Zoom.md) class, which provides the capabilities of checking the support for zoom operations and performing zoom operations on the device.
- [Others](arkts-apis-camera-i.md): property information of the camera device, including video configuration items, photo output capabilities, and flashlight.
- [Enums](arkts-apis-camera-e.md): camera-related enums and their meanings, including the camera position, flash mode, and smooth zoom mode.

## Modules to Import

```ts
import { camera } from '@kit.CameraKit';
```
