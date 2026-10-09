# YUV Capture (ArkTS)

<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=45526eba67080b876eb51af31a33be43ae26f701 translatedAt=2026-07-13T13:21:48.304Z pushedAt=2026-07-21T10:23:29.444Z -->

Starting from API version 23, Camera Kit provides the capability to capture images in YUV format. Compared with regular photo capture, YUV capture obtains unencoded image data, which fully preserves the raw luminance and chrominance information captured by the sensor, making it suitable for video encoding or professional processing. However, the capture process incurs higher energy consumption, and saving the data occupies more storage space.

## How to Develop

For detailed camera API descriptions, see [OH_Camera](../../reference/apis-camera-kit/arkts-apis-camera.md).

1. Import required modules.

   To obtain captured image data, use the system-provided `image`, `dataSharePredicates`, and `photoAccessHelper` APIs as follows.

   ```ts
   import { BusinessError } from '@kit.BasicServicesKit';
   import { camera } from '@kit.CameraKit';
   import { dataSharePredicates } from '@kit.ArkData';
   import { fileIo } from '@kit.CoreFileKit';
   import { image } from '@kit.ImageKit';
   import { photoAccessHelper} from '@kit.MediaLibraryKit';
   ```

2. Obtain the full output capability of the camera device.

   Use the [getSupportedFullOutputCapability](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#getsupportedfulloutputcapability23) method to obtain the capabilities of all output streams supported by the current camera device, including the preview stream, photo stream, and video stream. The output streams are contained in the respective profile fields of [CameraOutputCapability](../../reference/apis-camera-kit/arkts-apis-camera-i.md#cameraoutputcapability), where the photo stream supports the YUV format.

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

   Use the `photoProfiles` property in [CameraOutputCapability](../../reference/apis-camera-kit/arkts-apis-camera-i.md#cameraoutputcapability) to obtain the photo output streams supported by the current device.

   Call the [createPhotoOutput](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#createphotooutput11) method, passing a supported output stream [Profile](../../reference/apis-camera-kit/arkts-apis-camera-i.md#profile), to create a photo output stream.

   Obtain the camera's full output capability `cameraOutputCapability` through [getSupportedFullOutputCapability](../../reference/apis-camera-kit/arkts-apis-camera-CameraManager.md#getsupportedfulloutputcapability23), as described in step 2. From the `photoProfiles` in `cameraOutputCapability`, select a profile that supports the YUV format as the `photoProfile` parameter for creating the photo output stream.

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

4. Set callbacks for the photo output stream.

   Set the callback for one-shot photo capture [onCapturePhotoAvailable](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#oncapturephotoavailable23) or deferred photo capture [on('photoAssetAvailable')](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#onphotoassetavailable12), and save the captured pixelMap data as an image. If the app needs to receive the image quickly, the deferred photo capture callback is recommended.

   For details about how to obtain the context, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

   To view the saved images and video resources in Gallery, you need to first save them to the media library. For details, see [Saving Media Assets](../medialibrary/photoAccessHelper-savebutton.md).

   If you need to obtain the buffer in [onCapturePhotoAvailable](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#oncapturephotoavailable23), first save the [PixelMap](../../reference/apis-image-kit/arkts-apis-image-PixelMap.md) data to the media library through a security component.

   - **One-shot photo capture (onCapturePhotoAvailable) development**:

     - Register the one-shot photo capture callback before the session calls [commitConfig](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#commitconfig11-1).

     - In the one-shot photo capture callback function, obtain the image information, parse the pixelMap data, and perform custom service processing.

     - Return the processed pixelMap through the callback for image display, or save the image to a file using a security component.

     - After use, unregister the one-shot photo capture callback.

     ```ts
     // One-shot photo capture callback function.
     function setPhotoOutputSingleCb(context: Context, photoOutput: camera.PhotoOutput)
     {
       // After the callback is set, calling the capture method of photoOutput returns the captured pixelMap through the callback.
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
         // Obtain the pixelMap of the main image captured.
         let mainPixelMap: image.PixelMap = pictureObj.getMainPixelmap();
         if (mainPixelMap === undefined) {
           console.error("getPhoto failed, mainPixelMap is null or undefined");
           return;
         }
         // Encode the data in pixelMap.
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
           // Specify the URI of the image in the app sandbox to be saved to the media library.
           let srcFileUris: string[] = [
             srcFileUri
           ];
           // Specify the creation options for the photo to be saved, including the file extension and photo type. The title and photo subtype are optional.
           let photoCreationConfigs: photoAccessHelper.PhotoCreationConfig[] = [
             {
               title: 'test', // Optional.
               fileNameExtension: 'jpg',
               photoType: photoAccessHelper.PhotoType.IMAGE,
               subtype: photoAccessHelper.PhotoSubtype.DEFAULT, // Optional.
             }
           ];
           // Obtain the target URI of the media library through dialog-based authorization.
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
         // Obtain metadata from the PixelMap.
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

   - **Deferred photo capture (PhotoAvailable) development**:

     - Register the deferred photo capture callback before the session [commitConfig](../../reference/apis-camera-kit/arkts-apis-camera-Session.md#commitconfig11-1).

     - Obtain image information in the deferred photo capture callback function, parse the pixelMap data, and perform custom service processing.

     - Return the processed pixelMap for image display or save the image by writing to a file through a security component.

     - After calling [capture](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#capture-2) to take a photo, promptly call [saveCameraPhoto](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md#savecameraphoto12) to save the image or [discardCameraPhoto](../../reference/apis-media-library-kit/arkts-apis-photoAccessHelper-MediaAssetChangeRequest.md#discardcameraphoto12) to cancel saving the image. Otherwise, subsequent image capture will be affected.

     - After use, unregister the deferred photo capture callback function.

     ```ts
     // Deferred photo capture callback function.
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
              // Save the photo captured by the camera.
              await assetChangeRequest.saveCameraPhoto(photoAccessHelper.ImageFileType.JPEG);
              // Submit the media change request.
              await phAccessHelper.applyChanges(assetChangeRequest);
              console.info("Save camera photo end");
              await phAccessHelper.release();
            } catch (error) {
              console.error("On photoAssetAvailable save camera photo error:  ${error.code}, ${error.message}");
            }
            // Obtain the image pixelMap information.
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
              // Create a data sharing predicate.
              let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
              // Configure the media asset retrieval conditions.
              let fetchOptions: photoAccessHelper.FetchOptions = {
                fetchColumns: [],
                predicates: predicates,
              };
              // Configure the request strategy to balanced mode.
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

   Use the [capture](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#capture-2) method of `photoOutput` to execute the capture task. This method has two parameters: the first parameter is the capture settings (`setting`), in which you can set the image quality, image rotation angle, and other information; the second parameter is an asynchronous callback used to return the result. If the API call fails, the corresponding error code is returned.

   Use the [getPhotoRotation](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#getphotorotation12) method in PhotoOutput to obtain the capture rotation angle.

   Use the [geoLocationManager.getCurrentLocation](../../reference/apis-location-kit/js-apis-geoLocationManager.md#geolocationmanagergetcurrentlocation) method in `geoLocationManager` to obtain the geographic location information of the image. For usage, refer to the [capture](../../reference/apis-camera-kit/arkts-apis-camera-PhotoOutput.md#capture-3) example.

   ```ts
   function capture(captureLocation: camera.Location, photoOutput: camera.PhotoOutput): void {
     let settings: camera.PhotoCaptureSetting = {
       quality: camera.QualityLevel.QUALITY_LEVEL_HIGH,  // Set the image quality to high.
       rotation: camera.ImageRotation.ROTATION_0,  // Set the image rotation angle to 0 degrees.
       location: captureLocation,  // Set the image geographic location.
       mirror: false  // Set the mirror enable switch (disabled by default).
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

During camera app development, you can monitor the status of the photo output stream at any time, including the start of the photo stream, the start and end of capture frames, whether the next photo is ready for capture, and errors of the photo output stream.

- By registering the fixed `captureStart` callback, you can listen for the capture start result. This callback can be registered once the `photoOutput` is successfully created. It is triggered when the camera device is ready to start the current capture, and the event returns the `captureId` of this capture.

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

- By registering the fixed `captureEnd` callback, you can listen for the capture end result. This callback can be registered once the `photoOutput` is successfully created. The event returns information related to the completion of the capture, specifically [CaptureEndInfo](../../reference/apis-camera-kit/arkts-apis-camera-i.md#captureendinfo).

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

- By registering the fixed `captureReady` callback, you can listen for whether the next photo can be captured. This callback can be registered once the `photoOutput` is successfully created. It is triggered when the next photo is ready for capture, and the event returns information related to the readiness of the next photo.

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

- You can register a fixed error callback to listen for error results of the photo output stream. The callback returns the corresponding error code when an error occurs while using the photo output APIs. For details about the error codes, see [CameraErrorCode](../../reference/apis-camera-kit/arkts-apis-camera-e.md#cameraerrorcode).

  ```ts
  function onPhotoOutputError(photoOutput: camera.PhotoOutput): void {
    photoOutput.on('error', (error: BusinessError) => {
      console.error("Photo output error code: ${error.code}");
    });
  }
  ```