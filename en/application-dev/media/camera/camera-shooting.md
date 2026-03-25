# Photo Capture (ArkTS)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->

## Overview

Photo capture is one of the important functions of the camera. The photo capture module is built on complex camera logic. To ensure the quality of photos taken by users, settings such as resolution, flash, focal length, photo quality, and rotation angle can be configured during intermediate steps.

There are currently two photo capture solutions for camera development: [deferred photo capture](./camera-deferred-capture.md) and one-shot photo capture. **This section uses one-shot photo capture as an example.**

- Deferred photo capture delivers low-quality images for thumbnail display, improving the perceived capture speed, while preserving high-quality images to ensure final output matches the system camera standard. This approach satisfies image processing algorithm requirements without blocking foreground capture speed, helping deliver competitive camera performance and a better user experience.
- One-shot photo capture produces a single high-quality image after multi-frame fusion and multiple low-level algorithmic processing. As a result, Shot2See latency—the time from when the user taps the capture control to when a thumbnail appears in the thumbnail display area—is relatively long. One-shot photo capture also supports [quality-first strategy](#quality-first-strategy) via [high-performance photo capture](#high-performance-photo-capture), allowing you to optimize for either faster image output or higher image quality.
 

## How to Develop

Read [Camera](../../reference/apis-camera-kit/arkts-apis-camera.md) for the API reference.

1. Import the [Image](../../reference/apis-image-kit/arkts-apis-image-Image.md) API. Retrieving photo capture output data requires using the **Image** API capabilities provided by the system. The method for importing the **Image** API is as follows.

   ```ts
   import { image } from '@kit.ImageKit';
   import { camera } from '@kit.CameraKit';
   import { fileIo as fs } from '@kit.CoreFileKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. Create a photo output stream.

   Obtain the photo output streams supported by the current device from **photoProfiles** in [CameraOutputCapability](../../reference/apis-camera-kit/arkts-apis-camera-i.md#cameraoutputcapability). Call [createPhotoOutput](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#createphotooutput11), passing in a supported output stream [profile](../../reference/apis-camera-kit/arkts-apis-camera-i.md#profile), to create a photo output stream.

   ```ts
   function getPhotoOutput(cameraManager: camera.CameraManager, cameraOutputCapability: camera.CameraOutputCapability): camera.PhotoOutput | undefined {
     let photoProfilesArray: Array<camera.Profile> = cameraOutputCapability.photoProfiles;
     if (!photoProfilesArray || photoProfilesArray.length === 0) {
       console.error("photoProfilesArray is null or []");
     }
     let photoOutput: camera.PhotoOutput | undefined = undefined;
     try {
       photoOutput = cameraManager.createPhotoOutput(photoProfilesArray[0]);
     } catch (error) {
       let err = error as BusinessError;
       console.error(`Failed to createPhotoOutput. error: ${err}`);
     }
     return photoOutput;
   }
   ```

3. Set up the callback for [on('photoAvailable')](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#onphotoavailable11) and save the captured buffer as an image.

    For details about how to obtain the context, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

    To view the saved images and videos in Gallery, you must save them to the media library. For details, see [Saving Media Assets](../medialibrary/photoAccessHelper-savebutton.md).

    When the buffer is received via the [photoOutput.on('photoAvailable')](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#onphotoavailable11) callback, it must be saved to the media library within a secure control.
   ```ts
   function setPhotoOutputCb(photoOutput: camera.PhotoOutput) {
   // After the callback is set, call capture() of photoOutput to transfer the photo buffer back to the callback.
     photoOutput.on('photoAvailable', (errCode: BusinessError, photo: camera.Photo): void => {
        console.info('getPhoto start');
        if (errCode || photo === undefined) {
          console.error('getPhoto failed, err: ${errCode}');
          return;
        }
        let imageObj: image.Image = photo.main;
        imageObj.getComponent(image.ComponentType.JPEG, (errCode: BusinessError, component: image.Component): void => {
          console.info('getComponent start');
          if (errCode || component === undefined) {
            console.error('getComponent failed');
            return;
          }
          let buffer: ArrayBuffer;
          if (component.byteBuffer) {
            buffer = component.byteBuffer;
          } else {
            console.error('byteBuffer is null');
            return;
          }
          // To view the saved image and video resources in Gallery, use a security component to create media assets.

         // After the buffer processing is complete, the buffer must be released. Otherwise, no buffer is available for subsequent photo capture.
         imageObj.release();
       });
     });
   }
   ```

4. Set camera parameters.

   You can set camera parameters to adjust photo capture functions, including the flash, zoom ratio, and focal length.

   ```ts
   function configuringSession(photoSession: camera.PhotoSession): void {
     // Check whether the camera has flash.
     let flashStatus: boolean = false;
     try {
       flashStatus = photoSession.hasFlash();
     } catch (error) {
       let err = error as BusinessError;
       console.error(`Failed to hasFlash. error: ${err}`);
     }
     console.info(`Returned with the flash light support status: ${flashStatus}`);
     if (flashStatus) {
       // Check whether the auto flash mode is supported.
       let flashModeStatus: boolean = false;
       try {
         flashModeStatus = photoSession?.isFlashModeSupported(camera.FlashMode.FLASH_MODE_AUTO);
       } catch (error) {
         let err = error as BusinessError;
         console.error(`Failed to check whether the flash mode is supported. error: ${err}`);
       }
       if (flashModeStatus) {
         // Set the flash mode to auto.
         try {
           photoSession?.setFlashMode(camera.FlashMode.FLASH_MODE_AUTO);
         } catch (error) {
           let err = error as BusinessError;
           console.error(`Failed to set the flash mode. error: ${err}`);
         }
       }
     }
     // Check whether the continuous auto focus is supported.
     let focusModeStatus: boolean = false;
     try {
       focusModeStatus = photoSession?.isFocusModeSupported(camera.FocusMode.FOCUS_MODE_CONTINUOUS_AUTO);
     } catch (error) {
       let err = error as BusinessError;
       console.error(`Failed to check whether the focus mode is supported. error: ${err}`);
     }
     if (focusModeStatus) {
       // Set the focus mode to continuous auto focus.
       try {
         photoSession?.setFocusMode(camera.FocusMode.FOCUS_MODE_CONTINUOUS_AUTO);
       } catch (error) {
         let err = error as BusinessError;
         console.error(`Failed to set the focus mode. error: ${err}`);
       }
     }
     // Obtain the zoom ratio range supported by the camera.
     let zoomRatioRange: Array<number> = [];
     try {
       zoomRatioRange = photoSession?.getZoomRatioRange();
     } catch (error) {
       let err = error as BusinessError;
       console.error(`Failed to get the zoom ratio range. error: ${err}`);
     }
     if (zoomRatioRange.length <= 0 ) {
       return;
     }
     // Set a zoom ratio.
     try {
       photoSession?.setZoomRatio(zoomRatioRange[0]);
     } catch (error) {
       let err = error as BusinessError;
       console.error(`Failed to set the zoom ratio value. error: ${err}`);
     }
   }
   ```

5. Trigger photo capture.

   Call [capture](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#capture-2) in **PhotoOutput** to capture a photo. In this API, the first parameter specifies the settings (for example, photo quality and rotation angle) for photo capture, and the second parameter is a callback function.

   To obtain the photo rotation angle (specified by **rotation**), call [getPhotoRotation](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#getphotorotation12) in [PhotoOutput](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md).

   > **NOTE**
   >
   > For details about the photo's geographical location information (specified by [Location](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geolocationmanagergetcurrentlocation)), you can refer to the implementation in the [capture](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#capture-3) example.

   ```ts
   function capture(captureLocation: camera.Location, photoOutput: camera.PhotoOutput): void {
     let settings: camera.PhotoCaptureSetting = {
       quality: camera.QualityLevel.QUALITY_LEVEL_HIGH, // Set the photo quality to high.
       rotation: camera.ImageRotation.ROTATION_0, // The photo rotation angle, camera.ImageRotation.ROTATION_0, is obtained through getPhotoRotation.
       location: captureLocation, // Set the geolocation information of the photo.
       mirror: false // Disable mirroring (disabled by default).
     };
     try {
       photoOutput.capture(settings, (err: BusinessError) => {
         if (err) {
           console.error(`Failed to capture the photo. error: ${err}`);
           return;
         }
         console.info('Callback invoked to indicate the photo capture request success.');
       });
     } catch (error) {
       console.error(`capture call failed. error: ${error}`);
     }
   }
   ```
## High-Performance Photo Capture

High-performance photo capture is supported starting from API version 21. This feature allows you to set an explicit [quality-first strategy](#quality-first-strategy) for one-shot photo capture.

User experience of one-shot photo capture is primarily measured by image output speed and final image quality. To meet differentiated requirements across scenarios, the emphasis on these two metrics varies. For example, street photography requires fast capture of fleeting moments, while landscape or portrait photography prioritizes optimal image quality.

> **NOTE**
>
> Quality-first strategy is supported only for one-shot photo capture. Any such settings configured for deferred photo capture will not take effect.
 	

### Quality-First Strategy

For one-shot photo capture, two quality-first strategies are supported, each mapped to a distinct [PhotoQualityPrioritization](../../reference/apis-camera-kit/arkts-apis-camera-e.md#photoqualityprioritization21) enumeration value:

- [SPEED](../../reference/apis-camera-kit/arkts-apis-camera-e.md#photoqualityprioritization21): prioritizes speed by reducing image quality to accelerate capture. This is the **default strategy** for one-shot photo capture if no explicit quality-first strategy is configured.
- [HIGH_QUALITY](../../reference/apis-camera-kit/arkts-apis-camera-e.md#photoqualityprioritization21): prioritizes quality by allowing longer processing time to produce higher-quality images.

### How to Correctly Set a Quality-First Strategy

To properly set a quality-first strategy for one-shot photo capture, the high-performance photo capture feature provides the following two APIs:

- [isPhotoQualityPrioritizationSupported](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#isphotoqualityprioritizationsupported21): queries whether the current device supports a specified quality-first strategy. Returns **true** if supported, **false** if not. You must verify support for the target strategy on the current device before configuration.
- [setPhotoQualityPrioritization](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#setphotoqualityprioritization21): The core API for setting a quality-first strategy. Use this API to configure the desired strategy and enable high-performance photo capture.

### How to Develop
 	 
APIs related to high-performance photo capture must be called during the [camera session management (ArkTS)](camera-session-management.md) workflow. 
 	 
The specific call timing is as follows: 

- Call the following APIs after the completion of [commitConfig](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#commitconfig11) in the enablement step of the [camera session management (ArkTS)](camera-session-management.md) workflow.

  ```ts
  async function startSession(videoSession: camera.VideoSession, cameraInput: camera.CameraInput, previewOutput: camera.PreviewOutput, photoOutput: camera.PhotoOutput): Promise<void> {
    try {
      videoSession.addInput(cameraInput);
    } catch (error) {
      let err = error as BusinessError;
      console.error(`Failed to addInput. error: ${err.code}`);
    }
    let canAddPreviewOutput : boolean = false;
    try {
      canAddPreviewOutput = videoSession.canAddOutput(previewOutput);
    } catch (error) {
      let err = error as BusinessError;
      console.error(`Failed to add previewOutput. error: ${err.code}`);
    } 
    if (!canAddPreviewOutput) {
      console.error(`Failed to add preview output.`);
      return;
    }
    try {
      videoSession.addOutput(previewOutput);
    } catch (error) {
      let err = error as BusinessError;
      console.error(`Failed to add previewOutput. error: ${err.code}`);
    }
    let canAddPhotoOutput : boolean = false
    try {
      canAddPhotoOutput = videoSession.canAddOutput(photoOutput);
    } catch (error) {
      let err = error as BusinessError;
      console.error(`Failed to add photoOutput error: ${err.code}`);
    }
    if (!canAddPhotoOutput) {
      console.error(`Failed to add photo output.`);
      return;
    }
    try {
      videoSession.addOutput(photoOutput);
    } catch (error) {
      let err = error as BusinessError;
      console.error(`Failed to add photoOutput. error: ${err.code}`);
    }
    try {
      await videoSession.commitConfig();
    } catch (error) {
      let err = error as BusinessError;
      console.error(`Failed to commitConfig. error: ${err.code}`);
      return;
    }
   
    try {
      await videoSession.start();
    } catch (error) {
      let err = error as BusinessError;
      console.error(`Failed to start. error: ${err.code}`);
    }
    modeSwitchToHigh(videoSession, photoOutput);
  }

  async function modeSwitchToHigh(videoSession: camera.VideoSession, photoOutput: camera.PhotoOutput): Promise<void> {
    try {
      if (videoSession) {
        let quality: camera.PhotoQualityPrioritization = camera.PhotoQualityPrioritization.HIGH_QUALITY;
        let isSupported = false;
        isSupported = photoOutput.isPhotoQualityPrioritizationSupported(quality);
        if (isSupported) {
          photoOutput.setPhotoQualityPrioritization(quality);
        } else {
          console.error(`session is not supported`);
        }
      } else {
        console.error(`session is null`);
      }
    } catch {
      console.error(`catch error`);
    }
  }
  ```

- Call the following APIs before [commitConfig](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#commitconfig11) in the enablement step of the [camera session management (ArkTS)](camera-session-management.md) workflow.

  ```ts
  async function startSession(videoSession: camera.VideoSession, cameraInput: camera.CameraInput, previewOutput: camera.PreviewOutput, photoOutput: camera.PhotoOutput): Promise<void> {
    try {
      videoSession.addInput(cameraInput);
    } catch (error) {
      let err = error as BusinessError;
      console.error(`Failed to addInput. error: ${err.code}`);
    }
    let canAddPreviewOutput : boolean = false;
    try {
      canAddPreviewOutput = videoSession.canAddOutput(previewOutput);
    } catch (error) {
      let err = error as BusinessError;
      console.error(`Failed to add previewOutput. error: ${err.code}`);
    } 
    if (!canAddPreviewOutput) {
      console.error(`Failed to add preview output.`);
      return;
    }
    try {
      videoSession.addOutput(previewOutput);
    } catch (error) {
      let err = error as BusinessError;
      console.error(`Failed to add previewOutput. error: ${err.code}`);
    }
    let canAddPhotoOutput : boolean = false
    try {
      canAddPhotoOutput = videoSession.canAddOutput(photoOutput);
    } catch (error) {
      let err = error as BusinessError;
      console.error(`Failed to add photoOutput error: ${err.code}`);
    }
    if (!canAddPhotoOutput) {
      console.error(`Failed to add photo output.`);
      return;
    }
    try {
      videoSession.addOutput(photoOutput);
    } catch (error) {
      let err = error as BusinessError;
      console.error(`Failed to add photoOutput. error: ${err.code}`);
    }
    modeSwitchToHigh(videoSession, photoOutput);
    try {
      await videoSession.commitConfig();
    } catch (error) {
      let err = error as BusinessError;
      console.error(`Failed to commitConfig. error: ${err.code}`);
      return;
    }
   
    try {
      await videoSession.start();
    } catch (error) {
      let err = error as BusinessError;
      console.error(`Failed to start. error: ${err.code}`);
    }
  }

  async function modeSwitchToHigh(videoSession: camera.VideoSession, photoOutput: camera.PhotoOutput): Promise<void> {
    try {
      if (videoSession) {
        let quality: camera.PhotoQualityPrioritization = camera.PhotoQualityPrioritization.HIGH_QUALITY;
        let isSupported = false;
        isSupported = photoOutput.isPhotoQualityPrioritizationSupported(quality);
        if (isSupported) {
          photoOutput.setPhotoQualityPrioritization(quality);
        } else {
          console.error(`session is not supported`);
        }
      } else {
        console.error(`session is null`);
      }
    } catch {
      console.error(`catch error`);
    }
  }
  ```

## Status Listening

During camera application development, you can listen for the status of the photo output stream, including the start of the photo stream, the start and end of the photo frame, and the errors of the photo output stream.

- Register the **'captureStart'** event to listen for photo capture start events. This event can be registered when a PhotoOutput instance is created and is triggered when the camera device starts photo capture. The capture ID is returned.

  ```ts
  function onPhotoOutputCaptureStart(photoOutput: camera.PhotoOutput): void {
    photoOutput.on('captureStartWithInfo', (err: BusinessError, captureStartInfo: camera.CaptureStartInfo) => {
      if (err !== undefined && err.code !== 0) {
        return;
      }
      console.info(`photo capture started, captureId : ${captureStartInfo.captureId}`);
    });
  }
  ```

- Register the **'captureEnd'** event to listen for photo capture end events. This event can be registered when a PhotoOutput instance is created and is triggered when the photo capture is complete. [CaptureEndInfo](../../reference/apis-camera-kit/arkts-apis-camera-i.md#captureendinfo) is returned.

  ```ts
  function onPhotoOutputCaptureEnd(photoOutput: camera.PhotoOutput): void {
    photoOutput.on('captureEnd', (err: BusinessError, captureEndInfo: camera.CaptureEndInfo) => {
      if (err !== undefined && err.code !== 0) {
        return;
      }
      console.info(`photo capture end, captureId : ${captureEndInfo.captureId}`);
      console.info(`frameCount : ${captureEndInfo.frameCount}`);
    });
  }
  ```

- Register the **'captureReady'** event to obtain the result of the next photo capture. This event can be registered when a PhotoOutput instance is created and is triggered when the camera device is ready for taking a photo. The information about the next photo capture is returned.

  ```ts
  function onPhotoOutputCaptureReady(photoOutput: camera.PhotoOutput): void {
    photoOutput.on('captureReady', (err: BusinessError) => {
      if (err !== undefined && err.code !== 0) {
        return;
      }
      console.info(`photo capture ready`);
    });
  }
  ```

- Register the **'error'** event to listen for photo output errors. The callback function returns an error code when an API is incorrectly used. For details about the error code types, see [CameraErrorCode](../../reference/apis-camera-kit/arkts-apis-camera-e.md#cameraerrorcode).

  ```ts
  function onPhotoOutputError(photoOutput: camera.PhotoOutput): void {
    photoOutput.on('error', (error: BusinessError) => {
      console.error(`Photo output error code: ${error.code}`);
    });
  }
  ```
