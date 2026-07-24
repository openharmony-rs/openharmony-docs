# YUV Capture (C/C++)

<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=45526eba67080b876eb51af31a33be43ae26f701 translatedAt=2026-07-13T13:21:40.484Z pushedAt=2026-07-21T10:35:00.182Z -->

Starting from API version 23, Camera Kit provides the capability to capture images in YUV format. Compared with regular photo capture, YUV photo capture obtains unencoded image data, fully preserving the raw luminance and chrominance information captured by the sensor, making it suitable for video encoding or professional processing. However, the capture process incurs higher power consumption, and saving the images requires more storage space.

## How to Develop

For detailed camera API descriptions, see [OH_Camera](../../reference/apis-camera-kit/capi-oh-camera.md).

1. Import the NDK APIs, which provide camera-related properties and methods. The import method is as follows:

   ```c++
   // Include the NDK header files.
   #include <cstdint>
   #include <cstdlib>
   #include <cstring>
   #include <string.h>
   #include <new>
   #include "hilog/log.h"
   #include "multimedia/image_framework/image/image_source_native.h"
   #include "multimedia/image_framework/image/image_packer_native.h"
   #include "multimedia/media_library/media_access_helper_capi.h"
   #include "multimedia/media_library/media_asset_base_capi.h"
   #include "multimedia/media_library/media_asset_capi.h"
   #include "multimedia/media_library/media_asset_change_request_capi.h"
   #include "multimedia/media_library/media_asset_manager_capi.h"
   #include "ohcamera/camera.h"
   #include "ohcamera/camera_input.h"
   #include "ohcamera/camera_manager.h"
   #include "ohcamera/capture_session.h"
   #include "ohcamera/photo_native.h"
   #include "ohcamera/photo_output.h"
   #include "ohcamera/preview_output.h"
   #include "ohcamera/video_output.h"
   ```

2. Link the relevant dynamic libraries in the CMake script.

   ```txt
   target_link_libraries(entry PUBLIC
       libace_napi.z.so
       libhilog_ndk.z.so
       libnative_buffer.so
       libohcamera.so
       libohimage.so
       libohfileuri.so
       libmedia_asset_manager.so
       libimage_source.so
       libpixelmap.so
       libimage_packer.so
       libpicture.so
   )
   ```

3. Create and open the camera device. For details, see steps 3 and 4 in [Device Input Management (C/C++)](./native-camera-device-input.md).

4. Obtain the complete output capabilities of the camera device.

   Use the [OH_CameraManager_GetSupportedFullCameraOutputCapabilityWithSceneMode()](../../reference/apis-camera-kit/capi-camera-manager-h.md#oh_cameramanager_getsupportedfullcameraoutputcapabilitywithscenemode) method to obtain the capabilities of all output streams supported by the current device, including preview streams, photo streams, and video streams. The output streams are in the respective profile fields of `CameraOutputCapability`, where the photo stream supports the YUV format. Different types of output streams need to be added depending on the specified camera device mode [Camera_SceneMode](../../reference/apis-camera-kit/capi-camera-h.md#camera_scenemode).

   ```c++
   Camera_OutputCapability* GetSupportedFullCameraOutputCapability(Camera_Manager* cameraManager, Camera_Device &camera)
   {
        Camera_OutputCapability* cameraOutputCapability = nullptr;
        // Obtain the output stream capabilities supported by the camera device.
        const Camera_Profile* previewProfile = nullptr;
        const Camera_Profile* photoProfile = nullptr;
        Camera_ErrorCode ret = OH_CameraManager_GetSupportedFullCameraOutputCapabilityWithSceneMode(cameraManager, &camera,
            Camera_SceneMode::NORMAL_PHOTO, &cameraOutputCapability);
        if (cameraOutputCapability == nullptr || ret != CAMERA_OK) {
            OH_LOG_ERROR(LOG_APP, "OH_CameraManager_GetSupportedCameraOutputCapability failed.");
            return nullptr;
        }
        return cameraOutputCapability;
   }
   ```

5. Select an output stream capability supported by the device and create a photo output stream.

   The photo output stream is created via the [OH_CameraManager_CreatePhotoOutputWithoutSurface()](../../reference/apis-camera-kit/capi-camera-manager-h.md#oh_cameramanager_createphotooutputwithoutsurface) method.

   The full output capability `cameraOutputCapability` supported by the camera in a specified mode can be obtained via [OH_CameraManager_GetSupportedFullCameraOutputCapabilityWithSceneMode()](../../reference/apis-camera-kit/capi-camera-manager-h.md#oh_cameramanager_getsupportedfullcameraoutputcapabilitywithscenemode). For details, see step 2. From the `photoProfiles` in `cameraOutputCapability`, select a profile that supports the YUV format as the `photoProfile` parameter for creating the photo output stream.

   ```c++
   Camera_PhotoOutput* CreatePhotoOutput(Camera_Manager* cameraManager, const Camera_Profile* photoProfile)
   {
       Camera_PhotoOutput* photoOutput = nullptr;
       // Create the photo stream directly without passing a surfaceId.
       Camera_ErrorCode ret = OH_CameraManager_CreatePhotoOutputWithoutSurface(cameraManager, photoProfile, &photoOutput);
       if (photoOutput == nullptr || ret != CAMERA_OK) {
           OH_LOG_ERROR(LOG_APP, "OH_CameraManager_CreatePhotoOutputWithoutSurface failed.");
       }
       return photoOutput;
   }
   ```  

6. Register the one-shot photo capture (PhotoAvailable) or deferred photo capture (PhotoAssetAvailable) callback. If the app needs to receive images quickly, the [deferred photo capture (PhotoAssetAvailable)](./native-camera-deferred-capture.md) callback is recommended.

   > **NOTE**
   >
   > If the `PhotoAssetAvailable` callback has already been registered and the `PhotoAvailable` callback is registered again after the session starts, registering both `PhotoAssetAvailable` and `PhotoAvailable` simultaneously will cause the stream to restart, and only `PhotoAssetAvailable` will take effect.

   - **One-shot photo capture (PhotoAvailable) development**:

     - Register the one-shot photo capture callback before the session [OH_CaptureSession_CommitConfig](../../reference/apis-camera-kit/capi-capture-session-h.md#oh_capturesession_commitconfig).

     - Obtain image information in the one-shot photo capture callback function, parse the pixelMap data, and perform custom service processing.

     - Pass the processed pixelMap to the ArkTS side via the callback for image display or for saving the image to a file through a security component.

     - Unregister the one-shot photo capture callback after use.

     ```c++
     // One-shot photo capture callback function.
     void OnPhotoAvailable(Camera_PhotoOutput* photoOutput, OH_PhotoNative* photo)
     {
         OH_LOG_INFO(LOG_APP, "OnPhotoAvailable start!");
         OH_PictureNative* picture;
         Camera_ErrorCode errCode = OH_PhotoNative_GetUncompressedImage(photo, &picture);
         if (errCode != CAMERA_OK || picture == nullptr) {
             OH_LOG_ERROR(LOG_APP, "OH_PhotoNative_GetUncompressedImage call failed, errorCode: %{public}d", errCode);
             return;
         }
         OH_LOG_INFO(LOG_APP, "OnPhotoAvailable errCode:%{public}d picture:%{public}p", errCode, picture);
         // Read the main image mainPixelMap from OH_PictureNative.
         OH_PixelmapNative* mainPixelmap;
         Image_ErrorCode imageErr = OH_PictureNative_GetMainPixelmap(picture, &mainPixelmap);
         if (imageErr != IMAGE_SUCCESS || mainPixelmap == nullptr) {
             OH_LOG_ERROR(LOG_APP, "OH_ImageNative_GetImageSize call failed, errorCode: %{public}d", imageErr);
             return;
         }
         OH_LOG_INFO(LOG_APP, "OH_PictureNative_GetMainPixelmap success");
         // Obtain the total number of bytes occupied by all pixels in the main image Pixelmap.
         uint32_t byteCount = 0;
         imageErr = OH_PixelmapNative_GetByteCount(mainPixelmap, &byteCount);
         OH_LOG_INFO(LOG_APP, "OH_PixelmapNative_GetByteCount count:%{public}u", byteCount);
         // Obtain the image pixel information of the main image.
         OH_Pixelmap_ImageInfo* imageInfo;
         imageErr = OH_PixelmapNative_GetImageInfo(mainPixelmap, imageInfo);
         OH_LOG_INFO(LOG_APP, "OH_PixelmapNative_GetImageInfo errorCode:%{public}d", imageErr);

         uint32_t width = 0;
         uint32_t height = 0;
         uint32_t rowStride = 0;
         int32_t pixelFormat = PIXEL_FORMAT::PIXEL_FORMAT_UNKNOWN;
         int32_t alphaMode = PIXELMAP_ALPHA_TYPE::PIXELMAP_ALPHA_TYPE_UNKNOWN;
         int32_t alphaType = PIXELMAP_ALPHA_TYPE::PIXELMAP_ALPHA_TYPE_UNKNOWN;
         // Obtain the width from the main image pixel information.
         OH_PixelmapImageInfo_GetWidth(imageInfo, &width);
         // Obtain the height from the main image pixel information.
         OH_PixelmapImageInfo_GetHeight(imageInfo, &height);
         // Obtain the row stride from the main image pixel information.
         OH_PixelmapImageInfo_GetRowStride(imageInfo, &rowStride);
         // Obtain the pixel format from the main image pixel information.
         OH_PixelmapImageInfo_GetPixelFormat(imageInfo, &pixelFormat);
         // Obtain the alpha channel type from the main image pixel information.
         OH_PixelmapImageInfo_GetAlphaMode(imageInfo, &alphaMode);
         // Obtain the default alpha type from the main image pixel information.
         OH_PixelmapImageInfo_GetAlphaType(imageInfo, &alphaType);
         OH_LOG_INFO(LOG_APP, "OH_PixelmapNative_GetImageInfo width:%{public}u height:%{public}u rowStride:%{public}u pixelFormat:%{public}d alphaMode:%{public}d alphaType:%{public}d", width, height, rowStride, pixelFormat, alphaMode, alphaType);
        // Release resources.
         OH_PixelmapNative_Release(mainPixelmap);
         OH_PictureNative_Release(picture);
     }

     // Register the one-shot photo capture callback.
     Camera_ErrorCode PhotoOutputRegisterPhotoAvailableCallback(Camera_PhotoOutput* photoOutput)
     {
         OH_LOG_INFO(LOG_APP, "PhotoOutputRegisterPhotoAvailableCallback start!");
         Camera_ErrorCode ret = OH_PhotoOutput_RegisterPhotoAvailableCallback(photoOutput, OnPhotoAvailable);
         if (ret != CAMERA_OK) {
             OH_LOG_ERROR(LOG_APP, "PhotoOutputRegisterPhotoAvailableCallback failed.");
         }
         OH_LOG_INFO(LOG_APP, "PhotoOutputRegisterPhotoAvailableCallback return with ret code: %{public}d!", ret);
         return ret;
     }

     // Unregister the one-shot photo capture callback.
     Camera_ErrorCode PhotoOutputUnRegisterPhotoAvailableCallback(Camera_PhotoOutput* photoOutput)
     {
         OH_LOG_INFO(LOG_APP, "PhotoOutputUnRegisterPhotoAvailableCallback start!");
         Camera_ErrorCode ret = OH_PhotoOutput_UnregisterPhotoAvailableCallback(photoOutput, OnPhotoAvailable);
         if (ret != CAMERA_OK) {
             OH_LOG_ERROR(LOG_APP, "PhotoOutputUnRegisterPhotoAvailableCallback failed.");
         }
         OH_LOG_INFO(LOG_APP, "PhotoOutputUnRegisterPhotoAvailableCallback return with ret code: %{public}d!", ret);
         return ret;
     }
     ```

   - **Deferred photo capture (PhotoAvailable) development**:

     - Register the deferred photo capture callback before the session [OH_CaptureSession_CommitConfig](../../reference/apis-camera-kit/capi-capture-session-h.md#oh_capturesession_commitconfig).

     - In the deferred photo capture callback function, obtain the image information, parse the pixelMap data, and perform custom service processing.

     - Pass the processed pixelMap via the callback to the ArkTS side for image display or for saving the image to a file through a security component.

     - After calling [OH_PhotoOutput_Capture](../../reference/apis-camera-kit/capi-photo-output-h.md#oh_photooutput_capture) to take a photo, promptly call [OH_MediaAssetChangeRequest_SaveCameraPhoto](../../reference/apis-media-library-kit/capi-media-asset-change-request-capi-h.md#oh_mediaassetchangerequest_savecameraphoto) to save the image or [OH_MediaAssetChangeRequest_DiscardCameraPhoto](../../reference/apis-media-library-kit/capi-media-asset-change-request-capi-h.md#oh_mediaassetchangerequest_discardcameraphoto) to discard it. Otherwise, subsequent photo capture will be affected.

     - Unregister the deferred photo capture callback function after use.

     ```c++
     // Declare the quick image return callback.
     void OnRequestQuickImageDataPreparedWithDetails(MediaLibrary_ErrorCode result, MediaLibrary_RequestId requestId, MediaLibrary_MediaQuality mediaQuality, MediaLibrary_MediaContentType type, OH_ImageSourceNative* imageSourceNative, OH_PictureNative* pictureNative)
     {
         OH_LOG_INFO(LOG_APP, "OnRequestQuickImageDataPreparedWithDetails start!");
         if (!pictureNative && !imageSourceNative) {
             OH_LOG_ERROR(LOG_APP, "OnRequestQuickImageDataPreparedWithDetails, pictureNative and imageSourceNative are null.");
             return;
         } else if (!pictureNative && imageSourceNative) {
             OH_LOG_ERROR(LOG_APP, "OnRequestQuickImageDataPreparedWithDetails, pictureNative is null.");
         } else if (pictureNative && !imageSourceNative) {
             OH_LOG_ERROR(LOG_APP, "OnRequestQuickImageDataPreparedWithDetails, imageSourceNative is null.");
         } else {
             OH_LOG_INFO(LOG_APP, "OnRequestQuickImageDataPreparedWithDetails, pictureNative and imageSourceNative are not null.");
         }
     }

     // Deferred photo capture callback function.
     void OnPhotoAssetAvailable(Camera_PhotoOutput* photoOutput, OH_MediaAsset* mediaAsset)
     {
         OH_LOG_INFO(LOG_APP, "OnPhotoAssetAvailable start!");
         if (mediaAsset == nullptr) {
             OH_LOG_ERROR(LOG_APP, "OnPhotoAssetAvailable invalid error, mediaAsset is null.");
             return;
         }
         // Obtain the URI information from mediaAsset.
         const char* uri = nullptr;
         MediaLibrary_ErrorCode result = OH_MediaAsset_GetUri(mediaAsset, &uri);
         if (uri == nullptr || result != MEDIA_LIBRARY_OK) {
             OH_LOG_ERROR(LOG_APP, "OnPhotoAssetAvailable failed to get uri.");
         }
         // Obtain the displayName information from mediaAsset.
         const char* displayName = nullptr;
         result = OH_MediaAsset_GetDisplayName(mediaAsset, &displayName);
         if (displayName == nullptr || result != MEDIA_LIBRARY_OK) {
             OH_LOG_ERROR(LOG_APP, "OnPhotoAssetAvailable failed to get displayName.");
         }
         // Create a media asset management object.
         OH_MediaAssetManager* mediaAssetManager = OH_MediaAssetManager_Create();
         if (mediaAssetManager == nullptr) {
             OH_LOG_ERROR(LOG_APP, "OnPhotoAssetAvailable failed to create mediaAssetManager.");
             return;
         }

         // Create a media asset change request.
         OH_MediaAssetChangeRequest* changeRequest = OH_MediaAssetChangeRequest_Create(mediaAsset);
         if (changeRequest == nullptr) {
             OH_LOG_ERROR(LOG_APP, "OnPhotoAssetAvailable failed to create changeRequest.");
         }
         // Register the media asset quick request callback.
         MediaLibrary_RequestOptions requestOptions;
         requestOptions.deliveryMode = MEDIA_LIBRARY_BALANCED_MODE;
         MediaLibrary_RequestId requestId;
         result = OH_MediaAssetManager_QuickRequestImage(mediaAssetManager, mediaAsset, requestOptions, &requestId, OnRequestQuickImageDataPreparedWithDetails);
         if (result != MEDIA_LIBRARY_OK) {
             OH_LOG_ERROR(LOG_APP, "OnPhotoAssetAvailable failed to quick image.");
         }
         // Create a media asset save change request.
         result = OH_MediaAssetChangeRequest_SaveCameraPhoto(changeRequest, MediaLibrary_ImageFileType::MEDIA_LIBRARY_IMAGE_JPEG);
         if (result != MEDIA_LIBRARY_OK) {
             OH_LOG_ERROR(LOG_APP, "OnPhotoAssetAvailable failed to save camera photo.");
         }
         result = OH_MediaAccessHelper_ApplyChanges(changeRequest);
         if (result != MEDIA_LIBRARY_OK) {
             OH_LOG_ERROR(LOG_APP, "OnPhotoAssetAvailable failed to apply changes.");
         }
     }

     // Register the deferred photo capture callback function.
     Camera_ErrorCode RegisterPhotoAssetAvailable(Camera_PhotoOutput* photoOutput)
     {
         Camera_ErrorCode ret = OH_PhotoOutput_RegisterPhotoAssetAvailableCallback(photoOutput, OnPhotoAssetAvailable);
         if (ret != CAMERA_OK) {
             OH_LOG_ERROR(LOG_APP, "RegisterPhotoAssetAvailable failed. %d ", ret);
         }
         return ret;
     }
     // Unregister the deferred photo capture callback function.
     Camera_ErrorCode UnregisterPhotoAssetAvailable(Camera_PhotoOutput* photoOutput)
     {
         Camera_ErrorCode ret = OH_PhotoOutput_UnregisterPhotoAssetAvailableCallback(photoOutput, OnPhotoAssetAvailable);
         if (ret != CAMERA_OK) {
             OH_LOG_ERROR(LOG_APP, "UnregisterPhotoAssetAvailable failed. %d ", ret);
         }
         return ret;
     }
     ```

7. Create a photo session (see [Session Management (C/C++)](./native-camera-session-management.md)), start the session, and prepare for photo capture.

8. Trigger photo capture.

   Execute the photo capture task via the [OH_PhotoOutput_Capture()](../../reference/apis-camera-kit/capi-photo-output-h.md#oh_photooutput_capture) method.

   ```c++
   Camera_ErrorCode Capture(Camera_PhotoOutput* photoOutput)
   {
       Camera_ErrorCode ret = OH_PhotoOutput_Capture(photoOutput);
       if (ret == CAMERA_OK) {
           OH_LOG_INFO(LOG_APP, "OH_PhotoOutput_Capture success ");
       } else {
           OH_LOG_ERROR(LOG_APP, "OH_PhotoOutput_Capture failed. %d ", ret);
       }
       return ret;
   }
   ```

## Status Listening

During camera app development, the photo output stream status can be monitored at any time, including the start of the photo stream, the start and end of photo frames, whether the next photo is ready for capture, and errors of the photo output stream.

- The result of photo capture start can be obtained by registering the fixed `onFrameStart` callback function to listen for the event when `photoOutput` is created successfully. This callback is triggered upon the first exposure of a photo.

  ```c++
  void PhotoOutputOnFrameStart(Camera_PhotoOutput* photoOutput)
  {
      OH_LOG_INFO(LOG_APP, "PhotoOutputOnFrameStart");
  }
  void PhotoOutputOnFrameShutter(Camera_PhotoOutput* photoOutput, Camera_FrameShutterInfo* info)
  {
      OH_LOG_INFO(LOG_APP, "PhotoOutputOnFrameShutter");
  }
  ```

- The result of photo capture end can be listened for by registering the fixed `onFrameEnd` callback function when `photoOutput` is created successfully.

  ```c++
  void PhotoOutputOnFrameEnd(Camera_PhotoOutput* photoOutput, int32_t frameCount)
  {
      OH_LOG_INFO(LOG_APP, "PhotoOutput frameCount = %{public}d", frameCount);
  }
  ```

- The result of whether the next photo can be captured can be listened for by registering the `captureReady` callback function when `photoOutput` is created successfully. This callback is triggered when the next photo is ready for capture, and the event returns information about the readiness of the next photo.

  ```c++
  static bool g_captureReadyFlag = false;
  void CaptureReadyCb(Camera_PhotoOutput* photoOutput) {
    g_captureReadyFlag = true;
    OH_LOG_INFO(LOG_APP, "PhotoOutputOnCaptureReady captureReadyFlag = %{public}d", g_captureReadyFlag);
  }

  void OnPhotoOutputOnCaptureReady(Camera_PhotoOutput* photoOutput)
  {
      OH_LOG_INFO(LOG_APP, "PhotoOutputOnCaptureReady");
      Camera_ErrorCode ret = OH_PhotoOutput_RegisterCaptureReadyCallback(photoOutput, CaptureReadyCb);
  }
  ```

- You can listen for error results of the photo output stream by registering a fixed `onError` callback function. The callback returns the corresponding error code when the photo output API encounters an error. For details about the error codes, see [Camera_ErrorCode](../../reference/apis-camera-kit/capi-camera-h.md#camera_errorcode).

  ```c++
  void PhotoOutputOnError(Camera_PhotoOutput* photoOutput, Camera_ErrorCode errorCode)
  {
      OH_LOG_INFO(LOG_APP, "PhotoOutput errorCode = %{public}d", errorCode);
  }
  ```

  ```c++
  PhotoOutput_Callbacks* GetPhotoOutputListener()
  {
      static PhotoOutput_Callbacks photoOutputListener = {
          .onFrameStart = PhotoOutputOnFrameStart,
          .onFrameShutter = PhotoOutputOnFrameShutter,
          .onFrameEnd = PhotoOutputOnFrameEnd,
          .onError = PhotoOutputOnError
      };
      return &photoOutputListener;
  }
  Camera_ErrorCode RegisterPhotoOutputCallback(Camera_PhotoOutput* photoOutput)
  {
      Camera_ErrorCode ret = OH_PhotoOutput_RegisterCallback(photoOutput, GetPhotoOutputListener());
      if (ret != CAMERA_OK) {
          OH_LOG_ERROR(LOG_APP, "OH_PhotoOutput_RegisterCallback failed.");
      }
      return ret;
  }
  ```