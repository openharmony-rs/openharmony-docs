# DRM Development (ArkTS)

<!--Kit: Drm Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanzhengshi-->
<!--Designer: @chris2981-->
<!--Tester: @xdlinc-->
<!--Adviser: @qin_wei_jie-->
<!-- md-trans-meta sourceCommit=e4b0ca60eae587775eeae97f31ef4d7083b5ebc9 translatedAt=2026-11-04T06:36:58.098Z pushedAt=2026-11-04T06:36:58.098Z nl=1 -->

DRM Kit provides ArkTS APIs for comprehensive digital rights management, covering certificate management, license management, content authorization, and content decryption.

Its implementation is built around two core classes: MediaKeySystem and MediaKeySession. MediaKeySystem handles system-level management of DRM certificates and licenses, as well as the lifecycle of MediaKeySession instances. MediaKeySession, in turn, is responsible for authorizing specific content and enabling its decryption through integration with Media Kit or AVCodec Kit for playback.

## How to Develop

For detailed API descriptions, refer to [@ohos.multimedia.drm](../../reference/apis-drm-kit/arkts-apis-drm.md).

1. Import the DRM Kit module.

   <!-- @[arkts_import_drm](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   import { drm } from '@kit.DrmKit';
   ```

2. Import the BusinessError module to handle error codes from DRM Kit APIs.

   <!-- @[arkts_import_business_error](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   import { BusinessError } from '@kit.BasicServicesKit';
   ```

3. (Optional) Call [getMediaKeySystems](../../reference/apis-drm-kit/arkts-apis-drm-f.md#drmgetmediakeysystems12) to obtain the name and ID list of the DRM solutions supported by the device.

   <!-- @[arkts_getMediaKeySystems](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   const descriptions: drm.MediaKeySystemDescription[] = drm.getMediaKeySystems();
   ```

   If the returned array is empty, no supported DRM solutions are available on the device.

4. (Optional) Call [isMediaKeySystemSupported](../../reference/apis-drm-kit/arkts-apis-drm-f.md#drmismediakeysystemsupported) to check whether the device supports a specific DRM solution based on the name, MIME type, and content protection level.

   <!-- @[arkts_isMediaKeySystemSupported](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   const byName = drm.isMediaKeySystemSupported(DRM_SOLUTION_NAME);
   // ...
   const byMimeType = drm.isMediaKeySystemSupported(DRM_SOLUTION_NAME, MIME_TYPE);
   // ...
   const byLevel = drm.isMediaKeySystemSupported(
     DRM_SOLUTION_NAME, MIME_TYPE, drm.ContentProtectionLevel.CONTENT_PROTECTION_LEVEL_SW_CRYPTO);
   // ...
   ```

   If the return value is **false**, the device does not support the specified DRM solution.

5. Call [createMediaKeySystem](../../reference/apis-drm-kit/arkts-apis-drm-f.md#drmcreatemediakeysystem) to create a MediaKeySystem instance.

   <!-- @[arkts_createMediaKeySystem](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   mediaKeySystem = drm.createMediaKeySystem(DRM_SOLUTION_NAME);
   ```

   If the creation fails, **undefined** is returned, indicating that the device does not support this DRM solution.

6. (Optional) Call [on('keySystemRequired')](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySystem.md#onkeysystemrequired) to set a MediaKeySystem status listener.

   Register the **keySystemRequired** callback to listen for DRM certificate request events. This event is triggered when a DRM certificate is needed. Complete the certificate request and handling process at this point.

   <!-- @[arkts_onKeySystemRequired](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   mediaKeySystem.on('keySystemRequired', (eventInfo: drm.EventInfo) => {
     console.info(`keySystemRequired extra:${eventInfo.extraInfo} data:${eventInfo.info}`);
     // Request and process the DRM certificate.
   });
   ```

7. (Optional) Call [getCertificateStatus](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySystem.md#getcertificatestatus) to obtain the status of the DRM certificate.

   <!-- @[arkts_getCertificateStatus](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   const certificateStatus = mediaKeySystem.getCertificateStatus();
   ```

8. (Optional) Call [generateKeySystemRequest](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySystem.md#generatekeysystemrequest) and [processKeySystemResponse](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySystem.md#processkeysystemresponse) to generate a DRM certificate request and process its response.

   If the DRM certificate status is not **drm.CertificateStatus.CERT_STATUS_PROVISIONED**, generate a DRM certificate request and process its response.

   <!-- @[arkts_generateKeySystemRequest](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   const provisionRequest = await mediaKeySystem.generateKeySystemRequest();
   ```

   <!-- @[arkts_processKeySystemResponse](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   // Send provisionRequest.data to the DRM certificate service over the network to obtain and process the device DRM certificate response.
   const provisionResponse = new Uint8Array([0x00, 0x00, 0x00, 0x00]); // Device DRM certificate response.
   await mediaKeySystem.processKeySystemResponse(provisionResponse);
   ```

9. Call [createMediaKeySession](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySystem.md#createmediakeysession) to create a MediaKeySession instance.

   Create a MediaKeySession instance with the default content protection level of the DRM solution.

   <!-- @[arkts_createMediaKeySession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   mediaKeySession = mediaKeySystem.createMediaKeySession();
   ```

10. (Optional) Set MediaKeySession status listeners.

    Listen for MediaKeySession instance events, including media key request, expiration, validity period updates, and change events.

    - Call [on('keyRequired')](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySession.md#onkeyrequired) to listen for media key request events. Complete the media key request and handling process at this point.

      <!-- @[arkts_onKeyRequired](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

      ``` TypeScript
      mediaKeySession.on('keyRequired', (eventInfo: drm.EventInfo) => {
        console.info(`keyRequired info:${eventInfo.info} extraInfo:${eventInfo.extraInfo}`);
        // Request and process the media key.
      });
      ```

    - Call [on('keyExpired')](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySession.md#onkeyexpired) to listen for media key expiration events.

      <!-- @[arkts_onKeyExpired](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

      ``` TypeScript
      mediaKeySession.on('keyExpired', (eventInfo: drm.EventInfo) => {
        console.info(`keyExpired info:${eventInfo.info} extraInfo:${eventInfo.extraInfo}`);
      });
      ```

    - Call [on('expirationUpdate')](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySession.md#onexpirationupdate) to listen for media key validity period update events.

      <!-- @[arkts_onExpirationUpdate](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

      ``` TypeScript
      mediaKeySession.on('expirationUpdate', (eventInfo: drm.EventInfo) => {
        console.info(`expirationUpdate info:${eventInfo.info} extraInfo:${eventInfo.extraInfo}`);
      });
      ```

    - Call [on('keysChange')](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySession.md#onkeyschange) to listen for media key change events.

      <!-- @[arkts_onKeysChange](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

      ``` TypeScript
      mediaKeySession.on('keysChange', (keyInfo: drm.KeysInfo[], newKeyAvailable: boolean) => {
        for (let i = 0; i < keyInfo.length; i++) {
          console.info(`keysChange keyId:${keyInfo[i].keyId} value:${keyInfo[i].value}`);
        }
      });
      ```

11. (Optional) Call [requireSecureDecoderModule](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySession.md#requiresecuredecodermodule) to check whether secure decoding is required.

    <!-- @[arkts_requireSecureDecoderModule](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    const needSecureDecoder = mediaKeySession.requireSecureDecoderModule(MIME_TYPE);
    ```

12. Call [generateMediaKeyRequest](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySession.md#generatemediakeyrequest) and [processMediaKeyResponse](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySession.md#processmediakeyresponse) to generate a media key request and process its response.

    When DRM information is obtained from protected content, generate a media key request and process its response to acquire a license for content authorization.

    <!-- @[arkts_generateMediaKeyRequest](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    // In an actual app, extract initData from the PSSH box of the media content.
    const initData = new Uint8Array([0x00, 0x01, 0x02, 0x03]);
    // Set optional data.
    const optionalData: drm.OptionsData[] = [{
      name: 'optionalDataName',
      value: 'optionalDataValue'
    }];
    const mediaKeyRequest = await mediaKeySession.generateMediaKeyRequest(
      MIME_TYPE, initData, drm.MediaKeyType.MEDIA_KEY_TYPE_ONLINE, optionalData);
    ```

    <!-- @[arkts_processMediaKeyResponse](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    // Send mediaKeyRequest.data to the DRM service over the network to obtain and process the media key response.
    const mediaKeyResponse = new Uint8Array([0x00, 0x00, 0x00, 0x00]); // Example response data.
    const offlineMediaKeyId = await mediaKeySession.processMediaKeyResponse(mediaKeyResponse);
    ```

13. (Optional) Call [restoreOfflineMediaKeys](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySession.md#restoreofflinemediakeys) to restore offline media keys.

    <!-- @[arkts_restoreOfflineMediaKeys](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    await mediaKeySession.restoreOfflineMediaKeys(offlineMediaKeyId);
    ```

14. (Optional) Call [checkMediaKeyStatus](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySession.md#checkmediakeystatus) to check the status of media keys.

    <!-- @[arkts_checkMediaKeyStatus](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    const keyStatus = mediaKeySession.checkMediaKeyStatus();
    ```

15. (Optional) Call [getOfflineMediaKeyIds](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySystem.md#getofflinemediakeyids) to obtain the IDs of offline media keys, call [getOfflineMediaKeyStatus](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySystem.md#getofflinemediakeystatus) to obtain their status, and call [clearOfflineMediaKeys](../../reference/apis-drm-kit/arkts-apis-drm-MediaKeySystem.md#clearofflinemediakeys) to remove them.

    The media key ID is used for offline media key management.

    <!-- @[arkts_offlineMediaKeyManagement](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    const offlineMediaKeyIds = mediaKeySystem.getOfflineMediaKeyIds();
    if (offlineMediaKeyIds.length > 0) {
      const offlineStatus = mediaKeySystem.getOfflineMediaKeyStatus(offlineMediaKeyIds[0]);
      mediaKeySystem.clearOfflineMediaKeys(offlineMediaKeyIds[0]);
    }
    ```

16. Destroy the MediaKeySession instance.

    Destroy the MediaKeySession instance when decryption is complete and the instance is no longer needed.

    <!-- @[arkts_destroyMediaKeySession](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    mediaKeySession.destroy();
    ```

17. Destroy the MediaKeySystem instance.

    Destroy the MediaKeySystem instance when DRM operations are complete and the instance is no longer needed.

    <!-- @[arkts_destroyMediaKeySystem](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Media/Drm/entry/src/main/ets/pages/Index.ets) -->

    ``` TypeScript
    mediaKeySystem.destroy();
    ```