# YUV Photo Capture (C/C++)

<!--Kit: Camera Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @qano-->
<!--Designer: @leo_ysl-->
<!--Tester: @xchaosioda-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=444d4b7458e1317b3c2f1a471488b9c4b8344c2e translatedAt=2026-06-03T06:23:47.018Z pushedAt=2026-06-03T10:06:11.112Z -->

Starting from API version 23, the camera framework provides the capability to capture photos in YUV format. Compared with regular photo capture, YUV photo capture obtains unencoded image data, fully preserving the original luminance and chrominance information captured by the sensor. This is suitable for video encoding or professional processing. However, the capture process incurs higher energy consumption, and saving the data occupies more storage space.

## How to Develop

For detailed camera function API descriptions, see the Camera module [OH_Camera](../../reference/apis-camera-kit/capi-oh-camera.md).

1. Import the NDK interface, which provides camera-related properties and methods. The import method is as follows.

   ```c++
   // Import the NDK interface header file.
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

3. Create and open the camera device. For details, see steps 3-4 in [Device Input Management (C/C++)](./native-camera-device-input.md).

4. Obtain the full output capabilities of the camera device.

   Use the [OH_CameraManager_GetSupportedFullCameraOutputCapabilityWithSceneMode()](../../reference/apis-camera-kit/capi-camera-manager-h.md#oh_cameramanager_getsupportedfullcameraoutputcapabilitywithscenemode) method to obtain the capabilities of all output streams supported by the current device, including preview streams, photo streams, and video streams. The output streams are in the respective profile fields of CameraOutputCapability, where the photo stream supports YUV format. Depending on the specified camera device mode [Camera_SceneMode](../../reference/apis-camera-kit/capi-camera-h.md#camera_scenemode), different types of output streams need to be added.

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

5. Select the output stream capability supported by the device and create a photo output stream.

   Create a photo output stream using the [OH_CameraManager_CreatePhotoOutputWithoutSurface()](../../reference/apis-camera-kit/capi-camera-manager-h.md#oh_cameramanager_createphotooutputwithoutsurface) method.

   You can obtain the complete output capability **cameraOutputCapability** supported by the camera in a specified mode through [OH_CameraManager_GetSupportedFullCameraOutputCapabilityWithSceneMode()](../../reference/apis-camera-kit/capi-camera-manager-h.md#oh_cameramanager_getsupportedfullcameraoutputcapabilitywithscenemode), referring to step 2. In the **photoProfiles** of **cameraOutputCapability**, select a profile that supports the YUV format as the parameter **photoProfile** for creating the photo output stream.

   ```c++
   Camera_PhotoOutput* CreatePhotoOutput(Camera_Manager* cameraManager, const Camera_Profile* photoProfile)
   {
       Camera_PhotoOutput* photoOutput = nullptr;
       // Create a photo stream directly without passing in a surfaceId.
       Camera_ErrorCode ret = OH_CameraManager_CreatePhotoOutputWithoutSurface(cameraManager, photoProfile, &photoOutput);
       if (photoOutput == nullptr || ret != CAMERA_OK) {
           OH_LOG_ERROR(LOG_APP, "OH_CameraManager_CreatePhotoOutputWithoutSurface failed.");
       }
       return photoOutput;
   }
   ```   

6. Register the single-segment (PhotoAvailable) or deferred (PhotoAssetAvailable) photo capture callback. If the application wants to get the image back quickly, it is recommended to use the [deferred photo capture (PhotoAssetAvailable)](./native-camera-deferred-capture.md) callback.

   > **NOTE**
   >
   > If the PhotoAssetAvailable callback has already been registered, and the PhotoAvailable callback is registered again after the session starts, registering both PhotoAssetAvailable and PhotoAvailable simultaneously will cause the stream to be restarted, and only PhotoAssetAvailable will take effect.

   - **Single-segment photo capture (PhotoAvailable) development process**:

     - Register the single-segment photo capture callback before the session [OH_CaptureSession_CommitConfig](../../reference/apis-camera-kit/capi-capture-session-h.md#oh_capturesession_commitconfig).

     - Obtain image information in the single-segment photo capture callback function, parse the pixelMap data, and perform custom business processing.

     - Pass the processed pixelMap to the ArkTS side through a callback for image display or save the image to a file through a security component.

     - Unregister the single-segment photo capture callback function after use.

     ```c++
     // Single-segment photo capture callback function.
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
         // Read the main image mainPixelMap in OH_PictureNative.
         OH_PixelmapNative* mainPixelmap;
         Image_ErrorCode imageErr = OH_PictureNative_GetMainPixelmap(picture, &mainPixelmap);
         if (imageErr != IMAGE_SUCCESS || mainPixelmap == nullptr) {
             OH_LOG_ERROR(LOG_APP, "OH_ImageNative_GetImageSize call failed, errorCode: %{public}d", imageErr);
             return;
         }
         OH_LOG_INFO(LOG_APP, "OH_PictureNative_GetMainPixelmap success");
         // Get the total number of bytes occupied by all pixels in the main image Pixelmap.
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
         // Obtain the width in the image pixel information of the main image.
         OH_PixelmapImageInfo_GetWidth(imageInfo, &width);
         // Obtain the height in the image pixel information of the main image.
         OH_PixelmapImageInfo_GetHeight(imageInfo, &height);
         // Obtain the row stride in the image pixel information of the main image.
         OH_PixelmapImageInfo_GetRowStride(imageInfo, &rowStride);
         // Obtain the pixel format in the image pixel information of the main image.
         OH_PixelmapImageInfo_GetPixelFormat(imageInfo, &pixelFormat);
         // Obtains the alpha channel type in the pixel information of the main image.
         OH_PixelmapImageInfo_GetAlphaMode(imageInfo, &alphaMode);
         // Obtains the default alpha channel type in the pixel information of the main image.
         OH_PixelmapImageInfo_GetAlphaType(imageInfo, &alphaType);
         OH_LOG_INFO(LOG_APP, "OH_PixelmapNative_GetImageInfo width:%{public}u height:%{public}u rowStride:%{public}u pixelFormat:%{public}d alphaMode:%{public}d alphaType:%{public}d", width, height, rowStride, pixelFormat, alphaMode, alphaType);
        // Releases resources.
         OH_PixelmapNative_Release(mainPixelmap);
         OH_PictureNative_Release(picture);
     }

     // Registers a single-segment photo capture callback.
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

     // Unregisters a single-segment photo capture callback.
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

   - **Deferred photo capture (PhotoAvailable) development process**:

     - Register the deferred photo capture callback before the session [OH_CaptureSession_CommitConfig](../../reference/apis-camera-kit/capi-capture-session-h.md#oh_capturesession_commitconfig).

     - Obtain image information in the deferred photo capture callback function, parse the pixelMap data, and perform custom business processing.

     - Pass the processed pixelMap to the ArkTS side through a callback for image display or file saving via a security component.

     - After calling [OH_PhotoOutput_Capture](../../reference/apis-camera-kit/capi-photo-output-h.md#oh_photooutput_capture) to take a photo, promptly call [OH_MediaAssetChangeRequest_SaveCameraPhoto](../../reference/apis-media-library-kit/capi-media-asset-change-request-capi-h.md#oh_mediaassetchangerequest_savecameraphoto) to save the photo or [OH_MediaAssetChangeRequest_DiscardCameraPhoto](../../reference/apis-media-library-kit/capi-media-asset-change-request-capi-h.md#oh_mediaassetchangerequest_discardcameraphoto) to discard it. Otherwise, subsequent photo capture will be affected.

     - After use, unregister the deferred photo capture callback function.

     ```c++
     // Declare the quick return callback.
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
         // Attempt to obtain the URI information in mediaAsset.
         const char* uri = nullptr;
         MediaLibrary_ErrorCode result = OH_MediaAsset_GetUri(mediaAsset, &uri);
         if (uri == nullptr || result != MEDIA_LIBRARY_OK) {
             OH_LOG_ERROR(LOG_APP, "OnPhotoAssetAvailable failed to get uri.");
         }
         // Attempt to obtain the displayName information in mediaAsset.
         const char* displayName = nullptr;
         result = OH_MediaAsset_GetDisplayName(mediaAsset, &displayName);
         if (displayName == nullptr || result != MEDIA_LIBRARY_OK) {
             OH_LOG_ERROR(LOG_APP, "OnPhotoAssetAvailable failed to get displayName.");
         }
         // Attempt to obtain the size information in mediaAsset.
         uint32_t mediaAssetSize = 0;
         result = OH_MediaAsset_GetSize(mediaAsset, &mediaAssetSize);
         if (result != MEDIA_LIBRARY_OK) {
             OH_LOG_ERROR(LOG_APP, "OnPhotoAssetAvailable failed to get size.");
         }
         // Attempt to obtain the modification time information in mediaAsset.
         uint32_t modifiedMs = 0;
         result = OH_MediaAsset_GetDateModifiedMs(mediaAsset, &modifiedMs);
         if (result != MEDIA_LIBRARY_OK) {
             OH_LOG_ERROR(LOG_APP, "OnPhotoAssetAvailable failed to get modifiedMs.");
         }
         // Attempt to obtain the image width information in mediaAsset.
         uint32_t width = 0;
         result = OH_MediaAsset_GetWidth(mediaAsset, &width);
         if (result != MEDIA_LIBRARY_OK) {
             OH_LOG_ERROR(LOG_APP, "OnPhotoAssetAvailable failed to get width.");
         }
         // Attempt to obtain the image height information in mediaAsset.
         uint32_t height = 0;
         result = OH_MediaAsset_GetHeight(mediaAsset, &height);
         if (result != MEDIA_LIBRARY_OK) {
             OH_LOG_ERROR(LOG_APP, "OnPhotoAssetAvailable failed to get height.");
         }
         // Attempt to obtain the image orientation information in mediaAsset.
         uint32_t orientation = 0;
         result = OH_MediaAsset_GetOrientation(mediaAsset, &orientation);
         if (result != MEDIA_LIBRARY_OK) {
             OH_LOG_ERROR(LOG_APP, "OnPhotoAssetAvailable failed to get orientation.");
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
         // Register a media asset quick request callback.
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

     // Register a deferred photo capture callback function.
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

7. Create a photo session (for details, see [Camera Session Management (C/C++)](./native-camera-session-management.md)), start the session, and prepare for photo capture.

8. Trigger photo capture.

   Execute the photo capture task through the [OH_PhotoOutput_Capture()](../../reference/apis-camera-kit/capi-photo-output-h.md#oh_photooutput_capture) method.

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

During camera application development, you can listen for photo output stream status at any time, including the start of the photo stream, the start and end of photo frames, whether the next photo is ready to be captured, and errors in the photo output stream.

- Register the fixed onFrameStart callback function to listen for the photo capture start result. Listening is available once the photoOutput is successfully created. This callback is triggered upon the first exposure of a photo.

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

- Register the fixed onFrameEnd callback function to listen for the photo capture end result. Listening is available once the photoOutput is successfully created.

  ```c++
  void PhotoOutputOnFrameEnd(Camera_PhotoOutput* photoOutput, int32_t frameCount)
  {
      OH_LOG_INFO(LOG_APP, "PhotoOutput frameCount = %{public}d", frameCount);
  }
  ```

- Register the fixed captureReady callback function to listen for the result of whether the next photo can be captured. Listening is available once the photoOutput is successfully created. This callback is triggered when the next photo is ready to be captured, and the event returns information related to the next photo.

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

- Register the fixed onError callback function to listen for error results of the photo output stream. The callback returns the corresponding error code when an error occurs while using the photo output interface. For details about the error code types, see [Camera_ErrorCode](../../reference/apis-camera-kit/capi-camera-h.md#camera_errorcode).

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