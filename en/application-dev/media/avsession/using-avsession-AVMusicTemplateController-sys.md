# Audio Template Overview (for System Applications Only)

<!--Kit: AVSession Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @gcw_gyH0B0hP-->
<!--Designer: @ccfriend-->
<!--Tester: @chen-gong1-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=45526eba67080b876eb51af31a33be43ae26f701 translatedAt=2026-07-13T13:20:31.959Z pushedAt=2026-07-21T10:40:10.702Z -->

Starting from API version 23, the audio template capability is supported, which enables a system application to create an audio template controller for unified management of media applications that integrate with the audio template. The controller provides a unified user interface for features such as playlists, favorites, and media details, and supports media playback controls such as play, pause, search, and favorite. This section describes the system APIs for the audio template capability and the basic development workflow, including listening for media applications that integrate with the audio template, querying media data, and sending playback control commands to media applications. For details about media application integration, see [Using the Audio Template](using-avsession-AVMusicTemplate.md).

The audio template supports both audio and video content. Because the integration workflow is the same, this topic uses audio as an example.

> **NOTE**
>
> This feature is only supported in Car device projects running API version 23 or later. When creating a project, select **Car** in **Device type**.

## Basic Concepts

Audio template (`AVMusicTemplate`): A class that encapsulates interactions between a media application and the playback control center. It includes properties such as the current media session ID (`sessionId`) and session tag (`sessionTag`), and provides methods for exchanging data with the playback control center. Media applications use this class to report media information and respond to playback control commands.

Audio template controller (`AVMusicTemplateController`): A class that encapsulates interactions between the playback control center and a media application. It includes properties such as the media session ID (`sessionId`) and whether the controller has been destroyed (`isDestroy`), and provides methods for exchanging data with the media application. For media applications that integrate with the audio template, the playback control center uses this class to obtain media data for UI presentation and send user commands to the media application.

## Available APIs

For detailed API descriptions, see [AVMusicTemplateController](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplateController.md).

## How to Develop

The basic steps for developing the audio template system are as follows:

1. Create an audio template controller for each media application that integrates with the audio template. Each media application requires only one controller instance. Listen for audio template creation and destruction events to create and destroy the corresponding controller as needed. The following APIs are required:

   - [createAVMusicTemplateController](../../reference/apis-avsession-kit/js-apis-avMusicTemplate-sys.md#avmusictemplatecreateavmusictemplatecontroller): Creates an `AVMusicTemplateController`. The `sessionId` parameter is required.

   - [getAllAVMusicTemplateDescriptors](../../reference/apis-avsession-kit/js-apis-avMusicTemplate-sys.md#avmusictemplategetallavmusictemplatedescriptors): Obtains all audio template descriptors. Since a media application may create an audio template before the playback control center starts, the corresponding `sessionId` might not be available through the creation event. After startup, call this API to obtain existing `sessionId` values.

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

     /**
      * Create a template via getAllAVMusicTemplateDescriptors.
      */
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

     /**
      * Register the template listener.
      */
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
         console.warn(TAG, 'createController: currentBundleName is invalid');
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

     /**
      * Unregister the listener.
      */
     public unregisterListener() {
       // Unregister the listener for user information changes.
       this.controller?.offUserInfoChange();
   
       // Unregister the listener for dialog command changes.
       this.controller?.offDialogCommandChange();
   
       // Unregister the listener for current single changes.
       this.controller?.offCurrentSingleChange();
   
       // Unregister the listener for media entity changes.
       this.controller?.offMediaEntitiesChange();
   
       // Unregister the listener for tab content changes.
       this.controller?.offTabContentChange();
   
       // Unregister the listener for playlist changes.
       this.controller?.offPlaylistChange();
   
       // Unregister the listener for download media entity status changes.
       this.controller?.offDownloadMediaEntityStatusChange();
   
       // Unregister the listener for custom element changes.
       this.controller?.offCustomElementsChange();
   
       // Unregister the listener for settings changes.
       this.controller?.offSettingsChange();
   
       // Unregister the listener for reporting execution actions.
       this.controller?.offReportExecuteAction();
   
       // Unregister the listener for notifying the media center to launch the specified third-party application interface.
       this.controller?.offExtensionAbilityChange();
     }

     /**
      * Destroy the controller.
      */
     public destroyController() {
       console.info(TAG, 'destroyController')
       this.controller?.destroy();
       this.controller = undefined;
       this.currentBundleName = undefined;
     }

     /**
      * Unregister the template listener.
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

2. The audio template system can query data provided by the media application for UI display. For details about the query APIs, see [AVMusicTemplateController](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplateController.md).

   For example, to display the main screen of the audio template system, first call [queryMainTabs](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplateController.md#querymaintabs) to obtain the main tab data of the media application, and then call [queryMediaTabContent](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplateController.md#querymediatabcontent) to obtain the tab content of the media application.

   ``` TypeScript
   import { avMusicTemplate } from '@kit.AVSessionKit';

   const TAG: string = 'ControllerManager';

   export class ControllerManager {
     private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

     /**
      * Query the main tabs.
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

     /**
      * Simulate querying media tab content.
      *
      * @param tabId Tab ID.
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

3. Deliver media operation instructions. The audio template system delivers instructions to the media application based on operations. For details about the instruction APIs, see [AVMusicTemplateController](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplateController.md).

   For example, search-and-play requires calling the [playForSearch](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplateController.md#playforsearch) API to deliver a search-and-play instruction to the media application (this API supports both audio and video; the example uses audio only). For video, replace the member variable of the parameter entity class `SearchPlayInfo` with `videoInfo` of the `SearchPlayVideoInfo` type.

   ``` TypeScript
   import { avMusicTemplate } from '@kit.AVSessionKit';

   const TAG: string = 'ControllerManager';

   export class ControllerManager {
     private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;

     /**
      * Simulate search-and-play.
      *
      * @returns Promise type operation result.
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

4. In scenarios where data cannot be obtained in real time (such as login or download), the audio template system needs to register listeners to receive data proactively synchronized by the media app. For details about the listener APIs, see [AVMusicTemplateController](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplateController.md).

   For example, in a scenario where a login causes user information changes, it is necessary to register a listener for [onUserInfoChange](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplateController.md#onuserinfochange). This is because when a user scans a QR code to log in on the audio template system UI, only the media application can perceive the login status.

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

5. When the audio template system application exits, promptly unregister event listeners and release resources. For details about the audio template unregistration API, see [@ohos.multimedia.avMusicTemplate (Audio Template) (System API)](../../reference/apis-avsession-kit/js-apis-avMusicTemplate-sys.md). For details, see [AVMusicTemplateController](../../reference/apis-avsession-kit/arkts-apis-avMusicTemplate-AVMusicTemplateController.md).

   ``` TypeScript
   import { avMusicTemplate } from '@kit.AVSessionKit';

   const TAG: string = 'ControllerManager';

   export class ControllerManager {
     private controller: avMusicTemplate.AVMusicTemplateController | undefined = undefined;
     private currentBundleName: string | undefined = undefined;

     /**
      * Unregister the listener.
      */
     public unregisterListener() {
       // Unregister the listener for user information changes.
       this.controller?.offUserInfoChange();
   
       // Unregister the listener for dialog command changes.
       this.controller?.offDialogCommandChange();
   
       // Unregister the listener for current single changes.
       this.controller?.offCurrentSingleChange();
   
       // Unregister the listener for media entity changes.
       this.controller?.offMediaEntitiesChange();
   
       // Unregister the listener for tab content changes.
       this.controller?.offTabContentChange();
   
       // Unregister the listener for playlist changes.
       this.controller?.offPlaylistChange();
   
       // Unregister the listener for download media entity status changes.
       this.controller?.offDownloadMediaEntityStatusChange();
   
       // Unregister the listener for custom element changes.
       this.controller?.offCustomElementsChange();
   
       // Unregister the listener for settings changes.
       this.controller?.offSettingsChange();
   
       // Unregister the listener for reporting execution actions.
       this.controller?.offReportExecuteAction();
   
       // Unregister the listener for notifying the media center to launch the specified third-party application interface.
       this.controller?.offExtensionAbilityChange();
     }

     /**
      * Destroy the controller.
      */
     public destroyController() {
       console.info(TAG, 'destroyController')
       this.controller?.destroy();
       this.controller = undefined;
       this.currentBundleName = undefined;
     }

     /**
      * Unregister the template listener.*/
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