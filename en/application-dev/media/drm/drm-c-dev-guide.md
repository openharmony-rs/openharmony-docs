---
kits: ["Drm Kit"]
description: "Describes using DRM Kit C/C++ APIs for certificate management, license management, content authorization, and decryption for native DRM development."
keywords: [DRM, C/C++, Native API, certificate management, MediaKeySystem, MediaKeySession, content authorization, content decryption, security protection level]
doctype: guide
status: active
---
# DRM Development (C/C++)

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=df601d4dba6b4a39196e7a57e3dfef1b2e9b742e translatedAt=2026-11-02T02:33:31.187Z pushedAt=2026-11-02T02:33:31.187Z nl=1 -->

## When to Use

DRM Kit provides C/C++ APIs for comprehensive digital rights management, covering certificate management, license management, content authorization, and content decryption.

Its implementation is built around two core classes: MediaKeySystem and MediaKeySession. MediaKeySystem handles system-level management of DRM certificates and licenses, as well as the lifecycle of MediaKeySession instances. MediaKeySession, in turn, is responsible for authorizing specific content and enabling its decryption through integration with AVCodec Kit for playback.

## How to Develop

For detailed API descriptions, see [DRM](../../reference/apis-drm-kit/capi-drm.md).

1. Import the DRM Kit module.

   <!-- @[drm_import_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   // ...
   #include <cstring>
   #include <multimedia/drm_framework/native_drm_common.h>
   #include <multimedia/drm_framework/native_drm_err.h>
   #include <multimedia/drm_framework/native_mediakeysession.h>
   #include <multimedia/drm_framework/native_mediakeysystem.h>
   ```

2. Link the dynamic libraries in the CMake script.

   ```txt
   target_link_libraries(PUBLIC libnative_drm.so)
   ```

3. Obtain the name and ID list of the DRM solutions supported by the device.

   <!-- @[drm_getMediaKeySystems](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   uint32_t count = 3; // count specifies the number of DRM plugins supported by the device. Pass in the actual number.
   DRM_MediaKeySystemDescription descriptions[3];
   memset(descriptions, 0, sizeof(descriptions));
   Drm_ErrCode ret = OH_MediaKeySystem_GetMediaKeySystems(descriptions, &count);
   // ...
   ```

4. (Optional) Check whether the device supports a specific DRM solution based on the name, MIME type, and content protection level.

   <!-- @[drm_isSupported3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   bool isSupported = OH_MediaKeySystem_IsSupported3(name, mimeType, CONTENT_PROTECTION_LEVEL_SW_CRYPTO);
   // ...
   ```

5. Create a MediaKeySystem instance.

   <!-- @[drm_createMediaKeySystem](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   Drm_ErrCode ret = OH_MediaKeySystem_Create(name, &mediaKeySystem);
   if (ret != DRM_ERR_OK || mediaKeySystem == nullptr) {
       // ...
       return log;
   }
   // ...
   ```

6. (Optional) Set the MediaKeySystem event listener callback.

   <!-- @[drm_bindMediaKeySystemCallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   ret = OH_MediaKeySystem_SetCallback(mediaKeySystem, SystemCallBackWithObj);
   // ...
   ```

7. (Optional) Obtain the status of the DRM certificate.

   <!-- @[drm_getCertificateStatus](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   DRM_CertificateStatus certStatus = CERT_STATUS_NOT_PROVISIONED;
   ret = OH_MediaKeySystem_GetCertificateStatus(mediaKeySystem, &certStatus);
   // ...
   ```

8. (Optional) Generate a DRM certificate request and process its response.

   <!-- @[drm_generateKeySystemRequest](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   unsigned char request[MAX_DRM_PROVISION_BUF_SIZE] = {0x00};
   int32_t requestLen = MAX_DRM_PROVISION_BUF_SIZE;
   char defaultUrl[2048] = {0x00};
   int32_t defaultUrlLen = 2048;
   ret = OH_MediaKeySystem_GenerateKeySystemRequest(mediaKeySystem, request, &requestLen, defaultUrl, defaultUrlLen);
   // ...
   ```

   <!-- @[drm_processKeySystemResponse](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   // Send the device DRM certificate request to the DRM service over the network and pass in the actual keySystemResponse.
   unsigned char keySystemResponse[MAX_DRM_PROVISION_BUF_SIZE] = {0x00};
   ret = OH_MediaKeySystem_ProcessKeySystemResponse(mediaKeySystem, keySystemResponse, sizeof(keySystemResponse));
   // ...
   ```

9. (Optional) Obtain the maximum content protection level supported by the device.

   <!-- @[drm_getMaxContentProtectionLevel](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   DRM_ContentProtectionLevel level = CONTENT_PROTECTION_LEVEL_UNKNOWN;
   ret = OH_MediaKeySystem_GetMaxContentProtectionLevel(mediaKeySystem, &level);
   // ...
   ```

10. Create a MediaKeySession instance.

    <!-- @[drm_createMediaKeySession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
    
    ``` C++
    DRM_ContentProtectionLevel securityLevel = CONTENT_PROTECTION_LEVEL_SW_CRYPTO;
    ret = OH_MediaKeySystem_CreateMediaKeySession(mediaKeySystem, &securityLevel, &mediaKeySession);
    // ...
    ```

11. (Optional) Set the MediaKeySession event listener callback.

    <!-- @[drm_bindMediaKeySessionCallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
    
    ``` C++
    OH_MediaKeySession_Callback sessionCallback = { SessionEventCallBackWithObj, SessionKeyChangeCallBackWithObj };
    ret = OH_MediaKeySession_SetCallback(mediaKeySession, &sessionCallback);
    // ...
    ```

12. (Optional) Check whether secure decoding is required.

    <!-- @[drm_requireSecureDecoderModule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
    
    ``` C++
    bool requireSecureDecoder = false;
    ret = OH_MediaKeySession_RequireSecureDecoderModule(mediaKeySession, mimeType, &requireSecureDecoder);
    // ...
    ```

13. Generate a media key request and process its response to request a license for content authorization.

    <!-- @[drm_generateMediaKeyRequest](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
    
    ``` C++
    DRM_MediaKeyRequest mediaKeyRequest;
    DRM_MediaKeyRequestInfo info;
    // Set initData to the actual PSSH data in the media stream.
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

    <!-- @[drm_processMediaKeyResponse](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
    
    ``` C++
    // Obtain mediaKeyResponse from the DRM service over the network and pass in the actual response data.
    unsigned char mediaKeyId[128] = {0x00};
    int32_t mediaKeyIdLen = 128;
    unsigned char mediaKeyResponse[MAX_DRM_MEDIA_KEY_RESPONSE_BUF_SIZE] = {0x00};
    int32_t mediaKeyResponseLen = MAX_DRM_MEDIA_KEY_RESPONSE_BUF_SIZE;
    ret = OH_MediaKeySession_ProcessMediaKeyResponse(mediaKeySession, mediaKeyResponse,
        mediaKeyResponseLen, mediaKeyId, &mediaKeyIdLen);
    // ...
    ```

14. (Optional) Restore offline media keys.

    <!-- @[drm_restoreOfflineMediaKeys](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
    
    ``` C++
    ret = OH_MediaKeySession_RestoreOfflineMediaKeys(mediaKeySession, mediaKeyId, mediaKeyIdLen);
    // ...
    ```

15. (Optional) Check the status of media keys.

    <!-- @[drm_checkMediaKeyStatus](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
    
    ``` C++
    DRM_MediaKeyStatus mediaKeyStatus = {0};
    ret = OH_MediaKeySession_CheckMediaKeyStatus(mediaKeySession, &mediaKeyStatus);
    // ...
    ```

16. (Optional) Obtain the IDs of offline media keys, obtain their status, and clear them.

    <!-- @[drm_offlineMediaKeyManagement](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
    
    ``` C++
    DRM_OfflineMediakeyIdArray offlineMediaKeyIds;
    ret = OH_MediaKeySystem_GetOfflineMediaKeyIds(mediaKeySystem, &offlineMediaKeyIds);
    // ...
    if (ret == DRM_ERR_OK && offlineMediaKeyIds.idsCount > 0) {
        DRM_OfflineMediaKeyStatus offlineStatus = OFFLINE_MEDIA_KEY_STATUS_UNKNOWN;
        ret = OH_MediaKeySystem_GetOfflineMediaKeyStatus(mediaKeySystem, offlineMediaKeyIds.ids[0],
            offlineMediaKeyIds.idsLen[0], &offlineStatus);
        // ...
        ret = OH_MediaKeySystem_ClearOfflineMediaKeys(mediaKeySystem, offlineMediaKeyIds.ids[0],
            offlineMediaKeyIds.idsLen[0]);
        // ...
    }
    ```

17. Destroy the MediaKeySession instance.

    <!-- @[drm_destroyMediaKeySession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
    
    ``` C++
    ret = OH_MediaKeySession_Destroy(mediaKeySession);
    // ...
    ```

18. Destroy the MediaKeySystem instance.

    <!-- @[drm_destroyMediaKeySystem](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
    
    ``` C++
    ret = OH_MediaKeySystem_Destroy(mediaKeySystem);
    // ...
    ```