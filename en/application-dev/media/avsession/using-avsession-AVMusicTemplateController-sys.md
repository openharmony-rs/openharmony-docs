# Audio Template Overview (for System Applications Only)

<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_gyH0B0hP-->
<!--Designer: @ccfriend-->
<!--Tester: @chen-gong1-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=444d4b7458e1317b3c2f1a471488b9c4b8344c2e translatedAt=2026-06-03T06:22:29.036Z pushedAt=2026-06-03T10:01:42.987Z -->

Starting from API version 23, you can create an audio template controller to provide unified UI management (playlists, favorites, media details, etc.) and media playback control (play, pause, search, favorite, etc.) for other media applications that have accessed the audio template. This document introduces the system interface capabilities of the audio template and the basic development process, including listening for media applications accessing the audio template, querying media application service data, and sending operation commands to media applications. For media application access, refer to the document [Using Audio Template](using-avsession-AVMusicTemplate.md).

The audio template supports both audio and video content, and the access method is the same for both. This document uses the audio scenario as an example for description.

> **NOTE**
>
> This feature is only supported in Car device projects with API version 23 or later. When creating a project, select "Car" in Device type.

## Basic Concepts

Audio template (AVMusicTemplate): A class that describes the capabilities related to audio templates. It contains attributes such as the ID (sessionId) identifying the current media session and the session tag (sessionTag), as well as methods for data interaction with the playback control center (system application). Media applications can report media-related information to the playback control center and respond to operation commands from the playback control center through the audio template.

Audio template controller (AVMusicTemplateController): A class that describes the capabilities related to the audio template controller. It contains attributes such as the ID (sessionId) identifying the media session and whether the audio template controller has been destroyed (isDestroy), as well as methods for data interaction with media applications. For media applications that have accessed the audio template, the playback control center can obtain media application data through the audio template controller for page display and deliver user commands to the media application.

## Available APIs

For detailed API descriptions, refer to [AVMusicTemplateController](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplateController.md).

## How to Develop

The basic steps for developing the audio template system are as follows:

1. Create an audio template controller (create one audio template controller for each media application that accesses the audio template; do not create duplicates), listen for audio template creation and destruction states, and synchronously create and destroy the audio template controller. The following APIs are required:

   - [createAVMusicTemplateController](../../reference/apis-avsession-kit/js-apis-avMusicTemplate-sys.md#avmusictemplatecreateavmusictemplatecontroller): Creates an audio template controller. Requires the sessionId parameter.

   - [getAllAVMusicTemplateDescriptors](../../reference/apis-avsession-kit/js-apis-avMusicTemplate-sys.md#avmusictemplategetallavmusictemplatedescriptors): Obtains all audio template descriptors. Since a media application may create an audio template before the process starts, the sessionId cannot be obtained through the audio template creation event. You can obtain the sessionId through this method after the process starts.

   - [onAVMusicTemplateCreate](../../reference/apis-avsession-kit/js-apis-avMusicTemplate-sys.md#avmusictemplateonavmusictemplatecreate): Listens for audio template creation events.

   - [onAVMusicTemplateDestroy](../../reference/apis-avsession-kit/js-apis-avMusicTemplate-sys.md#avmusictemplateonavmusictemplatedestroy): Listens for audio template destruction events.

   ``` TypeScript
   import { avMusicTemplate } from '@kit.AVSessionKit';

   const TAG: string = 'ControllerManager';

   export class ControllerManager {
     private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
     private currentBundleName: string | undefined = undefined;
     private templateCreateCallback: Callback<avMusicTemplate.AVMusicTemplateDescriptor> =
       (descriptor: avMusicTemplate.AVMusicTemplateDescriptor) => {
         if (this.isInvalid(descriptor)) {
           console.warn(TAG, 'templateCreateCallback: descriptor is invalid');
           return;
         }
         console.info(TAG, `templateCreateCallback, bundleName: ${descriptor.bundleName}`);
         this.createController(descriptor.sessionId, descriptor.bundleName);
       };
     private templateDestroyCallback: Callback<avMusicTemplate.AVMusicTemplateDescriptor> =
       (descriptor: avMusicTemplate.AVMusicTemplateDescriptor) => {
         if (this.isInvalid(descriptor)) {
           console.warn(TAG, 'templateDestroyCallback: descriptor is invalid');
           return;
         }
         if (this.isStringEmpty(this.currentBundleName)) {
           console.warn(TAG, 'templateDestroyCallback: current bundleName is empty');
           return;
         }
         if (this.currentBundleName !== descriptor.bundleName) {
           console.warn(TAG, 'templateDestroyCallback: not current bundleName');
           return;
         }
         this.unregisterListener();
         this.destroyController();
       };

     /**      * Create a template through getAllAVMusicTemplateDescriptors.*/
     public createAvMusicTemplateController(bundleName: string) {
       if (this.isStringEmpty(bundleName)) {
         console.warn(TAG, 'createAvMusicTemplateController: bundleName is empty');
         return;
       }
       this.currentBundleName = bundleName;
       try {
         // This method requires the ohos.permission.MANAGE_MEDIA_RESOURCES permission.
         let descriptors: avMusicTemplate.AVMusicTemplateDescriptor[] = avMusicTemplate.getAllAVMusicTemplateDescriptors();
         if (this.isEmptyArray(descriptors)) {
           console.info(TAG, 'createAvMusicTemplateController: descriptors is empty');
           return;
         }
         for (let descriptor of descriptors) {
           if (descriptor === null || descriptor === undefined) {
             console.warn(TAG, 'createAvMusicTemplateController: descriptor is invalid continue');
             continue;
           }
           if (this.currentBundleName === descriptor.bundleName) {
             this.createController(descriptor.sessionId, descriptor.bundleName);
             return;
           }
         }
       } catch (e) {
         console.error(TAG, `getAllAVMusicTemplateDescriptors failed, errCode: ${e?.code}`);
       }
     };

     private isInvalid<T>(obj: T): boolean {
       return obj === undefined || obj === null;
     }

     private isStringEmpty(str: string | undefined): boolean {
       return str === undefined || str === null || str.trim().length === 0;
     }

     private isEmptyArray<T>(array: T[]): boolean {
       return this.isInvalid(array) || array.length <= 0;
     }

     /**      * Register a template listener.*/
     public registerAVMusicTemplateListener() {
       try {
         // This method requires the ohos.permission.MANAGE_MEDIA_RESOURCES permission.
         avMusicTemplate.onAVMusicTemplateCreate(this.templateCreateCallback);

         // This method requires the ohos.permission.MANAGE_MEDIA_RESOURCES permission.
         avMusicTemplate.onAVMusicTemplateDestroy(this.templateDestroyCallback);
       } catch (e) {
         console.error(TAG, `registerAVMusicTemplateListener: errCode: ${e?.code}`);
       }
     }

     private createController(sessionId: string, bundleName: string) {
       if (this.currentBundleName === null || this.currentBundleName === undefined) {
         console.warn(TAG, 'createController: sessionId is invalid');
         return;
       }
       if (sessionId === null || sessionId === undefined) {
         console.warn(TAG, 'createController: sessionId is invalid');
         return;
       }
       if (bundleName === null || bundleName === undefined) {
         console.warn(TAG, 'createController: bundleName is invalid');
         return;
       }
       if (this.currentBundleName !== bundleName) {
         console.warn(TAG, 'createController: not current bundleName');
         return;
       }
       if (this.controller != undefined) {
         console.warn(TAG, 'createController: controller not undefined');
         return;
       }
       try {
         this.controller = avMusicTemplate.createAVMusicTemplateController(sessionId);
         console.info(TAG, `createController success, bundleName: ${this.currentBundleName}`);
       } catch (e) {
         console.error(TAG, `createController: errCode: ${e?.code}`);
       }
     }

     /**      * Unregister the listener.*/
     public unregisterListener() {
       // Unregister the listener for user information changes.
       this.controller?.offUserInfoChange();
   
       // Unregisters the listener for dialog command changes.
       this.controller?.offDialogCommandChange();
   
       // Unregisters the listener for current track changes.
       this.controller?.offCurrentSingleChange();
   
       // Unregisters the listener for media entity changes.
       this.controller?.offMediaEntitiesChange();
   
       // Unregisters the listener for tab content changes.
       this.controller?.offTabContentChange();
   
       // Unregisters the listener for playlist changes.
       this.controller?.offPlaylistChange();
   
       // Unregisters listening for download media state changes.
       this.controller?.offDownloadMediaEntityStatusChange();
   
       // Unregisters listening for custom element changes.
       this.controller?.offCustomElementsChange();
   
       // Unregisters listening for setting changes.
       this.controller?.offSettingsChange();
   
       // Unregisters listening for reported execution actions.
       this.controller?.offReportExecuteAction();
   
       // Unregisters listening for information that notifies the media center to pull up the specified third-party application interface.
       this.controller?.offExtensionAbilityChange();
     }

     /**      * Destroy the controller.*/
     public destroyController() {
       console.info(TAG, 'destroyController')
       this.controller?.destroy();
       this.controller = undefined;
       this.currentBundleName = undefined;
     }

     /**      * Unregister the template listener.
      */
     public unregisterAVMusicTemplateListener() {
       try {
         avMusicTemplate.offAVMusicTemplateCreate();
         avMusicTemplate.offAVMusicTemplateDestroy();
       } catch (e) {
         console.error(TAG, `unregisterAVMusicTemplateListener: errCode: ${e?.code}`);
       }
     }
   }
   ```

2. The audio template system can query data provided by media applications for UI display. For details about the query APIs, see [AVMusicTemplateController](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplateController.md).

   For example, to display the main screen of the audio template system, you need to first call [queryMainTabs](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplateController.md#querymaintabs) to obtain the main tab data of the media application, and then call [queryMediaTabContent](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplateController.md#querymediatabcontent) to obtain the tab page content of the media application.

   ``` TypeScript
   import { avMusicTemplate } from '@kit.AVSessionKit';

   const TAG: string = 'ControllerManager';

   export class ControllerManager {
     private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

     /**      * Query the main tabs.
      */
     public async queryMainTabs(): Promise<avMusicTemplate.MediaTab[]> {
       let tabs: avMusicTemplate.MediaTab[] = [];
       if (!this.controller) {
         console.info(TAG, 'queryMainTabs: controller is undefined')
         return tabs;
       }
       try {
         console.info(TAG, 'queryMainTabs')
         tabs = await this.controller.queryMainTabs();
       } catch (e) {
         console.error(TAG, `queryMainTabs failed, errCode: ${e?.code}`)
       }
       return tabs;
     }

     /**      * Simulate querying media tab page content.
      *
      * @param tabId Tab page ID.
      */
     public async queryMediaTabContent(tabId: string): Promise<avMusicTemplate.MediaTabContent | undefined> {
       try {
         let tabContent: avMusicTemplate.MediaTabContent | undefined = await this.controller?.queryMediaTabContent(tabId);
         if (tabContent?.errorCode != 0) {
           console.warn(TAG, 'queryMediaTabContent fail')
           return undefined;
         }
         console.info(TAG, 'queryMediaTabContent success')
         return tabContent;
       } catch (e) {
         console.error(TAG, `queryMediaTabContent failed, errCode: ${e?.code}`)
         return undefined;
       }
     }
   }
   ```

3. Send media operation commands. The audio template system sends commands to the media application based on operations. For details about the command APIs, see [AVMusicTemplateController](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplateController.md).

    For example, search-and-play needs to call the [playForSearch](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplateController.md#playforsearch) API to send a search-and-play command to the media application (this API supports both audio and video, but the example uses audio only). For video, replace the member variable of the parameter entity class SearchPlayInfo with videoInfo of the SearchPlayVideoInfo type.

   ``` TypeScript
   import { avMusicTemplate } from '@kit.AVSessionKit';

   const TAG: string = 'ControllerManager';

   export class ControllerManager {
     private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

     /**      * Simulate search-and-play.
      *
      * @returns Promise indicating the operation result.
      */
     public async playForSearch(): Promise<boolean> {
       let command: avMusicTemplate.SearchPlayInfoType = avMusicTemplate.SearchPlayInfoType.PLAY_MUSIC;
       let searchPlayMusicItems: avMusicTemplate.SearchPlayMusicItem[] = [{
         entityId: 'entityId',
         entityName: 'entityName'
       }];
       let searchPlayMusicInfo: avMusicTemplate.SearchPlayMusicInfo = {
         items: searchPlayMusicItems,
         displayName: 'displayName',
         description: 'description'
       };
       let searchPlayInfo: avMusicTemplate.SearchPlayInfo = {
         musicInfo: searchPlayMusicInfo
       };
       try {
         let operResult: avMusicTemplate.OperResult | undefined =
           await this.controller?.playForSearch(command, searchPlayInfo);
         if (operResult?.errorCode != 0) {
           console.warn(TAG, 'playForSearch fail')
           return false;
         }
         console.info(TAG, 'playForSearch success')
         return true;
       } catch (e) {
         console.error(TAG, `playForSearch failed, errCode: ${e?.code}`)
         return false;
       }
     };
   }
   ```

4. In scenarios where data cannot be obtained in real time (such as login and download), the audio template system needs to register listeners to receive data actively synchronized by the media application. For details about the listener APIs, see [AVMusicTemplateController](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplateController.md).

For example, in a scenario where login causes user information changes, you need to register a listener for [onUserInfoChange](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplateController.md#onuserinfochange). This is because when a user scans a QR code to log in on the audio template system UI, only the media application can perceive the login status.

      ``` TypeScript
      import { avMusicTemplate } from '@kit.AVSessionKit';

      const TAG: string = 'ControllerManager';

      export class ControllerManager {
        private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
        private userInfoChangeCallback: Callback<avMusicTemplate.UserInfo> = (userInfo: avMusicTemplate.UserInfo) => {
          console.info(TAG, 'userInfoChangeCallback');
        };
      
        private registerListener() {
          // Register a listener for user information changes.
          this.controller?.onUserInfoChange(this.userInfoChangeCallback);
        }
      }
      ```

5. When the audio template system application exits, promptly cancel event listeners and release resources. For details on unregistering the audio template interface, see [@ohos.multimedia.avMusicTemplate (Audio Template) (System API)](../../reference/apis-avsession-kit/js-apis-avMusicTemplate-sys.md). For details on unregistering event listener interfaces, see [AVMusicTemplateController](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplateController.md).

   ``` TypeScript
   import { avMusicTemplate } from '@kit.AVSessionKit';

   const TAG: string = 'ControllerManager';

   export class ControllerManager {
     private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
     private currentBundleName: string | undefined = undefined;

     /**      * Unregister listeners.
      */
     public unregisterListener() {
       // Unregister the listener for user information changes.
       this.controller?.offUserInfoChange();
   
       // Deregisters the listener for dialog command changes.
       this.controller?.offDialogCommandChange();
   
       // Deregisters the listener for current track changes.
       this.controller?.offCurrentSingleChange();
   
       // Deregisters the listener for media entity changes.
       this.controller?.offMediaEntitiesChange();
   
       // Deregisters the listener for tab content changes.
       this.controller?.offTabContentChange();
   
       // Deregisters the listener for playlist changes.
       this.controller?.offPlaylistChange();
   
       // Unregisters the listener for download media status changes.
       this.controller?.offDownloadMediaEntityStatusChange();
   
       // Unregisters the listener for custom element changes.
       this.controller?.offCustomElementsChange();
   
       // Unregisters the listener for setting changes.
       this.controller?.offSettingsChange();
   
       // Unregisters the listener for reporting execution actions.
       this.controller?.offReportExecuteAction();
   
       // Unregisters the listener for notifying the media center to pull up the specified third-party application interface.
       this.controller?.offExtensionAbilityChange();
     }

     /**      * Destroy the controller.
      */
     public destroyController() {
       console.info(TAG, 'destroyController')
       this.controller?.destroy();
       this.controller = undefined;
       this.currentBundleName = undefined;
     }

     /**      * Unregister template listeners.
      */
     public unregisterAVMusicTemplateListener() {
       try {
         avMusicTemplate.offAVMusicTemplateCreate();
         avMusicTemplate.offAVMusicTemplateDestroy();
       } catch (e) {
         console.error(TAG, `unregisterAVMusicTemplateListener: errCode: ${e?.code}`);
       }
     }
   }
   ```