---
kits: ["Drm Kit / 数字版权保护服务", "AVCodec Kit / 音视频编解码服务"]
description: "介绍如何通过DRM Kit的Native API与AVCodec Kit配合，在C/C++环境下实现DRM加密节目的解密与播放，适用于需要底层编解码集成的DRM场景。"
keywords: [DRM, AVCodec, C/C++, Native API, DRM节目播放, MediaKeySession, 节目解密, 媒体数据解析]
doctype: guide
status: active
---
# 基于AVCodec播放DRM节目(C/C++)

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->

## 功能介绍

开发者可以调用DRM Kit的Native API，完成DRM节目播放。

当前支持的解密能力如下：

| 音频容器规格 | 音频解密类型 |
|----------|:-------|
| mp4      | AAC    |

| 视频容器规格 | 视频解密类型 |
|----------|:------------|
| ts       | AVC(H.264)  |
| mp4      | AVC(H.264)  |
<!--RP1--><!--RP1End-->

**适用场景**

在创建DRM之前，需获取到DRM信息(参考[媒体数据解析](../avcodec/audio-video-demuxer.md#开发步骤)开发步骤第4步)。

## 开发指导

详细的API说明请参考[Drm](../../reference/apis-drm-kit/capi-drm.md)。

参考以下示例代码，完成DRM的全流程，包括：获取设备支持的DRM解决方案的名称和唯一标识的列表、创建MediaKeySystem、创建MediaKeySession、生成媒体密钥请求、处理媒体密钥响应、获取是否需要安全视频解码以及销毁资源。

在应用开发过程中，开发者应按一定顺序调用方法，执行对应操作，否则系统可能会抛出异常或生成其他未定义的行为。具体顺序可参考下列开发步骤及对应说明。

### 在 CMake 脚本中链接动态库

``` cmake
target_link_libraries(sample PUBLIC libnative_drm.so)
```

> **说明：**
>
> 上述'sample'字样仅为示例，此处由调用者根据实际工程目录自定义。
>

## 开发步骤

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

2. 获取设备支持的DRM解决方案名称和唯一标识的列表。

   <!-- @[drm_getMediaKeySystems](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   uint32_t count = 3; // count是当前设备实际支持的DRM插件的个数，用户根据实际情况设置。
   DRM_MediaKeySystemDescription descriptions[3];
   memset(descriptions, 0, sizeof(descriptions));
   Drm_ErrCode ret = OH_MediaKeySystem_GetMediaKeySystems(descriptions, &count);
   // ...
   ```

   获取到设备支持的DRM解决方案的名称和唯一标识的列表后，与DRM信息做匹配，创建对应的DRM解决方案。DRM信息可通过[媒体数据解析](../avcodec/audio-video-demuxer.md#开发步骤)开发步骤第4步获取，

   或者直接解析媒体协议或媒体数据得到DRM解决方案唯一标识及pssh数据以生成DRM信息。

3. 创建MediaKeySystem实例。

   <!-- @[drm_createMediaKeySystem](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   Drm_ErrCode ret = OH_MediaKeySystem_Create(name, &mediaKeySystem);
   if (ret != DRM_ERR_OK || mediaKeySystem == nullptr) {
       // ...
       return log;
   }
   // ...
   ```

4. 创建MediaKeySession实例。

   <!-- @[drm_createMediaKeySession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   DRM_ContentProtectionLevel securityLevel = CONTENT_PROTECTION_LEVEL_SW_CRYPTO;
   ret = OH_MediaKeySystem_CreateMediaKeySession(mediaKeySystem, &securityLevel, &mediaKeySession);
   // ...
   ```

5. 查询是否需要安全解码。

   <!-- @[drm_requireSecureDecoderModule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   bool requireSecureDecoder = false;
   ret = OH_MediaKeySession_RequireSecureDecoderModule(mediaKeySession, mimeType, &requireSecureDecoder);
   // ...
   ```

6. 生成媒体密钥请求与处理媒体密钥响应。

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

   根据需要设置音频解密配置(详见[音频解码开发指南开发步骤](../avcodec/audio-decoding.md#开发步骤)第4步)、设置视频解密配置(详见[视频解码开发指南开发步骤Surface模式](../avcodec/video-decoding.md#surface模式)第4步或[Buffer模式](../avcodec/video-decoding.md#buffer模式)第4步)，实现DRM内容解密。

7. 销毁MediaKeySession实例。

   <!-- @[drm_destroyMediaKeySession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   ret = OH_MediaKeySession_Destroy(mediaKeySession);
   // ...
   ```

8. 销毁MediaKeySystem实例。

   <!-- @[drm_destroyMediaKeySystem](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/cpp/drm_sample.cpp) -->
   
   ``` C++
   ret = OH_MediaKeySystem_Destroy(mediaKeySystem);
   // ...
   ```
