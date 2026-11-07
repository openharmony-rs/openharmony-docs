# DRM Playback with AVCodec (C/C++)

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=75e4d415ae0aa5a64aaac872b79ad9c25b972c67 translatedAt=2026-11-05T06:16:33.953Z pushedAt=2026-09-15T13:38:29.061Z nl=1 -->

## When to Use

To play DRM-protected content using AVCodec, you can use the native APIs provided by DRM Kit.

Currently, the following decryption capabilities are supported:

| Audio Container| Audio Decryption|
|----------|:-------|
| mp4      | AAC    |

| Video Container| Video Decryption|
|----------|:------------|
| ts       | AVC(H.264)  |
| mp4      | AVC(H.264)  |
<!--RP1--><!--RP1End-->

**Usage Scenario**

Before setting up DRM, obtain the DRM information. For details, see step 4 in [Media Data Demultiplexing](../avcodec/audio-video-demuxer.md#how-to-develop).

## Development Guidelines

For detailed API descriptions, refer to [DRM](../../reference/apis-drm-kit/capi-drm.md).

Follow the sample code below to implement the entire DRM workflow, including obtaining a name and ID list of the DRM solutions supported by the device, creating a MediaKeySystem, creating a MediaKeySession, generating a media key request, processing a media key response, checking for secure video decoding requirements, and cleaning up resources.

When developing your application, follow the specified order of API calls to avoid exceptions or undefined behaviors. The development steps and explanations below outline the correct sequence.

### Linking the Dynamic Libraries in the CMake Script

``` cmake
target_link_libraries(sample PUBLIC libnative_drm.so)
```

> **NOTE**
>
> Replace 'sample' with your actual project name as needed.
>

## How to Develop

1. Import the DRM Kit module.

   <!-- @[drm_import_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/DrmNDK/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   // ...
   #include <cstring>
   #include <multimedia/drm_framework/native_drm_common.h>
   #include <multimedia/drm_framework/native_drm_err.h>
   #include <multimedia/drm_framework/native_mediakeysession.h>
   #include <multimedia/drm_framework/native_mediakeysystem.h>
   ```

2. Obtain the name and ID list of the DRM solutions supported by the device.

   <!-- @[drm_getMediaKeySystems](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/DrmNDK/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   uint32_t count = 3; // Set count to the actual number of DRM plugins supported by the current device.
   DRM_MediaKeySystemDescription descriptions[3];
   memset(descriptions, 0, sizeof(descriptions));
   Drm_ErrCode ret = OH_MediaKeySystem_GetMediaKeySystems(descriptions, &count);
   // ...
   ```

    After obtaining the list of names and unique identifiers of the DRM solutions supported by the device, match them with the DRM information and create the corresponding DRM solution. The DRM information can be obtained through step 4 of the development procedure in [Media Data Demultiplexing](../avcodec/audio-video-demuxer.md#how-to-develop).

    Alternatively, directly parse the media protocol or media data to extract the unique identifier of the DRM solution and the PSSH data to generate the DRM information.

3. Create a MediaKeySystem instance.

   <!-- @[drm_createMediaKeySystem](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/DrmNDK/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   Drm_ErrCode ret = OH_MediaKeySystem_Create(name, &mediaKeySystem);
   if (ret != DRM_ERR_OK || mediaKeySystem == nullptr) {
       // ...
       return log;
   }
   // ...
   ```

4. Create a MediaKeySession instance.

   <!-- @[drm_createMediaKeySession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/DrmNDK/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   DRM_ContentProtectionLevel securityLevel = CONTENT_PROTECTION_LEVEL_SW_CRYPTO;
   ret = OH_MediaKeySystem_CreateMediaKeySession(mediaKeySystem, &securityLevel, &mediaKeySession);
   // ...
   ```

5. Check whether secure decoding is required.

   <!-- @[drm_requireSecureDecoderModule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/DrmNDK/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   bool requireSecureDecoder = false;
   ret = OH_MediaKeySession_RequireSecureDecoderModule(mediaKeySession, mimeType, &requireSecureDecoder);
   // ...
   ```

6. Generate a media key request and process its response.

   <!-- @[drm_generateMediaKeyRequest](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/DrmNDK/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   DRM_MediaKeyRequest mediaKeyRequest;
   DRM_MediaKeyRequestInfo info;
   // initData corresponds to the PSSH data in the media stream. Pass in the actual data.
   unsigned char initData[512] = {0x00};
   memset(&info, 0, sizeof(DRM_MediaKeyRequestInfo));
   info.initDataLen = sizeof(initData);
   info.type = MEDIA_KEY_TYPE_ONLINE; // MEDIA_KEY_TYPE_ONLINE: online media key request; MEDIA_KEY_TYPE_OFFLINE: offline media key request.
   memcpy(info.mimeType, (char *)"video/mp4", sizeof("video/mp4"));
   memcpy(info.initData, initData, sizeof(initData));
   memcpy(info.optionName[0], (char *)"optionalDataName", sizeof("optionalDataName"));
   memcpy(info.optionData[0], (char *)"optionalDataValue", sizeof("optionalDataValue"));
   info.optionsCount = 1;
   ret = OH_MediaKeySession_GenerateMediaKeyRequest(mediaKeySession, &info, &mediaKeyRequest);
   // ...
   ```

   <!-- @[drm_processMediaKeyResponse](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/DrmNDK/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   // Obtain mediaKeyResponse from the DRM service over the network. Pass in the actual response data.
   unsigned char mediaKeyId[128] = {0x00};
   int32_t mediaKeyIdLen = 128;
   unsigned char mediaKeyResponse[MAX_DRM_MEDIA_KEY_RESPONSE_BUF_SIZE] = {0x00};
   int32_t mediaKeyResponseLen = MAX_DRM_MEDIA_KEY_RESPONSE_BUF_SIZE;
   ret = OH_MediaKeySession_ProcessMediaKeyResponse(mediaKeySession, mediaKeyResponse,
       mediaKeyResponseLen, mediaKeyId, &mediaKeyIdLen);
   // ...
   ```

    If required, set the audio decryption configuration by following step 4 in [Audio Decoding](../avcodec/audio-decoding.md#how-to-develop), and set the video decryption configuration by following step 4 in [Surface Mode in Video Decoding](../avcodec/video-decoding.md#surface-mode) or step 4 in [Buffer Mode in Video Decoding](../avcodec/video-decoding.md#buffer-mode).

7. Destroy the MediaKeySession instance.

   <!-- @[drm_destroyMediaKeySession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/DrmNDK/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   ret = OH_MediaKeySession_Destroy(mediaKeySession);
   // ...
   ```

8. Destroy the MediaKeySystem instance.

   <!-- @[drm_destroyMediaKeySystem](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/DrmNDK/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   ret = OH_MediaKeySystem_Destroy(mediaKeySystem);
   // ...
   ```
