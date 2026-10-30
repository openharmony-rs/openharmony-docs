---
kits: ["Drm Kit / 数字版权保护服务", "Media Kit / 媒体服务"]
description: "介绍如何结合DRM Kit与Media Kit的ArkTS接口，通过AVPlayer实现DRM加密节目的播放，适用于应用层播放版权保护音视频内容的场景。"
keywords: [DRM, AVPlayer, ArkTS, DRM节目播放, 媒体密钥, mediaKeySystemInfoUpdate, MediaKeySession, 节目解密]
doctype: guide
status: active
---
# 基于AVPlayer播放DRM节目(ArkTS)

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->

开发者可以调用DRM Kit和Media Kit的ArkTS接口实现AVPlayer播放器，完成DRM节目播放。

## 开发步骤

1. 导入DRM Kit和Media Kit接口。

   <!-- @[avplayer_import_kits](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/AVPlayerDrm.ets) -->
   
   ``` TypeScript
   import { drm } from '@kit.DrmKit';
   import { media } from '@kit.MediaKit';
   ```

2. 导入BusinessError模块抛出Drm Kit接口的错误码。

   <!-- @[avplayer_import_business_error](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/AVPlayerDrm.ets) -->
   
   ``` TypeScript
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

3. 调用[createAVPlayer](../../reference/apis-media-kit/arkts-apis-media-f.md#mediacreateavplayer9)，创建AVPlayer实例并设置DRM信息监听事件。

   <!-- @[avplayer_initPlayer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/AVPlayerDrm.ets) -->
   
   ``` TypeScript
   private playerHandle?: media.AVPlayer;
   
   async initPlayer(): Promise<void> {
     this.playerHandle = await media.createAVPlayer();
     this.playerHandle.on('mediaKeySystemInfoUpdate', async (mediaKeySystemInfo: drm.MediaKeySystemInfo[]) => {
       console.info('player has received drmInfo signal: ' + JSON.stringify(mediaKeySystemInfo));
       // 处理DRM信息，根据DRM信息中的uuid创建MediaKeySystem与MediaKeySession实例，并完成媒体密钥请求与处理。
       try {
         await this.processDrmInfo(mediaKeySystemInfo);
       } catch (err) {
         const e = err as BusinessError;
         console.error(`processDrmInfo failed, code: ${e.code}, message: ${e.message}`);
       }
     });
   }
   ```

4. 调用[createMediaKeySystem](../../reference/apis-drm-kit/arkts-apis-drm-f.md#drmcreatemediakeysystem)和[createMediaKeySession](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySystem.md#createmediakeysession-1)根据DRM信息中的uuid创建MediaKeySystem和MediaKeySession实例。

   <!-- @[avplayer_processDrmInfo](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/AVPlayerDrm.ets) -->
   
   ``` TypeScript
   private mediaKeySystem?: drm.MediaKeySystem;
   private mediaKeySession?: drm.MediaKeySession;
   
   async processDrmInfo(mediaKeySystemInfo: drm.MediaKeySystemInfo[]): Promise<void> {
     const drmInfoArr: drm.MediaKeySystemInfo[] = mediaKeySystemInfo;
     for (let i = 0; i < drmInfoArr.length; i++) {
       console.info('drmInfoArr - uuid: ' + drmInfoArr[i].uuid);
       console.info('drmInfoArr - pssh: ' + drmInfoArr[i].pssh);
       const description: drm.MediaKeySystemDescription[] = drm.getMediaKeySystems();
       let solutionName: string = 'com.clearplay.drm';
       for (let item of description) {
         if (drmInfoArr[i].uuid == item.uuid) {
           solutionName = item.name;
         }
       }
       // 实际开发中应从播放内容的轨道信息（如AVPlayer.getTrackDescription()）或已知媒体源获取mimeType。
       // drm.MediaKeySystemInfo不包含mimeType字段，无法直接从drmInfoArr[i]获取。
       const mimeType: string = 'video/mp4';
       const isSupported: boolean = drm.isMediaKeySystemSupported(solutionName, mimeType);
       if (isSupported) {
         this.mediaKeySystem = drm.createMediaKeySystem(solutionName);
         this.mediaKeySession = this.mediaKeySystem.createMediaKeySession();
         // 媒体密钥请求与处理。
         await this.processMediaKey(drmInfoArr[i].pssh, mimeType);
       }
     }
     // 媒体密钥请求与处理后，设置解密session。
     this.setDecryptionConfig();
   }
   ```

5. 调用[generateMediaKeyRequest](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySession.md#generatemediakeyrequest)生成媒体密钥请求，并调用[processMediaKeyResponse](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySession.md#processmediakeyresponse)处理媒体密钥响应。

   <!-- @[avplayer_processMediaKey](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/AVPlayerDrm.ets) -->
   
   ``` TypeScript
   async processMediaKey(pssh: Uint8Array, mimeType: string): Promise<void> {
     if (this.mediaKeySession === undefined) {
       return;
     }
     const initData: Uint8Array = new Uint8Array(pssh);
     const optionsData: drm.OptionsData[] = [{
       name: 'optionalDataName',
       value: 'optionalDataValue'
     }];
     try {
       const licenseRequest = await this.mediaKeySession.generateMediaKeyRequest(
         mimeType, initData, drm.MediaKeyType.MEDIA_KEY_TYPE_ONLINE, optionsData);
       console.info('generateMediaKeyRequest success, type: ' + licenseRequest.mediaKeyRequestType);
       // 将媒体密钥请求返回的licenseRequest.data通过网络请求发送给DRM服务获取媒体密钥响应，并处理。
       const licenseResponse = new Uint8Array([0x00, 0x00, 0x00, 0x00]); // 媒体密钥响应。
       await this.mediaKeySession.processMediaKeyResponse(licenseResponse);
     } catch (err) {
       const e = err as BusinessError;
       console.error(`generateMediaKeyRequest or processMediaKeyResponse failed, code: ${e.code}`);
     }
   }
   ```

6. 调用[requireSecureDecoderModule](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySession.md#requiresecuredecodermodule)和[setDecryptionConfig](../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#setdecryptionconfig11)，在处理媒体密钥响应成功后设置解密session。

   <!-- @[avplayer_setDecryptionConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/AVPlayerDrm.ets) -->
   
   ``` TypeScript
   setDecryptionConfig(): void {
     if (this.playerHandle === undefined || this.mediaKeySession === undefined) {
       return;
     }
     // 实际开发中应从轨道信息获取codec mime type（如video/avc），再传入requireSecureDecoderModule。
     const svp: boolean = this.mediaKeySession.requireSecureDecoderModule('video/avc');
     this.playerHandle.setDecryptionConfig(this.mediaKeySession, svp);
   }
   ```

7. 销毁AVPlayer实例并根据released事件监听销毁MediaKeySession和MediaKeySystem实例。

   <!-- @[avplayer_releasePlayer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/AVPlayerDrm.ets) -->
   
   ``` TypeScript
   async releasePlayer(): Promise<void> {
     if (this.playerHandle === undefined) {
       return;
     }
     // 销毁AVPlayer实例，并根据released事件监听销毁MediaKeySession和MediaKeySystem实例。
     this.playerHandle.on('stateChange', async (state: string, reason: media.StateChangeReason) => {
       if (state == 'released') {
         this.mediaKeySession?.destroy();
         this.mediaKeySystem?.destroy();
         this.mediaKeySession = undefined;
         this.mediaKeySystem = undefined;
         this.playerHandle = undefined;
         // ...
       }
     });
     await this.playerHandle.release();
   }
   ```
