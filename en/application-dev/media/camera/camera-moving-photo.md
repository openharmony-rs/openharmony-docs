# Moving Photos (ArkTS)

<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=baffdc55af4ff940b6bf4d2ec2752bb12fa2d285 translatedAt=2026-06-04T07:30:11.447Z pushedAt=2026-06-04T07:33:35.987Z -->

The camera framework provides the capability of taking moving photos. With this capability, users can take a moving photo in one-click mode, in a way similar to taking an ordinary photo.

To develop the moving photo feature, perform the following steps:

- Configure the mandatory capabilities required for camera application development by following the instructions provided in [Requesting Camera Development Permissions](camera-preparation.md), [Camera Device Management](camera-device-management.md), [Device Input Management](camera-device-input.md), and [Camera Session Management](camera-session-management.md).

- Check whether the device supports taking moving photos.

- Enable the capability of taking moving photos (if supported).

- Listen for the photo callback function and save the photo to the media library. For details, see [Accessing and Managing Moving Photos](../medialibrary/photoAccessHelper-movingphoto.md).

## How to Develop

For details about the API, see [@ohos.multimedia.camera (Camera Management)](../../reference/apis-camera-kit/arkts-apis-camera.md).

> **NOTE**
>
> - The permission ohos.permission.MICROPHONE is required for taking moving photos. For details about how to apply for and verify the permission, see [Preparations](camera-preparation.md). Otherwise, the photos taken will have no sound.

1. Import dependencies. Specifically, import the camera, image, and mediaLibrary modules.

   ```ts
   import { camera } from '@kit.CameraKit';
   import { photoAccessHelper } from '@kit.MediaLibraryKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

2. Determine the photo output stream.

   You can use the **photoProfiles** property of [CameraOutputCapability](../../reference/apis-camera-kit/arkts-apis-camera-i.md#cameraoutputcapability) to obtain the photo output streams supported by the device and use [createPhotoOutput](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#createphotooutput11) to create a photo output stream.

   <!-- @[camera_getPhotoOutput](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/PhotoSameSource/entry/src/main/ets/mode/CameraService.ets) -->

   ```ts
   function getPhotoOutput(cameraManager: camera.CameraManager, 
     cameraOutputCapability: camera.CameraOutputCapability): camera.PhotoOutput | undefined {
     if (!cameraOutputCapability || !cameraOutputCapability.photoProfiles) {
       return;
     }
     let photoProfilesArray: Array<camera.Profile> = cameraOutputCapability.photoProfiles;
     if (!photoProfilesArray || photoProfilesArray.length === 0) {
       console.error("photoProfilesArray is null or []");
       return;
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

3. Check whether the device supports taking moving photos.

   > **NOTE**
   >
   > Before checking whether moving photo is supported, you must configure, commit, and start a camera session. For details about the development procedure, see [Session Management](camera-session-management.md).

   <!-- @[camera_moving_photo_support](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/PhotoSameSource/entry/src/main/ets/mode/CameraService.ets) -->

    ```ts
    function isMovingPhotoSupported(photoOutput: camera.PhotoOutput): boolean {
      let isSupported: boolean = false;
      try {
        isSupported = photoOutput.isMovingPhotoSupported();
      } catch (error) {
        // If the operation fails, error.code is returned and processed.
        let err = error as BusinessError;
        console.error(`The isMovingPhotoSupported call failed. error code: ${err.code}`);
      }
      return isSupported;
    }
    ```

4. Enable the capability of taking moving photos.

   > **NOTE**
   >
   > Before enabling moving photo, you must enable the [Deferred Photo Delivery (ArkTS)](camera-deferred-capture.md) capability.

   <!-- @[camera_moving_photo_enable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/PhotoSameSource/entry/src/main/ets/mode/CameraService.ets) -->

    ```ts
    function enableMovingPhoto(photoOutput: camera.PhotoOutput): void {
      try {
        photoOutput.enableMovingPhoto(true);
      } catch (error) {
        // If the operation fails, error.code is returned and processed.
        let err = error as BusinessError;
       console.error(`The enableMovingPhoto call failed. error code: ${err.code}`);
      }
    }
    ```

5. Trigger photo capture. This procedure is the same as that in the common photo capture mode. For details, see [Photo Capture](camera-shooting.md).

## Status Listening

During camera application development, you can listen for the output stream status of moving photos by registering the **'photoAsset'** event. This event can be registered when a PhotoOutput instance is created.

<!-- @[photo_asset_available](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Camera/PhotoSameSource/entry/src/main/ets/mode/CameraService.ets) -->

   ```ts
   function getPhotoAccessHelper(context: Context): photoAccessHelper.PhotoAccessHelper {
     let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
     return phAccessHelper;
   }

   async function mediaLibSavePhoto(photoAsset: photoAccessHelper.PhotoAsset,
     phAccessHelper: photoAccessHelper.PhotoAccessHelper): Promise<void> {
     try {
       let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(photoAsset);
       assetChangeRequest.saveCameraPhoto();
       await phAccessHelper.applyChanges(assetChangeRequest);
       console.info('apply saveCameraPhoto successfully');
     } catch (err) {
       console.error(`apply saveCameraPhoto failed with error: ${err.code}, ${err.message}`);
     }
   }

   function onPhotoOutputPhotoAssetAvailable(photoOutput: camera.PhotoOutput, context: Context): void {
     photoOutput.on('photoAssetAvailable', (err: BusinessError, photoAsset: photoAccessHelper.PhotoAsset): void => {
       if (err) {
         console.error(`photoAssetAvailable error: ${err}.`);
         return;
       }
       console.info('photoOutPutCallBack photoAssetAvailable');
       // Call the mediaLibrary flush API to save the first-phase images and moving photos.
       mediaLibSavePhoto(photoAsset, getPhotoAccessHelper(context));
     });
   }
   ```

## HDR Moving Photo

Starting from API version 23, the camera provides the HDR moving photo capability. That is, both the static image and the dynamic short video that make up a moving photo are high dynamic range (HDR) content, which can outperform SDR results in highlight and shadow details, color gradation, and overall texture.

You can flexibly determine whether to output SDR or HDR moving photos by configuring the preview output format (Profile.format) and color space (ColorSpace). The specific mapping is shown in the table below. All capabilities must be queried before use. The supported preview output formats can be queried through the [getSupportedFullOutputCapability](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#getsupportedfulloutputcapability23) API, and the supported color spaces can be queried through the [getSupportedColorSpaces](../../reference/apis-camera-kit/arkts-apis-camera-ColorManagementQuery.md#getsupportedcolorspaces12) API.

| Static Image Dynamic Range | Short Video Dynamic Range | Preview Output Format | Color Space |
|----------------|------------|------------|------------|
| SDR       | SDR       | CAMERA_FORMAT_YUV_420_SP       | SRGB |
| HDR       | SDR       | CAMERA_FORMAT_YUV_420_SP       | DISPLAY_P3 |
| HDR       | HDR       | CAMERA_FORMAT_YCRCB_P010, <br>CAMERA_FORMAT_YCBCR_P010 | BT2020_HLG |

**HDR Configuration Notes**

- When configuring the preview output stream, you must first query the complete capabilities supported by the current camera and mode through the [getSupportedFullOutputCapability](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#getsupportedfulloutputcapability23) API, and select the preview output format as P010 (CAMERA_FORMAT_YCRCB_P010/CAMERA_FORMAT_YCBCR_P010).

- When configuring the color space, you must first obtain the color spaces supported by the current device through the [getSupportedColorSpaces](../../reference/apis-camera-kit/arkts-apis-camera-ColorManagementQuery.md#getsupportedcolorspaces12) API, and then set the color space to BT2020_HLG through the [setColorSpace](../../reference/apis-camera-kit/arkts-apis-camera-ColorManagement.md#setcolorspace12) API. For details, see [setColorSpace](../../reference/apis-camera-kit/arkts-apis-camera-ColorManagement.md#setcolorspace12).