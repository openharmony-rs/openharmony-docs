---
kits: ["Drm Kit / Digital Rights Management Services", "Media Kit / Media Services"]
description: "Describes combining DRM Kit and Media Kit ArkTS APIs to play DRM-encrypted content through AVPlayer for copyright-protected audio and video playback in apps."
keywords: [DRM, AVPlayer, ArkTS, DRM content playback, media keys, mediaKeySystemInfoUpdate, MediaKeySession, content decryption]
doctype: guide
status: active
---
# DRM Playback with AVPlayer (ArkTS)

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=df601d4dba6b4a39196e7a57e3dfef1b2e9b742e translatedAt=2026-11-02T02:33:31.187Z pushedAt=2026-11-02T02:33:31.187Z nl=1 -->

To play DRM-protected content using AVPlayer, you can use the ArkTS APIs provided by DRM Kit and Media Kit.

## How to Develop

1. Import the DRM Kit and Media Kit modules.

   <!-- @[avplayer_import_kits](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/AVPlayerDrm.ets) -->
   
   ``` TypeScript
   import { drm } from '@kit.DrmKit';
   import { media } from '@kit.MediaKit';
   ```

2. Import the BusinessError module to handle error codes from DRM Kit APIs.

   <!-- @[avplayer_import_business_error](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/AVPlayerDrm.ets) -->
   
   ``` TypeScript
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

3. Call [createAVPlayer](../../reference/apis-media-kit/arkts-apis-media-f.md#mediacreateavplayer9) to create an AVPlayer instance and set a DRM information listener.

   <!-- @[avplayer_initPlayer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/AVPlayerDrm.ets) -->
   
   ``` TypeScript
   private playerHandle?: media.AVPlayer;
   
   async initPlayer(): Promise<void> {
     this.playerHandle = await media.createAVPlayer();
     this.playerHandle.on('mediaKeySystemInfoUpdate', async (mediaKeySystemInfo: drm.MediaKeySystemInfo[]) => {
       console.info('player has received drmInfo signal: ' + JSON.stringify(mediaKeySystemInfo));
       // Process the DRM information, create MediaKeySystem and MediaKeySession instances based on its uuid, and request and process media keys.
       try {
         await this.processDrmInfo(mediaKeySystemInfo);
       } catch (err) {
         const e = err as BusinessError;
         console.error(`processDrmInfo failed, code: ${e.code}, message: ${e.message}`);
       }
     });
   }
   ```

4. Call [createMediaKeySystem](../../reference/apis-drm-kit/arkts-apis-drm-f.md#drmcreatemediakeysystem) and [createMediaKeySession](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySystem.md#createmediakeysession-1) to create MediaKeySystem and MediaKeySession instances based on the UUID in the DRM information.

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
       // Obtain mimeType from the track information of the playback content (for example, using AVPlayer.getTrackDescription()) or from the known media source.
       // drm.MediaKeySystemInfo has no mimeType field, so it cannot be obtained directly from drmInfoArr[i].
       const mimeType: string = 'video/mp4';
       const isSupported: boolean = drm.isMediaKeySystemSupported(solutionName, mimeType);
       if (isSupported) {
         this.mediaKeySystem = drm.createMediaKeySystem(solutionName);
         this.mediaKeySession = this.mediaKeySystem.createMediaKeySession();
         // Request and process the media key.
         await this.processMediaKey(drmInfoArr[i].pssh, mimeType);
       }
     }
     // Set the decryption session after requesting and processing the media keys.
     this.setDecryptionConfig();
   }
   ```

5. Call [generateMediaKeyRequest](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySession.md#generatemediakeyrequest) to generate a media key request, and call [processMediaKeyResponse](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySession.md#processmediakeyresponse) to process its response.

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
       // Send licenseRequest.data returned by the media key request to the DRM service through a network request and process the response.
       const licenseResponse = new Uint8Array([0x00, 0x00, 0x00, 0x00]); // Example response data.
       await this.mediaKeySession.processMediaKeyResponse(licenseResponse);
     } catch (err) {
       const e = err as BusinessError;
       console.error(`generateMediaKeyRequest or processMediaKeyResponse failed, code: ${e.code}`);
     }
   }
   ```

6. Call [requireSecureDecoderModule](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySession.md#requiresecuredecodermodule) and [setDecryptionConfig](../../reference/apis-media-kit/arkts-apis-media-AVPlayer.md#setdecryptionconfig11) to set the decryption session after the media key response is successfully processed.

   <!-- @[avplayer_setDecryptionConfig](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/AVPlayerDrm.ets) -->
   
   ``` TypeScript
   setDecryptionConfig(): void {
     if (this.playerHandle === undefined || this.mediaKeySession === undefined) {
       return;
     }
     // Obtain the codec MIME type (for example, video/avc) from the track information and pass it to requireSecureDecoderModule.
     const svp: boolean = this.mediaKeySession.requireSecureDecoderModule('video/avc');
     this.playerHandle.setDecryptionConfig(this.mediaKeySession, svp);
   }
   ```

7. Destroy the AVPlayer instance and destroy the MediaKeySession and MediaKeySystem instances based on the released event.

   <!-- @[avplayer_releasePlayer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/AVPlayerDrm.ets) -->
   
   ``` TypeScript
   async releasePlayer(): Promise<void> {
     if (this.playerHandle === undefined) {
       return;
     }
     // Destroy the AVPlayer instance, then destroy the MediaKeySession and MediaKeySystem instances in the released event callback.
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
