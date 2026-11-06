# Video Recording (ArkTS)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=7f4d210fc38f3d9e54eb91674f92d1017632961d translatedAt=2026-11-02T02:33:31.187Z pushedAt=2026-11-02T02:33:31.187Z nl=1 -->

Before developing a camera application, you must [request required permissions](camera-preparation.md).

A camera application invokes and controls a camera device to perform basic operations such as preview, photo capture, and video recording.

Video recording is another key function of camera apps and involves capturing frames continuously. To customize recording, refer to step 6 in [Photo Capture](camera-shooting.md) to configure resolution, flash, focal length, photo quality, rotation angle, and other parameters.

## How to Develop

For detailed API descriptions, see [@ohos.multimedia.camera (Camera Management)](../../reference/apis-camera-kit/arkts-apis-camera.md).

1. Import the media module.

   Creating the SurfaceId for the recording output stream and the recording output data requires the media APIs provided by the system, that is, [@ohos.multimedia.media (Media Service)](../../reference/apis-media-kit/arkts-apis-media.md). The following shows how to import the media APIs.

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   import { camera } from '@kit.CameraKit';
   import { media } from '@kit.MediaKit';
   ```

2. Check whether the camera supports video mode.

   Call [getSupportedSceneModes](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#getsupportedscenemodes11) to obtain the modes supported by the camera and check for video mode.

   ```ts
   function isCaptureModeSupported(cameraManager: camera.CameraManager, cameraDevice: camera.CameraDevice): boolean
   {
     try {
       let modeArray = cameraManager.getSupportedSceneModes(cameraDevice);
       return modeArray.includes(camera.SceneMode.NORMAL_VIDEO);
     } catch (error) {
       let err = error as BusinessError;
       console.error(`failed to getSupportedSceneModes, err code: ${err.code}`);
       return false;
     }
   }
   ```

3. Create a Surface.

   Call createAVRecorder() of the media module to create an [AVRecorder](../../reference/apis-media-kit/arkts-apis-media-AVRecorder.md) instance, and call [getInputSurface](../../reference/apis-media-kit/arkts-apis-media-AVRecorder.md#getinputsurface9) of the instance to obtain the surface ID, which is associated with the video output stream to process the stream data.

   <!-- @[camera_video_getVideoSurface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/PhotoSameSource/entry/src/main/ets/mode/CameraService.ets) -->
   
   ``` TypeScript
   this.avRecorder = await this.createAVRecorder();
   if (this.avRecorder === undefined) {
     Logger.error(TAG, 'Failed to create the avRecorder.');
     return;
   }
   await this.prepareAVRecorder();
   let videoSurfaceId = await this.avRecorder.getInputSurface();
   ```

4. Create a video output stream.

   Obtain the video output streams supported by the current device from **videoProfiles** in [CameraOutputCapability](../../reference/apis-camera-kit/arkts-apis-camera-i.md#cameraoutputcapability). Then, define video recording parameters and use [createVideoOutput](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#createvideooutput) to create a video output stream.

   > **NOTE**
   >
   > 1. The preview and video output streams must use the same resolution aspect ratio. For example, if the video ratio is 640:480 = 4:3, the preview must also use 4:3, such as 640:480, 960:720, or 1440:1080.
   >
   > 2. Before setting the preview resolution, query the configurable video frame width and height ranges through [AVRecorderProfile](../../reference/apis-media-kit/arkts-apis-media-i.md#avrecorderprofile9).
   >
   > 3. Obtain the actual recording rotation angle through [getVideoRotation](../../reference/apis-camera-kit/arkts-apis-camera-VideoOutput.md#getvideorotation12) in [VideoOutput](../../reference/apis-camera-kit/arkts-apis-camera-VideoOutput.md).
   >
   > 4. For the video output stream frame rate, use videoProfiles in [CameraOutputCapability](../../reference/apis-camera-kit/arkts-apis-camera-i.md#cameraoutputcapability) to select a videoProfile whose [frameRateRange](../../reference/apis-camera-kit/arkts-apis-camera-i.md#frameraterange) in [VideoProfile](../../reference/apis-camera-kit/arkts-apis-camera-i.md#videoprofile) meets your requirements.

   <!-- @[camera_video_createAVRecorder](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/PhotoSameSource/entry/src/main/ets/mode/CameraService.ets) -->    
   
   ``` TypeScript
   createVideoOutputFn(cameraManager: camera.CameraManager, videoProfileObj: camera.VideoProfile,
     surfaceId: string): camera.VideoOutput | undefined {
     let videoOutput: camera.VideoOutput | undefined = undefined;
     try {
       videoOutput = cameraManager.createVideoOutput(videoProfileObj, surfaceId);
       Logger.info(TAG, `createVideoOutputFn success: ${videoOutput}`);
     } catch (error) {
       let err = error as BusinessError;
       Logger.error(TAG, `createVideoOutputFn failed: ${err.code}`);
     }
     return videoOutput;
   }
   ```

5. Start recording.

   > **NOTE**
   >
   >  - Before setting the preview stream frame rate, call [getActiveFrameRate](../../reference/apis-camera-kit/arkts-apis-camera-PreviewOutput.md#getactiveframerate12) to query the frame rate of the current recording stream.
   >
   > - If a frame rate range has been set for the recording stream, the preview stream frame rate must be set to the same range.
   >
   > - If a fixed frame rate has been set for the recording stream, the preview stream frame rate must be set to a divisor of the recording frame rate and must also be a fixed frame rate.
   >
   > - On some devices, if the front camera recording resolution is set to 3280*2160, the video may appear upside down in recording mode. It is recommended that you call [setVideoStabilizationMode](../../reference/apis-camera-kit/arkts-apis-camera-Stabilization.md#setvideostabilizationmode11) after [commitConfig](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#commitconfig11) to avoid this issue.

   Call [start](../../reference/apis-camera-kit/arkts-apis-camera-VideoOutput.md#start-1) of the VideoOutput instance to start the video output stream, and then call [start](../../reference/apis-media-kit/arkts-apis-media-AVRecorder.md#start9) of the AVRecorder instance to start recording.

   <!-- @[camera_video_start](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/PhotoSameSource/entry/src/main/ets/mode/CameraService.ets) -->    
   
   ``` TypeScript
   async startVideo(): Promise<void> {
     Logger.info(TAG, 'startVideo is called');
     try {
       await this.videoOutput?.start();
       await this.avRecorder?.start();
       this.isRecording = true;
     } catch (error) {
       let err = error as BusinessError;
       Logger.error(TAG, `startVideo err: ${err.code}`);
     }
     Logger.info(TAG, 'startVideo End of call');
   }
   ```

6. Stop recording.

   Call [stop](../../reference/apis-media-kit/arkts-apis-media-AVRecorder.md#stop9-1) of the AVRecorder instance to stop recording, and then call [stop](../../reference/apis-camera-kit/arkts-apis-camera-VideoOutput.md#stop-1) of the VideoOutput instance to stop the video output stream.

   <!-- @[camera_video_stop](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/PhotoSameSource/entry/src/main/ets/mode/CameraService.ets) -->    
   
   ``` TypeScript
   async stopVideo(): Promise<void> {
     Logger.info(TAG, 'stopVideo is called');
     if (!this.isRecording) {
       Logger.info(TAG, 'not in recording');
       return;
     }
     try {
       if (this.avRecorder) {
         await this.avRecorder.stop();
       }
       if (this.videoOutput) {
         await this.videoOutput.stop();
       }
       this.isRecording = false;
     } catch (error) {
       let err = error as BusinessError;
       Logger.error(TAG, `stopVideo err: ${err.code}`);
     }
     Logger.info(TAG, 'stopVideo End of call');
   }
   ```


## Status Listening

During camera application development, you can listen for the status of the video output stream, including recording start, recording end, and video output errors.

- Register the **'frameStart'** event to listen for recording start events. This event can be registered when a VideoOutput instance is created and is triggered when the bottom layer starts exposure for recording for the first time. Video recording starts as long as a result is returned.

  <!-- @[camera_video_frameStart](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/PhotoSameSource/entry/src/main/ets/mode/CameraService.ets) -->    
  
  ``` TypeScript
  videoOutput.on('frameStart', (err: BusinessError) => {
    if (err !== undefined && err.code !== 0) {
      return;
    }
    console.info('Video frame started');
  });
  ```

- Register the **'frameEnd'** event to listen for recording end events. This event can be registered when a VideoOutput instance is created and is triggered when the last frame of recording ends. Video recording ends as long as a result is returned.

  <!-- @[camera_video_frameEnd](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/PhotoSameSource/entry/src/main/ets/mode/CameraService.ets) -->    
  
  ``` TypeScript
  videoOutput.on('frameEnd', (err: BusinessError) => {
    if (err !== undefined && err.code !== 0) {
      return;
    }
    console.info('Video frame ended');
  });
  ```

- Register an error callback to obtain video output errors. The callback returns the error code corresponding to incorrect use of the video output APIs. For error code types, see [CameraErrorCode](../../reference/apis-camera-kit/arkts-apis-camera-e.md#cameraerrorcode).

  <!-- @[camera_video_error](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/PhotoSameSource/entry/src/main/ets/mode/CameraService.ets) -->   
  
  ``` TypeScript
  videoOutput.on('error', (error: BusinessError) => {
    console.error(`Video output error code: ${error.code}`);
  });
  ```

<!--RP1-->
<!--RP1End-->