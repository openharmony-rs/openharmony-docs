# Depth Data (for System Applications Only) (ArkTS)
<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=f355c35e40135af02bb0c82bdc51132081295077 translatedAt=2026-09-28T02:41:16.473Z pushedAt=2026-09-29T07:40:50.878Z -->

Depth data reflects the spatial arrangement of image pixels in relation to the camera lens. It facilitates enhanced focus precision, background blurring effects, and the like. Depth data can be reported in the preview, photo capture, and video scenarios of camera applications.

## How to Develop

For detailed API descriptions, see [@ohos.multimedia.camera (Camera Management) (System API)](../../reference/apis-camera-kit/js-apis-camera-sys.md).

1. Import the camera module, which provides camera-related properties and methods.
     
   ```ts
   import { camera } from '@kit.CameraKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. Use **depthProfiles** in [CameraOutputCapability](../../reference/apis-camera-kit/js-apis-camera-sys.md#cameraoutputcapability) to obtain the depth data capabilities, in the format of a **depthProfilesArray** array, supported by the current device. Call [createDepthDataOutput](../../reference/apis-camera-kit/js-apis-camera-sys.md#createdepthdataoutput13) to create a depth data stream.

   ```ts
   function getDepthDataOutput(cameraManager: camera.CameraManager,
    cameraOutputCapability: camera.CameraOutputCapability): camera.DepthDataOutput | undefined {
      let depthProfilesArray: Array<camera.DepthProfile> = cameraOutputCapability.depthProfiles;
      if (!depthProfilesArray) {
        console.error("createOutput depthProfilesArray is null");
        return undefined;
      }
      let depthDataOutput: camera.DepthDataOutput | undefined = undefined;
      try {
        if (depthProfilesArray.length > 0) {
          depthDataOutput = cameraManager.createDepthDataOutput(depthProfilesArray[0]);
        } else {
          console.error("the length of depthProfilesArray<=0!");
          return undefined;
        }
      } catch (error) {
        let err = error as BusinessError;
        console.error(`Failed to create the DepthDataOutput instance. error: ${err}`);
      }
      return depthDataOutput;
   }
   ```

3. Use the [start](../../reference/apis-camera-kit/js-apis-camera-sys.md#start13) method of **depthDataOutput** to output the depth stream. If the API call fails, the corresponding error code is returned. For details about the error codes, see [CameraErrorCode](../../reference/apis-camera-kit/arkts-apis-camera-e.md#cameraerrorcode).
     
   ```ts
   async function startDepthDataOutput(depthDataOutput: camera.DepthDataOutput): Promise<void> {
     if (!depthDataOutput) {
       console.error('depthDataOutput Undefined');
       return;
     }
     try {
       await depthDataOutput.start();
     } catch (err) {
       const error = err as BusinessError;
       console.error(`Failed to start depth data output. error: ${err}`);
     }
   }
   ```

## Status Listening

During camera application development, you can listen for depth data and depth data output errors.

- Register the fixed callback function **depthDataAvailable** to obtain the depth data.
    
  ```ts
  function onDepthDataAvailable(depthDataOutput: camera.DepthDataOutput): void {
    depthDataOutput.on('depthDataAvailable', (err: BusinessError, depthData: camera.DepthData) => {
      if (err == undefined || err.code !== 0) {
        console.error(`Depth data callback error: ${err.code}`);
        return;
      }
      console.info(`Depth data available: ${depthData}`);
    });
  }
  ```

- Register a fixed error callback to listen for error results of the depth stream output. The callback returns the error code corresponding to the error when using the depth output API. For details about the error codes, see [CameraErrorCode](../../reference/apis-camera-kit/arkts-apis-camera-e.md#cameraerrorcode).
    
  ```ts
  function onDepthDataOutputError(depthDataOutput: camera.DepthDataOutput): void {
    depthDataOutput.on('error', (depthDataOutputError: BusinessError) => {
      console.error(`Depth data output error code: ${depthDataOutputError.code}`);
    });
  }
  ```
