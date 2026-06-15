# YUV Photo Capture (ArkTS)

<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=444d4b7458e1317b3c2f1a471488b9c4b8344c2e translatedAt=2026-06-03T06:22:42.744Z pushedAt=2026-06-03T10:04:25.609Z -->

Starting from API version 23, the camera framework provides the capability to capture photos in YUV format. Compared with regular photo capture, YUV photo capture obtains unencoded image data, fully preserving the raw luminance and chrominance information captured by the sensor, making it suitable for video encoding or professional processing. At the same time, the capture process incurs higher power consumption, and saving the files occupies more storage space.

## How to Develop

For detailed camera function API descriptions, refer to the camera module [OH_Camera](../../reference/apis-camera-kit/arkts-apis-camera.md).

1. Import the dependent modules.

   Obtaining photo output data requires the use of the system-provided image, dataSharePredicates, and photoAccessHelper interface capabilities. The method is as follows.

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   import { camera } from '@kit.CameraKit';
   import { dataSharePredicates } from '@kit.ArkData';
   import { fileIo } from '@kit.CoreFileKit';
   import { image } from '@kit.ImageKit';
   import { photoAccessHelper} from '@kit.MediaLibraryKit';
   ```

2. Obtain the complete output capabilities of the camera device.

   Use the [getSupportedFullOutputCapability](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#getsupportedfulloutputcapability23) method to obtain the capabilities of all output streams supported by the current camera device, including preview stream, photo stream, and video stream. The output streams are in the respective profile fields of [CameraOutputCapability](../../reference/apis-camera-kit/arkts-apis-camera-i.md#cameraoutputcapability), where the photo stream supports the YUV format.

   ```ts
   function getFullOutputCapability(cameraManager: camera.CameraManager, cameraDevice: camera.CameraDevice, sceneMode: camera.SceneMode): camera.CameraOutputCapability | undefined {
     let cameraOutputCapability = cameraManager.getSupportedFullOutputCapability(cameraDevice, sceneMode);
     if (!cameraOutputCapability) {
       console.error("cameraManager.getSupportedFullOutputCapability error");
       return undefined;
     }
     return cameraOutputCapability;
   }
   ```

3. Create a photo output stream.

   Use the photoProfiles attribute in [CameraOutputCapability](../../reference/apis-camera-kit/arkts-apis-camera-i.md#cameraoutputcapability) to obtain the photo output streams supported by the current device.

   Create a photo output stream by passing a supported output stream [Profile](../../reference/apis-camera-kit/arkts-apis-camera-i.md#profile) to the [createPhotoOutput](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#createphotooutput11) method.

   Obtain the complete output capability cameraOutputCapability supported by the camera through [getSupportedFullOutputCapability](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#getsupportedfulloutputcapability23), referring to step 2. Select a Profile that supports the YUV format from the photoProfiles of cameraOutputCapability as the parameter photoProfile for creating the photo output stream.

   ```ts
   function getPhotoOutput(cameraManager: camera.CameraManager, photoProfile: camera.Profile): camera.PhotoOutput | undefined {
     // Create a photo output stream.
     let photoOutput: camera.PhotoOutput | undefined = undefined;
     try {
       photoOutput = cameraManager.createPhotoOutput(photoProfile);
     } catch (error) {
       let err = error as BusinessError;
       console.error("Failed to createPhotoOutput. error: ${err}");
     }
     return photoOutput;
   }
   ```

4. Set the callback for the photo output stream.

   Set the callback for single-stage photo capture [onCapturePhotoAvailable](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#oncapturephotoavailable23) or multi-stage photo capture [on('photoAssetAvailable')](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#onphotoassetavailable12), and save the captured pixelMap data as an image. If the application needs to get the image back quickly, it is recommended to use the multi-stage photo capture callback.

   For the method to obtain the Context, refer to: [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

   If you need to view the saved photo and video assets in the gallery, you must first save them to the media library. For the saving method, refer to: [Saving Media Assets](../medialibrary/photoAccessHelper-savebutton.md).

   If you need to obtain the buffer in the [onCapturePhotoAvailable](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#oncapturephotoavailable23) API, first save the [PixelMap](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md) data to the media library in a security component.

   - **Single-stage photo capture (onCapturePhotoAvailable) development process**:

     - Register the single-stage photo capture callback before the session [commitConfig](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#commitconfig11-1).

     - In the single-stage photo callback, obtain image information, parse the pixelMap data, and perform custom business processing.

     - Return the processed pixelMap through the callback for image display or save the image to a file via a security component.

     - Unregister the single-stage photo callback after use.

     ```ts
     // Single-stage photo callback.
     function setPhotoOutputSingleCb(context: Context, photoOutput: camera.PhotoOutput)
     {
       // After setting the callback, calling the capture method of photoOutput will return the captured pixelMap in the callback.
       photoOutput.onCapturePhotoAvailable(async (capturePhoto: camera.CapturePhoto): Promise<void> => {
         console.info("getPhoto start");
         if (capturePhoto === undefined) {
           console.error("getPhoto failed, capturePhoto is null or undefined");
           return;
         }
         let pictureObj: image.Picture = capturePhoto.main as image.Picture;
         if (pictureObj === undefined) {
           console.error("getPhoto failed, pictureObj is null or undefined");
           return;
         }
         // Obtain the pixelMap of the main photo image.
         let mainPixelMap: image.PixelMap = pictureObj.getMainPixelmap();
         if (mainPixelMap === undefined) {
           console.error("getPhoto failed, mainPixelMap is null or undefined");
           return;
         }
         // Encode the data in the pixelMap.
         const imagePackerApi = image.createImagePacker();
         let packOpts: image.PackingOption = {format: 'image/jpeg', quality: 95};
         const path: string = context.cacheDir + '/pixel_map.jpg';
         let srcFileUri: string = '';
         let file = fileIo.openSync(path, fileIo.OpenMode.CREATE | fileIo.OpenMode.READ_WRITE);
         try {
           await imagePackerApi.packToFile(mainPixelMap, file.fd, packOpts);
           srcFileUri = file.path;
         } catch (error) {
           console.error("Failed to pack the pixelMap to file. And the errorcode: ${error.code} ,error.message: ${error.message}");
         }
         // Save the image.
         let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
         try {
           // Specify the URI of the image in the application sandbox to be saved to the media library.
           let srcFileUris: string[] = [
             srcFileUri
           ];
           // Specify the creation options for the photo to be saved, including the file extension and photo type; the title and photo subtype are optional.
           let photoCreationConfigs: photoAccessHelper.PhotoCreationConfig[] = [
             {
               title: 'test', // Optional.
               fileNameExtension: 'jpg',
               photoType: photoAccessHelper.PhotoType.IMAGE,
               subtype: photoAccessHelper.PhotoSubtype.DEFAULT, // Optional.
             }
           ];
           // Obtain the target URI of the media library through pop-up authorization.
           let desFileUris: string[] = await phAccessHelper.showAssetsCreationDialog(srcFileUris, photoCreationConfigs);
           // Write the photo content from the application sandbox to the target URI of the media library.
           let desFile: fileIo.File = await fileIo.open(desFileUris[0], fileIo.OpenMode.WRITE_ONLY);
           let srcFile: fileIo.File = await fileIo.open(srcFileUri, fileIo.OpenMode.READ_ONLY);
           await fileIo.copyFile(srcFile.fd, desFile.fd);
           fileIo.closeSync(srcFile);
           fileIo.closeSync(desFile);
           console.info("create asset by dialog successfully");
         } catch (err) {
           console.error("failed to create asset by dialog successfully errCode is: ${err.code}, ${err.message}");
         }
         // Obtain metadata from PixelMap.
         let metadataType: image.MetadataType = image.MetadataType.EXIF_METADATA;
         let pictureMetadata: Promise<image.Metadata>  = pictureObj.getMetadata(metadataType);
         if (pictureMetadata != undefined) {
           console.info("Get picture metadata with EXIF_METADATA successfully");
         } else {
           console.error("Get picture metadata with EXIF_METADATA failed");
         }
         // Release resources.
         mainPixelMap.release();
         pictureObj.release();
       });
     }
     ```

   - **Multi-stage photo (PhotoAvailable) development process**:

     - Register the multi-stage photo callback before the session [commitConfig](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#commitconfig11-1).

     - Obtain image information in the multi-stage photo callback, parse the pixelMap data, and perform custom business processing.

     - Return the processed pixelMap for image display or write the file to save the image through a security component.

     - After calling [capture](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#capture-2) to take a photo, you need to promptly call [saveCameraPhoto](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md#savecameraphoto12) to save the image or [discardCameraPhoto](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md#discardcameraphoto12) to cancel saving the image; otherwise, subsequent photo capture will be affected.

     - After use, unregister the multi-stage photo callback.

     ```ts
     // Multi-stage photo callback.
     function setPhotoOutputDefferCb(photoOutput: camera.PhotoOutput, context: Context, callback: (pixelMap: image.PixelMap, uri: string) => void)
     {
        photoOutput.on('photoAssetAvailable', async (_err: BusinessError, photoAsset: photoAccessHelper.PhotoAsset): Promise<void> => {
          try {
            console.info("On photoAssetAvailable callback uri: ${photoAsset.uri}");
            let accessHelper: photoAccessHelper.PhotoAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
            // Save the image.
            try {
              // Create a media asset change request.
              let assetChangeRequest: photoAccessHelper.MediaAssetChangeRequest = new photoAccessHelper.MediaAssetChangeRequest(photoAsset);
              let phAccessHelper = photoAccessHelper.getPhotoAccessHelper(context);
              console.info("Start to save camera photo");
              // Save the photo taken by the camera.
              await assetChangeRequest.saveCameraPhoto(photoAccessHelper.ImageFileType.JPEG);
              // Submit the media change request.
              await phAccessHelper.applyChanges(assetChangeRequest);
              console.info("Save camera photo end");
              await phAccessHelper.release();
            } catch (error) {
              console.error("On photoAssetAvailable save camera photo error:  ${error.code}, ${error.message}");
            }
            // Obtain the image pixelmap information.
            try {
              class MediaDataHandler implements photoAccessHelper.QuickImageDataHandler<image.Picture> {
                onDataPrepared(data: image.Picture, imageSource: image.ImageSource, map: Map<string, string>) {
                  if (data != undefined) {
                    console.info("On photoAssetAvailable callback data is not undefined");
                    let pixelMap: image.PixelMap = data.getMainPixelmap();
                    pixelMap.getImageInfo().then((info) => {
                      console.info("On photoAssetAvailable pixelMap.width: " + info.size.width + ", pixelMap.height: " +
                        info.size.height + ", pixelMap.pixelFormat: " + info.pixelFormat);
                    })
                    callback(pixelMap, photoAsset.uri);
                  } else if (data === undefined && imageSource != undefined) {
                    console.info("On photoAssetAvailable callback data is undefined, and imageSource is not undefined");
                    imageSource.createPixelMap().then((pixelMap: image.PixelMap) => {
                      callback(pixelMap, photoAsset.uri);
                    }).catch((error: BusinessError) => {
                      console.error("On photoAssetAvailable callback createPixelMap failed, error: ${error.message}");
                    })
                  } else {
                    console.error("On photoAssetAvailable callback data and imageSource are both undefined");
                    return;
                  }
                }
              }
              // Create a data share predicate.
              let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
              // Configure the media asset retrieval conditions.
              let fetchOptions: photoAccessHelper.FetchOptions = {
                fetchColumns: [],
                predicates: predicates,
              };
              // Set the request policy to balanced mode.
              let requestOptions: photoAccessHelper.RequestOptions = {
                deliveryMode: photoAccessHelper.DeliveryMode.BALANCE_MODE
              };
              const handler = new MediaDataHandler();
              await photoAccessHelper.MediaAssetManager.quickRequestImage(context, photoAsset, requestOptions, handler);
              console.info("On photoAssetAvailable callback end");
            } catch (error) {
              console.error("On photoAssetAvailable quickRequest error:  ${error.code}, ${error.message}");
            }
          } catch (error) {
            console.error("On photoAssetAvailable callback error:  ${error.code}, ${error.message}");
          }
        });
        console.info("Set photoAssetAvailable callback end");
     }
     ```

5. Trigger photo capture.

   Execute the photo capture task using the [capture](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#capture-2) method of photoOutput. This method takes two parameters: the first is the capture settings (setting), where you can configure image quality, image rotation angle, and other information; the second is an asynchronous callback used to obtain the result. If the API call fails, a corresponding error code will be returned.

   Use the [getPhotoRotation](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#getphotorotation12) method in PhotoOutput to obtain the photo rotation angle.

   Use the [geoLocationManager.getCurrentLocation](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geolocationmanagergetcurrentlocation) method in geoLocationManager to obtain the geographic location information of the image. For usage, refer to the [capture](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#capture-3) example.

   ```ts
   function capture(captureLocation: camera.Location, photoOutput: camera.PhotoOutput): void {
     let settings: camera.PhotoCaptureSetting = {
       quality: camera.QualityLevel.QUALITY_LEVEL_HIGH,  // Set the image quality to high.
       rotation: camera.ImageRotation.ROTATION_0,  // Set the image rotation angle to 0 degrees.
       location: captureLocation,  // Set the image geographic location.
       mirror: false  // Set the mirroring enable switch (off by default).
     };
     try {
       photoOutput.capture(settings, (err: BusinessError) => {
         if (err) {
           console.error("Failed to capture the photo. error: ${err}");
           return;
         }
         console.info("Callback invoked to indicate the photo capture request success.");
       });
     } catch (error) {
       console.error("capture call failed. error: ${error}");
     }
   }
   ```

## Status Listening

During camera application development, you can listen for the photo output stream status at any time, including the start of the photo stream, the start and end of photo frames, whether the next photo is ready to be taken, and errors in the photo output stream.

- Listen for the photo start result by registering a fixed captureStart callback, which can be monitored once the photoOutput is successfully created. This event is triggered when the camera device is ready to start the current photo capture, and it returns the captureId of this photo capture.

  ```ts
  function onPhotoOutputCaptureStart(photoOutput: camera.PhotoOutput): void {
    photoOutput.on('captureStartWithInfo', (err: BusinessError, captureStartInfo: camera.CaptureStartInfo) => {
      if (err !== undefined && err.code !== 0) {
        return;
      }
      console.info("photo capture started, captureId : ${captureStartInfo.captureId}");
    });
  }
  ```

- Listen for the photo end result by registering a fixed captureEnd callback, which can be monitored once the photoOutput is successfully created. This event returns the relevant information [CaptureEndInfo](../../reference/apis-camera-kit/arkts-apis-camera-i.md#captureendinfo) after the photo capture is completely finished.

  ```ts
  function onPhotoOutputCaptureEnd(photoOutput: camera.PhotoOutput): void {
    photoOutput.on('captureEnd', (err: BusinessError, captureEndInfo: camera.CaptureEndInfo) => {
      if (err !== undefined && err.code !== 0) {
        return;
      }
      console.info("photo capture end, captureId : ${captureEndInfo.captureId}");
      console.info("frameCount : ${captureEndInfo.frameCount}");
    });
  }
  ```

- Obtain the result of whether the next photo can be taken by registering a fixed captureReady callback, which can be monitored once the photoOutput is successfully created. This event is triggered when the next photo can be taken, and it returns the relevant information about the next photo being ready.

  ```ts
  function onPhotoOutputCaptureReady(photoOutput: camera.PhotoOutput): void {
    photoOutput.on('captureReady', (err: BusinessError) => {
      if (err !== undefined && err.code !== 0) {
        return;
      }
      console.info("photo capture ready");
    });
  }
  ```

- Obtain the error result of the photo output stream by registering a fixed error callback. The callback returns the corresponding error code when an error occurs in using the photo output interface. For error code types, see [CameraErrorCode](../../reference/apis-camera-kit/arkts-apis-camera-e.md#cameraerrorcode).

  ```ts
  function onPhotoOutputError(photoOutput: camera.PhotoOutput): void {
    photoOutput.on('error', (error: BusinessError) => {
      console.error("Photo output error code: ${error.code}");
    });
  }
  ```