---
kits: ["Drm Kit / 数字版权保护服务"]
description: "介绍如何通过C/C++接口调用DRM Kit实现证书管理、许可证管理、节目授权与解密，适用于需要底层Native开发的DRM版权保护场景。"
keywords: [DRM, C/C++, Native API, 证书管理, MediaKeySystem, MediaKeySession, 节目授权, 节目解密, 安全保护级别]
doctype: guide
status: active
---
# 数字版权保护(C/C++)

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->

## 功能介绍

开发者可以调用DRM Kit的C/C++接口实现DRM证书管理、DRM许可证管理、DRM节目授权、DRM节目解密等数字版权保护功能。

DRM Kit提供MediaKeySystem实现DRM证书管理、DRM许可证管理功能，并管理MediaKeySession实例；MediaKeySession实现DRM节目授权，并可支持Media Kit或AVCodec Kit实现DRM节目解密以实现DRM节目播放。

## 开发步骤

详细的API说明请参考[Drm](../../reference/apis-drm-kit/capi-drm.md)。

1. 导入DRM Kit接口。

   <!-- @[drm_import_header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   // ...
   #include <cstring>
   #include <multimedia/drm_framework/native_drm_common.h>
   #include <multimedia/drm_framework/native_drm_err.h>
   #include <multimedia/drm_framework/native_mediakeysession.h>
   #include <multimedia/drm_framework/native_mediakeysystem.h>
   ```

2. 在CMake脚本中链接动态库。

   ```txt
   target_link_libraries(PUBLIC libnative_drm.so)
   ```

3. 获取设备支持的DRM解决方案名称和唯一标识的列表。

   <!-- @[drm_getMediaKeySystems](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   uint32_t count = 3; // count是当前设备实际支持的DRM插件的个数，用户根据实际情况设置。
   DRM_MediaKeySystemDescription descriptions[3];
   memset(descriptions, 0, sizeof(descriptions));
   Drm_ErrCode ret = OH_MediaKeySystem_GetMediaKeySystems(descriptions, &count);
   // ...
   ```

4. （可选）查询设备是否支持对应DRM解决方案名称、媒体类型、安全保护级别的DRM解决方案。

   <!-- @[drm_isSupported3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   bool isSupported = OH_MediaKeySystem_IsSupported3(name, mimeType, CONTENT_PROTECTION_LEVEL_SW_CRYPTO);
   // ...
   ```

5. 创建MediaKeySystem实例。

   <!-- @[drm_createMediaKeySystem](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   Drm_ErrCode ret = OH_MediaKeySystem_Create(name, &mediaKeySystem);
   if (ret != DRM_ERR_OK || mediaKeySystem == nullptr) {
       // ...
       return log;
   }
   // ...
   ```

6. （可选）设置MediaKeySystem事件监听回调。

   <!-- @[drm_bindMediaKeySystemCallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   ret = OH_MediaKeySystem_SetCallback(mediaKeySystem, SystemCallBackWithObj);
   // ...
   ```

7. （可选）获取设备DRM证书状态。

   <!-- @[drm_getCertificateStatus](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   DRM_CertificateStatus certStatus = CERT_STATUS_NOT_PROVISIONED;
   ret = OH_MediaKeySystem_GetCertificateStatus(mediaKeySystem, &certStatus);
   // ...
   ```

8. （可选）生成设备DRM证书请求与处理设备DRM证书响应。

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
   // 应用通过网络请求将设备DRM证书请求传到DRM服务获取响应keySystemResponse，请按实际数据传入。
   unsigned char keySystemResponse[MAX_DRM_PROVISION_BUF_SIZE] = {0x00};
   ret = OH_MediaKeySystem_ProcessKeySystemResponse(mediaKeySystem, keySystemResponse, sizeof(keySystemResponse));
   // ...
   ```

9. （可选）获取设备支持的最大内容保护级别。

   <!-- @[drm_getMaxContentProtectionLevel](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   DRM_ContentProtectionLevel level = CONTENT_PROTECTION_LEVEL_UNKNOWN;
   ret = OH_MediaKeySystem_GetMaxContentProtectionLevel(mediaKeySystem, &level);
   // ...
   ```

10. 创建MediaKeySession实例。

    <!-- @[drm_createMediaKeySession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
    
    ``` C++
    DRM_ContentProtectionLevel securityLevel = CONTENT_PROTECTION_LEVEL_SW_CRYPTO;
    ret = OH_MediaKeySystem_CreateMediaKeySession(mediaKeySystem, &securityLevel, &mediaKeySession);
    // ...
    ```

11. （可选）设置MediaKeySession事件监听回调。

    <!-- @[drm_bindMediaKeySessionCallback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
    
    ``` C++
    OH_MediaKeySession_Callback sessionCallback = { SessionEventCallBackWithObj, SessionKeyChangeCallBackWithObj };
    ret = OH_MediaKeySession_SetCallback(mediaKeySession, &sessionCallback);
    // ...
    ```

12. （可选）查询是否需要安全解码。

    <!-- @[drm_requireSecureDecoderModule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
    
    ``` C++
    bool requireSecureDecoder = false;
    ret = OH_MediaKeySession_RequireSecureDecoderModule(mediaKeySession, mimeType, &requireSecureDecoder);
    // ...
    ```

13. 生成媒体密钥请求与处理媒体密钥响应，以请求许可证完成DRM节目授权。

    <!-- @[drm_generateMediaKeyRequest](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
    
    ``` C++
    DRM_MediaKeyRequest mediaKeyRequest;
    DRM_MediaKeyRequestInfo info;
    // initData对应媒体流中的PSSH数据，请按实际数据传入。
    unsigned char initData[512] = {0x00};
    memset(&info, 0, sizeof(DRM_MediaKeyRequestInfo));
    info.initDataLen = sizeof(initData);
    info.type = MEDIA_KEY_TYPE_ONLINE; // MEDIA_KEY_TYPE_ONLINE：在线媒体密钥请求；MEDIA_KEY_TYPE_OFFLINE：离线媒体密钥请求。
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
    // 应用通过网络请求DRM服务获取媒体密钥响应mediaKeyResponse，请按实际数据传入。
    unsigned char mediaKeyId[128] = {0x00};
    int32_t mediaKeyIdLen = 128;
    unsigned char mediaKeyResponse[MAX_DRM_MEDIA_KEY_RESPONSE_BUF_SIZE] = {0x00};
    int32_t mediaKeyResponseLen = MAX_DRM_MEDIA_KEY_RESPONSE_BUF_SIZE;
    ret = OH_MediaKeySession_ProcessMediaKeyResponse(mediaKeySession, mediaKeyResponse,
        mediaKeyResponseLen, mediaKeyId, &mediaKeyIdLen);
    // ...
    ```

14. （可选）恢复离线媒体密钥。

    <!-- @[drm_restoreOfflineMediaKeys](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
    
    ``` C++
    ret = OH_MediaKeySession_RestoreOfflineMediaKeys(mediaKeySession, mediaKeyId, mediaKeyIdLen);
    // ...
    ```

15. （可选）检查媒体密钥状态。

    <!-- @[drm_checkMediaKeyStatus](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
    
    ``` C++
    DRM_MediaKeyStatus mediaKeyStatus = {0};
    ret = OH_MediaKeySession_CheckMediaKeyStatus(mediaKeySession, &mediaKeyStatus);
    // ...
    ```

16. （可选）获取离线媒体密钥标识列表、获取离线媒体密钥状态与清除离线媒体密钥。

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

17. 销毁MediaKeySession实例。

    <!-- @[drm_destroyMediaKeySession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
    
    ``` C++
    ret = OH_MediaKeySession_Destroy(mediaKeySession);
    // ...
    ```

18. 销毁MediaKeySystem实例。

    <!-- @[drm_destroyMediaKeySystem](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
    
    ``` C++
    ret = OH_MediaKeySystem_Destroy(mediaKeySystem);
    // ...
    ```